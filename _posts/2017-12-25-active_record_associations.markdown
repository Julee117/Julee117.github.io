---
layout: post
title:      "Active Record Associations"
date:       2017-12-25 13:39:11 -0500
permalink:  active_record_associations
---

I am up to the rails project and one of the requirements in the rails project is that our models must include, a `belongs_to`, a `has_many`  and a `has_many :through`.  I feel that it would be helpful for me to go over the associations. 

### ```belongs_to```

A `belongs_to` sets up a one-to-one connection with another model. 

For example, a comment belongs to an article. In the comments table, there will be a column named `article_id`, which is a foreign key that references to articles. A foreign key links one table to another’s primary key. 

Some of the methods added to our model are:
-	`comment.article`
    - This gives us the article that the comment is associated with.
-	`comment.article=(article)`  
    - Instead of writing `comment.article_id = article.id`.
-	`comment.build_article`
    - This is similar to `comment.article = Article.new`.
-	`comment.create_article`
    - The difference between this and the build method is that create method saves the created object where the build method only returns the created object.

### ```has_many```

A `has_many` association specifies a one-to-many association. 

For example, an article has many comments. 

Some of the methods given to us are:
-	`article.comments`  
    - This gives an array of comments associated with it. If there is none found, an empty array is returned.
-	`article.comments<<` 
    - We can add one or more objects to the collection.
- `article.comments.delete`  
    - This removes one or more objects from the collection by setting their foreign keys to `NULL`.
-	`article.comments.destroy` 
    - This removes one or more objects from the collection by running destroy on each record.
-	`article.comments_ids`  
    - This returns an array of associated comments ids.
-	`article.comments.build` 
-	`article.comments.create`


### ```has_many :through```

A `has_many :through` association is often used to set up a many-to-many connection with another model. 

An example of this is many-to-many relationship between programmers and projects through assignments. 

```
class Programmer
  has_many :assignments 
  has_many :projects, through: :assignments 
end 

class Assignment 
  belongs_to :programmer 
  belongs_to :project
end 

class Project 
  has_many :assignments 
  has_many :programmers, through: :assignments 
end 
```

Assignment table will have `programmer_id` and `project_id` columns. 

In addition to having a join table, `has_many :through` association has a join model which allows us to create more columns to store extra information. The collection of join models can be managed via the `has_many` association methods. When destroy or delete methods are called, it will remove the link between the two models, not the models themselves. 

Now, I need to go and start my project. Happy Holidays! 



