---
layout: post
title: 5 Reasons Why You Should NOT Rewrite Your System
date: '2018-01-21 22:18:25'
permalink: 5-reasons-why-you-should-not-rewrite-your-system
tags:
- software-rewrite
- software
- refactor
- software-refactoring
---

After many years working in your system, building, tinkering, improving, breaking and reassembling, you decide that what is really needed is a full software rewrite. After all, what can go wrong?

If you were ever involved in a full rewrite project, you know the answer. Absolutely everything can go wrong. 

## Why you think you want it

There's plenty of reasons for developers to advocate for a full software rewrite, but the most common is the software complexity and cost of maintenance. This translates to "the system is so complex/bad written that it is impossible to effectively fix it without rewriting everything".

It actually makes a lot of sense, so much that I've already written a blog post [guaranteeing that your software will be rewritten](http://allanvital.com/your-system-is-born-to-die/). Today I still think that this is the case, but, instead of focusing on full rewrites, **we should strive for more refactoring**.

Emphasis: as a rule of thumb you should never push for a full system rewrite.

## Why you shouldn't do it 

#### 1. The estimates will be wrong by a large margin

[Have I told you how hard it is to give good estimates?](http://allanvital.com/why-estimates-never-work/) In software rewrites, they tend to be even worse than in normal circumstances. The main reason for this is simple: we usually focus on the areas we know that need to be worked, but rarely have a full understanding of important details inside a software (for any real-world system, it is almost impossible to know everything that is happening under the hood).

The estimate problem is even worse in this scenario because, given the approval for a full rewrite, **stakeholders will be extra picky about the project evolution.** Usually, the programmers need to make big promises about dates and results, which will inevitably lead to disappointment and badly managed expectations. 

#### 2. Knowledge and bug fixes will be thrown away

There are two main reasons for "bad written software": the first one is bad design. The second one is bug fixes. Although sometimes it is hard to tell them apart, it is an important distinction in weighing the pros and cons of a full rewrite. It's hard to argue positively for bad design, but even if this is the case, are you sure that the whole system is fundamentally broken, or are there isolated islands of terrible decisions? Because the second one doesn't sound a good excuse for a full rewrite.

Bug fixes, on the other hand, can turn maintenance work harder because it usually brings some trail of code smells, like methods that are larger than they should or extra boolean conditions, making it harder to read the code. This is usually called "bad code", but it is necessary to keep in mind that they also are the knowledge base of your software.

Reading software is a lot harder than writing, that is why sometimes you don't see reason in some code chunk, but simply **throwing it away is throwing real-world time spent** in bug fixing. Also, code running in production is battle-tested code. There is a high chance that given time, you'll need to add the same checks to your new software because things broke in production.

#### 3. Time spent in the rewrite can be focused on the improving of the existing software

So, after arguing your best you got the green light for a full rewrite. How long will it take? Four months? Cool. Just one thing:

**How much can you better the existing software in four months, instead of a full rewrite?**

If your answer is "None!", it means that you know nothing about the project yet.

The first reaction to an old code base is an urgent necessity to rewrite it. This usually happens because we don't know what is what in that project, and rewriting it will bring us to control again. But is it a rational thought? The optimal decision, usually, is to give time to mature the code in your head and try to understand what brought things to the actual state. After this, it is possible to, at least, improve things a little. And if this goes well, improve another little. And them, a little more.

**That's how good software is made/fixed.**

#### 4. You won't bring anything new for clients or stakeholders, even if successful

The hardest part of a rewrite is the idea that you will be working a lot to deliver the very same thing that your customers and stakeholders already got. Of course, there will be some performance improvements or better UI, but the core features and works will (or should) remain similar. It is a rewrite after all. 

Another thing to keep in mind is that, in some projects, **during the time in which you rewrite your software, you are a sitting duck for your competition.** While you rewrite and rewrite, your competitors will keep improving and adding new features. What's keeping your clients in your system: the new beautiful code or built and tested software?

#### 5. It's an endless cycle
Even if you tackled a full rewrite and all goes well and everybody is happy. **What's keeping the next dev in this project to advocate for a full software rewrite again?** How does one end this? 

Can you possibly improve things if you are only rewriting existing features? How much work will it take to keep the legacy working while you build the next big thing? What of the new things to add? Will they be frozen until you finish the new one?

#### Bonus: Never rewrite?

There are, of course, times in which a full rewrite is mandatory. Sometimes the software is too broken, or too complex to maintain that you must fix the plane while it is in the air. The main tips for this are to keep everyone on the same page, showing why it is a good decision and, obviously and as always, manage the expectations. Tinker your estimates and keep an updated backlog of what is left to do. Show how you are improving things in the new software using real-world problems that you are solving (preferably, problems that haunted the legacy one). As long as everyone is aboard the rewrite train, you can be reassured that it was the right decision.

If it is possible to delete and create your project in one month (that is your estimate? It will take six. Believe me), and there is support from upper management and areas outside TI, you should go for it.

But do not say that I did not warn you.