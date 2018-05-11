---
layout: post
title:      "Punchcard - Rails Porfolio Project"
date:       2018-05-11 21:40:48 +0000
permalink:  punchcard_-_rails_porfolio_project
---

Naively, I wasn't expecting Rails to be as difficult as it turned out to be for me. With Sinatra being fairly simple (especially compared to Rails) and explicit, I initially had trouble with the complexity and abstraction of Rails- it's a massive framework! Through my project and the lessons I've come to really enjoy the 'magic' of Rails and what can be accomplished so elegantly with this framework. 

I've tried creating ptojects that I would use/have fun with and am most excited about this app so far. Punchcard helps track what [Square](https://squareup.com/) loyalty programs a User is a part of. I noticed I was enrolled in a few of these loyalty programs when paying at merchant's that used Square, however, I had no way to keep track of what merchant's had enrolled me. While the merchant could keep track of their customer's enrolled in loyalty programs, there wasn't a client-side application available to track this information.

When you first enroll into a merchant's loyalty program at the point of sale, a text is sent to your phone with a unique link that entails all of your specific loyalty program information including what card is linked, your phone number, your current star status, and activity with that merchant. In order to refer back to this link, you have to either save it in your texts, copy and paste it somewhere (like a Note section) and label it accordingly, or have the merchant resend it to you *after* you make another purchase with them.

This system didn't seem ideal to me, so you can now copy and paste your unique link into Punchcard, where you'll be able to easily reference all of your Square loyalty programs whenever you want from one location! This gives the User the ability to edit their information within the loyalty program link at any time and enables them to see when they're getting close to earning a merchant's reward.

For user authentication and authorization, I used Devise as well as Omniauth for Github. I had a bit of trouble with Omniauth and plan on coming back to add other providers like Twitter, as well. Funny enough, I didn't have many issues with Devise, which was the gem I was really nervous about implementing. 

I plan on returning to this app as I work through the rest of the Flatiron program. Some features I'd like to this app are:
* When a customer earns a reward through a merchant, save the seperate reward link that is sent to them
* Have the information provided by the Square Up link available directly in Punchcard, instead of redirecting to another page. 
* If this web app were to be a phone app, it would be really cool if recieving a text from Square Up would prompt Punchcard to open and save the link automatically. 
* Add Omniauth for other providers as well
* Deploy with Heroku

For now, check it out on Github [here](https://github.com/jamiegiuliano/punchcard)

