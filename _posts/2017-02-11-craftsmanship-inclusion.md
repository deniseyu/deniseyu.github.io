---
layout: post
title: Craftmanship, Inclusivity, and Community-Building
---

A lot of things have been on my mind lately. Among them, [Sarah Mei's latest thoughts on Twitter about "No True Developer" tribalism](https://twitter.com/sarahmei/status/830030863605735425). She and a few others call out this troubling pattern that has been happening in tech for a really long time, where people who are part of an "in" group publicly make assertions like "You're not a *true developer* if you don't do/know/follow X". As someone who is relatively new to the industry (I started learning to code in September 2014, and have been working professionally since February 2015), I can relate to so much of this. I can't recall how many times I've been in talks nights, hands-on events, or even just casual conversations at a pub, where a variation on this exchange has happened:

> Person A: "I just started learning Ruby"

> Person B: "Ruby is OK, but if you *really* want to learn to program, you should learn C, like all the hardcore programmers."

Substitute "Ruby" and "C" with any other combination of programming languages, frameworks, tools, practices, etc etc. Sometimes it's not even a two-way dialogue: so many talks I've seen have set up "Person A" as a strawman, just so they can spend the entirety of their talk tearing it down and proving why something else is superior and everyone should totally be using that other thing. Sucks if you've been learning "Ruby" the last few months, doesn't it?

*Aside: I'm going to use "Ruby" and "C" as stand-ins throughout this blog post, but I'm not literally referring to these two languages. I don't hate the C programming language (although it might hate me).*

There is a lot of problematic reasoning here, most of all that the basic premise doesn't make sense --  *what the heck is a true developer*? Is it like, passing a test and getting a certificate? Our industry doesn't confer any equivalent to medical licenses, which you could argue differentiate a "true doctor" from a layperson or a medical student. And no... those very-expensive AWS/Docker/Jira/whatever enterprise certifications *don't count*.

From [Jenn Schiffer](https://twitter.com/jennschiffer/status/830062433557499904):

> the "real developer" is a fake idea created by white men to enforce their dominance in an industry of constant learners

I believe that Jenn is fundamentally correct. I believe that these dismissive dialogues that I've witnessed, during my very short time in the tech industry, have done unconscious damage to at least one person's motivation to keep learning and to stick around in the industry. I also believe that the people disproportionately affected are those who don't identify as cisgender, straight, white men.

Two further thoughts before I move on - **(1)** If we grant that there is such a class of concepts that are somehow more "worth" learning, I think that these are inherently moving goalposts, simply because technologies iterate and go into and out of fashion very very quickly, and our priorities are ALWAYS oscillating between "the essentials" and new, shiny things. This is a surefire way to demoralize people who are still learning the basics, and **(2)** I find it difficult to stomach that if I were to go out there and learn "C", that I'd magically be granted admission into the inner circle of "true developers". This was never a choice-of-technology problem, and we should stop pretending that that's our 49th parallel.

This all got me thinking -- what about software craftsmanship communities? I've been hanging around with the London Software Craftsmanship Community for the last year or so, and I've been to a handful of [SoCraTes](http://socratesuk.org/) conferences now. I had a great time at every open space event, learnt loads, and met lots of awesome people.

Some key people in the craftsmanship community have gone to great lengths over the years to emphasize that software craftsmanship is not about writing "perfect" code for the sake of creating something beautiful. It's also not about using a particular technology or language -- all of those decisions are incidental means to an end. It's about learning a set of practices and guidelines so that, as professional software developers who want to do the right thing, we can deliver the best products for our clients, with the same efficiency in six months' time as today. It's essentially a set of practical principles to help avoid the decay of productivity that usually sets in when codebases get too big and/or too old.

This all sounds pretty reasonable. It benefits the client who gets more value for their money, it's good for the industry writ-large if more time is spent solving problems rather than untangling legacy systems, and it's good for the developer because it frees us up to do more interesting, rewarding work.

It's such a valuable proposition in fact, that a lot of companies nowadays are asking candidates to pass interviews that test their working knowledge of various craftsmanship principles, such as Test-Driven Development (and its various flavors, outside-in, bottom-up, etc..),  naming and implementing design patterns, and so on. I work at Pivotal, and [our interview process focuses heavily on TDD and pair-programming skills](http://blog.jonrshar.pe/2016/Dec/05/pivotal-interviews.html). Pivotal is not unique in asking candidates to demonstrate these types of skills.

**When we ask for developers, particularly juniors, to demonstrate craftsmanship-related skills, are we making the "No True Developer" fallacy again**?

On the one hand, this is an important screening mechanism, because TDD, XP, pairing, etc. are things that, at Pivotal, we practice everyday *to the extent that they are embedded characteristics of our culture*, and we need to know that someone is on board before we hire them, right? But on the other hand, I'm confident that these are the key reasons I was able to pass these components of the interview:

- My family had enough financial security to support me while I took three months off of life at the end of 2014 to study at Makers Academy, where [Enrique Comba Riepenhausen](twitter.com/ecomba), a great teacher and a very vocal TDD proponent, was my first coach.
- I live in central London, and I have highly privileged access to some of the best events, conferences, and people who are talking about craftsmanship.
- In my second job, I had the random opportunity to pair with some extremely talented full-timers as well as contractors from Equal Experts who corrected a *lot* of my developed misconceptions about TDD.

These are all incidental circumstances that helped me in immeasurable ways, but they're not easily replicable. As much as I've tried... Enrique cannot be cloned and deployed to help every new programmer. Someone who is self-taught, particularly from a non-traditional background, has lower odds for serendipitous experiences to line up. Also, that last one! I learnt *on the job*! How do you do that without being given a chance?

On yet another hand, these are skills that are not-impossible to learn, and they are valuable and transferrable for reasons that go beyond learning "C" for (arguably) esoteric reasons. Maybe asking for learnable skills such as TDD is more field-leveling than expecting a CS degree. Maybe craftsmanship skills are fundamentally more demanding of interpersonal skills, where people from non-linear backgrounds might start with an advantage. People who've worked in hospitality, for example, cultivate untold levels of patience that I think would translate phenomenally to product development. These soft skill sets surely come across more vibrantly in an interview where you're asked to pair-program rather than to whiteboard a binary tree search.

But let's separate *the value of having the skills* from *skill acquisition* for a minute. I think the problem, and the solution, is broader than hiring and interviewing. My point is also certainly *not* that standards ought to be lowered or scrapped.

I believe that more consideration can be given to *how* we expect people to acquire these skills -- and I'm going to keep picking on TDD because I'm lazy -- what feedback mechanisms are available for beginners to know whether they're practicing the right thing, and if we can create feedback loops that are shorter than "You passed the interview!" or "Come back and talk to us again in six months."

And what about going to meetups? I find that sometimes, craftsmanship meetups, including the LSCC, which I've helped to organize so I am a self-admitted, complicit, bad actor in all of this -- take it for granted that you know what TDD is, you're on board with it, and you just want to learn how to *tweak* your existing expertise. This certainly is not the case for *every* event, but when it IS the case, it isn't approachable for people who don't yet know what the heck TDD is and just want to learn. I think this is a shame, because if we believe that running awesome meetups is a viable way to transfer knowledge, then we need to also examine who is coming to the meetups, and why (or why not).

Last year, I was at a pub with some friends who were successful mid-level developers, but had never been to a craftsmanship-focused meetup or event. It was not because they didn't care about producing good software, but rather, it was because they felt put off by the perceived mentality in these communities of "We are the only enlightened people doing things properly here." Whatever factors fed into that perception, right or wrong, for me there was now evidence that **there is a tribalism problem in software craftsmanship communities**, and *we are not going to grow if we don't address it*. If we do not succeed at creating welcoming spaces, new people with different experiences won't come, and organic knowledge transfer won't happen. If we think that our communities are important places to inspire and train up newer programmers in craftsmanship practices, then this is a problem. We need to think more carefully about who our communities are serving. I don't have any easy solutions here.
