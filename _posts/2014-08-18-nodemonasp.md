---
layout: blog
title: Nodemon + ASP C# 
category: blog
tags: [nodejs, c#]  
summary: Using nodemon for continuous publishing
image: /images/blog/nodemonasp.jpg
---


C# ain't pretty if you are coming from PHP which has a quick turn around from editing to refreshing the page and looking at your change. Using live reload makes it more easier.

In ASP after you edit you need to press publish and wait till it compile to look at my edit I found the solution.


###Solution

Use [nodemon](http://github.com/remy/nodemon) this is a nodejs file watcher which excutes a command if there are any file changes. This can be used with msbuild for continuous publishing, where in each file change within a interval kicks off the msbuild publishing.


1. Install [Node Js](http://nodejs.org/)
2. From terminal ```npm install -g nodemon``` this will install nodemon globally where you can just call it from cmd using ```nodemon```
3. Set msbuild to you environment commonly found in ```C:\Program Files (x86)\MSBuild\12.0\Bin``` this will allow you to access msbuild from cli.

###Start Publishing

1. Open cmd Run as administrator
2. Go your project solution or project example - ```cd C:\Users\Pasindu\Documents\Visual Studio 2013\Projects\{solution name}\{project}```

3. Then Type the following insert your publishing profile

```nodemon --exec "msbuild /verbosity:q" /p:DeployOnBuild=true  /p:PublishProfile=PublisingProfileNameHere --watch *.*  --ignore obj/ --ext cs,css,html,js
```

###Deciphering the command

```--exec "msbuild /verbosity:q"``` - [msbuild cmd] This will start msbuild quitely

```/p:PublishProfile= {{ Publishing profile name }}``` - [msbuild cmd] Set the publishing profile name

``` --Watch ``` - [Nodemon cmd] This set what to folders and files to watch,  ```*.*```  this say to watch all, other than this there are many other options.

```--ignore obj/``` - [Nodemon cmd] This ignores any files changes in "obj" folder. ignore has priority over --watch

```--ext cs,css,html,js``` - [Nodemon cmd]  Watch for file extension .cs and others in the list.


Issues - File created after running nodemon might not be track
so will have to restart nodemon by typing ```rs```


###Other
This can be used for stuff like running test and stuff like that. Need to check whether this can be used with live reload to make life more easier. You could even write a bat and then excute that also.


More Info on [MSBuild](http://msdn.microsoft.com/en-us/library/ms164311.aspx)

More Info on [Nodemon](http://github.com/remy/nodemon)



