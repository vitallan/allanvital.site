---
layout: post
title: Your software will be rewritten
date: '2016-02-22 16:00:00'
permalink: your-system-is-born-to-die
---

So, there’s this thing about your system.

It’s born to die.

I’m talking more specifically about the Web Systems, because that’s my area of expertise, but it’s valid for several areas of software development. Systems are created to be destructed in the long run. And that’s okay.

I’ll explain myself.

If you already worked in some big project, or for some years in a company, you already saw what people call Legacy Code. It’s more common known as that code that runs in production for so long that people don’t know anymore how it works. Sometimes these legacy systems hold the very core features of a company, which every other satellite system will depend on. In this case we have some terryfing scenario in play: my “fundamental stone” works, but nobody knows exactly how, and everybody is scared of touching it.

How it happens is somewhat simple:

1. We start with some dev team that build System X
2. Everybody knows everything about X (best case cenario)
3. With new features coming in and members changing (reallocations, retirement, etc), entropy takes place and things get complex
4. X grows in complexity and size, and members don’t know how some parts work
5. Members get scared of touching in some areas of X, fearing the overall impacts (usually the more core and complex features)
6. These “dark areas” grow in number until there are more “fear zones” than “known zones”
7. All development reach really low levels of speed

By the time of 5, some developers might already be claiming that the system must be rewritten. In 7, the overall development speed reaches a terminal point, in which the business value deliveried is almost null and more developers must be hired. Unfortunatelly, these new folks usually make things worse, because of the already chaotic enviroment.

(and by “make things worse” I mean that they usually add layers of abstraction to avoid the “fear zones”, which make things even more complex)

But how can you rewrite your main system? So much time spent in a product to simply “recreate it” doesn’t sound like a good deal.

(banks, until this day, keep puting more money in COBOL because it’s SO HARD and SO EXPENSIVE to try to rewrite their whole systems that they apparently given up trying. I can’t blame them)

Thinking about this problem (and how to solve it) we can see that this behaviour will potentially occur in any system. With the acceleration of technology, a new system might become obsolete in less than an year. I’ve seen recently one been called “legacy” in six months. And yes, sometimes it’s just the eagerness of developers to try new things, but this scenario should be analyzed to check it’s veracity.

With this information in mind, we can reach the next conclusion: in a project that is planned to run for more than a year (I’ll talk about estimates another time :-) ), there is a good possibility that it will be born with the label “legacy” in it. And I mean, any system, not just “system rewrite” projects.

I remember clearly one of my old experiences, where we had been working with some huge old system and, after big arguments and politics, the dev team could get the approval from business to recreate the system. Entirely, from scratch!

I was happy with the decision and it seemed the right path. So I went to talk to one of senior programmers about this, and he just asked me “That’s good… but what’s keeping us from not bumping into the same problem in the future?”, and until this day I don’t know what I could have answered him. I believe that this is one of the greatest questions in commercial software development.

I don’t believe that there’s a way to solve this problem, but I do believe that there are ways to mitigate it. Unit testing goes a long way, but I see it more like a way to help maintenance than to make it easier to rewrite it. I mean, it helps, but if you want to change technology, you will probably throw away the whole suite.

(but I can’t expect to solve anything in a project that doesn’t have unit tests. It’s the bare minimum in a serious project)

I believe that the best strategy is to embrace the rewrite idea. Keeping legacy systems running is really expensive, and hiring people and training them to learn something from an old software is even more expensive. Therefore, I think that embracing the idea is the best way.

“But will l keep rewriting my system all the time? How can I find time to deliver new features?”, I can hear your claims, hipotetical reader, and I understand you.

The middle ground would be: keeping the systems so small that it’s write and rewrite proccess takes, at maximum, weeks, and not years. To reach that scenario, you’ll need to separate your software in a lot of sub-systems, and I’m not talking about component or plugin architecture. The idea is to have an ecossystem of software, ideally communicating through rest to reinforce the idea of loose connected parts, and to force the developers to reach an ideal interface. To keep it all together, you’ll need, besides the unit testing, complex integration tests, which hits every one of those systems. That way, you’ll could simply throw away one and recreate it without a lot of pain, and keep the guarantee that everything else works.

Yes, I’m talking about micro-services architecture.
I believe that, today, with cloud in our reach, this is possible and desirable. We can create and destroy VMs in an automated way and keep the whole ecossystem ok. If you can’t use cloud in a nice way, docker and kubernates can be your best friends. What I mean is that you have tools to think about this implementation.

I understand that micro-services is, today, a buzz word, and if you don’t like it, just call it a service architecture. But the concept is around for quite some time, even the idea of “breaking big problem in a serie of small ones” is the whole core of Object Oriented development. We should think more about it and use this knowledge more often.