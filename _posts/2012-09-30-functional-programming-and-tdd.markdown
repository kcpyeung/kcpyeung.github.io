---
layout: post
title:  "Functional programming and TDD"
date:   2012-09-30 22:00:16 +0800
categories: programming
---
I'm studying the online course [Functional Programming Principles in Scala](https://class.coursera.org/progfun-2012-001/class/index) by Martin Odersky. At the moment the course is still in week 2. While doing this week's assignment I noticed how TDD helps me understand functional programming better.

When composing Scala functions I find myself making a series of assertions that are very much like assertions I'd make in a unit test. For example, the following function defines a singleton set:

{% highlight scala %}
  def singletonSet(elem: Int): Int => Boolean = {
    def createSingleton(e: Int): Boolean = e == elem
    createSingleton
  }                                               //> singletonSet: (elem: Int)Int => Boolean
  
  val ten = singletonSet(10)                      //> ten  : Int => Boolean = <function1>
  ten(5)                                          //> res0: Boolean = false
  ten(10)                                         //> res1: Boolean = true
{% endhighlight %}

Using ```singletonSet``` it's easy to define ```union```:

{% highlight scala %}
  def union(s: Int => Boolean, t: Int => Boolean): Int => Boolean = {
    def createUnion(e: Int): Boolean = s(e) || t(e)
    createUnion
  }                                               //> union: (s: Int => Boolean, t: Int => Boolean)Int => Boolean
  
  val ten = singletonSet(10)                      //> ten  : Int => Boolean = <function1>
  val six = singletonSet(6)                       //> six  : Int => Boolean = <function1>
  
  val sixOrTen = union(ten, six)                  //> sixOrTen  : Int => Boolean = <function1>
  sixOrTen(6)                                     //> res0: Boolean = true
  sixOrTen(10)                                    //> res1: Boolean = true
  sixOrTen(16)                                    //> res2: Boolean = false
{% endhighlight %}

In my mind when I wrote ```union``` I had in mind a series of assertions that will make the function work - exactly the way I'd think in TDD except that in TDD I'm doing it from the outside of the function whereas in functional programming I'm actually asserting the body of the function. In TDD, using Java for instance, I'd then have to implement the method body in imperative style by creating a new set and adding the two sets passed in as arguments to the new set and returning it.

Obviously the comparison isn't perfect but I find it a helpful guide at the moment. I'm eager to see how the course pans out but so far my gut tells me it's not an easy course. Quite a bit of reading outside the supplied course material to really make progress.

