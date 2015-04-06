some notes
===

checking out how some basic CRUD ops work [here](http://meanjs.org/docs.html#article-example)

##Express backend

MVC -> MC, handling model and controller, Angular handling the views.

1. Mongoose Model

schema objects

2. mongoose schema

used to define the structure of app data.
Entries -> Documents in MongoDB
schemas describing the types of properties they have
++ relations and references exist between them.



3. validation and middleware

where we can add additonal functions that validate our data before saving it
done properly with middleware.. passport??

*middleware* is used whenever we want to execute code before or after we run any kind
of operation on a entry. allowing validation, authorization, monitoring and other operations.


### Express controller

controllers -> add query to db, + perform server side calculations before relaying data to client.

basic CRUD operations in our Express controller are:
- create
- read  // return single article entry
- update  // single article
- delete
- list  // list of all articles
- articleById // sets the current article obj by its ID.
- hasAuthorization  // methods checks if the current user created the current article.

