---
layout: post
title:      "Sinatra Portfolio Project "
date:       2017-11-30 23:03:16 +0000
permalink:  sinatra_portfolio_project
---


For my Sinatra project, I decided to create an app where the user can collect ideas, favorites and interests and put it onto boards. I started by writing a list of what I would need to create this app:

* project folder 
* config directory with environment.rb file where it loads Bundler and also creates  a connection to our database
* config.ru file to load the environment and where the controllers are mounted
* Gemfile to add the gems so that Bundler can install them 
* Rakefile where rake is defined which makes files and setup automated tasks
* app directory to hold MVC directories – models, views,  and controllers
* db directory to run migrations to create tables
* public directory to hold front-end assets

For the MVC file structure, I created 3 models: User, Board and Item. The User would be required to have a username, email address and a password. The User would have many boards and many items through boards. The Board would have a name. It would have many items and belong to a user. The Item would consist of a description, url, and name of the site source. The Item would belong to a board. 

Looking at this helped when I was working on my controllers.  
![CRUD diagram](http://readme-pics.s3.amazonaws.com/Screen%20Shot%202015-12-28%20at%2010.49.31%20AM.png)

While working on this project and getting errors, I am going to be more mindful to remember to put `use Rack::MethodOverride` above all my controllers in config.ru so that the Sinatra Middleware can let the app send patch and delete requests. I also need to keep in mind to place for example: `get ‘/items/new’` before `get '/items/:id` so that Sinatra does not feed all requests for `/items/new` to `/items/:id`.

I was very happy to see everything working. I also enjoyed getting exposure in developing the front end of the project. I am looking forward to learning and building my knowledge base so that I can develop more sophisticated apps. 



