---
layout: post
title:      "Basic Fantasy Overwatch League - Sinatra Project Edition"
date:       2018-05-19 15:28:49 +0000
permalink:  basic_fantasy_overwatch_league_-_sinatra_project_edition
---


Now that I have gotten to a point where I can create more realistic and complicated relationships, I felt that it was necessary to work on a project that more accurately modeled a real world need than I had been able to previously.

Something that came up while my roommates and I were watching Overwatch on Twitch was the viability of a Fantasy League just like there exists Fantasy leagues for other non-esports. So I said for this project why not create a basic template of what that might look like.

The relationships turned out to be a bit more complicated and I ended up with 9 models, 7 controllers, and many views. While this doesn't compare much to full size enterprise applications, it was a pretty big step up from the 3 model apps before. I found that I really enjoyed the logic puzzle of figuring out based on the desired relationship how each model was supposed to interact. Here is an example:

    Every user has their own account.

    There should be multiple different leagues going on at once, shouldn't have to make an entire new site everyone wants their own fantasy league.

    Each user should be able to participate in multiple leagues if they wanted to.

    Leagues need to have multiple users or they will be useless.

    I need the following models:

    User
    League
    User_League

Of course, relationships also had to be modified as I progressed through the actual coding.

The final result is an application where a user can create an account, login, logout, and view their profile. Users can look at, join or create leagues. Once they are a member of a league they can edit the name, add a roster to the league, or delete the league. Once they have a roster in a league, they can choose to add, edit, or remove players from the roster.

Each player has a team and heroes that they play.

The trickiest thing about the project was ensuring that each league has exactly one copy of each Player and once it is in one of the league user's rosters, it cannot be drafted by another user in that same league.

I still would like to add some flash messages so that users know when they've done something in error and I think I will be close to done.





