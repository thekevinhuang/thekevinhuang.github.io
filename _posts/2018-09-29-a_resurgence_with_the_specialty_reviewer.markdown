---
layout: post
title:      "A Resurgence with the Specialty Reviewer"
date:       2018-09-29 16:29:18 +0000
permalink:  a_resurgence_with_the_specialty_reviewer
---


Hello Folks, coming back from a number of life events. But coming back with force!

Recently I have been working on something I've been interested in creating for a little while. Everyone knows that these days people are obsessed with reviews. Everything has to be the best for your hard earned money.

While some believe this results in people that are obsessed with ratings like in the Black Mirror episode "Nosedive" or really picky consumers, I do believe there is value in amassing people's collective experience with products.

In the true spirit of an open economy, nothing wrong with competition. Knowing that your products are so readily reviewable should provide some pressure to innovate and make better products.

The issue is there are so many niche product areas where knowledge is siloed. Getting involved in a new hobby requires so much research and often a reliance on some top 10 list from one person whose experience may be completely different from yours.

Well I thought it would be cool to have a completely independent site for reviews of specialty products.

So here we are.

Like most more "realistic" applications, the structure of this application provided some organizational challenges. I had to create the ability to create:

**Users**

**Activities** (e.g. Cycling) => **Item Categories** (e.g. Bicycle) => **Item Models** (e.g. Focus Mares AX 1.0) 

**Characteristics** (e.g. Durability)

**Ratings**

Something that was particularly challenging was managing the parent and children relationships across many pages. Even all the way down to the individual Rating for a Item Model X Characteristic pairing you probably still want to know what Activity it was for.

Another main challenge was trying not to hamfistedly code a huge view with tons of plain html and logic. Using one form to allow for the creation of Activities, Item Categories, and Item Models while maintaining the parent relationships was challenging but very satisfying in terms of code redundancy reduction.

I may build this out more in the future but for now I think I've tackled a lot and made something halfway decent. On to more!!
