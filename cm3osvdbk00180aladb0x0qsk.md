---
title: "Thoughts on Tailwind"
datePublished: Tue Nov 19 2024 18:40:38 GMT+0000 (Coordinated Universal Time)
cuid: cm3osvdbk00180aladb0x0qsk
slug: thoughts-on-tailwind
tags: css, nextjs, tailwind

---

I’ve been through few busy weeks because I am leading the UI team on a new project at work where everything we use is a new tech stack for all of us. Somehow, project like these seem to find me attractive and land on my plate.

I don’t want to rant on how I ended up here, but in short I was an Angular developer who made few edits in one CRA based react app and suddenly was the lead developer in a NextJS/tailwind project.

We’re only doing the UI mockups so far and the team caught up quickly on some immediately needed parts of NextJS. It is not as hard or as bad as I thought it would be. But this project helped me get into one of the long time tech wish list. That is trying out [Tailwind](https://tailwindcss.com).

Though I’m not [Josh Comeau](https://www.joshwcomeau.com), I like CSS and enjoy working on UI conversions. I’m the kind of psycho that asks you about [CSS specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) calculations in an interview. So the idea of putting all the style definitions into HTML itself is a big anti pattern to me. But I’ve seen developers I admire say many great things about Tailwind and wanted to give it a try.

We’re using a Prime react theme in this project which is based on Tailwind. After using it for few weeks, I have to say that Tailwind makes much more sense once you actually build something with it.

My main concerns of making code unreadable and putting everything in one file violating the single responsibility are not very valid. IDEs can handle long lines and we can always wrap the code or break them into multiple lines.

The other concern about mixing up everything actually makes more sense. Since the styles are not global anymore, there is no worry of which class name convention you should use or how to nest and encapsulate the styles. I’m pretty confident that if I change something it will not break something else in the app.

It is like taking the cascading nature of CSS away and just giving us freedom to use CSS freely without worrying about breaking something else. Since React doesn’t define how you write your style, Tailwind is a perfect combination with it. There is literally very rare cases where you would want to write inline styles and I guess that’s ok if you know what you’re doing.

There are few catches of course:

1. I can’t get few classes like max-w-\* or truncate to work properly, I’m not entirely sure why. I just changed those into inline styles and added a todo as a stop-gap.
    
2. There are lot of classes, though I should read their docs well. Still feels like lot of classes to remember and cycle through.
    

But overall I like tailwind, it makes working with css, responsiveness much easier than writing plain CSS. I would like to continue using it in upcoming projects as well.