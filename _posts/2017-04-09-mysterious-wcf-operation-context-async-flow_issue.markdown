---
layout: post
title: "Mysterious WCF Operation Context async flow issue"
date: 2017-04-09
categories: development
summary: "I'd like to tell you short story about very strange failure of an application after windows update."
---

"After installing latest Windows updates our application does not work." - it is rather unusual situation. Several days ago we had such problem in my team (async flow of WCF Operation Context fixed in .NET 4.6.2 stopped working correctly).

We were forced to uninstall updates on two development environments. But then we had to find a cause of a problem and reasonable solution.

After installing updates on my machine application was broken. Not bad. At least I knew that almost for sure our problem was caused by one of updates. But which one?

My first idea was [KB4013429](https://support.microsoft.com/en-gb/help/4013429/windows-10-update-kb4013429) because cumulative update was far more suspicious than security fixes. And indeed: after uninstalling [KB4013429](https://support.microsoft.com/en-gb/help/4013429/windows-10-update-kb4013429) application started working again.

There were nothing suspicious in changelog of problematic update. I was forced to analyse changes. I started from *System.ServiceModel* (with Operation Context and related stuff). I decomplied two versions of *System.ServiceModel.dll* (before and after update) to be able to find important differences. This was bull's eye.

In *OperationContext.cs* I discovered additional check in in *ShouldUseAsyncLocalContext* property setter (*!ServiceModelAppSettings.DisableOperationContextAsyncFlow*). In *ServiceModelAppSettings* I found new **wcf:disableOperationContextAsyncFlow** flag set to **true** by default!

I was suprised: it was against common sense and backward compatibility. I was angry: it cost us a lot of lost time. But finally I was glad: as I suposed setting *wcf:disableOperationContextAsyncFlow* to false in appconfig solved our problem.