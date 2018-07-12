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

Requirement #4 seemed to be the most difficult for me, I first needed to hijack the 'click' event 
```
$(function newLink() {
  $('#btn_manage').on("click", function(e) {
    e.preventDefault();
    const values = $('form#new_link').serialize();
    const action = $('form#new_link').attr('action');
    createNewLink(values, action);
  });
})
```

Instead of using `f.submit` on my form, I used `f.button` and grabbed the values from the form by calling `serialize()` after querying the DOM to grab the form. With submit, I was only able to submit the form once and then would have to refresh the page to submit it again. After googling for a while I found [this](https://stackoverflow.com/questions/38597295/ajax-jquery-form-submit-only-works-once-requires-page-refresh), which fixed the issue! 

The 'action' constant in this function stores the action from the form, which was really helpful since it's nested. These values are then passed to the `createNewLink` function: 
```
const createNewLink = function(values, action){
  $.ajax({
    url: action,
    type: 'POST',
    data: values,
    dataType: 'JSON',
     success: function(data) {
      const link = new Link(data)
      const html = link.buildLinks();
      $('#link_list').append(html);
      $('#link_url').val('');
     }
	 });
 }
```
			
This function makes an AJAX post request and if successful, creates a link from the Link Model Object, then calls the  `buildLinks()` prototype function on the object, which formats the link data, and appends the html to the DOM. I then clear the input of the form to improve the user experience when immediately creating another link.

In the end - it all works and I'm really happy with the improvement to the UI! My next goal for this project is to make it responsive. 

One last thing- when I was deploying this project to Heroku I ran into a strange error that, after hours of googling, was fixed by changing `config.assets.js_compressor = :uglifier` in '/config/environments/production.rb' to `config.assets.js_compressor = Uglifier.new(harmony: true)`. From what I've gathered, this has something to do with the current version of Uglifier's lack of support of ES6. Hopefully that will save someone a headache! 

Check out the final project [here](https://square-punchcard.herokuapp.com/)<br />
a walkthrough [here](https://youtu.be/5Aqdi9EE8H8)<br />
and the repo [here](https://github.com/jamiegiuliano/punchcard).

