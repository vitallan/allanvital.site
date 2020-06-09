---
layout: post
title: What is a Unit in Unit Testing?
date: '2020-06-08 19:00:00'
permalink: what-is-a-unit-in-unit-testing
tags:
- unit test
- software
- testing
---

Sometimes I miss the adrenaline of decompiling a jar file (because the source was lost ages ago), adding a feature and putting it back in production. But, believe me, those days sucked.

In the bad old days, people pushed to production without any kind of automated testing. We would just build the features needed, tested locally and copied the files manually to a server, usually after midnight, accompained by pizzas and fear. As our systems got bigger and bigger, it was harder to keep all things working as intended. **Without any kind of regression guaranteeing that what was working before an upgrade was still working after it, there was a real feeling of risk in any small change.**

{% include image.html url="/assets/early-programmer.jpg" description="Real image of an early 2000 software engineer. We were called 'programmers' back then" %}

We can still see these systems working almost by magic in the legacies of big companies, being worked only by those who already tinkered with it, but the approach in the **good** big companies changed. Even in those monstrosities, people usually build some kind of automated tests for safety.

I credit a lot of these improvements in quality to some of the software communities that grew in the last ten years. The ruby on rails community deserves special kudos: in the beginning, projects were usually rated bad if there were less then 100% of test coverage in a rails software. [Today things are more flexible](https://signalvnoise.com/posts/3159-testing-like-the-tsa) (as they should be), but that doesn't mean less careful. The idea that there should be real and useful automated tests in your system is unanimous in any mature software development discussion.

However, the methods differ in definition and implementation, specially in the concept of **unit testing**.

According to wikipedia, ["unit testing is a software testing method by which individual units of source code, sets of one or more computer program modules together with associated control data, usage procedures, and operating procedures, are tested to determine whether they are fit for use"](https://en.wikipedia.org/wiki/Unit_testing).

All nice and cool, we should individually test our units. But the question arise:

## What is a unit?

The purists advocates to test every method, because **in this mindset the method is viewed as a unit**. In Java projects this means something like that:

{% highlight java %}
class CoolEndpoint {
    String getMeAString(); // or should_ReturnMeAString_when_ICallItDamnIt
}
class CoolEndpointTest{
    void getMeAStringTest();
}
/////
class CoolService {
    String getMeBusinessString();
}
class CoolServiceTest{
    void getMeBusinessStringTest();
}
/////
class CoolRepository {
    String findMeAString();
}
class CoolRepositoryTest{
    void findMeAStringTest();
}
{% endhighlight %}

If you got any more layers (like a *ResourceAssembler* or an *Adapter*), these layers should also have specific testing. Even deeper: any method (the *"unit"*) of any layer should have at the bare minimum one test, and the more the better as a rule of thumb.

However, **here be dragons**. In interpreted languages, like Ruby, where you don't have your most trustworthy ally (the compiler), it makes some sense: it's better to catch any kind of errors running your tests than having to run the program and manually check. But I see that, in these scenarios, we are using the automated tests for two different things:

1. **Guaranteing that the code is structuraly correct. The focus here is to check if everything is technically working. Useful for language updates or big refactorings.**
2. **Guaranteing that your business rules are correct, meaning your old and new features are still working as intended after some code change (feature regression testing)**

I know that those two things are important and should be given it's deserved attention, but I think that **what actually consists of a "unit" is only the second type**. The first type is more technichal than business oriented, and sounds more like a type of [Structural Test](https://www.geeksforgeeks.org/structural-software-testing/).

It's possible to cement this position comparing what each test covers going from an interpreted language to a compiled one, because the majority of problems that the first kind checks, the compiler will catch without needing specialized tests.
 
We can go even deeper: with the help of a compiler, structural testing becomes more a nuisanse than actually a helping hand. In a refactoring scenario, they will break, even if the business rules are actually working **and** the code is technically correct, only doubling the work without bringing any kind of real safety.

**That is why I label a "unit" a specific business rule, and test accordingly.**

## How it works

It highly depends on what kind of internal architecture your aplication is built on, but it usually contains some kind of "service" layer, where the business logic is stored. That's a good map of what should we test, but I like to move the important tests to a higher level of abstraction. **Entrypoints or controllers are usually a good interface to test**. These are the points were your application will be stressed and it's "face" to the world. 

To avoid test dependancy, mock all external components (things like database, other applications, caches, queues, etc) and **make your test hit the most external interface.** Hopefully, even in monolithics applications, your system will expose some kind of web service. Use it. If not, well, use your "service" layer. It is not ideal, but good enough.

The idea is simple: given an input, the most external interface you chose should return some output. [Completely black box](https://en.wikipedia.org/wiki/Black-box_testing). If your interface has more than one business-rule, try to create a specific test for each rule, even if it is the same interface. Some people call it ["Component Testing"](https://martinfowler.com/bliki/ComponentTest.html) but it seems the name itself is not widely known or agreed upon.

Yes, these tests are more expensive than the *"method unit test"*, but it is nowhere near the cost of a full integration test, and it gives you all the benefits and almost none of the problems. If you need to refactor all the internal logic, move all the infrastructure, change all the dependencies of the project, if you maintain things working as expected, no test will be broken, **which is the whole idea.** You have full autonomy for refactorings and complete control if your business rules are still being respected.

{% include image.html url="/assets/safety-net.jpg" description="Test safety net!" %}

And, above all, if a business rule changes, you just have to correct the tests, which should now break, **working as intended.**

In java web services, you can focus on tools like [RestAssured](http://rest-assured.io/), which tests and forces your interfaces to maintain their functionality and sanity. Check the below example, where you validate the returned json of a webservice.
{% highlight json %}
{
   "lotto":{
      "lottoId":5,
      "winning-numbers":[2,45,34,23,7,5,3],
      "winners":[
         {
            "winnerId":23,
            "numbers":[2,45,34,23,3,5]
         },
         {
            "winnerId":54,
            "numbers":[52,3,12,11,18,22]
         }
      ]
   }
}
{% endhighlight %}
{% highlight java %}
@Test public void
lotto_resource_returns_200_with_expected_id_and_winners() {

    when().
            get("/lotto/{id}", 5).
    then().
            statusCode(200).
            body("lotto.lottoId", equalTo(5),
                 "lotto.winners.winnerId", hasItems(23, 54));

}
{% endhighlight %}

In applications that also serves html, some kind of functional test ([like selenium](https://www.selenium.dev/)) will be necessary.

### "But tests help us build better method interfaces!"

Yes, this is true. The thing is, if you use your tests to help you tailor your method interfaces, you still can, but it is important to ask: **Will these tests be useful to the project, or simply to help your first version of some method?**

Besides, after some time, the rules of better interfaces are interiorized, and you start doing it almost by feeling. And, like I said above, these black box, high level tests give you the freedom to refactor, in case some internal interface is not optimal.

In the end, these are the kind of tests that offer the flexibility to refactor but with the safety net of business rules being respected.

{% include image.html url="/assets/refactoring.jpg" description="A real photo of me, refactoring some areas of the codebase yesterday" %}

#### References
[The Pragmatic Programmer](https://www.amazon.com.br/Pragmatic-Programmer-Journeyman-Master-English-ebook/dp/B003GCTQAE/)

[Component-based usability testing](https://en.wikipedia.org/wiki/Component-based_usability_testing)

[Unit Testing vs Component Testing](https://www.geeksforgeeks.org/difference-between-component-and-unit-testing/)
