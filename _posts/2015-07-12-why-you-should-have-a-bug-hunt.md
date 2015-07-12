---
layout: post
title: The Great TSL Bug-Hunting Competition
---

A few months ago, my company upgraded our core application from Rails 3 to Rails
4. Despite the best efforts of the Rails maintainers in making the transition as
   smooth as possible, we still anticipated many subtle bugs and breakages.

Our application has a lot of moving parts, as is the case with most companies
that have a core application. Moreover, every developer was familiar with a few
key parts of the code, but nobody knew 100%. As a result, we were wary of the 
abilities of the dev team alone to think of every edge case that could 
potentially break the application logic.

The solution that we ultimately came up with led to one of the most fun,
productive afternoons during my time at TSL: We held a company-wide
*bug-catching competition*. For one hour, everybody suspended what they were
working on, and tried to produce bugs in the staging environment. These bugs
were logged in a Google Doc to avoid duplication. The winner was promised a
prize, a task which we graciously delegated to our project manager.

There are about twenty people in the company, and everyone interacts with a
different part of the application each day. Even if we didn't find every subtle
crack in the system, the bugs that we found during the Bug Hunting Competition
covered the majority of the application that we used internally and externally.
Twenty combined employee hours is costly, and this idea is probably not suitable
for companies that have more people, but consider whether a QA tester could have
produced as many bugs in half a week of work. Another clear advantage is
twenty fresh sets of eyes, as opposed to one.

The bug hunt was great for a few other reasons. There is often a feeling of
insulation between the product development team and the non-technical team. In
many ways this is good -- in addition to an organizational barrier (i.e. the
project manager and/or scrum master), there ought to be a psychological barrier
so that developers are not constantly having to be the "bad guy" and explain to
their non-technical colleagues why they can't take a feature request over a
water cooler conversation. With the bug hunt, the non-technical parts of the
company were involved in a valuable problem-solving process for the tech team,
and it was a nice reminder that at the end of the day, product ownership extends
beyond the people who write the code. Everyone at a company should take pride in
the product, and helping to find and fix the problems before they reach the
client is a really valuable step -- one that should involve non-technical team
members whenever possible.

All other "business benefits" aside, the competition was also really fun. It was
a nice way to build team solidarity, and people had a lot of fun competing for
the top spot. Although we (hopefully) won't need to upgrade our Rails version
anytime soon, the bug hunt is something we may incorporate into regular business
processes.
