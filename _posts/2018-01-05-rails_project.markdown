---
layout: post
title:      "Rails Project"
date:       2018-01-05 16:29:52 +0000
permalink:  rails_project
---


For my Rails project, I created an app where each user has a calendar. A user can create event notifications such as dinners, appointments, meet ups, etc.  The notification consists of an event title, note, date, start time, end time and location. A user has the ability to notify others and place the notification on their calendars. Only the creator can edit and delete the notification that will be updated to everyone the user notified. The person who has been notified is able to only remove the event from their own calendar. 

I used the "Simple Calendar" gem for my project. I watched YouTube clips of Chris Oliver explaining his process of creating this gem. This introduced me to methods I did not know Rails had such as `beginning_of_week` which returns a new date/time of the start of the week on a given day, `beginning_of_month`, `end_of_week`, etc from module DateandTime::Calculations. In my app, the user has a month view with all the events’ titles scheduled on that month. The user can click on the title, which will show them the full details of the specific event. 

I created nested resource routes with calendars and events.
```
resources :calendars, param: :name do
    resources :events
  end
```

This created routes such as `/calendars/:calendar_name/events/:id`. This route would show the specific event of that user’s calendar.  

I created a nested form of the new/edit event page where the user can: 
- Check off one or multiple users to send the notification to 
- Select date and time 
- Select from a list of locations or create a new location 
- Add more users when they edit without creating duplicates to already notified users’ calendars 

Doing this project was eye-opening as it made me realize how much goes on behind the scenes of the many applications/tools that we use daily. As I was developing my app, I had to go back several times to update my codes and associations to accommodate new parameters added during the lifecycle of the project. In the future, I would like to revisit this project and create more functionality as I gain more knowledge.  


