---
layout: post
title:      "Ruby on Rails Project - The Guitar Gallery"
date:       2021-01-06 12:28:47 -0500
permalink:  ruby_on_rails_project_-_the_guitar_gallery
---


For my third project at Flatiron School I’ve created a continuation of the Sinatra project; a more in-depth version of the Guitar Gallery Auction app. The original app allows for a user to signup, log in, create an auction, create a guitar and then view all of the guitars available for the current auctions. This version allows for a user to create an auction in multiple locations nationwide. I’ve also added the functionality of signing up securely with a Facebook account, using the Omniauth gem. For usability, I’ve included some errors and checkers which will help the user enter in the correct information and prevent bad data from polluting the database of the app. Finally I’ve improved the user interface compared to the earlier version which is all text based. This application is an upgrade stylistically, in security and also in functionality. 


				      Creating The Models and Relationships

The 3 models being Users, Auctions, and Guitars, it’s required that the relationships must be established. In this case, a Guitar belongs to a User and an Auction. A User has many auctions and guitars. I’ve also set some validations for the User to require a email, username and password and that the email and username are unique. The Auctions model validates that a title, start date and end date are present. A location has many auctions and an auction validates that a location exists, as well as a title, start date and end date. A guitar is validated with an auction_id, as well as a brand, model, year and price. Using a scope method, we can ensure that the guitars will be sorted alphabetically based on the guitar’s brand. In the user’s model I’ve created a method, “find or create from auth hash” which converts the information from a user’s Facebook profile to fill in the account information such as name, username, and email address.

								Serializers 
I’ve included 4 serializers, users, guitars, auctions, and locations which uses FastJSONapi to format the information in an organized manner via strings.
		
							
								Setting Up The Views

The view is where we render and test the routes in the controller files. For each object, I’ve created a view for the index, create, edit and show pages. The forms were created using POST requests will allow us to grab the data from the user’s input. On the edit pages I’m using a PATCH request which will update the data from the user’s input. On the Users show page I’m using an ‘each’ loop to iterate over the indexes and for the user’s account they can view the guitars and auction’s they’ve personally created. In the objects’ ‘new’ pages I’m using a form_for to grab the user’s inputs and I’ve included error methods to improve the functionality of the app, informing users when they’ve entered incorrect information. In the layouts I’ve included a helper method for the errors. As for the layout, I’ve designed the navigation bar in application.html.erb. The nav links include the routes which communicates with the model via the controller. Sessions index contains the root page which displays the welcome header and if a user is not logged in they are prompted to login, and if they are logged in their username is displayed.

						   Building the Controllers

The controllers are responsible for handling the logic of the app. Here I’ve created controllers for the user, sessions, guitars and auctions objects. The controllers are equipped with methods such as index, show, create, new and destroy, along with strong params to narrow down the search in the database for precisely the information we’re requiring. This prevents errors or bad data being entered into the database. JSON objects are being used to render ruby into html formatting. The sessions controller is where the omniauth create method is stored. It converts third party user login info into user’s data which then gets stored in a session.   The omniauth.rb file in the initializers folder is where my personal Facebook API key is located. 


									Routes
Here we can see the the routes for all of the objects. In the login routes, I have a session which is created via the omniauth provider, in this case Facebook, which will redirect to the index once logged in. There is a nested index route for joining users and auctions based on a combined id. I also have nested resources for joining users to their guitars. 


			                            	Migrations	 

The migrations table is where we format the attribute columns in the database tables. I’ve created a table for all the objects, plus some tables to combine the auction_id to guitars, email to users, user_id to guitars and guitar_id to auctions. The schema also displays all of the objects and their attributes in the database tables.


							Gemfile

Some interesting gems worth mentioning that were used to make this app are the omniauth gem to include all of the Facebook dependencies. The fast_jsonapi is used to build objects and convert them to information usable in web browser. Bcrypt is helpful to encrypt username and password data which ensures a secure login process for those signing up and logging in without using a third party app for login purposes.

