---
layout: post
title:  "**CLI Data Gem Project**"
date:   2016-06-06 01:18:12 +0000
---


I'll start off by letting you all know that I've never written a blog post before and I'm sure it will show here. This was a challenging project! I didn't really know where to begin or what I would try to accomplished, but luckily the instructions gave you enough direction to get started. 

My original idea was scraping the top 10 newest game releases on steam, I had been on a steam game binge and thought it would be nice to combine my studies with one of my hobbies. I created my gem's structure and set up the scraper and interface, with plenty of help form [Avi's gem walkthrough](https://www.youtube.com/watch?v=_lDExWIhYKI). Using Avi's approach to creating the interface first while using placeholder data was a great idea. This really helped get the project moving, while making a functional interface for future scraped data. This was a very good thing, because getting data to scrape from your favorite website isn't always an easy task.

Turns out steam uses a lot of JavaScript and pulls the top 10 game info from the individual game pages via links. I first attempted to collect the links and then scrape the data from each individual link. It worked... sort of... There would be several that didn't return any data, due to them being sets (game and expansion) which linked to a different type of page with different tags. The other major problem was the time it took to return the original list. It collected all the information on each page every time you started it or ran 'list'. Between these two issues, I decided to try something else. 

What else do I spend my 'internet time' doing? Reading MMORPG websites, of course! I started working on pulling data from my most frequented site, mmorpg.com and quickly ran into a brand new problem. After numerous attempts to scrape data, I realized there a message popping up complaining about my suspicious activity. The site was blocking my scraping attempts.... I turned to google and was able to find another site massivelyop.com that played nice and I was finally able to put together my gem.

Publishing and updating my newly created gem was somewhat difficult. The provided links didn't really give enough information to get it completed. I ended up talking with other students and stumbling around the internet to figure how to first get it published. I managed to get it published, but when I downloaded and installed my gem, it wouldn't execute. After talking with a few more students while doing additional research, I found I needed to set the 'bindir' value to "bin". I had used bundle to create the gem layout and its default value is "exe". I figured out how to create a new version, push it out to rubygems.org, downloaded, installed and it ran correctly!

Overall the project was fun, a bit frustrating but very rewarding. I'm looking forward to my first assessment and moving into the next section!

- Thank you for tolerating my first blog post... Perhaps this is a skill that improves over time....


Overall the project was fun, a bit frustating but very rewarding. I'm looking forward to my first assessment and moving into the next section!

- Thank you for tolorating my first blog post.. Perhaps this is a skill that improves over time....


