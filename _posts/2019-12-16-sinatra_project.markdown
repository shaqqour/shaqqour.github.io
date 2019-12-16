---
layout: post
title:      "Sinatra Project"
date:       2019-12-16 23:19:08 +0000
permalink:  sinatra_project
---

User-Movies Controller
https://github.com/shaqqour/user-movies

The User Movie Controller is a library of movies that users can signup to and login to search for their favorite movies. They can create their list of movies by adding and deleting to that list. A user also have the ability to create a new movie as well as modify an exsiting movie. There is a local database that was created by scraping some data from a webpage. All the user interactions with the database are controlled by models: User, Movie, Actor, Director. Databse table association are either one to many relationship or many to many. So a User can have many movies, and a movie can have many users and so on.
