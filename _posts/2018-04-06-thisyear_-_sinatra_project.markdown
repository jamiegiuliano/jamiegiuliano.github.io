---
layout: post
title:      "ThisYear - Sinatra Project"
date:       2018-03-20 19:52:26 -0400
permalink:  thisyear_-_portfolio_project
---

# Test
Every year, I attempt keep a running list of the resolutions I've created at the beginning of the year and all of special events, big or small, that occur throughout the year. I've added all types of events- from trying and loving a new restaurant to traveling to New York for the first time. This way, at the end of the year, I get to look back at all the exciting things that have happened over the past 12 months - a lot of which I forget even occurred! 
So, I thought this would make for a fun app. Plus, I wouldn't have to carry a journal with me everywhere and the app would be a lot simpler to read over at the end of the year when the events and resolutions begin to pile up. 

Check it out on [Github](https://github.com/jamiegiuliano/this-year)


ThisYear is a CRUD Sinatra Application that uses ORM techniques through ActiveRecord to manage relational data via a method driven structure. The models include **User**, **Event**, and **Resolution**. A User 'has many' resolutions and events. A resolution also 'has many' Users- this way a user can either create their own unique resolutions and/or pick from a list of those already created. This many to many relationship required a join table, **UserResolutions**. Events, however, 'belong to' a User, since they tend to be more personal and unique in nature.

## Validations 

I set up a few different validations through the three main models with the most interesting being in the User model. I used  ActiveRecord's validation: validates_presence_of to validate that a user creates a password. In the email validation, I was able to validate format with, format: /@/. This validation, coupled with Bootstrap, enabled a warning pop up when a user's input doesn't contain an '@' symbol. For username and email I also included the  :uniqueness validation, so a user can't create multiple accounts with the same email and has to input a unique username.

## Improvements 

* I spent quite a bit of my time learning more about Bootstrap and implementing CSS/HTML styling. I'd like to keep playing with this and improving the overall style.
* Create a Signup/Login form on the landing page.
* Create the ability to 'check off' Resolutions that the user has completed.
* Create a 'Year in Review' page where all of a User's events and resolutions can be viewed in a fun way.
* Work on rspec tests with Capybara
* Deploy to Heroku - I've been messing with this and haven't been successful just yet




