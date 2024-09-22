---
title: "Catching up with Angular releases"
datePublished: Sun Sep 22 2024 15:24:52 GMT+0000 (Coordinated Universal Time)
cuid: cm1dqc7of000n09l9gav8cl0o
slug: catching-up-with-angular-releases
tags: angular, angular-18-features

---

The tech world moves fast and while you’re looking at something else, you miss what’s happening under your feet. That’s what happened to me in regards to Angular’s recent features.

The last project and the last time I worked in Angular is about 6 months ago and the project was Angular 14. The team was downsized and I had to move to other assignments, so I never had the chance to work on the upgrade path or on understanding the new features released since 14 like standalone components, new control flow syntax and signals.

But I’ve been working in Angular so long that people expect me to be to be on top of every change. My rule of thumb is don’t look deeply into what’s not currently relevant. I was learning React and NestJS along with MongoDB in the meantime.

I got along very well with NestJS, but I will need few more projects to be able to independently work with react. MongoDB is quite simple as well. I wrote schema and decent db design with the help of a teammate. But I couldn’t still wrap my head around how to write the lookup and pipeline in Mongo for querying data from different collections. I know, Mongo is not the best for this kind of work. But we can’t completely live without some data relationship.

Back to Angular, the updates reminds of the past of AngularJS to Angular 2 with some breaking changes and some fundamentals changes like removing modules altogether, rewriting control flow syntax, etc. This is the exact reason why react caught on instead of Angular like wildfire.

The only thing I understood on basic level was the standalone components and removal of modules. The reasoning behind the change as I understood is that they want to,

1. Simplify learning
    
2. Simplify development
    
3. Lazy loading made easy
    

I don’t know how #1 and #2 are true, because now a developer has to learn both the old way and new way, not every business prioritise angular upgrades. The simplified development is not a strong reason either. I believe modules are not complicated to wrap your head around, you just think of them as some sort of index file. Whatever Angular team thought they are simplifying here, was not very complicated to begin with.

Now #3 could be interesting depends on what exactly happened, but lazy loading was easy even with modules as well. So the whole standalone component thing feels like unwanted optimisation to my eyes. But I don’t understand the whole story yet, just getting started with this catch up.

But I don’t want Angular to give us options, option of choosing between modules and standalone. Option to choose between structural directives and control flow syntax. Stay opinionated. What makes react very complex is that they have multiple options for every thing and then change the right way for something on every major release. We don’t want Angular to go down that path.

The nice thing about Angular is they provide automated upgrades/migrations for any breaking change. So all the above upgrades could also be done with few terminal commands. I’m going to try and build some small application with Angular 18 and see how it goes. Will share with you about the progress.