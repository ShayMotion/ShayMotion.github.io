---
layout: post
title:      "Programming a Guitar Gallery Auction in Sinatra"
date:       2021-01-05 15:05:10 -0500
permalink:  programming_a_guitar_gallery_auction_in_sinatra
---

                                                                                                            
                                                                                                        
After completing my CLI Gem Project at Flatiron School I'm really starting to grasp the fundamental concepts of Ruby on Rails, and programming in general, for that matter. For my second project, I will now create an application based on Sinatra which I've found to be a quick and easy way to build a functioning database with a user interface that persists and collect data via a user's input.
​
As an Electric Guitarist and guitar collector, I've been inspired to build a database for an online guitar auction that allows fellow guitar collectors to create an account and add their guitar to an auction gallery which displays the important information about the particular guitar item such as the "Brand", "Model", "Year", and "Price". Users can either add their guitars to an existing auction, or create a new auction which contains a "Title", "Start Date" and "End Date". An Auction also displays a list of guitars available for that auction.


I will now demonstrate a walkthrough of the app:

1. First, the user signs up, or if they already have an account they can simply login. 
2. A user can create a new auction, enter a start and end date and hit submit. 
3. They can then browse a list of all the current auctions. 
4. A user can also add a new guitar to an existing auction, by selection the respective auction title and then inputting the brand, model, year and price of that guitar. 
5. By hitting submit they will add a guitar to an auction. 
6. When viewing an auction, the user can see the list of guitars for that auction which they can also edit and delete. 
7. A user can also edit the information of the auction.
8. Finally a user can view their personal account along with their own listings of auctions and guitars.
​
​
                                                                                       Sinatra Setup Process
                                                                                             
The application has been created using the Corneal gem, (which by the way, I heard was created by a former Flatiron student). It's a convenient way to fast-track your Sinatra application that comes fully-loaded with all of the necessary documentation, folder structure and Ruby gems, everything you need to get started. 


Building the Database and Migration Files

An ActiveRecord database is essential to having a functional application the collects and persists data. I’ve included 3 tables in the database, Users, Auctions, and Guitars. Some of the unique datatypes worth mentioning are the “datetime” datatype which allows me to receive the data in a calendar-date format. I’ve used an integer datatype for the auction_id and user_id. I’ve created a “float datatype to format the “price” attribute of the Guitar model and most of the rest of the datatypes are strings. Finally I’ve added the auction_id to the Guitars table. This is because a guitar must belong to an auction in order to exist. More in this in the next paragraph. 

Creating The Models and Relationships

The 3 models being Users, Auctions, and Guitars, it’s required that the relationships must be established. In this case, a Guitar belongs to a User and an Auction. A User has many auctions and guitars. A guitar can only belong to one User through an auction. I’ve also set some validations for the User to require a email, username and password and that the email and username are unique. The authenticate method was created as a checker for the password, using a conditional statement- if the User’s password is exactly a password then save itself, or else return false. The Auctions model validates that a title, start date and end date are present. I’ve also added some methods to format how slugs are displayed, as we as a method to find an auction by it’s slug. 
				


Setting Up The Views 

The view is where we render and test the routes in the controller files. For each object, I’ve created a view for the index, create, edit and show pages. The forms were created using POST requests will allow us to grab the data from the user’s input. On the edit pages I’m using a PATCH request which will update the data from the user’s input. On the show pages I’m using an ‘each’ loop to iterate over the indexes and for the user’s account they can view the guitars and auction’s they’ve personally created.
 
Building the Controllers

The controllers are responsible for handling the logic of the app. Here I’ve created controllers for the user, guitar and auctions objects. The user controller is equipped with get requests, as well as post, patch and delete requests to create, read, update and delete instances of users. In the guitars controller, I have a checker on the index and new requests so that a user must be logged in to add a guitar to an auction. The auction controller has basically the functionality as the guitars controllers, as it creates a new auction based on the current user. The CRUD routes are used to direct the models to the views. 

The Layout

I’ve created a navigation bar in the user’s layout which displays all of the links in the navigation to make the app functional and user-friendly. 

Here’s my GitHub repository for a more in-depth view of the programming: https://github.com/ShayMotion/sinatra-final
			
                                                                    
Gemfile Contents

* Sinatra: To transform my Ruby application into an application that can respond to HTTP requests&#x2028;• ActiveRecord: To map my objects to the database.&#x2028;• Sinatra-ActiveRecord: To dealing with my SQL database using the ActiveRecord ORM.&#x2028;• Rake: To run my tasks.&#x2028;• Require_all: To execute my code from other files.&#x2028;• Sqlite3: To manage my data in the database.&#x2028;• Shotgun: To test my Ruby application in the browser.&#x2028;• Pry: To debug my code.&#x2028;• Bcrypt: To hash/salt users password.&#x2028;• Sinatra-Flash: To display custom error messages.
```
