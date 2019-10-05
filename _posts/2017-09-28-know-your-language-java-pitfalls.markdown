---
layout: post
title: 'Know Your Language: Java Pitfalls'
date: '2017-09-28 13:45:59'
permalink: know-your-language-java-pitfalls
tags:
- know-your-language
---

*Let's get more technical. 'Know your Language' is a new category in my blog, about Programming Languages and their most common problems in enterprise environments*

According to [Tiobe](https://www.tiobe.com/tiobe-index/) Java is the most used backend programming language of the world. According to [StackOverflow](https://insights.stackoverflow.com/survey/2017#technology), this title goes to Javascript, but Java gets third place. Java and the JVM are also almost omnipresent in mobile, with Android using it as a platform. 

It is adopted by major companies and there are a lot of job openings for it. Also, you can always find some tool or framework that solves that particular problem you are facing, given it's huge history and fame.

It is also extremely verbose, prone to code bloat, low level (compared with newer languages), clunky all around and resource-eating.

I know that all boils down to "there are bad programs in all languages", but I believe that there are design details of each language that puts developers in a easy position to fall down in some traps, specially considering that we usually tend to "follow the guidelines" of the gurus.

Sticking to code and design, let's see what are the most common pitfalls I've seen in Java projects.

#### Complex Build
Pretty simple. You do your clone, access the directory and do a build command
{% highlight java %}
./gradlew build
{% endhighlight %}
And then it fails.

Usually this means an environment dependency or a manually added hosts to run the build or tests. Unless your build actually runs in a single command, you are doing it wrong. 

Gradle is a specially offender in this case because of the easiness to create customized tasks. Avoid overly *romantic* tasks and approaches, like code generation.

#### Thrown Design Patterns

The idea behind a design pattern is somewhat simple: You have a recurrent problem and a design pattern is a known way to solve that problem. Pretty straightforward, Problem leads to Solution. The issues arise when you like one solution and tends to apply it anywhere you see fit (the old ["when all you have is a hammer, everything looks like a nail"](https://en.wikipedia.org/wiki/Law_of_the_instrument)).

Simple example, a Strategy Pattern. In cool words Strategy is a way that enables algorithm selecting at runtime. In common terms, it is used to hide an "if" statement.

**[Wikipedia example:](https://en.wikipedia.org/wiki/Strategy_pattern)**

Interface with price calculation
{% highlight java %}
interface BillingStrategy {
    double getActPrice(final double rawPrice);
}
{% endhighlight %}
First implementation

{% highlight java %}
class NormalStrategy implements BillingStrategy {
    @Override
    public double getActPrice(final double rawPrice) {
        return rawPrice;
    }
}
{% endhighlight %}

Second implementation
{% highlight java %}
class HappyHourStrategy implements BillingStrategy {

    @Override
    public double getActPrice(final double rawPrice) {
        return rawPrice*0.5;
    }

}
{% endhighlight %}

We could have our customer class:
{% highlight java %}
class Customer {
    /* fields */
    public Customer(final BillingStrategy strategy) {
        this.drinks = new ArrayList<Double>();
        this.strategy = strategy;
    }

    public void add(final double price, final int quantity) {
      drinks.add(strategy.getActPrice(price*quantity));
    }

    public void setStrategy(final BillingStrategy strategy) {
        this.strategy = strategy;
    }

}

{% endhighlight %}
And now we can use it neatly:
{% highlight java %}
public class StrategyPatternWiki {

    public static void main(final String[] arguments) {
        Customer firstCustomer = new Customer(new NormalStrategy());

        // Normal billing
        firstCustomer.add(1.0, 1);

        // Start Happy Hour
        firstCustomer.setStrategy(new HappyHourStrategy());
        firstCustomer.add(1.0, 2);
    }
}
{% endhighlight %}

Cool right? How can it be bad? Let's apply this everywhere!

But there is a catch, even in this simple example. How do I know when to use HappyHourStrategy or NormalStrategy? Can I hide this specific if with another strategy? If yes, would it be better than a single if? Maybe, instead of this, I could add in the customer class:

{% highlight java %}
class Customer {
...
    public void add(final double price, final int quantity) {
        drinks.add(floatingPriceCalculator.getCurrentPrice(price*quantity));
    }
...
}
{% endhighlight %}
And then
{% highlight java %}
class FloatingPriceCalculator {
    public double getCurrentPrice(final double rawPrice) {
        if (isHappyHourTime()){
           return rawPrice * 0.5;
        } else {
           return rawPrice;
        }
    }
}
{% endhighlight %}

Is it so bad? You're making the decision in a single IF-ELSE instead of building an indirection layer, and besides it, still in a single point, in case you need to refactor or read it. If this if else grow in number, maybe it is time to refactor, but right now, I think it is good enough.

Design patterns are tools, not the only way to do something.

#### Functional Interface Misuse

Functional interfaces are awesome. It can really make your code more elegant and simple. Let's take a look, using [OReilly](https://www.oreilly.com/learning/java-8-functional-interfaces) as a resource.

{% highlight java %}
@FunctionalInterface
public interface Runnable {
  public void run();
}
{% endhighlight %}

In the old days, we would use it like this:
{% highlight java %}
Thread thread1 = new Thread(new Runnable() {
    @Override
    public void run(){
        System.out.println("Run now!");
    }
});
{% endhighlight %}
With Java8 and Lambdas, the compiler knows that you are calling the single method from the functional interface. 
{% highlight java %}
Runnable task1 = () -> { System.out.println("run you damn!"); };
new Thread(task1).start();
{% endhighlight %}

Neat, right? The "()" syntax is useful because you can just pass the arguments there and the compiler knows the types.

The problems arise when you try to build a DSL for fluent language with this, because nowadays you see things like:
{% highlight java %}
maClass.needDoThis()
       .AndThis()
       .withALittleBitOfThis()
       .andNowDone();
{% endhighlight %}
And to build this, you create a single functional interface for each of the dots, like this:
{% highlight java %}
public interface AndThis {
    LittleBitOfThis andThis();
}
public interface LittleBitOfThis {
    AndThis withALittleBitOfThis();
}
public interface NowDone {
    void andNowDone();
}
{% endhighlight %}
And in maClass.needDoThis() you get:
{% highlight java %}
public class MaClass{
    public void needDoThis() {
        () -> () -> () -> {
           //do a lot of things
        }
    }
}
{% endhighlight %}
I've seen it more than once. Don't do this. You created a lot of complication just to make a pretty oneliner, which, in the end, is just a single method anyway. Wouldn't be easier if you just called the method?

#### Poor (or overused) OO 

I know that this is possible in any OO language, but Java suffers it hard. There's a lot of confusion about concepts like composition over inheritance, or loose coupled parts or plain simple class design, and big problems arise from this confusion.

(Java8 default methods in interfaces made this even more common)

A great smell of bad class design is the `instanceof` operator used a lot. It, of course, has its uses, but always think through when you use it to check if your design is OO adherent. 

A bad example from [StackOverflow](https://stackoverflow.com/a/13292073/3632899):

{% highlight java %}
class Cage {
  public static Cage createCage(Animal animal) {
    if (animal instanceof Dog)
      return new DogHouse();
    else if (animal instanceof Lion)
      return new SteelCage();
    else if (animal instanceof Chicken)
      return new ChickenWiredCage();
    else if (animal instanceof AlienPreditor)
      return new ForceFieldCage();
    else
      return new GenericCage();
  }
}
{% endhighlight %}
You could replace and put the responsibility inside the Animal interface:
{% highlight java %}
interface Animal {
  Cage getCage();
}

class Dog implements Animal {
  ...
  public Cage getCage() {
    return new DogCage();
  }
  ...
}
{% endhighlight %}

(I know, it's just an academic example, but you got the idea)

In the other side of the spectrum, [there's the overly complex class design](https://blog.codinghorror.com/your-code-oop-or-poo/), which should also be avoided.

#### Reflection
Reflection is one of the most powerful features of Java. You can, basically, access anything at runtime, even modify the methods or fields. The majority of frameworks use it to be able to call your code using the conventions of the language (getters and setters. How do you think hibernate fills your fields?).

Again, the problem with it is the layer of abstraction that you put in your code. When you use reflection, your errors will be in runtime, and your IDE will not be able to help you with the "find usages". You are basically on your own.

As a rule of thumb, use Reflection to build frameworks, [because they need to be able to call yet nonexistent code](https://www.quora.com/Whats-the-difference-between-a-library-and-a-framework/answer/Kurt-Guntheroth-1?srid=oiBW). To build your applications, avoid it always.

[There are some examples here, and you can see why it is so bad.](https://examples.javacodegeeks.com/core-java/reflection/java-reflection-example/)

#### Aspect Overuse 

I think that this one is the most "personal" problem, because I see a lot of people praising AOP and the benefits of AspectJ, but I find myself enjoying it less and less as time passes. Right now I wouldn't use it in application code, but, as it is with reflection, it is useful for framework creation.

One of the main reasons why I think it is harmful is for debugging. You came across a legacy system with a bug and you catch a glimpse of the log:

```
2017-05-25 00:22:31.496  INFO 1 --- [Thread-3] maProject.maPackage.maClass1 : Trying to do something
2017-05-25 00:22:31.512  INFO 1 --- [Thread-2] maProject.maPackage.maClass2 : I shoudn't be trying this, but I am nonetheless
2017-05-25 00:22:31.530  INFO 1 --- [Thread-3] maProject.maPackage.maClass3 : Continuing ok, nothing to see here
```

Cool, maClass2 seems to be the aggressor. Then you open the class and don't find the log line. And don't see where maClass1 is calling maClass2. And neither the call to maClass1. Everything is build around aspects, and your whole project is a huge collection of indirection layers, one after another.

Avoid it. It is not harmful to see a `log.info("")` inside your method. 

Sometimes it is better to be straightforward than clever.

#### EJB 2

Just don't. I mean it.
