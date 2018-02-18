---
layout: post
title:      "Amaz_Scrape the Amazon Scraping CLI Project"
date:       2018-02-18 16:01:06 +0000
permalink:  amaz_scrape_the_amazon_scraping_cli_project
---


As the first real project that was to be graded, I really wanted to do something I thought was interesting. As I was thinking about things that I could potentially scrape for this project, I wanted to do something that I did with some degree of regularity.

I love Amazon. This blog post won't really focus on this but I did spend the holiday season doing a lot of shopping so I figured Amazon would be an exciting/challenging project to try and base my CLI project on.

It was. I had the basic structure of the CLI loops down for quite some time but there were so many things that I needed to work out to get it to work.

**1. Scraping Amazon doesn't work 100% of the time.**  Obviously I should have expected this. They definitely have things in place to block rampant scraping and collection of their data, which is extremely important in the retail space.

I had to repeatedly try the scrape again over and over to get it to work sometimes. This ended up being really awesome because I eventually worked out some code that would automatically retry the scrape if it failed after a 5 second delay. Necessity (more like annoyance) breeds innovation I suppose!

**2. Man, their HTML is complicated.** This is another 'duh' thing about this endeavor. As one of the biggest and most complext online retailers the world has ever seen, they didn't achieve the layout with grade school HTML. Using nokogiri and sawing through that was brutal. Finding the similar elements that aligned every page and accounting for potentially missing data turned out to occupy a huge amount of time.

**3. Limiting Scope is Critical.** Initially I was going to just scrape everything I could find on a specific item. This lead to a few problems: 
     - It was impossible for the user to see the complete list, thus making the CLI cluttered and almost useless
     - It became impossible to figure out where issues were coming from with so many results
     - It took forever to make progress. Letting the scope creep meant having to solve problems that you didn't need to.
 
 **4. Nothing is permanent.** The first way I coded my CLI loops to work was very convoluted. I started by piecing things together making one thing work at a time.
 
 There were these methods that had so many jobs. They asked for input, they displayed something, they called another method based on certain conditions and did something else in other situations. It was honestly impossible to figure out why something wasn't working after a while.
 
 It absolutely killed me to have to take apart something that was so close to working. But it felt amazing to have more simple methods that allowed me to better isolate issues. I separated methods that validated user inputs, displayed an instruction and waited for input, scraping methods, and when something displayed multiple times, I knew where to go.
 
 It still wasn't easy but not hanging onto my old code because it sorta worked was the best decision I made.
 
 It wasn't done in one sitting but I think that made me more proud of the work that I put into it. I was dedicated and I could have switched to a simpler subject but now I've captured real useful information from a website that everyone knows. I've always intended to work on things that have a real world impact and with this project i've done something like that.
