## Don't start from scratch

Last year, after reading a couple of books I thought I should try launching my own SaaS app. I planned and developed  [whereAmI](htpps://whereami.dev) until November. In November, I burned out and stopped doing anything outside my full-time job.

The app is very simple and could've been done within a few weeks. But I am evolved for long-term maintenance. I made a lot of choices and a lot of work that should've waited until after the launch. Eventually, I never finished the app.

On the bright side, I learned to talk to random people and validate an idea, and how hard it is to launch and succeed in a project as an Indiehacker. I can use this experience to do better on my next attempt.

A lot of things I did are regular development-chore and only a little is the actual business logic. Some of the chores are,

- Repo setup
- Local env setup
- Tech stack selection
- App name selection
- Domain selection and setup 
- Server setup. 
- User authentication setup
- Front-end app setup

Most of the steps are unnecessary at least from the second app you build. So we don't have to start from scratch every time. For some context let me share the tech stack I used.
- Laravel
- Auth0
- Angular
- Figma
- Angular material

Using Laravel I finished the APIs within 8-10 hours. The culprit that slowed me down was Auth0. I tried following a guide from their docs and it stopped working somewhere in the steps. So I followed multiple guides with varying degrees of success but not completion, weeks passed just on fixing the auth0 issue. It turned out to be a small exception handling problem on the sample code Auth0 docs shared.

If saving time is a reason for using auth0, I could've finished the User & Auth modules using Laravel within that time. I'm sure Auth0 solutions are great. I even had great success using it on the front-end at work. But it is my mistake, choosing it on the backend where I never used it before.

I started developing APIs first. The earlier time is an important period where the motivation is high. I spent it all on a totally unrelated problem that should be avoided.

As for WhereAmI is concerned, I'm not sure if I want to continue pursuing the development of it. I thought of sharing some mistakes I did and the lessons learned.

- Either build to sell or build to learn. When selling is the goal, stick to what you already know.
- Use (copy/paste from another project) existing code for most things such as user auth, front-end, etc.
- Make yourself comfortable with using starter templates. I am a victim of the  [Not invented here](https://en.wikipedia.org/wiki/Not_invented_here)  syndrome.
- Use docker for env setup, I should start learning it too.
- Don't waste too much time on decision-making.
- Don't worry about maintaining the app for years, your app is more likely to fail than succeed.
- Automate the things which can be automated, such as deploying.
- Have a clear plan and attainable schedule.

The above list seems obvious in retrospect, but when you're working on the micro-level this can be hard to realize. Maybe this is how all the Indie hackers are doing and I'm the one who hasn't realized. Either way, I'm really happy I attempted to build something on my own, it was a stretch project for me.

I hope this helps anyone on a similar journey and would love to see your thoughts on it. If you enjoyed reading this, consider %%[buymeacoffee]