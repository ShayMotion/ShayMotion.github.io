---
layout: post
title:      "React Redux Project - The Guitar Gallery"
date:       2021-01-13 13:57:32 +0000
permalink:  react_redux_project_-_the_guitar_gallery
---


    

As my final portfolio project at Flatiron School I’ve created an alternate application of my previous projects, The Guitar Gallery, which is a continuation of the same concept but utilizing the React and Redux frameworks. What I enjoy about React/Redux is it’s easy integration as a frontend with a Rails API backend and Javascript as the programming language turning a static website into a dynamically functioning software with a user interface and a secure backend database.  

Here is a demonstration of my application:
1. A user can either sign up by entering a username, password, as well as their city, state and country. 
2. Once they hit the sign up button, They are brought to the homepage with a navigation bar and their username is displayed on the top right along with the ability to Log out. 
3. The user can select from a multitude of pages to either view all of the auctions, or create a new auction, as well as view all of the guitars or create a new guitar. 
4. An auction is created by entering a title, start date and end date, and a guitar is created by entering a guitar brand, model year and price.
5. Once submitted the auctions and guitars will be displayed with the correct information from the user’s inputs.

									App.js
App.js is mainframe of the application. Here we have all of the components connected and we’ve imported react and router to create a switch in the DOM that will react based on events that occur when a user interacts with the page. I’ve created an object of App which extends the React component. Upon mounting the object, the current user will be retrieved based on the current session. We’ll render the loggedin, auctions and guitars functionality as properties of App, and establish the switch on the navigation bar, if the user has either signed up or logged in, the home navigation will appear along with an Indication of the current user by displaying the current user’s username. When logged in, there will be 4 paths available, to either view all the auctions, view guitars, create a new auction, or create a new guitar. I’ve included routes in the switch to finding guitars and users based on id, and edit functionality which I’ve included in the code but plan to expand on that functionality in the future. The mapstatetoprops will map the state of the current user, as well as auction and guitar form inputs based on the current state of the store. Finally, we will export the data to the current user of the app based on the state of the store.


									Index.js
Index.js is where the entirety of the DOM is rendered. I’ve imported the essential tools such as the ReactDOM, Provider, Store and BrowserRouter. I’m also rendering the the root document based on the element id and I’ve attached the provider, which is the store.  
					
				
								Components
In the components, the Home.js file is the page that opens at the startup of the app. Here is where a user will signup or login. In login.js, I’ve created the login object which will attach the login form and upon hitting submit the username and password will be rendered into the state. 


									
									Actions
The actions folder is where all the action takes place. In currentUser.js I’ve included the fetch requests for the login, logout and signup information of the user. Rails being hosted on localhost 3002 it’s using JSON to retrieve and send data to and from the backend. I’ve also created fetch requests for the guitar data in myGuitars.js and auction data from myAuctions.js. When a fetch request is triggered the store will dispatch a response of the data from the backend. In auctionForm as well as guitarForm and signupForm I’m getting, reseting, and deleting the information of the formData. 


									Reducers
In the reducers folder, we are declaring the initial state of the forms, which is typically an empty array of attributes. The reducers execute a switch response according to each case of entering the form data. Based on conditionals, the switch returns an action and the store will dispatch a response. 


									Store.js
The store is where the current state of all the components in the app are held. Using thunk as a middleware, redux is able to dispatch responses from the store to and from the frontend. Here we create a reducer which combines the components and then the store is exported to the application.


					          			Building a Rails API
I’ve created a secure backend database with Rails so that we can store all of the information from the user’s inputs.  

											
									Models 

The Users model is equipped with has_secure_password via the bcrypt gem to encrypt user’s private information. A user has many guitars and auctions. It validates a name, username to ensure that the user’s information exists in order to create a new instance of a user. A guitar belongs to a user and an auction. An auction belongs to a user, has many guitars, brands through guitars and models. An auction validates that a title and a user exists.

								Controllers

I’ve included 4 controllers, sessions, users, auctions and guitars. In the sessions controller is where the user authentication logic takes place. This will ensure a user must be logged in and then it will store that session as the current user.

											CORS 
Cross-origin resource sharing (CORS) is a mechanism that allows restricted resources on a web page to be requested from another domain outside the server’s domain. Here I’ve stored my origins which include localhost servers 3000, 3001 and 3002.

Serializers

The Active Model Serializer is used to build the JSON objects. I’ve created 3 serializers, user, auction and guitar. This will allow the application to select only the information that the user is looking for. 


									Routes.rb
In my routes I’ve established the resources for all of the objects. I’ve specified post, delete and get requests for the signup, login, logout, and get current user functionality. This will connect the model to the controller.			

                                                      Migrations

The notable migrations worth mentioned are add user id to auctions, add name to auctions, add auction id to guitars and add user id to guitars. This will establish the objects’ relationships in the database. 


								Gemfile
Some gems worth mentioning that are required in order to use rails with react are the web packer and react on rails gems, as well as fast jsonapi to connect the ruby data into javascript objects. Also the rack-cors gem which secures a server and prevents malicious hackers from entering the API. 

