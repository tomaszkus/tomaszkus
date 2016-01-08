---
layout: post
title:  "Crimson Tide – a lot of fun with simple game"
date:   2014-12-07
categories: other team
summary: Summary
---

Several weeks ago at our team party we had a simple competition.

* discover hidden world (looking for information / tips concealed here and there, solving riddles)
* determine cheapest path that allows to visit all towns in this world.

Game story was (not strictly) based on [Game of Thrones](http://www.hbo.com/game-of-thrones#/).

Last time delegation from our customer was in [FP](https://www.future-processing.com/). 
We had decided to give up traditional “going out to eat on the city” one day. 
Instead were playing a game again. From technical point of view infrastructure of both games was similar:

![game infrastructure](/images/game_infrastructure.jpg)

I’ve had very few time to prepare it, so maybe it is not very advanced but works;)

I created 2 simple nodejs applications:

* first to take, process and store results
* second to collect and visualise results after competition

I used Mongo DB for data storage as it fitted well my needs. Additionally it proved to be very easy to install and use.
As a result I managed to prepare competition on time.

The second game story was inspired by [“Crimson Tide”](https://en.wikipedia.org/wiki/Crimson_Tide) movie.

The goal is to capture nuclear submarine not allowing the other teams to do so. Instruction for this game along with 
both simple applications is available [on github](https://github.com/tomaszkus/CrimsonTide). 
Don’t hesitate to use it as pattern, skeleton and inspiration to your own competitions.

*The goal of such games is not (only) fun. They help us to build invaluable: team spirit, cooperation and unity.*

*Visualisation of results from one team:*

![example results](/images/example_results.png)

* officers: orange
* keyPoints: red
* water: steelblue
* radiation: pink
* weapons: violet
* soldiers: lightGreen

black dots – captured points