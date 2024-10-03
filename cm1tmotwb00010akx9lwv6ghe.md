---
title: "Angular and environment files"
datePublished: Thu Oct 03 2024 18:27:01 GMT+0000 (Coordinated Universal Time)
cuid: cm1tmotwb00010akx9lwv6ghe
slug: angular-and-environment-files
tags: angularjs, dotenv, environment-variables

---

I'm coming back to Angular to learn the new stuff happened in Angular 18 and thought of building something small with the [Readwise Reader API](https://readwise.io/reader_api). The API gives us an API key and we should not share it with others. Let’s use environment files I thought, but that was proven to be complicated than I thought.

The last time I set up an Angular app from scratch must be around 4 years back, having worked on React and Nest.JS recently, I thought we could put this in the .env file and Angular environment file can read from the process.env variable. Turns out, I was wrong. Angular doesn’t support .env files by default, their logic is that whatever stuff you put there is going to end up in the source code once it is built.

But I don’t care about that, all I want is for the API keys to not end up in the git repository. But there is no easier way for us to use the .env file in Angular without relying on 3rd party modules or ejecting from the ng cli into a custom webpack configuration.

### Git to the rescue

I wanted to do this within the core of Angular, so I thought why not just put the environment files themselves into `.gitignore`. To begin this, let’s generate the environment files by running the following command

```bash
ng generate environments
```

This creates the environments folder with two files in it, we are free to generate multiple environments files here. IIRC, this environment directory and files are used to be generated as a default in older versions of Angular, but I like the current setup where it is optional but still easy to create if needed.

Once these files are generated, I just added them into .gitignore and put the API key directly in the env files. It solved the immediate issue at hand, but there is another problem. If you want to share this code with another developer, they don’t know what are the actual env variables they must create.

### Environment Interface

To overcome the issue of non-sharable environments, I just created an interface called `IEnvironment`, and changed the .gitignore to add this file into VCS while ignoring the other environment files.

```typescript
export interface IEnvironment {
  apiKey: string;
}
```

This interface should contain all the env variables you have in you application and it shared to others by git. They must add values and create env files based on this interface.

This, of course is far from perfect setup. We previously used some sort of node script to replace the environment file values at run time. But this felt much easier than that.

But I do wish the comfort of just adding the .env file and forgetting about it, I don’t really know why Angular did not implement the gold standard for env files called `dotenv`. Let me know if you know the reason.