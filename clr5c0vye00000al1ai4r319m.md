---
title: "Story points, KPIs, vanity metrics and the Goodhart's law"
datePublished: Mon Jan 08 2024 19:44:56 GMT+0000 (Coordinated Universal Time)
cuid: clr5c0vye00000al1ai4r319m
slug: goodharts-law
tags: productivity, software-development, engineering, software-engineering

---

A few months ago, I had a disagreement with a colleague about moving a card into the sprint on the last day of the sprint. His argument was that I should keep the card in the backlog and continue working. If I add a card on last day, it disturbs the JIRA insights like burn-down chart of the current sprint.

My argument was that the metrics should be the representation of the actual work, not the other way around. If I'm running light and don't have work at the end of the sprint, the burn down chart should reflect that. This is the only way to get good at estimating work for the team for each sprint. In the end, we agreed that the card must be moved to the sprint if I'm working on it.

This got me thinking about the good old Goodhart's law.

> Goodhart's law: When a measure becomes a target, it ceases to be a good measure.

Measuring efficiency of a software developer or a team is hard. The more accurate measure you're aiming for, the more difficult and inaccurate it gets.

This must've happened lot of times in many software teams. When set a metric, people always try and optimise towards it. The point of a metric is to have a pulse of what is going on. But lot of times, the metrics are treated as goals by both managers and devs because it is difficult to measure productivity in any other way.

What's the solution? I don't know. It is hard to measure developer productivity and that's not going to stop people from trying. You should keep an eye on yourself and your team for optimising to get better at the metrics instead of doing what you're supposed to do.

If you're an individual contributor, just forget chasing the metrics. Focus on the task at hand and give your best, the metrics will fall in line eventually. If you're a lead or manager, avoid chasing the metrics obsessively. The team might perceive those as targets to be met.

If you actually want to measure the productivity, look at alternate methods such as [DORA metrics](https://newsletter.pragmaticengineer.com/i/62678384/dora-metrics). But remember every metric could be skewed, DORA is also not one fit for all, and no one is immune to the Goodhart's law.