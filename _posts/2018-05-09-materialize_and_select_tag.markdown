---
layout: post
title:      "Select Tag with Materialize"
date:       2018-05-09 15:17:22 -0400
permalink:  materialize_and_select_tag
---

Right now I'm building a Ruby on Rails and decided to utilize the CSS framework Materialize rather than using Bootstrap. However, I ran into an issue with a select_tag not showing and am hoping to save another developer the time I spent on troubleshooting this issue. 

* To setup Materialize in a Rails app, include this in your Gemfile:

`gem 'materialize-sass'`

* Next, run

`bundle install`

* Then, in `app/assets/stylesheets/application.scss` add:

`@import "materialize";`

You're now ready to get started with Materialize with just this basic setup!

However, I quickly realized my select tag wasn't working anymore and after struggling for a while and combining information from different blogs and stackoverflow answers, I resolved this issue by:

* First, adding to my Gemfile:

`gem 'jquery-rails'`

* Next, running

`bundle install`

* Then, in `app/assets/javascripts/application.js` adding:

`//= require jquery
//= require materialize-sprockets`

* Then, creating a new JS file:

`app/assets/javascripts/materialize.js`

* And including in this file:

`$(document).ready(function() {
  $('select').material_select();
});`

This bit of jQuery manually initializes Materialize's custom implementation of the select element ~ now your select tag should be functional again! 

For more info on Materialize and Initialization, check out [MaterializeCSS](https://materializecss.com/forms.html#select-initialization)


