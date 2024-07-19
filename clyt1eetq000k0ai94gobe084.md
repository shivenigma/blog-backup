---
title: "Today is a great day"
datePublished: Fri Jul 19 2024 18:31:56 GMT+0000 (Coordinated Universal Time)
cuid: clyt1eetq000k0ai94gobe084
slug: today-is-a-great-day

---

I've been doing a lot of stuff at work in this week but nothing felt significant as it today. There are two things that made me really happy today.

### Fixed a long standing issue in social login with LinkedIn

In my current project, we implemented social login with google and LinkedIn. Google worked well from the beginning, but LinkedIn failed most of the times and only worked randomly. We're facing this issue for almost 2 months and luckily our app isn't released to users yet. We had the liberty to put a lid on the issue until now.

Today, I managed find time to pair with the team member who worked on the social login. We followed the social login flow from LinkedIn docs and various blogs and he did not make any mistakes. We were able to get the access\_token successfully every time from the `https://www.linkedin.com/oauth/v2/accessToken`.

The problem happened at the next stage when we tried to get the user profile by calling [`https://api.linkedin.com/v2/userinfo`](https://api.linkedin.com/v2/userinfo) with the access token. The request failed randomly and we couldn't figured out why.

Both of us looked for a solution for this in multiple places with no luck. But I found this [blog post](https://dev.to/fardinabir/fetching-linkedin-user-data-and-sign-in-with-linkedin-using-openid-connect-3kf) which covers the same flow we used. But I read an interesting thing in this post, if we add openId in the scope of an auth call, LinkedIn will return a JWT token which contains all the info we need. So we removed our code to call user info and used the data from the decoded JWT.

After this change, the social login is working well now. It is a huge relief since we are very close to going live and this issue was a mystery for so long.

### Created my first meaningful PR to our react app

I am an Angular developer and never worked with react before. But ever since I started to lead this project, I've been doing some minor tweaks, bug fixes here and there in our react code without understanding much of react.

My usual method is to search for the page URL, go to the relevant component, search for the nearby text or element in code, then find out the function being called or adding some more components in that place.

Today I created a PR that involves some significant understanding of how the whole app works and how things are connected. I wanted to add something into the global state with redux and reading it in different part of the app, then doing some more work with the data.

I'm really surprised after I finished the feature because I never really learned anything about react except for frustrated or confused tweet from React developers. It got me thinking, if you're good enough in one framework or language, you can pick something else up with relative ease.

Any developer who is worth his salt should be able to figure out other frameworks within few hours and can get good at it within 3-4 months. Companies usually filter out resumes/candidates based on what's on their resume. But the map is not the territory and a good developer is almost always language agnostic.

### Other updates

This poor job market makes me scared shit, so I finally got out of my comfort zone and started a course on MongoDB. I'm already working on NestJS and MongoDB and wrote out match and lookups that are complex with the help of Claude.

But I wanted to get better at querying mongo to the level of SQL. I can write basic SQL queries without internet, but every time I see some match and lookups, I flinch away in embarrassment, that I'm not smart enough to understand this. That's why I started on the course I purchased years ago. Let's see how it goes in a few weeks.