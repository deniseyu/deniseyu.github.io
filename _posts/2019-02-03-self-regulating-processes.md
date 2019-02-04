---
layout: post
title: Designing Self-Regulating Processes
---

I am currently reading [*The Manager's Path*](http://shop.oreilly.com/product/0636920056843.do), an
excellent book by [Camille Fournier](https://twitter.com/skamille) that I highly recommend to anyone who's not only considering
becoming an engineering manager or tech lead, but also for anyone who wants to understand how to
be more effective as an individual contributor. One thing that jumped out at me was this paragraph:

> As a new tech lead, be careful of relying on process to solve problems that are a result of 
> communication or leadership gaps on your team. Sometimes a change in process is helpful, but 
> it’s rarely a silver bullet, and no two great teams ever look exactly alike in process, tools, 
> or work style. My other piece of advice is to look for self-regulating processes.
> 
> "Chapter 3. Tech Lead", from The Managers' Path

I immediately liked the phrase "self-regulating process" because my undergraduate degree is in
economics, and I jump at any opportunity to apply economic thinking to practical problem-solving.
Self-regulating processes are tiny cycles of checks and balances, and it's so cool to find them in human systems.

In my tech network, I often hear about process experiments succeeding or failing by the emotional
and/or political bandwidth of the person who initiated the experiment. For example, when introducing
pair-programming to a new group of engineers, it often takes a confident, charismatic person to
coax reluctant teammates to start pairing for the first time. In fact, they might not even call it "pairing"
to begin with -- they'll say, "Hey, do you wanna come over here and have a look at this with me?" But
when that person leaves a company, pairing might fall by the wayside, because it was something driven by
the strength of a personality. These short-lived process innovations are valuable, but they don't last;
so in that context, we never learn how to adjust them, measure them, and scale them.

Self-regulating processes, on the other hand, don't depend on strong personalities in order to persist.
The way that they work is by aligning incentives (both the positive and negative kind) in such a way
that no one person is stuck with the unpleasant task of hassling other people to do their parts.
Micromanagement represents the exact opposite outcome of a self-regulating process.

To understand how to align incentives, let's talk about what incentives *are*. **Positive incentives**
represent net gains for an individual if they behave in a certain manner -- think carrots, not sticks. 
They come in many flavors: financial (ex. wages, stock awards), social (ex. peer recognition), intrinsic
(ex. mastery of a particular skill), to name a few. **Negative incentives** are the opposite: net losses. 
Slight aside: Humans oddly feel more strongly about losing something than gaining something, given the same overall "utility". For example,
when budget airlines used to charge an extra $15 for a hot meal bundled with my ticket price, I never thought twice
about paying it. Now that I'm charged the same $15 on board, for the same meal, I stubbornly endure a very hungry flight. This
phenomenon is called [loss aversion](https://www.behavioraleconomics.com/resources/mini-encyclopedia-of-be/loss-aversion/).

In software engineering companies, and probably in other companies as well, I believe that you can design self-regulating
processes if you stop and think about what incentives are in play. Most people are driven by the positive incentive of
wanting to earn more money, and perhaps wanting a better title. To facilitate that, most people, given that the organization
exhibits more of a [generative culture](https://continuousdelivery.com/implementing/culture/), would agree that receiving
honest and constructive feedback from their peers is a good way to improve their performance.

Most people also have a set of negative incentives that they react to. Many people want to avoid negative
social repercussions and unnecessarily spending social capital. Consider that at
[companies with unlimited vacation policies](https://www.theguardian.com/money/shortcuts/2018/jun/05/the-ugly-truth-about-unlimited-holidays),
people end up taking fewer vacation days than their peers who accrue fixed vacation throughout the year.
This is because a financial incentive structure became replaced by a social incentive structure, and the
social anti-incentives *feel* more costly -- in part, because they're really hard to quantify, and we're
wired to dislike uncertainty. Negative social incentives can interestingly be leveraged even in the absence
of any clear "enforcement mechanism" (in other words, public shaming can't actually happen). 
Hotels have figured out that an effective way to encourage guests to reuse towels is to tell them that
[a high percentage of other guests chose to reuse their towels](https://www.fastcompany.com/3037679/read-about-how-hotels-get-you-to-reuse-towels-everyones-doing-it).

A self-regulating process sets up the right combination
of positive incentives and negative incentives, so that people are intrinsically motivated to follow
the process, and no external encouragement or facilitation is necessarily required once things get underway.
Balancing positive with negative incentives is important: too much negativity, and people will start to
feel fearful; too much positivity and you bank on the assumption that everyone feels equally motivated by the same carrots.
(That often is not true.)

I previously wrote about a process I invented called [Feedback Week](http://deniseyu.github.io/better-team-feedback/).
After reading this chapter and running this process for the first time in the Toronto office, I realized
that Feedback Week is a self-regulating process. Participants are motivated by the positive outcome of
receiving feedback for themselves, and perhaps the opportunity to give the gift of nice feedback to one of
their teammates. At the same time, seeing everyone participate in feedback collection one-to-one meetings
throughout the week creates a gentle negative incentive to not disappoint your feedback recipient.

Since I first ran Feedback Week in the London office, I've learnt that the Services API team (where it all began)
has continued to run it once a quarter. It also spread to the Platform Recovery team, and one person who rotated off
the Services API team is now evangelizing it in a Dublin-based team. This makes me think that another heuristic
of a self-regulating process is that it should be easy to replicate on a new team, without too much cultural context
from previous iterations required.

Have you ever been part of a self-regulating process? I'm curious to learn if examples of these exist elsewhere in the wild.
[Tweet at me](https://twitter.com/deniseyu21) if you have, let's chat!
