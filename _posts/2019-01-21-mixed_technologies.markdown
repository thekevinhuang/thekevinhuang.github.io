---
layout: post
title:      "Mixed Technologies"
date:       2019-01-21 22:18:30 +0000
permalink:  mixed_technologies
---


This was a project of many stages.

**Stage 1: Understanding the opportunities for improvement**

On one hand, I knew almost exactly what needed to be done. The structure of application that I had built previously gave many opportunities to streamline the user experience using AJAX requests.

With many parent/child relationships and various forms to submit on almost every page, there were many places to improve the flow and reflect the modern unwillingness to continually load or navigate to new pages to aquire or submit related information.

I remember when Google maps couldn't be scrolled or zoomed naturally. I remember when the internet was so slow that multiple page reloads made the internet experience feel incredibly slow. I remember when I initially built this application, there was this feeling of a dimensional disruption. Time itself had somehow broken down and I just sat there staring at a blank page while the next one was being rendered. At the time I didn't know what I could do about it.

But now I do!

**Stage 2: Surprise at the increased complexity**

Or do I?

Turns out while I had handled quite a few one page projects using AJAX (e.g. tic-tac-toe) I hadn't really had much experience creating applications with many pages using JS script. I went through an almost meltdown where I wanted to organize page specific JS code but it seems like all my js code would load on every page. I was in the middle of a war between wanting to have very targeted scripts while hearing that almost all of the efficiencies of the rails asset pipeline and only downloading JS scripts a single time.

I couldn't necessarily make an organization decision at that point so I took it one step at a time. Let me create a page that is able to load assets asynchronously like I had learned and we can move from there.

Wait. There was another issue. I was trying to be clever when I first developed my app. I created a form partial that was generic and if you submitted a parent and child as locals, a dynamic form would be created and displayed. This way you wouldn't have to create almost identical forms for every parent/child relationship.

After reviewing some material and some google searching. I realized I could still utilize some of the Ruby instance variables if I handled requests in my controller by responding with a new js.erb file. This way I would have access to many of the variables from the backend, pages would have JS specific to them, and as an added bonus, I could greatly leverage the code I had previously painstakingly crafted.

But time froze again.

**Stage 3: Unmixing Technology**

Submitting forms would once again send me to another realm where I pondered the fate of my information.

Did it work? I found myself wondering this constantly. Response time was sluggish and the experience felt terrible. I couldn't really keep the experience like this. Did I technically create an AJAX request that would load new information without navigating to a new page? Yes, I did. But I really just shifted the loading time from a whole page load to an even stranger area where the page looked loaded but most of the page was mysteriously blank. Then all of a sudden a mass of html would pop into existence.

Yes AJAX requests feel almost like magic but this was maybe a little too magical. It felt like I had no control of what was happening or when.

I now had a better understanding of why people generally recommended not to have views, controllers, models, or scripts utilize too many different sets of code. Everything became confusing and felt unpleasant. 

For example, I was in a index view looking at HTML, it loaded the list of Item Categories using some ruby code in ERB. When I hit the button to add a new Item Category there was a blank space at the bottom of the page while an ajax request was sent, a new .js.erb file had to be loaded, the sole purpose of which was to dig up another file with ruby code in ERB. Then once that loaded, we were back in JS land which handled the request and (slowly) loaded the resulting form in the page in HTML. All this was just to get a form to show up.

Then we were back in JS once we tried to submit. The page would once again blank out at the bottom and you wait for the POST action. But since we added something asynchronously, we obviously had to call another JS script which then called out to the controller to ask for the whole list of Item Categories and replace the Ruby/ERB loaded code in the beginning.

The result was a miserable experience both for the user and for the devloper.

So we decided to attempt to streamline.

**Stage 4: Reinventing the wheel**

I know that people hate reinventing the wheel. I really didn't like taking apart aspects of my "working" application to make it better. I knew things would break and I had to be extremely careful to ensure that my new version played well with the existing rails structure.

I also hated the idea of having to create a new form for every class. I thought it was unnecessary before and it still is. So we set off on a new quest. Let's make the wheel better...but still the same. One of the first things I realized was that many of the neat little things I did with calling the child collection or an particular instance's parent were not really available to me if I cut out the ERB and partial rendering assist. I had to find other ways to acquire the same data. To the rescue: Serializers.

Serializers essentially allowed me to still access many of the rails Active Record relationships that were so important.

Custom routes and controller API endpoints allowed me to restrict/filter/sort the results as well.

Between serializers and the JS template literals, I was able to painstakingly recreate the templates I had built previously. So we were back in business!

**Stage 5: Disaster Relief - New Class of Problem**

Recreating the forms was a large effort. Many changes had to be made all around the application. The Javascript side of things was starting to get really out of hand since we shifted much of the view functionality back to JS. Something had to be done here to make the code more legible and streamlined.

New to the spotlight: Javascript Classes!

Now that we had things working again, it was once again time to break them down. After some pondering, I felt that each view could essentially be represented by one Javascript class. This way important attributes could be stored and functions would be more organized. While the change was mostly one of reorganization, the code changes required were not insignificant. But now we had solved another problem. The JS organization problem. Now it was very clear which methods were being used in which situations and there would be very little confusion. This made debugging and further tweaking much easier. It is much easier to find what you are looking for if you know where to look!

**Stage 6: Finishing Touches**

After going through and revamping all of the existing JS into the class structure, there were still more pages that had to be converted and additional features that were built out. But the major stucture and design had been completed. We achieved almost instantaneous AJAX asset loading as well as form creation/submission. Our javascript was well organized and clear in its intention. Most importantly, I had figured out a pattern specific to my application that appropriately mixed technologies to achieve the desired result beyond a single page.
