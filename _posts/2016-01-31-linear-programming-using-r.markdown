---
layout: post
title:  "Linear programming using R"
date:   2016-01-31 13:47:20 +0800
categories: programming
---
Quoting an example from [Head First Data Analysis](http://www.amazon.com/Head-First-Data-Analysis-statistics/dp/0596153937), the profit of a rubber duck is $5 and that of a rubber fish is $4. The profit, P, is therefore:

```P = 5d + 4f```

The production of a rubber duck uses 100 units of rubber pellet. Fish uses 125 units. Altogether, there is 50,000 units available, limiting production by the following constraint:

```100d + 125f <= 50000```

The objective is to find the numbers for d and f such that P is maximised. Unfortunately, the book uses Excel Solver. Here, I am showing how to solve this using the lpsolve library in R.

First, install and load the package if not already:

{% highlight r %}
> install.packages("lpSolveAPI")
> library("lpSolveAPI")
{% endhighlight %}

Now, our model has 2 variables, d and f. We construct an lprec to represent that:

{% highlight r %}
> lprec <- make.lp(0, 2)
{% endhighlight %}

And tell lpsolve we want to maximise the objective function, P.

{% highlight r %}
> lp.control(lprec, sense="max")
{% endhighlight %}

We have to maintain the same ordering of the variables throughout. Here, ```5d + 4f``` is represented in the vector ```c(5, 4)```.

{% highlight r %}
> set.objfn(lprec, c(5, 4))
{% endhighlight %}

To represent ```100d + 125f <= 50000```, we use:

{% highlight r %}
> add.constraint(lprec, c(100, 125), "<=", 50000)
{% endhighlight %}

Again, be careful to maintain the same ordering of d and f.

To see the model, do:

{% highlight r %}
> lprec
Model name: 
            C1    C2           
Maximize     5     4           
R1         100   125  <=  50000
Kind       Std   Std           
Type      Real  Real           
Upper      Inf   Inf           
Lower        0     0         
{% endhighlight %}

To solve it:

{% highlight r %}
> solve(lprec)
{% endhighlight %}

It is quite strange R does not give the results right away. To see the results:

{% highlight r %}
> get.objective(lprec)

[1] 2500
{% endhighlight %}

That says our profit will be $2,500.

Our profit is achieved by:

{% highlight r %}
> get.variables(lprec)

[1] 500   0
{% endhighlight %}

That is, we make 500 ducks and no fish at all.

The book example actually says we can't make more than 400 ducks or 300 fish. Just add the following constraints to the model to get the book answer of $2,320.

{% highlight r %}
> add.constraint(lprec, c(1,0), "<=", 400)
> add.constraint(lprec, c(0,1), "<=", 300)
{% endhighlight %}

They say ```1d + 0f <= 400``` and ```0d + 1f <= 300```, respectively.

{% highlight r %}
> lprec
Model name: 
            C1    C2           
Maximize     5     4           
R1         100   125  <=  50000
R2           1     0  <=    400
R3           0     1  <=    300
Kind       Std   Std           
Type      Real  Real           
Upper      Inf   Inf           
Lower        0     0         

> solve(lprec)
[1] 0

> get.objective(lprec)
[1] 2320

> get.variables(lprec)
[1] 400  80
{% endhighlight %}

lpsolve is applicable when we can represent our optimisation in the standard form of linear programming.

