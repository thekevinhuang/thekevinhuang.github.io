---
layout: post
title:      "I'm in pieces... but that's ok."
date:       2019-03-26 03:33:32 +0000
permalink:  im_in_pieces_but_thats_ok
---


**Wax Wings**

Usually when someone says that they are in pieces, things have gone terribly wrong. And for some time during the initial stages of this project, they had.

Fresh from learning about React components and managing state with Redux, I was ready to dive right into my final project. Hacking away, I was quickly able to get all my basic React components together. I whipped up a component to store the itineraries and display a form to create a new one. 

Using the relative simplicity of the React component structure and declarative style, I was able to quickly chain together the structure of the dates that comprise an Itinerary as well as a basic frame for the points of interest for each day. Import something, connect to something and render. We were rolling.

Everything seemed to be going well. All I had to do was create Users, have some sort of authentication, and manage the Rails persistance. All things I've done before so what is the big deal?

A thought likely shared by Icarus.

Turns out I had done all the different parts but I didn't yet know how to put the pieces all together. I tried my best to add in User functionality at the same time leaving room for authentication. The whole time also considering how the pieces would fit together with the rails backend. There were so many moving parts that when things inevitably didn't just magically work, I couldn't figure out what had gone wrong.

I fought hard but I knew I had to try a different approach.

**Piecemeal Revival**

Not all was lost. The outlines that I had created previously still applied. The structures I built were still valid. I needed to understand that the for me the frontend client couldn't be developed in a vaccuum. In fact, it was almost imperative that the backend was created first, despite what the name "Redux portfolio project" might suggest.

All of a sudden it came back to me:

Models
Controllers
Serializers for the JSON Endpoints

React had its own circle of life:

Component
Actions
Reducers

Adding anything to the app necessitated changes to all these parts.

Once I identified the pattern of modification, pieces fell into place.

I needed to manage and store Users:

1.  Create the User model => Create the appropriate migrations => Adjust the routes
2.  Create the Controller => Handle the inputs => Write functions for creating/showing/deleting
3.  Create the Serializers => Take the created objects and put them in JSON format => Return the JSON at the API endpoint

Then the client needs to handle it:

1. Create a component to show a Login/Signup => Import the appropriate actions and call them base on User inputs
2. Create Actions to manage the asynchronous requests to the backend => Take the results from the API calls and push them to the data store
3. Create the Reducer that makes Redux state information available to components => Component updates

This pattern generally held up when I recreated my Itineraries, Dates, and Points. I did so first in in Rails, created the corresponding piece in React, and put them together.

The result? Something greater than the sum of its parts.

**Skeletons in the Closet**

After working tirelessly to flesh out my application, it turned out I still only ended up with a skeleton. It was neat that people could create an Itinerary and it would fill in the appropriate days and you could add your own points. 

But that's not what I set out to do. Let's say you wanted to go to visit the Empire State Building on your trip to NYC. If you wanted to save the address of "20 W 34th St, New York, NY 10001" to your itinerary what would you do?

You would look it up on Google of course!

So why introduce the extra step where you would have to look it up on Google and copy and paste it into the app? Let's allow you to look up Points of Interest directly from Google. It will have the address for you, even a position on a map!

Of course you've heard this tale before. It can't be that easy. Let's insert some drama.

And drama it was.

Google has one of the most complete maps ever created by humankind. It is used by everyone from single person designed websites to entire enterprises. As such, Google APIs need to be flexible and applicable to many different situations. While this is great, it also means that there will be a wealth of documentation and examples leveraging different tech stacks and different software packages.

No example you read about or look to for inspiration will be exactly what you are looking for. Good thing I had already started thinking in pieces. I must thank countless tabs of StackOverflow, Github, Google Developer Pages, Medium Articles, and personal Blogs. Like many before me, I have incorporated nuggets of knowledge from so many sources to get to where I am.

**Giant Shoulders**

Nothing is quite as satisfying for me as making something relatable. I contemplated leaving Google Authentication out of my application. I almost didn't include maps and markers in the Point of Interest Show page.

I just couldn't bring myself to give up. Logging in with your Google account just feels official. It feels like an authentic web experience (pun not intended). Similarly, there are very few people who plan trips that don't use Google maps and their wealth of information contained in the Places Library.

I didn't come this far to back down and take an easier route.

So I overcame the restriction that you can't store Google Place information in your databases. I saved the Place ID (not to be confused with another ID attribute that you can get from a Google Place) and I asynchronously fetch data from Google to load information about points that you have added to your itineraries.

I read about the difference between Access tokens and ID tokens and whether they work with OmniAuth. I found out that after loading google libraries in your index.html file, they are globally available and React requires you to specifically state that you want to use that google variable in your components.

I spent days trying to figure out the appropriate authentication flow for a Rails + React stack, trying to avoid incorporating packages that work against the React style.

In the end seeing the Autocomplete bar work and having the POI data load from Google servers felt so awesome.

**To Infinity**

This was, by far, the most involved and complicated project that I have worked on. Itinerarian has the most relatable design and purpose. I am excited to show it off and continue to build it out. What started as something that I wanted to put together to organize my thoughts for an upcoming trip ended up being one of the biggest learning experiences I've had to date.

I learned a better way to organize and how to use some extremely powerful tools. Most importantly I am excited doing it. I can't wait to see what's next.



