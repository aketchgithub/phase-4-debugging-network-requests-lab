# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged:

- Update the number of likes for a toy

  - How I debugged:

- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged:
 <!-- Add a new toy when form is submitted; -->
 Made frontend requests, by enterig some data in the create new toys input form then submitted. 
 Then inspected Console tab, and the Network tab. The request returns a 500 Internal Server Error.
 Checked the rails server logs in the terminal and saw, 
 NameError (uninitialized constant ToysController::Toys):
 This gave me a clear place to look for the error indicating that we were using a constant 'Toys' incorrectly.

 <!-- update the number of likes for a toy -->
 Tried updating the likes for toy in the frontend, well, it errored out a syntax error. This is because we expect the server to return a string of JSON-formatted data, but the server is not returning any content.
 Back to our toys controller.rb file, updated the 'update action' to render to json and updating the likes should be working!

 <!-- Donating a toy to Goodwill and delete it from the database -->
 By donating a toy to Goodwill, it errored out 
 ActionController::RoutingError (No route matches [DELETE] "/toys/1"):
 The error message indicates there is no route defined for the delete method on the '/toys/:id' endpoint. To fix this, I defined the route for delete method on the '/toys/:id endpoint in the 'config/routes.rb' file.
 
 

