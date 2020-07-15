---
layout: post
title: Leader Election Using Spring-Boot
date: '2016-11-08 03:53:00'
permalink: leader-election-using-spring-boot
---

Warning: technical post ahead. You may want to take the children out of the room!

Spring-boot took the market by storm in the last years. Spring, as is, [with MVC dependency had already bitten a huge chunk of job posts and online questions](http://www.indeed.com/jobtrends/q-Spring-Framework-q--J2EE-q--Java-EE-q--Java.html?relative=1), but with the Boot simplicity, it practically set the new standart for frameworks in Java language. With it's auto-configuration features and [spring initiatizr](https://start.spring.io/) , projects setup now takes seconds.

But all simplicity comes with a price: It's hard to do some simple customized thing outside the framework. Maybe not hard, but when you become accustomed with blindly easy property setting, all complication gets frustrating. That's how it began my small quest.

I was testing some features for a new project at work and one of the many ideas was to, given a number of spring nodes, without intervention, set one node as a leader to run a background job. Simple as that. It's called [Cluster Leadership Election](https://en.wikipedia.org/wiki/Leader_election), and it's a commom problem in many clusterized environments ([Redis](http://redis.io/topics/sentinel) among others).

Spring philosophy is to keep your server stateless, therefore there's no need for election process, since the n nodes of your application are not exactly clusterized, in the way that they are not aware of each other. It's great for horizontal scalling, and I believe it's one of the "spring ways of life" wich brought it to the top. But in my case, all I wanted was a simple way to keep the nodes aware if they are or not the leader.

Searching the documentation, I've first come across [Leadership Election with Hazelcast Spring Cloud Cluster](https://github.com/spring-cloud/spring-cloud-cluster/tree/master/spring-cloud-cluster-hazelcast), but oops, it's Deprecated in favour of [Spring-Integration](https://projects.spring.io/spring-integration/). I started looking at this one instead, but it was an immense overkill for my use case. I didn't need complex interations between my nodes, neither needed grand integrations between many different protocols. Dead end.

The other way I've found was to use [ZooKeeper](https://zookeeper.apache.org/). It is an awesome project, which has by default the [Leadership Election](https://zookeeper.apache.org/doc/trunk/recipes.html#sc_leaderElection) that I so much needed. But, again, setting up a ZooKeeper cluster seemed a big step to execute something simple. I didn't need service discovery and the many more features it brings to the table. Seemed like a cannon to kill an ant. Discarded.

Besides these two I found... nothing. It was really difficult finding someone with the same problem, and, when I found, they usually built something big and complex, with database tables and the sort. Not the idea of quick and simple that I had in mind.

So, [I built one myself](https://github.com/vitallan/redis-leader-by-lock).

Using redis set to create a lock registry, the idea is: Whoever holds the lock, is the leader. This is somewhat different from other implementation where the oldest node is the leader until shutdown, because the leadership can go from node to node depending on the lock ping and the lock timout, but scratched my itch. It is simple, with easy configuration, reliable and expandable.

[Feel free to use it](https://github.com/vitallan/redis-leader-by-lock).

It's nice to test it in, say, four different terminals. That way you can kill and spawn the proccess and check it's own organization to define the leader and change it. One improvement would be to randomize the fixed delays and check the behaviour. I will do this test in a near future.

Please, oh please, if you find any bug or problem, [let me know](https://github.com/vitallan/redis-leader-by-lock/issues).