---
layout: post
title: Custom Rails Form Errors Without Gems
---

Everyone who's used Rails knows that a lot of magic is baked into the framework. One part of Rails that I've always been a little mystified with is how form validations work under the hood. Lately, I've had to do a lot of hacking around with forms -- sometimes to change error messages across the entire application, other times only for one particular use-case or one model. There are a couple of gems that make form customization a little bit more user-friendly -- [simple_form](https://github.com/plataformatec/simple_form) is perhaps the most well-known.

However, under certain circumstances (like legacy projects), it may not always be possible to install new gems due to dependency constraints. In this post, I'll cover a few ways to customize form errors with native configurations. I'm assuming you're using Rails 4.

### A simple use-case

Say that you have a model called User, and upon creation, you want to ensure that every user provides her name.

```ruby
class User < ActiveRecord::Base
  validates_presence_of :name
end
```

And the corresponding controller:

```ruby
class UsersController < ApplicationController
  def new
    @user = User.new
  end

  def create
    @user = User.new(user_params)
    if @user.save
      flash[:notice] = 'User successfully created'
    else
      flash[:notice] = 'User not saved'
    end
    render :action => :new
  end

  protected

  def user_params
    params.require(:user).permit(:name)
  end
end
```

This model won't save without some truthy `name` parameter passed in through this basic form view:

```html
<%= form_for @user do |f| %>
  <%= f.text_field :name %>
  <%= f.label :name %>
  <%= f.submit %>
<% end %>
```

You can log out the default errors on the resource the form page:

```html
<% if @user.errors %>
  <% @user.errors.full_messages.each do |msg| %>
    <li><%= msg %></li>
  <% end %>
<% end %>
```

And the error messages appear magically -- `Name can't be blank`. What if you want the error messages to say 'Please provide a name'?

### Understanding the errors hash

Rails models come pre-loaded with an errors hash that picks up on common validations. Some other common validations and the generated error messages:

```ruby
validates_numericality_of :year  # Year is not a number
validates_inclusion_of :name, in: ['Harry', 'Sally']  # Name is not included in list
validates_associated :friendship # Friendships is invalid
```

(One clear case where you might want to override these errors is if you want to validate fields on an associated model via a `has_many` relationship as in the last example there. The Rails pluralization engine isn't clever enough in some cases, which leads to poor user presentation.)

A warning on nested validations, from the docs: "Don't use `validates_associated` on both ends of your associations. They would call each other in an infinite loop."

To override these errors, we need to understand how the errors hash works. If you throw a `binding.pry` (assuming you're using [Pry](https://github.com/rweng/pry-rails), otherwise any other debugger of your choice) right before you render the view, and type `@user.errors.messages` into pry, you'll find something like:

```ruby
@base=#<User id: nil, email: "", created_at: nil, updated_at: nil, name: "", year: nil, archived: nil, description: nil>,
@messages=
 {:"friendships.network"=>["can't be blank"],
  :email=>["can't be blank"],
  :name=>["can't be blank", "is not included in the list"],
  :year=>["can't be blank", "is not a number"],
  :friendships=>["is invalid"]}>
```

If it's a quick change to the text within the values, you can just include an optional message parameter in the validation:

```ruby
validates_presence_of :email, message: 'is required!'
```

Fairly straightforward -- this changes the error message to "Email is required!"

But what if you needed to change the entire sentence? You can get a little closer by using a special type of Rails-specific string interpolation in the formation of the error message:

```ruby
validates_presence_of :email, message: "derp, %{attribute} invalid, do it again."
```

But, as long as you're still logging out `.full_messages`, the message will look funny -- "Email derp, Email invalid, do it again." A few options here... the first is to switch to using `.messages` and stop using the Rails `.full_messages` helper for all of your messages. This might look like the following:

```html
<% @user.errors.messages.values.flatten.each do |msg| %>
  <%= msg %>
<% end %>
```

This looks really horrible for a view though, so it's not a great option. An alternative is to define a custom helper method for only the attribute you want to display custom errors.

### Overriding Rails defaults

To change the error messages, the most granular, although not the most extensible, way is to wrap the output of the error messages in a helper method. It may look something like:

```ruby
module UsersHelper
  def custom_error_messages object
    new_messages = {
      :email => 'Email pls',
      :year => 'Wow year, such number',
      :friendships => 'Such friend, wow'
    }
    object.errors.messages.map {|key, val| new_messages[key]}
  end
end
```

A clear disadvantage to this method is that you will have to constantly keep the hash up-to-date with every validation that exists on the model. If no key exists, there will be `nils` in the result. This can be cumbersome and you risk throwing `nil` exceptions if you call any additional methods on the outputted array.

I haven't found an elegant way to reuse the Rails `.full_messages` helper in the event that a key doesn't exist in the custom hash (without re-engineering it).

If you find your piecemeal error handlers expanding out of control, it might be time to consider using a [service object to handle errors](http://brewhouse.io/blog/2014/04/30/gourmet-service-objects.html).
