---
layout: post
title: What defines a good Software Developer?
date: '2017-09-06 14:44:51'
permalink: what-defines-a-good-software-developer
tags:
- developer-performance
- team-building
---

There are hundreds of interview techniques, thousand of tools, each with a corresponding required knowledge to work with, countless "classic" algorithms and a myriad of different types of projects to try to evaluate a Software Developer. Yet, it is not easy to, nor formally or mathematically, separate a good Developer from a bad one. Why?

As always, there's no easy answer to this question. The main reason for this is, perhaps, that we don't know what a Software Developer actually does. Software creation is not a mechanical task, and, even if it was, writing software, in many cases, is **not** the main assignment of a software developer.

Even identifying this problem is a matter of debate. Saying that the main job of a Software Developer is not to develop software will surely raise a discussion, and I can understand that. But I think the real issue is that, even if we agree with this, we don't know what "develop software" actually is. Is it writing a program? Is it finding the right tool for the task? Is it debugging a system? And, if you answer "All of the above"... well, how do you measure each one of these? If you can't measure, you can't categorically say who is a good Developer. 

#### Levels of education and formal knowledge

One of the most basic ways to filter job applicants is to evaluate their formal knowledge of computer science. That's when we give a test asking things about algorithm complexity or ask some classic sorting problem.

This fails on some levels. Even though knowledge of these is good, there are a lot of jobs in which the applicant would never use it in the company. Why bother asking about merge sort if the main assignment will be a simple CRUD application? Further still, if it's not a pressing issue, why can't you hire and teach?

That kind of evaluation brings the worst type of interview: "Write in the white board a quick sort". If you failed in memorize all those 28 "classic code interview question", you failed.

[I really, really, really hate the idea that you will need to read a book](https://www.amazon.com/Cracking-Coding-Interview-Programming-Questions/dp/098478280X) just to pass in an interview for a job. And, the worst thing is: even if your applicant can solve these problems at point blank, it's not guaranteed that he will perform good with the stack and tool set of your environment.

#### Tooling knowledge

Every software developer worth his salt has some stack or tools in which they are comfortable. Better still, they should have lots of tools in their skill set, because this avoids the common pitfall in which "when your only tool is a hammer, everything looks like a nail".

But, as I said before, [we should always be careful about the right tool for the right job](http://allanvital.com/be-careful-with-the-right-tool-for-the-right-job/). Besides, relaying only in tooling you will miss good fits just because they don't know some of the tools used in your environment.

And when all is said and done, how do you measure if a software developer knows how to use some tool? They might have learned it, read it somewhere, but might fail in actually using it in a real world problem. We go back to the "what actually you do?". 

#### Different performance in different companies

Another problem of the measuring job is that a good Software Developer in company A can be a terrible Software Developer in company B. Even if these companies share the same technological stack. There are countless ways that a company differs from another, and every one of these can hinder the performance of a software developer.

Take a "Good" developer from a big company. He must be able to survive the bureaucracy to bring his problem solving skills to the table. He might not be the brightest coder, but he will be able to thrive and bring results in such environment.

On the other hand, a "Good" developer from a small company will probably need to be fast in delivering features. He might not build the most maintainable systems in the long run, but will surely be the best bet in this scenario.

(both scenarios are completely hypothetical. Any similarity with reality is pure coincidence)

If we exchange the developers, there is a high change that they will be labeled as "Bad" developers in each company, even with equal tooling, stack and technical knowledge. Worse, there is a high change that both will not tolerate the work conditions.

(of course, we could find the so famous "rock star developer" that can operate in every level of any company of any size... but it's a really rare fish)

#### Teams

After we fail to measure what is a good software developer, we reach the next level of difficulty: we usually work in teams, and, even though teams are the sure way to build something sustainable and good, it is also one of the easier ways to go "under the radar". If your team of four developers are delivering good, how can you know which one are performing great and which ones are poorer? This is necessary for a lot of reasons, that goes from training to promotions and raises.

This one is specially hard. If one of the developers commit less code (crappy metric, I know), is it because he is not working right, or is it because he is helping and pairing with the others? Worse still, is he heroically interfacing with the stakeholders and breaking the features in technical tasks? Is he correcting the delivery pipeline? Or is he... bad? (some of these are actually measurable, I know, but in some cases it is not that simple).

Also, teams are organically complex beings. What makes a team good is not easily definable (probably as hard as defining a good software developer), and team members that perform really well in one can be the drawback in another. Does that mean that this player were bad all along, or does this mean that he doesn't fit with the new environment? How can you answer this question?

#### What the hell does a Software Developer actually do?

A ton of things, actually.

In smaller environments (startups mostly) the software developer usually codes and ships a lot. When you are trying to get something out there fast, and your customer base is smaller enough, your main issue is to get new features and improving your product as fast as possible. Probably, your production issues won't eat your whole time, and you might be able to extinguish fires and keep the quick production and shipping dates. In such experience, you will probably be measured in your tickets moved to "done" and your ability to solve production issues quick, in a way that doesn't interfere with your coding speed.

In medium sized companies (I draw the line at 100 employees) you will probably start to lose speed. In most cases, you will need to hire specific operation people for your production outages so that you can keep the developers focused in the tasks. You will also need other specific titles, people that can prioritize the best tasks and efforts, business analysts to understand the idea and plan new directions. Since the environment became more complex, your team will need to, besides the obvious code skills, start communicating with all these areas. It's unfair to ask these people what is easier and faster to do inside your codebase, so, for them to be able to plan correctly, your team will start going to meetings and be able to explain it. Unfortunately you will need to start estimating your stories, which sometimes is overlooked in smaller companies. From coding and fire fighting, you now need people that can help business more closely, oiling the engines of the whole. Your dev team will need to interface with operations also, building solutions together, so the production environment keep sane and maintainable.

For big companies, take the medium size problems and make them even bigger, and throw the famous legacy systems in the scenario. Your dev team will need to get reeeeeally good at documentation and communication and will need to learn the skills to handle the coordination of features delivery, the process needed to organize many teams working on the same code base and the overall complexity of all systems working together. In such an environment, you can see your dev team working in the whole company. Helping in the business decisions, estimating the deliverables and coordinating the the order in which to attack the tasks. Helping in the outages and improving the preventive maintenance to mitigate them. Oh, and also building new features.

Given the huge mutability of the job description, one question comes back. 

#### How do you measure?

It is such a wide array of possibilities that it is almost impossible to mathematically judge who is a good or who is a bad developer. Joe might have fewer commits, but that is because he is teaching the less experienced ones. Julia fails at most of her estimates, but is the quicker to solve production outages. Bill is able to break the product area requests in nice sized histories. Mary is the most resourceful coder. Pan is the best code reviewer.

The only way that worked in my experience, in both measuring the good developers and helping them improve was **constant** feedback, both for pairs, and from the whole team.

#### Feedback 

When it comes to feedback, the closer the better. For a single developer, it's nice to have the feedback from another area, it's important to have the feedback from another team, it's necessary to have feedback from the manager and it's vital to have from her/his pairs. It's the manager job to collect these feedbacks to be able to evaluate her/him, and be able to mentor the individual to better themselves.

I like the 360 feedback format, but it is too time consuming, making it almost impractical as a constant feedback loop. Besides, such a meeting can have a negative impact in more anxious people, therefore it is better to collect the information separately.

For inter areas feedbacks, a message or email is "good enough", if you don't have the time. Send a message and politely ask about the team collaboration. Make it clear that it is for feedback purpose, and that, in this case, more information is better than less.

For another team, message is good, but direct contact is better. Ask them the same questions and be clear about the objective. Take notes about opinions or problems raised.

Inside the team, I like two formats. One open, which is sometimes called "Fast Feedback", where the team meets and, in pairs, say the good points and the "points to be improved" one to another. The other one is closed, the team meets without the evaluated member and lists the same points. That is useful for team members that are too shy to criticize or the "good guys" that, given their social skills, it is hard to point problems face to face.

With all this material in hand, it is possible to schedule one-on-ones meetings with the team members and face the problems or congratulate the performance. It's possible to, even inside a team, assess individual performance. It's a lot more personal than numbers, so there's always chances of errors and mistakes, but it's the closest thing you can get of real world developer performance.
