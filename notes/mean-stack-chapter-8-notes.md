MEAN Stack chapter 8 notes
====


MEAN Stack CRUD module is the basic building blocks of a MEAN App.

with MEAN our CRUD module is built from server-side Express components and
an Angular client module.

this chapter:
- set up mongoose model
- create Express controller
- wiring Express routes
- create & organize Angular module
- intro to `ngResource`
- implment Angular module MVC



each CRUD has
- 2 MVC structures supporting Express and Angular modular functionality.
- Express -> mongoose, express controller, and express routing.
- AngularJS -> views, AngularJS controller, service & routing config.
- 

## set up Express components

- create mongoose model used to save & valid articles/documents
- configure express controller
- wire Express routes to produce a RESTful API for controller methods

### p1. mongoose model

- call in mongoose dependencies
- Schema object
- create new Scehma
- -> define model fields
- lastly register this ArticleSchema to be used in Express Controller
- 
### p2. Express configuration

goto **config/mongoose.js**.

- prev make model,
- now: config model to be used by our app
`require` in our `module.exports = function() {...`
- next is create Articles Controller


### p3. setup Express controller

look in **app/controllers**
- create file
- require mongoose Article Obj. Scehma to be used in our new controller
- **before CRUD operations we write a simple function for mongoose error handling.**
- this error message works w/ mongoose error handling object!


```
// in app/controllers/articles.server.controller.js
var getErrorMessage = function(err) {
  if (err.errors) {
    for (var errName in err.errors) {
      if (err.errors[errName].message) return err.errors[errName].
        message;
    }
  } else {
    return 'Unknown server error';
  }
};

```

once error handling is done we may continue to writing our first CRUD controller: **create**.

#### create Express controller

- grabs item from body using HHTTP request body as JSON base object.
- mongoose model `save` method to save it into MongoDB
- i.e.:


```

exports.create = function(req, res) // http req and res
{
  var article = new Article(req.body);  // grabs whole body w/ entered data??
  
  article.creator = req.user; // grabs entry data
  
  
  article.save(function(err) {  // save to db function
    if(err) { // shoots out an error.
      return res.status(400).send({
        message: getErrorMessage(err);  // nice error message.
      });
    } else {
      res.json(article);  // output json data!
    }
  });
};

```



