---
layout: post
title:      "Scopes vs Class Methods"
date:       2020-03-05 14:10:02 -0500
permalink:  scopes_vs_class_methods
---


So lets start with this, "Every scope is a class method, but not every class method is a scope." smart talk lol.

Scopes are basically queries that are defined inside models as class methods. The reason they are different from regular class methods because they use SQL queries to search through the database.

A regular class method uses ruby to search the database for a specific record or records. This is a bad practice to retrieve data because ruby is very bad at this. The alternative option as I said is scopes which is much better in retrieving records from the database.

Example:

Scope
```
def self.search(title)
        where(title: title)
end
```

Regular class method
```
def self.search(title)
       Post.all.select { |post| post.title == title }
end
```

We noticed in the first method we used "where" which uses SQL quires that is faster in getting the post with the given title. While in the second method we used plain ruby code to find that post which is slower.

So in general, it is very good practice to use Scopes if you want to query the database.
