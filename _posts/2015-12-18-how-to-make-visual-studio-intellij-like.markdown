---
layout: post
title:  "How to make Visual Studio \"IntelliJ like\""
date:   2015-12-18
categories: tools ide
summary: summary
---

I've spend last years developing Java and Node.js applications using mostly IntelliJ and WebStorm. Some time ago I started 
new project with new team in .NET. Switching from Java to C\# is not hard. But losing your powerful IDE that you could 
use very fluently is a serious problem. 
Fortunately it turned out that I was able to transform Visual Studio into very user friendly, powerful and Intellij-like 
tool in just a few simple steps:

### 1. Install [ReSharper](https://www.jetbrains.com/resharper/)

This is a tool that gives a lot of power to Visual Studio and makes it very Intellij-like especially after switching to 
ReSharper 2.x/IntelliJ IDEA shortcut scheme. I have never heard about developers migrating back from IntelliJ to Eclipse. 
Similarly, after installing ReSharper and using it for several days nobody wants to use raw VS anymore.

### 2. Use ReSpeller extension

You can install it via menu:
`ReSharper -> Extension Manager`

Good tool for catching typos is very handy especially while developing Java Script code. But if you are protected 
well against spelling mistakes you do not care about them (not highlighted in green == without spelling mistakes). 
That's why it is not a good idea to stop using this kind of tool ;)

### 3. Improve Git integration using [Git Diff Margin](https://visualstudiogallery.msdn.microsoft.com/cf49cf30-2ca6-4ea0-b7cc-6a8e0dadc1a8)

It is very important for me to be able to see changes made in a file without a need to use a console or any external application.
Such functionality is integrated in JetBrains tools. In Visual Studio you can have it after installing Git Diff Margin extension.

### 4. Adjust default class pattern to your needs

It is annoying that by default each new class has several usings added (an is not public). 
You do not need default imports added automatically (and then manually removed, if not used ;)) when ReSharper manges 
imports for you. Fortunately you are able to change default class pattern very quickly.

File with it is in a following location:
`<path_to_vs>\Microsoft Visual Studio <your_vs_version>\Common7\IDE\ItemTemplates\CSharp\Code\1033\Class.cs`

My pattern is just:

```
namespace $rootnamespace$
{
    public class $safeitemrootname$
    {
    }
}
```

### 5. Integrate console with Visual Studio

Terminal in Intellij is very useful. You are able to perform commands without a need to switch to another window. 
The best solution for doing operations in console while working with Visual Studio is to use 
[ConEmu](https://conemu.github.io/) and [ConEmu Launcher extension](https://visualstudiogallery.msdn.microsoft.com/1ce30e82-c27c-40fd-b2d8-310ab234ab74)

With above modifications my work with Visual Studio is both effective and comfortable.