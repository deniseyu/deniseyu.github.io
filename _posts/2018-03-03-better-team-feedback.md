---
layout: post
title: An experiment to improve team feedback
---

I've been working at Pivotal Cloud Foundry for the last 16 months. During that
time, I've mostly been an engineer, but am currently putting on a Product
Management hat for a little while! More on that in a future blog post.

Pivotal is a company that spends a lot of time thinking about what good feedback
looks like. Not "feedback" from customers or end users, although that is also
extremely important; I'm talking specifically about peer-to-peer feedback that
is designed to help individual contributors grow as engineers, designers,
product managers, technical writers, and so on.

We have lots of rituals and tools for keeping feedback at the forefront of our
regular work cadence -- way more than I've seen elsewhere so far. For example,
during the first week that someone joins, odds are they'll learn what "TASK"
(Timely, Actionable, Specific, Kind) feedback looks like, either during HR
on-boarding or team on-boarding. We have an internal web application, called
"Feedback" (very creative, I know) that basically provides a nicer interface
than Gmail for giving someone else feedback. Some Labs teams also schedule "speed
dating" feedback sessions, especially with larger client teams. Throughout each
office, volunteers who have longer-term context about the company culture will
also conduct "Core Practice" sessions, with common topics being delivering and
receiving feedback.

Those things vary a bit from one office to the next. One constant is that
everyone has a manager, and a common activity that managers will conduct is to
have 1-to-1s with other members on the team to collect feedback. This feedback
is delivered on a regular cadence, often fortnightly, but it depends on the
individuals' preferences.

I recently worked on a Cloud Foundry Foundation team, which often have engineers
from different companies working together on Open Source codebases. My specific
team was working on the Cloud Foundry Services API, which is the point of
integration between the platform and service brokers. We had three engineers
from Pivotal, and one engineer, Jen, from SUSE who was based out of Nuremberg.
Jen brought up at one point that she had a feedback review session with her
manager coming up, but she hadn't received much formalized feedback from our
team. It seems obvious in retrospect that as Jen didn't work at Pivotal, she
couldn't have a Pivotal manager constantly gathering feedback on her behalf!

This got me thinking. Over one weekend I came up with an experiment to try to
address this deficit. I asked myself, "Why is it the case that only managers
should gather feedback on behalf of their reports?", and "What if we spent a
week playing the role of managers and did this exact exercise, for someone else
on the team?" In a team that has a healthy degree of psychological safety and
shared understanding of what empathetic behavior looks like, I could come up
with no compelling reasons not to at least try.

When we finally found a week when no one was traveling, this was the email I
sent to the team:

> Hi team,
>
> As mentioned at standup this morning, we have a retro item from a long time ago that we'd create time to give each other feedback. This week, we'll be giving each other the gift of feedback by actively collecting feedback on behalf of another team member.
>
> I wrote a sophisticated algorithm to randomly generate who will be collecting for whom:
>
>irb(main):001:0> ['denise', 'matt', 'jen', 'sam', 'alex'].shuffle
=> ["sam", "alex", "matt", "jen", "denise"]
>
>To prevent inner loops, we should each collect feedback for the person after us. So,
>
>- Sam is getting feedback for Alex
>- Alex for Matt
>- Matt for Jen
>- Jen for Denise
>- and Denise for Sam.

>Does that make sense?

>We have all week to gather insights from the rest of the team, and on Friday right after lunch (13:30 - 15:00) we can all deliver the feedback we've collected and synthesized.

>As you're soliciting, offering, and synthesizing feedback, try to keep in mind the TASK model: Feedback should be Timely, Actionable, Specific, and Kind.

>Ready set.... go!

It took a day or so for people to get into the swing of things. Some people
preferred collecting feedback over email or Slack; others booked in 15-minute
chats with others on the team. I personally found the in-person exchanges more
efficient.

The team decided to block out 30 minutes on Friday after standup for everyone to
synthesize the feedback they gathered, and 1.5 hours in the afternoon to deliver
it. Feedback delivery sessions were private 1-to-1s.

#### What did we learn?

Unsurprisingly, that it is really hard to give good feedback to everyone on the
team. The fact that Feedback Week was coming up made us all think harder about
our interactions with each other in the days leading up to it. Some of us
decided to start making time each week to jot down feedback for teammates.

For people who collected on behalf of a Product Manager or anchor, it was also a
good opportunity to read up on what those roles actually entail. I took some
time to research the anchor role by digging through our internal Google Drive.

The light social pressure created by watching everyone else gather feedback,
combined with the constrained timeframe of one week, motivated (at least) me to
prepare to make every feedback gathering conversation as productive as possible.
We learnt a lot about how to improve our own feedback delivery methods from
watching others do it. It's uncommon for non-managers at Pivotal to collect
feedback for others, and I gained more empathy for the managers!

#### Would we do this again?

I would recommend this exercise, but because it's relatively heavy on time
investment, perhaps only once every six months or every quarter. The feedback we
each received was valuable, actionable, and thoughtful.

It's worth pointing out that the bigger the team is, the more time this will
take. 4-6 people is a good number because you can deliver everyone's feedback in
1.5 hours or less, assuming each delivery session takes about 30 minutes. If you
have a bigger team, it may be worth splitting the team into subgroups to assign
collector/recipient pairs. (The reason I wanted to avoid internal loops during
the assignment was to maximize the potential to parallelize the feedback
delivery sessions on the last day.)

I had originally believed that this experiment required a high degree of social
familiarity among the team to work. After I rotated off this team, and two new
team members from yet another company joined, the team ran Feedback Week again --
with great success. I still believe that psychological safety matters, but I'm
now more confident recommending this experiment for teams that are still
storming and norming. If you try this on your team, please tell me how it goes
via [email](http://deniseyu.github.io/about/) or
[Twitter](https://twitter.com/deniseyu21)!
