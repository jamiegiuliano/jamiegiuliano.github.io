---
layout: post
title:      "jQuery Front End - Portfolio Project"
date:       2018-07-12 00:37:35 -0400
permalink:  jquery_front_end_-_portfolio_project
---

Punchcard is the client-side tracker for loyalty programs connected to Square. I talk a little more about some of the back-end functionality in [this post](https://jamiegiuliano.com/punchcard_-_rails_porfolio_project), but this portion of the project was about adding the jQuery front-end. I kind of fell for front-end during this project, which is huge for someone who really thought they would only enjoy back-end. I came out of this project really wanting to be a developer that design teams are excited to work with.  

My original project was pretty deeply nested, making implementing jQuery challenging. Some of the main requirements for this project include:
1. Must render at least one index page via jQuery and an Active Model Serialization JSON Backend. 
2. Must render at least one show page via jQuery and an Active Model Serialization JSON Backend.
3. The rails API must reveal at least one has-many relationship in the JSON that is then rendered to the page.
4. Must use your Rails API and a form to create a resource and render the response without a page refresh.
5. Must translate the JSON responses into Javascript Model Objects. The Model Objects must have at least one method on the prototype.

Requirement #4 seemed to be the most difficult for me, I first needed to grab the form and hijack the 'submit' event 
```
$(function newLink() {
  $('form#new_link').on("submit", function(e) {
    e.preventDefault();
    const values = $(this).serialize();
    const action = this.action;
    createNewLink(values, action);
  });
})
```

The 'action' constant in this function stores the action from the form, which was really helpful since it was nested. The 'values' constant stores the values that were submitted from the form with .serialize(), which creates URL encoded text (including the authenticity token!). These values are then passed to the `createNewLink` function: 
```
const createNewLink = function(values, action){
  $.ajax({
	cache: false,
    url: action,
    type: 'POST',
    data: values,
    dataType: 'JSON',
     success: function(data) {
      const link = new Link(data)
      const html = link.buildLinks();
      $('#link_list').append(html);
      $('#link_url').val('');
    };
```
			
This function makes an AJAX post request and if successful, creates a link from the Link Model Object, then calls the  `buildLinks()` function on the object, which concatenates the link data, and appends the html to the DOM. I then clear the input of the form to improve the user experience when immediately creating another link.

In the end - it all works and I'm really happy with the improvement to the UI! My next goal for this project is to make it responsive. 

One last thing- when I was deploying this project to Heroku I ran into a strange error that, after hours of googling, was fixed by changing `config.assets.js_compressor = :uglifier` in '/config/environments/production.rb' to `config.assets.js_compressor = Uglifier.new(harmony: true)`. From what I've gathered, this has something to do with the current version of Uglifier's lack of support of ES6. I also had to delete cache: false when deploying to Heroku for the same reason - however I kept it on my local environemt since this is what is allowing the user to create links back-to-back without a page refresh. Hopefully that will save someone a headache! 

Check out the final project [here](https://square-punchcard.herokuapp.com/)<br />
a walkthrough [here](https://youtu.be/5Aqdi9EE8H8)<br />
and the repo [here](https://github.com/jamiegiuliano/punchcard).

