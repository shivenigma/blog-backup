---
title: "The mysterious bug when consuming an Angular library with interceptor"
datePublished: Fri Mar 24 2023 14:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clfmn3oc404qeswnvd15fffiv
slug: the-mysterious-bug-when-consuming-an-angular-library-with-interceptor
tags: angular, debugging, http-interceptor

---

When I was working on an Angular library for our application, we encountered a weird issue. The HTTP interceptors we've added to our application stopped working when we load modules that imported the library. The interceptors don't resume even if we navigate back to modules that don't use the library. It behaved like the interceptors were not added at all.

Debugging this was hard, but we finally found the root cause after 2 days. Our library imported the HttpClientModule in one of the modules. If you import HttpClient Module in your code, it will overwrite any existing instances of the HttpClientModule that's been running.

According to the angular [Http interceptor usage notes](https://angular.io/api/common/http/HttpInterceptor#usage-notes),

> To use the same instance of `HttpInterceptors` for the entire app, import the `HttpClientModule` only in your `AppModule`, and add the interceptors to the root application injector. If you import `HttpClientModule` multiple times across different modules (for example, in lazy loading modules), each import creates a new copy of the `HttpClientModule`, which overwrites the interceptors provided in the root module.

It was an RTFM moment for me. I've been using interceptors for years but never knew this until I stumbled upon this bug. I found this part from the docs only when I started writing this blog post.

### The solution

We solved this issue by simply removing the HttpClientModule dependency and imports from the library modules. Do not get confused, You can use all the services such as HttpClient and any other components of the module in your library. The only requirement is that your library should not import the module directly on its own.

The library should rely on Angular's DI to provide the HttpClientModule when it is consumed in the end application.

### What to do if you don't control the library code?

There might be cases where the library code is not in your control such as a 3rd party NPM library. In this case, you can't remove the dependency yourself. Your best bet is to create an issue in the library and get it removed there. If that's not possible, we have another ugly workaround.

You can provide your HTTP Interceptors in all the modules of your application. This way, they'll be provided even if they're overwritten by the new instances. This workaround is ugly and brittle, I don't even like the idea. So use it only as a last resort.

It is amazing that no matter how long you've been working on Angular there are still things that can surprise you.