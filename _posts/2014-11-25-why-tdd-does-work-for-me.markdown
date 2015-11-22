---
layout: post
title:  "Why TDD does work for me?"
date:   2014-11-25
categories: development tdd
---

I’ve seen recently very inspiring video with [speech given by Erik Meijer](http://vimeo.com/110554082).
Although generally I do not agree with him, there is at least small element of truth in almost each of his 
controversial hypothesis. Each except one, I think: this one that TDD and tests in general have no value. As some time
ago [David Heinemeier Hansson announced death of TDD](http://david.heinemeierhansson.com/2014/tdd-is-dead-long-live-testing.html) 
I’d like to tell you that I’ve seen in today in a very good shape: in my code, in my team, in my company.


### Because I am not skilled enough (but better and better)

I’ve discovered that I am not able to write code of very good quality without TDD. I’m not crazy enough 
to abandon TDD while working with large codebase in enerprise project. Of course it does not prevent me from doing 
mistakes. Nobody’s perfect, no metodology is perfect. But with TDD I have: good tests, well defined, deeply considered 
interfaces and functionality, well written, clean code.

Although I am not perfect, every day I become better developer (at least I hope so). I am scared looking at my code 
written several years, well even months ago! With test I have opportunity to refactor this not good enough code now 
when I am working with it. Without tests I’ll be frightened while making any changes in it ;)

### Because we are all not skilled enough

Same problem, maybe even worse and most common is while working with someone’s else code. This job is far more convenient when we have:

* good tests
* well written readable code

We receive both as core benefits of TDD.

### Because TDD gives readability

Readability is crucial for code. Code is written once and read many times. It is worth to do my best while writing code 
in order to make job of its future reader less painful. Well, it is also quite likely that this future reader 
and maintainer will be … me :)

With TDD we have code easy to read and additionally tests that explain it. Do we need anything more?

### Because test code is not worse than production

Yes, we developers want to write as many code as possible. That’s true. But I do not understand programmers that treat 
test code as something worse than production code. Writing test may give you exacltly same fun like writing production 
code. Maybe statistically even more, becase you are often creating tests from stratch, while job to do in production 
code is sometimes only one line correction…

### Because tests are “real work” and provide value

You won’t feel satisfaction of doing not real, not necessary job. So keep in mind that tests are real work and provides
 real value: Not only for us, as described above, but also for customer.
 
### Because project with good test is more likely to be successful

“No tests, just make it work” or “put it into production and fix when crashes” strategies are for gamblers and lunatics. 
I see than more and more customers – “business people” are aware of that fact. I’m also sure that every developer knows 
about it although some of them are not keen on admitting it.

Project with good test are likely to be easier to change, develop, maintain and for sure better protected against 
unwanted modification (OCP). Regression on production may cost much. Too much. A lot more than a cost of writing good 
tests which finally isn’t very high.

### Because TDD is not my religion

I’m not a member of “the holly TDD church”. I abandon it while writting simple tool that will never be changed.
To be honest it is not a bad idea to not write tests in similar situations at all. Let’s just be pragmatic. 
But developing large enterprise project without test is a suicide for sure.

To sum up: in most cases TDD gives huge value for us and for customers.

Let’s do TDD for ourself.

Let’s do it for customers. (Sure, we are focused on code, but we should also take care of our customers. 
Well, without them we’ll die of starvation coding for fun :D)