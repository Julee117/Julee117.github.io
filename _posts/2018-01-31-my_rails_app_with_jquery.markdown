---
layout: post
title:      "My Rails App with jQuery"
date:       2018-02-01 03:04:39 +0000
permalink:  my_rails_app_with_jquery
---


In this project, I had to expand my rails app by adding dynamic features through jQuery and JSON API. As a recap, I created a rails app where each user has a calendar. The user can create event notifications, notify others and place the notification on their calendars. 

First, I  installed `gem ‘active_model_serializers’`. ActiveModel::Serializer helps us create custom JSON. 

We generate a serializer by: 

`rails g serializer comment`

We can place in attributes that we would like to whitelist and place `has_many/has_one/belongs_to` declarations. I added the functionality for users to add comments to events. I created serializers for Comment, User and Event. Comment belongs to user and event. User and Event has many comments. 

One of the project’s requirements was to render an index page. I rendered the comments index page to display the comments on the event’s show page.  In Comments controller, I updated the index method to be able to respond to json. 

```
def index
   @comments = @event.comments
   respond_to do |format|
     format.html
     format.json {render json: @comments}
   end
end
```
	
I added a “Comments” button where the user can click on it to see all the comments for that event. When the user clicks on the “Comments” button again, it hides the comments. 

```
$(".all-comments").on('click', function(e) {
    e.preventDefault();
    $.get(this.href + ".json", function(response) {
      const $div = $("div.comments")
      $div.fadeToggle()
      $div.html("")
      response.forEach(function(comment) {
        if (comment.content != "") {
          $div.append('<div class="comments-show">' + '<strong>' + 
					comment.user.username.charAt(0).toUpperCase() + comment.user.username.slice(1) 
					+ '</strong>: ' + comment.content + '</div><br>')
        }
      })
    })
  })
```

Another requirement was to translate the JSON responses into JavaScript Model Objects and the Model Objects must have at least one method on the prototype. By creating a Constructor function, objects can be created with those properties. 

```
function Event(event) {
  this.id = event.id
  this.title = event.title
  this.date = event.date
  this.start_time = event.start_time
  this.end_time = event.end_time
  this.note = event.note
  this.creator = event.creator
  this.users = event.users
  this.location = event.location
  this.comments = event.comments
}
```

I created displayEvent method to add to the prototype.

```
Event.prototype.displayEvent = function() {
  let eventHtml = `
  <h1>${this.title}</h1>
  <p>Date: ${this.convertToDate()}</p>
  <p>Start Time: ${this.convertStartTime()}</p>
  <p>End Time: ${this.convertEndTime()}</p>
  ${this.noteLocationName()}
  <p>${this.displayAddress()}</p>
  <p>Creator: ${this.creator}</p>
  <p>Notified: ${this.getUsers()}</p>
  `
  return eventHtml
}
```

I rendered the event’s show page to allow the user to sift through that day’s events by clicking a “Next Event” button.

```
$(".next-event").on('click', function(e) {
  e.preventDefault()
  let id= $(this).attr('data-id')
  $.get(`${id}/next`, function(data) {
    $(".show").html("")
    let newEvent = new Event(data)
    let event = newEvent.displayEvent()
    $(".show").append(event)
    $(".next-event").attr("data-id", data["id"])
    $(".prev-event").attr("data-id", data["id"])
    history.pushState({}, "", data["id"])
    $(".all-comments").attr("href", `/events/${data["id"]}/comments`)
})
```

`history.pushState()` allows you to change the URL displayed in the browser and add history entries. It takes in 3 parameters:
1.	state object – This is an object which is associated with a history
2.	title – According to Mozilla, Firefox currently ignores this parameter. We can parse an empty string or pass a short title for the state.
3.	URL – We place in the URL we would like to display in the browser. The browser won’t attempt to load this URL but may do so if the user restarts the browser.

The process in building this project gave me a new level of appreciation for all the intricacies behind the scenes of a well developed website. It also made me more aware of the thought process involved in creating websites that are visually appealing and user friendly. This is something that I want to continue to improve upon. 



