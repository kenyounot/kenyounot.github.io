---
layout: post
title:      "CLI Gem Project"
date:       2019-10-06 20:32:17 +0000
permalink:  cli_gem_project
---


If you would have told me a month ago that today I would be capable of pulling information from any website of my choosing and using that data for a project that I came up with I would've called you a liar. I was watching one of my favorite movies the other day "The Social Network", and one of the beginning scenes shows Mark Zuckerberg scraping pictures off of his college dorm's facebook. I thought what he was doing was magic a couple of months ago, but now I look at it as something that I can do. 

One of my favorite past times is to sit on Netflix for 4 hours before I finally decide which movie to put on, I'm so indecisive, so after watching "The Social Network" I couldn't decide which movie I wanted to watch next.  And that's how the idea for my project was born. I decided to create a program that returns a random movie based on the genre the user wanted to watch. I use RottenTomatoes for most of my movie review research so that's the site I decided to scrape from. 

I envisioned that once a user chose a genre to randomly generate a movie from, it would also show additional information about the movie like the summary, director, and date the movie was released. First, I wanted to get the basics of the program out of the way which only required going 2 levels deep, in my case that required returning the list of genres and then the random movie from that list. What I failed to realize is that each genre list (there are 17 genres) contains 100 movies, so to go another level deeper, it would require another scraper of 1700 URLs to get the movie bio, director and date. I tried scraping the data a couple of times and I thought I was stuck in an infinite loop, it turned out I was just asking for too much information, guess I found the limitations. 

Thankfully, the second level of information contained the movie rating and movie data so I wasn't just returning a title. I think I will come back in the future and scrape and save all the information into a file and then use that file to grab the movie info I need instead of scraping from a website.  I was happy with the outcome of the project and I'm very impressed with myself, I have been messing around with programming for a couple of years but this is the first time I've built something that I would actually use. The name I came up with for the gem was Flixpick! Can't wait to see what's next!
