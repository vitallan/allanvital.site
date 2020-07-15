---
layout: post
title: About Software Estimates
date: '2017-07-22 22:13:44'
permalink: why-estimates-never-work
tags:
- project-management
- estimates
---

There sure is a lot of [talk and work about estimates in software development](https://www.quora.com/Why-are-software-development-task-estimations-regularly-off-by-a-factor-of-2-3). Whether you are in a big company, a small agency or a "one-man army" project, the idea that you can predict how long will it take to build a system is widespread and adopted by all. 

Any management principle or project schedule has it as a bare minimum to operate. This is useful so you can plan in advance, and tackle the projects in a sane order, avoiding obvious trap holes and business errors. In a multiple-team environment, it is used to coordinate the deliverables in a way that one team does not block the other one, therefore mapping the dependencies and fitting the work appropriately.

The only problem is that, in the majority of cases, software estimates are **wrong**. Often, by a large margin.

[It is probably one of the most analyzed problems in the industry](https://www.quora.com/Why-are-software-development-task-estimations-regularly-off-by-a-factor-of-2-3), and yet, one of the most unresolved ones.

### The Elephant in The Room

[Software projects estimates fail hard since the dawn of software](http://calleam.com/WTPF/?tag=examples-of-failed-it-project).

In the old days, with methodologies like Waterfall, this problem was usually lost in the middle of the whole process. It was easy to blame the testers about the time it was taking to find bugs, and easier still to blame operations about the delays occurring during deploy attempts. The segmentation of the whole flow, and the idea that project time consisted mainly of "Coding Phase" kept the specific Feature Estimation problem hidden. Creating cross functional teams to solve this helped in the way of identifying and bringing the flawed process to light, but could do little in a months (or years) long project.

The blooming of Agile, carried by Agile Manifesto, acknowledged this problem and created a lot of ways to deal with it. There are Fibonacci Sequences, T-Shirt Sized User Stories, Sprint Velocity and many others, and the idea of breaking whole projects in a series of small features minimized the problem, because, of course, a missed week estimate is a lot better than a month long one. Another brilliant improvement above the older methods is the reaction and prioritization brought to the table by a clear feature list in the hands of the product owner and stakeholders. Being able to change course during the so called "Building Phase" is, probably, the single most valuable lesson that Agile brought to the software world.

(that we should always be on the "Building Phase" is a matter to another post)

With the sum of cross functional teams, feature slicing and prioritization we were able to bring everyone involved in the process in a way that makes it clear the efforts of software building. With this, we could explain why feature X is taking so long to complete, and why team Y is performing good. The rate of deliveries and the delivered value of each part became clear and more palpable.

However, the real, long time, projects, still miss the deadline. It is so widespread that some companies just don't estimate anymore, and, even with the transparency of the whole process, we still struggle to find any sane method that brings some level (any level) of assertiveness.

### Why Should We Care?

I'm a huge fan of the [Software Craftsman Manifesto](http://manifesto.softwarecraftsmanship.org/). I think that, in the current state of the market, Software Development is closer to art than it is to science. Take ten developers and ask every one of them the same task. Watch as they will come to you in different times, with different questions about the task and completely different solutions, each one with some special weird moving part.

(that is the reason why I think Software Developers, despite the stress, are [usually happy with their occupation](https://www.forbes.com/pictures/mkl45eeilm/no-6-happiest-job-software-developer/#4f7da09b6186). Maybe not happy in their company, but happy with their craft)

This is, obviously, a problem to any serious business. [Planning in advance, and most importantly planning assertively, is the difference between life and death of a company](http://www.nasdaq.com/article/the-importance-of-business-planning-cm59436). This is the current way of calculating budget values, monitoring goals and defining a project success or failure, and failing to do so is what makes the "IT Department" the most complex to run in any kind of industry field.

[Failing to bring any type of real and assertive estimates is an industry wide fail and hurts all sectors that depend on software](https://en.wikipedia.org/wiki/List_of_failed_and_overbudget_custom_software_projects) (in today's world, that is "all sectors"). Solving it, or just improving it a little, would bring us closer to more mature forms of engineering.

(That's why I usually avoid the term "Software Engineer", but that is also a topic for another post)

### Industry Approaches So Far

As said above, the Agile Manifesto addressed this issue and brought some ways to mitigate it. I'll list bellow some of the approaches that I experienced, and my opinion about them.

* **[Fibonacci Points](https://en.wikipedia.org/wiki/Fibonacci_scale_(agile))**: The most raw form of small time estimate. Scrum popularized it. The main problem with this one is that a 13 sized story is not the same than two 5s and one 3 (!). That is why it doesn't help in measuring the team velocity, therefore, failing to bring any type of assertiveness.
* **[Function Points](https://www.codeproject.com/Articles/18024/Calculating-Function-Points)**: This one is really complicated and... well, bad. It calculates a number that symbolizes the complexity of the requirements, based on user inputs and outputs and external interfaces (among other things). Since user inputs are one different from another, and external interfaces are hugely different among each other (try to integrate with a Rest and a Soap web service and tell me how long will each one take) the number always fails. 
* **Stories of same size**: Try to slice your stories all in a similar size so you can take a median of the time spent in each. This way you will know that if a project has X stories, it'll take X * time per story to finish. The tricky part is: "How to slice stories in the same size?"
* **[T Shirt Sizes](https://www.mountaingoatsoftware.com/blog/estimating-with-tee-shirt-sizes)**: More sane than Fibonacci points, because a *M* sized story is not the same size than two *P* sized ones. However this brings two problems: identifying the difference between a *M* and a *G* (and so on) and calculating the appropriate sprint size. Simply put, if your team spent three months doing only *M* sized ones, now that you only have *G*s, how many ones they can tackle this month? 

### Conclusion

There is no simple solution to the problem, but the best way to mitigate it is to break the work in small steps. Personally, I don't like to break it too small, because every story has an overhead in the process (that is, a story that is just a character change will take longer to write and validate than it is worth), but a "less than a week" size is good enough.

In my experience, it is worth to try to break the stories in the same size, or the most close to it possible. The main caveat is that developers will need to help slice the stories, because they are the only ones capable (since they know the system internals). You will also need to be OK with not optimal slices in favor of predictability.

Also, it all come down to expectation management. Make clear to everyone involved the plans and milestones. When stories start to prolong beyond expected, reexamine the problem and estimates. Broadcast the walkthrough. This way, the stakeholders can plan and react accordingly.

It sure doesn't solve the problem, but mitigate it and turns the process in a healthy and transparent one.