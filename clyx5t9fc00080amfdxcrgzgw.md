---
title: "Being Agile"
datePublished: Mon Jul 22 2024 15:46:32 GMT+0000 (Coordinated Universal Time)
cuid: clyx5t9fc00080amfdxcrgzgw
slug: being-agile
tags: agile, leadership

---

I'm leading a small project at work now and it is almost over. I'm just documenting my experience and what's on my mind about the project now.

One day, our QA guy asked why I'm not conducting a daily standup at a fixed time. I told him I'm not planning to conduct daily standup and will stick to separate discussions with the team members and a weekly check of working software.

I understand that daily standup meetings are very useful for remote teams and for stakeholders to understand the progress, blockers that are happening. It is essential when you're actually agile in everything.

But this is a project with fixed scope/budget and there is not much room for change. I did not see the value for conducting a standup as the only stakeholder in a fixed scope project. The team is sitting together in an office and they're free to discuss within them, or with me whenever they feel the need to.

But I like running sprints with clear definition and delivery expectation. So we settled on bi-weekly sprint. We start the sprint with a kick-off and a rough outline of the features we want to develop. There are unknowns at the time of beginning but we'll get to those eventually and finish things mostly by the end of the sprint.

Some members of the team are new to NodeJS and NestJS, me leading the project is new to React, NodeJS, NestJS, and MongoDB. I had to read through lot of MongoDb docs on first week to learn how to create better schema (mongoose) design for Mongo and how not to let my traditional SQL mindset define things in Mongo.

We struggled a lot for a first two sprints and often was working till 2 AM. But it was a good learning experience. I am now able to debug and write React, NestJS code. Create schemas for MongoDb and write complex match and lookup statements with documentation lookups.

We finalised on the database structure within first few days of the sprint even for features on the last sprint. I like to keep the database stuff planned in advance and try to avoid changes in database and keep changes only at code level.

IMO, if the database is defined, the rest of the work becomes easier as CRUD request towards each collections and juniors have easier time wrapping their head around features. If the database wasn't fixed at first, I couldn't see that if we could've had the same mileage.

## The fun part

Since most of the team are juniors, lot of decisions were on my plate about the design of the app. Sometimes they are mundane layout and UI stuff and sometimes they are interesting architectural problems to think about. I wanted to list few of the questions and the decisions we made.

### How to identify unique search criteria and how to skip paginating the result set?

We had a credit system that reduces on each search, we need to identify unique search requests. When the user come back to the first page from the 3rd page of the results, we should not reduce their search count again.

I decided to create a hash of the search query and store it in Redis with an expiration. On every new search we check if the hash exists there and compare it with the current criteria, if the hash matches, then we don't reduce the credit count as it is an existing search. The hash gets overwritten if the search results created a different hash and a credit will be reduced.

### Queue vs Event emitters for some asynchronous activities

We used event emitters for some of the activities like sending email or notifications to the user. I was skeptical of this as a server crash could make us lose data. But I do not want to add complexity to the simple app by adding a big queue system as this app is going to run in a single instance as a monolith.

I discussed the event emitters in our chennaiJS group and had some profound dialogue with Claude and finally decided it is better to go for a queue for some of the payment related notifications for better resilience. We settled with BullMQ, which uses redis. This is excellent because I'm not adding anything additional then what's already in the project but still got proper queue system.

## Mundane stuf

There are still client demos that I have to give after each sprint, there were changes that we accommodated within the fixed scope. We used to go over some small items in great details and change things that are done already. But in my experience, this is unavoidable in any scale of project.

There are some implementation details that you can not anticipate or plan for at the planning stage, no matter how thorough you were. There were some choices the clients could not visualise at the design stage and they often realise it once they see the actual implementation. This, exactly is the reason why Agile is created in the first place, right?

All good as long as we don't exceed the cost or the timeline by a large margin.

---

I think this is Agile for the constraints and the project's specific needs. The only metric I used was working software. I know most scrum masters and project managers might say this is not Agile and we did not follow the scrum framework properly. But that's alright.

In my opinion, Agile is all about context and being able to adapt, not following a specification to the letter. I'm pretty sure this method would have failed in a different project with different set of constraints, there is no silver bullet or a blanket method that works for any context.