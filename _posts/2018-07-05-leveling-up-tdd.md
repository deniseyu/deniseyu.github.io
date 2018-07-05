---
layout: post
title: How to level up your TDD skills?
---

I get asked pretty often by people who are interested in applying for a role at Pivotal, or a number of other companies
known to value test-first development, "I know about this TDD thing, but how do I know that I'm doing it *right*?"

Of course my first piece of advice is to try to work at a company that values TDD, but that's a chicken-and-egg problem 
if those companies are testing for TDD in the interview process!

This article is an attempt to summarise and categorise the advice that I generally offer to junior developers. All code examples in Ruby using RSpec syntax.

## Be like Gandhi

I like to tell people, "Write the code you want to see in the world." Like Gandhi! If he wrote code.

What this means is, if you're uncertain about the logic and interfaces you need to design, use your test as a safe place to start 
experimenting. I recently implemented a Markov chain kata, where I wrote:

```ruby
expect(MarkovChain.new(input: 'fairytale.txt').predict_next('Once')).to eq('upon')
```

I had no Ruby class at this point, let alone an initialiser or `predict_next` method defined. It didn't matter! Because of this next technique:

## Change the error message with small steps

When I started out with TDD, I viewed writing a test as this annoying tax I had to pay, in order to do the fun stuff: coding spaghetti logic.

But that's missing out on all of the help that the test framework is designed to give you!

If you start out the gate with a bold assertion about the interface you want, then you can incrementally and confidently iterate your way to 
workable, maintainable code. Using the MarkovChain example, I would do the following small steps, running the test suite in between each step:

1. Set up a Ruby class called MarkovChain.
1. Create the `initialize` method with no arguments.
1. Change the `initialize` method to accept a parameter argument called `input`.
1. Add a function called `predict_next` that takes no arguments.
1. Change `predict_next` to take one argument.
1. Hard-code `predict_next` to return the string 'upon'.

Why hard-code? Why not just do the thing? Because of this next technique...

## Slime until you've got an interface

"Sliming" a test means doing the cheekiest, most minimal, most hard-coded thing to make it pass, like:

```ruby
expect(square_root(4)).to eq(2)

def square_root(number)
  2
end
```

This is also the principle behind the [Evil Coder variant of the Global Day of Code Retreat](https://michalplachta.com/2016/11/15/the-best-training-for-programmers/) pairing exercise.

Sliming is useful for giving a "skeleton" to your object. Designing an interface and executing logic are two concerns, and sliming 
tests strategically lets you focus on one at a time. The meaty implementation can and should come next, 
and it should be forced out by more failing test cases. Which brings us to...

## Only write tests that will force the source code to evolve

Imagine you have this test and code:

```ruby
expect(fizzbuzz(14)).to eq(14)

def fizzbuzz(number)
  number
end
```

In this contrived example, a bad test to write next would be `expect(fizzbuzz(13)).to eq(13)`, because it would magically pass.
Never write a new test that will magically pass.

In the "real world", the impact of such a test case would be test code that costs the team extra time to maintain, but doesn't add any value.

## Zero, One, Many

When test-driving a new problem, a good way to drive out the smallest implementation possible is to use a
heuristic called "Zero, One, Many". I probably read about this on the internet at some point, but can't remember
where, so I apologise for lacking citation here. If you happen to know who wrote about this previously, please let me know!

Anyway - "Zero, One, Many" is the idea that you should first test the "zero case", then a very simple "one item" case, then "many items".

For example, if you are doing the [Bowling Kata](https://codingdojo.org/kata/Bowling):

* Zero: Expect the score of a game where zero frames have occurred to total zero points.
* One: Expect the score of a game where one frame has occurred to total the number of points earned in that one frame.
* Many: Expect the score of a game where multiple frames have occurred to the summed number of points in all frames.

For the "many" case here, I would choose simple examples, like adding two frames each containing 3 points.

You could then go on to write test cases involving edge cases, for example, strikes or spares in the context of bowling.

## [Sometimes] Start with an acceptance test and work your way down

If you're working in an actual code base (not a toy problem), then it's useful to write a high-level acceptance test
before writing unit tests. This high-level test serves as your "north star", so just in case refactoring the unit tests 
goes terribly, you can fall back on this test to give you certainty that the source code probably still works.

This probably won't be applicable in most interview situations, though. My brain likes to start wide before diving deep,
so writing this sort of test is an effective way for me to learn the vague boundaries of the system before diving into the details.

I would caveat out loud to my interviewer when writing this sort of test that I might delete this test code later. Integration 
tests are expensive to run, and if I feel confident that the behaviour is tested at the unit level, I would discard the slow and 
expensive tests before committing the code.

-------

I hope this was helpful. Lots of these things didn't "click" for me until I'd been practicing TDD for years.

Feedback and comments are welcome - you can reach me on email or any of those fun social media icons below.

