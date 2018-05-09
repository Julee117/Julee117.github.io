---
layout: post
title:      "Brief Overview of Caching in Ruby on Rails"
date:       2018-05-09 01:08:43 +0000
permalink:  brief_overview_of_caching_in_ruby_on_rails
---


Caching is the process of storing data so that future requests for that data can be served faster. This can improve the speed of your website and improve the user experience. There are various types of caching in Ruby on Rails such as:

- HTTP caching 
- Model caching
- Fragment caching
- Action caching
- Page caching

### HTTP Caching

HTTP caching utilizes `If-None-Match` and `If-Modified-Since` headers. ETags aka entity tags are used to verify whether the page was modified. The server compares the current ETag to the one provided by the client and if they are both the same, it means that the page was not modified. However, if they do not match, the server will respond with a new ETag and the updated response. 

### Model Caching

Model caching aka low level caching caches a value or query result. The most efficient way to implement this is to use the `Rails.cache.fetch` method. 

```
def cached 
  Rails.cache.fetch(“event”) { Event.all }
end 
```

`Rails.cache.fetch` method reads and writes to the cache. It fetches data from the cache with the given key. If there is data, then the data is returned however if it is not, `nil` will be returned. In the case `nil` is returned and a block was passed, that block will be passed the key and executed where the return value of the block will be written to the cache.

### Fragment Caching

In fragment caching, only a part of the page is being cached.  For example, if we want to cache each event: 

```
<% @events.each do |event| %>
  <% cache event do %>
    <%= event.title %> 
  <% end %>
<% end %> 
```

### Page Caching

In page caching, the page is saved to a file inside the public directory. This allows future requests of sending the file without going through the entire Rails stack. However, we cannot use this for pages that need authentication. Page caching has been removed from Rails 4 so you need to add `gem “actionpack-page_caching”`.

### Action Caching

Action caching is used for pages requiring authentication or other before/after filters. Add `caches_action :<action_name>` to your controller to turn on caching for specific actions.

```
class UsersController < ApplicationController
  caches_action :index

  def index
    @users = User.all
  end

end 
```

Action caching also has been removed from Rails 4 so you need to add `gem “actionpack-page_caching”`. 

You can read further [here](https://github.com/rails/actionpack-page_caching) on how to utilize the gem. To also read more about caching, you can find that [here](http://guides.rubyonrails.org/caching_with_rails.html#low-level-caching).

