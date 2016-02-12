---
layout: post
title: "Taxes Calculator - TDD and test first in practice."
date: 2016-02-12
categories: development tdd
summary: "I'd like to continue 'TDD is alive' topic. This post is all about practice: I'll show you how to use TDD while developing simple application."
---

Some time ago I wrote blog post trying to answer question ["Why TDD does work for me?"](http://tomaszkus.pl/development/tdd/2014/11/25/why-tdd-does-work-for-me.html).
My proposition for today is: let's develop simple "taxes calculator" application using test first / TDD approach.
I am going to give you application skeleton with calculating of flat tax already implemented. I'll show you how to use test first and TDD
in this project leaving final implementation to you. At the end of this exercise you'll have opportunity to check whether or not you implementation works.

It could be also a good example project for quick TDD training for your team (I've prepared it just for such training in my team).
My goal is to show you how beneficial and convenient is test first and TDD. And on the other hand how dangerous could be the opposite approach.

Ready to start? So let's go...

### Application infrastructure

...and start from application infrastructure to say that it is ... not important for us this time ;)
You may want to know that it is written in C#, self hosted, Owin based web application that exposes REST API.
After GET request to:
`http://localhost:8080/api/taxes/{amount}`
you'll receive tax calculated for given amount of money (in json format). For instance 200 for 1000 (currency also does not matter here).

### Application functionality - initial state

To start your adventure with Taxes Calculator, please clone git repository:
`git clone https://github.com/tomaszkus/TaxesCalculator.git`
and switch to branch develop:
`git checkout develop`
After importing Taxes solution into Visual Studio you are able to run application and check that it works (for instance using Postman).
In TaxesCalculatorTests project you can find:
* integration/feature test of REST API (*TaxesCalculatorIntegrationTest*)
* unit test of class resposible for flat tax calculation (*FlatTaxCalculatorTest*)

Indeed our application at this stage is able only to calculate flat tax for given amount of money.

### Application functionality - new feature

Let's assume that our client (government in this case) wants to extend this simple application.
When setting query parameter *flat* to *false*, application should calculate progressive tax for given amount of money basing on following assumptions:

| **incomes (amount of money)**  | **tax (%)** |
| < 0 - 40 000 )                 | 15          |
| < 40 000 - 80 000 )            | 30          |
| < 80 000 - ... )               | 45          |

Example values that could be used for unit tests are:

* in first range of incomes:

| **incomes** | **tax** |
| 5 000       | 750     |
| 20 000      | 3 000   |
| 35 000      | 5 250   |

* in second range of incomes:

| **incomes** | **tax** |
| 45 000      | 7 500   |
| 55 000      | 10 500  |
| 65 000      | 13 500  |

* in third range of incomes:

| **incomes** | **tax** |
| 75 000      | 16 500  |
| 85 000      | 20 250  |
| 95 000      | 24 750  |

### Implementation of new functionality - BDD/TDD cycle

"It's easy, I must only ..." No, wait. We are going to do it with test first approach. How exactly? Let's take a look
at diagram below:

![tdd bdd cycle](/images/bdd_tdd_cycle.png)

1) The first step is to prepare a test for the feature that we are going to implement. Our test should check that as
a result of GET request:
`http://localhost:8080/api/taxes/{amount}?flat=false`
we receive value of progressive tax for given amount of money.
You are not sure how to do it? No problem. This first test I've already prepared for you. It is on branch *integration*
so you have to switch to it (*git checkout integration*) and go to *ShouldReturnProgressiveTaxValueForGivenIncomes* test in
*TaxesCalculatorIntegrationTest*.
The next step is to run this test to make sure that it is red - failing from known reason. So let's do it to see that it
is ... green!
Why? The answer is on chart below:

![taxes graph](/images/taxes_graph.png)

We had no luck choosing the amount of money for which flat and progressive tax have same value!
The conclusion is that our test is not checking exactly what we want to check. Why we know it? Because we've prepared and
run test before implementation. Many problems with tests could be discovered in red phase.
Red phase is very important in TDD. To assume that red phase is done we have to do following operations:
- write a test before implementation
- run it
- make sure that it is failing from known reason

You can modify integration test with values specific to progressive tax calculation. Or switch to *unit* branch where I've 
done it for you (along with infrastructure for unit tests). No worry - I haven't done everything ;) 
It is exactly this moment where your mission begins.

Your goal is to implement *ProgressiveTaxCalculator.CreateFor* method that takes amount of money and return value of progressive
tax calculated basing on rules described above.

2) You should prepare first unit test - checking that for amount 5 000 returned tax is 750. You should run it and make sure that
it is red.

3) Then you should write simplest piece of code that could make your test green (something like just returning hardcoded value).

4) When test is green it is time for refactor of both production and test code. Do not forget about running tests to make sure 
that they are still green after refactor.

Steps 2-4 should be repeated until whole functionality is implemented.

n. The last step is verification that feature test is green. To do it you need to merge changes from *autofac* branch 
(in case of conflict in *.csproj file please include changes from both branches) where
dependency injection and choosing calculator basing on *flat* flag is implemented (you can also do it yourself if you want).

Is feature test green?
Are you convinced that test first approach is really beneficial?
Was this simple TDD training useful for you?

I am very happy if your answer is 3 x YES.

If you want additional practical information about TDD (especially about possible problems and ways of solving them) please
read [this post](https://www.future-processing.pl/blog/tdd-tests/) on FP Technical Blog.

