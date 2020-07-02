---
layout: post
title:      "How to build a Single-Page-Application(SPA)"
date:       2020-04-20 16:37:23 -0400
permalink:  how_to_build_a_single-page-application_spa
---

[https://github.com/shaqqour/list](https://github.com/shaqqour/list)

To-Do, Doing, Done List:
Are you wondering how to build a single page application(SPA)? I was too when I first started building my "To-Do, Doing, Done List" App.

You might be wondering, why did I build a to do list when other applications like [Trello](https://trello.com/ ) exist. Well, Trello is highly customizable with many boards, lists, etc. that can be overwhelming for some users. I wanted to create something simple on one page, that all users would be comfortable using. 

I chose to have every task/item migrate through three stages: to-do, doing, and done. This way users can monitor the progress of each task easily, and see everything from a higher-level perspective. 

I want to share with you some tips on how to build an SPA. 

For the SPA, you need a backend and a frontend platform. I used Ruby on Rails for the backend and JavaScript (since it is the best) for the frontend. This was my first time building something that had a backend and frontend platform.

## Rails as backend:
In this application rails is responsable of rendering APIs for the front end. My recomendation here is to use rails --api flag when building your backend. That would build a rails application that doesn't have any views and instead you will render api's  in your controller that would be used as a data provider for the frontend.

There are few ways to render an api from your controller. One of the ways is to use the gem 'fast_jsonapi' that would create a Serializer class for each model you have in your application. You can read more about it [here](https://learn.co/tracks/online-software-engineering-structured/front-end-web-programming/rails-as-an-api/using-the-fast-json-api-gem)

## Javascript as frontend:
This is the fun part of the application. Javascript has a "fetch" function that can perform http-requests from your backend which render json-api. When receiving this json-object which has the data, in my case would be List Objects that each one has many items. Iterating through that object allowed me to create lists object and add them to the DOM, Document Object Model. Each list is like a mini application on the DOM.
The most thing I like here is my buildList function that the list object from the iteration gets called on. Here is the code snipt for that:

```
for (const lst of jsonObject.data) {
        let list = new List(lst.attributes);
        list.buildList();
    }
```

```
buildList() {
        
        const main = document.createElement("main");
        body.appendChild(main);
        
        //create to_do containers
        const div = document.createElement("div");
        div.className = "list";
        div.id = this.id;
        main.appendChild(div);
        this.addToDoInfo(div);

        //create doing container
        const div_doing = document.createElement("div");
        div_doing.className = "list doing";
        div_doing.id = this.id + "doing";
        main.appendChild(div_doing);
        this.addDoingInfo(div_doing);

        //create done container
        const div_done = document.createElement("div");
        div_done.className = "list done";
        div_done.id = this.id + "done";
        main.appendChild(div_done);
        this.addDoneInfo(div_done);
        
    }
```

This project was a big learning curve for me. I got stuck on few things during my building, but I was able to get solutions and answers very fast. I can say without a doubt, I'm very proud of this SPA that I created over the last two weeks.
