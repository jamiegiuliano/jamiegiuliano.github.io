---
layout: post
title:      "Ruby Gem: Most_Haunted_Cli_Gem"
date:       2018-01-30 18:35:35 -0500
permalink:  ruby_gem_most_haunted_cli_gem
---

*Skills Used:* 

 * OO Ruby
 * Ruby Gems
 * Nokogiri

Most_Haunted is a CLI Gem for viewing the most haunted locations in America. This Ruby Gem provides a CLI for locating the most haunted locations in America as well as in-depth descriptions for the top 10 haunted locations in the country. 

It uses Nokogiri and OpenUri to scrape https://hauntedrooms.com/haunted-places for the top 10 most haunted locations in America and their descriptions as well as scraping all of the states and a list of their top haunted locations. This way you can discover the overall most haunted locations in the country as well as a haunted location in your state.

One of the highlights of this project was becoming more comfortable with scraping. Finding the right information to scrape is mainly trial and error and I was struggling on scraping not only the main page but 52 other pages depending on the user's input for which state (+ Canada) they'd like to view. I didn't want to hardcode 52 URLs (gross) and instead found a way to iterate over each section containing each URL and pull the value out with .attribute("href").value. Check out my code on Github [here](https://github.com/jamiegiuliano/most_haunted_cli_gem) to see the methods I created to accompany the URLs, giving the user the ability to choose a specific state and see a list of the top haunted locations in that area. 

I'm also in the process of adding the ability to choose a location from a state's top haunted locations list so that the user can also learn more about a specific location in their area. 
 
Download this gem from [RubyGems.org](https://rubygems.org/gems/most_haunted)

 See it in action [here](https://www.youtube.com/watch?v=hflEpSap-dc)
