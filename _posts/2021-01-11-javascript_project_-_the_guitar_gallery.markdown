---
layout: post
title:      "Javascript Project - The Guitar Gallery"
date:       2021-01-11 20:23:24 +0000
permalink:  javascript_project_-_the_guitar_gallery
---


For my fourth project I will be building The Guitar Gallery as a single page application using Ruby on Rails as a backend database. The guitar gallery is an online guitar auction and database that catalogs rare guitars that are currently up for auction. This app has 2 components, auction and guitar which we will combine so that we can see a list of current auctions and guitars available for those auctions. The “Create a New Auction” form will allow users to enter a title, start date and end date for their new auction. Once created, they can then add a guitar by entering the guitar brand, model, year, price and then they can select from a drop down list of current auctions. 
			

										index.html
This is the main page and navigation of the guitar gallery app. The style inherits it’s attributes from styles.css. The page has 3 containers, a Current Auctions container which displays the current auctions. We have the auction form, and the guitar form. At the bottom here is where the javascript scripts are rendered.


										AJAX/Fetch	

Asynchronous Javascript is a common technology that many websites use to dynamically present data. The frontend will use a multitude of Fetch requests to the backend in order to function properly. I’ve included 5 fetch requests to the API, to get auctions, create an auction, delete an auction, get guitars and delete a guitar. By accessing Rails via localhost 3000, we’re able to have the frontend and the backend communicating. 

		                                                 	index.js
Here we have the point of contact of the class objects from the frontend to communicate to the backend using localhost 3000 with the API Host URL being auctions and guitars. We have an event listener with a DOMContentLoaded which loads the create auction form and the create guitar form as well as a fetch of the auctions as soon as the page loads. Once the user hits submit, it will trigger an event to create an auction or a guitar. 


										auction.js
Our get elements are listed at the top which are retrieving the data from the backend according to their ‘id’. Here we instantiate a class object of auction with the attributes of id, title, start date and end date. An auction retrieves the current array of guitars. The render auctions function fills in the auction select element in the guitar form with the auctions fetched from the backend. The renderAuctionsOptions function renders the auction select data and then clears that data once submitted to reset the form. The fetchAuctions function will retrieve the data for the auctions list and then executes the renderAuctions and renderAuctionOptions functions. The createAuction is an event. I’ve included an event.preventDefault which prevents the entire page from refreshing after submitting the auction form. The createAuction function is a Post method which sends the data form the user’s input to the database. We have our render function which will render instances of the  auctions entered into each element and then functions to delete and reset the auctions. Finally, here is the fetch request to delete the auction from the database.




										guitar.js
In the guitar.js component we have our get elements for all of the inputs in the guitar form correlating with the attributes of the guitar as well as an auction selection list to choose the auction which the guitar will belong to. I’ve created a class object of Guitar with attributes such as id, brand, model, year, and price. The createGuitar function will set an event that will fetch the user’s data for the guitar and send it to the database. The response will be that an auction is retrieved to attach the guitar and then the guitar form resets. We have a render method for the inner text of the guitar form inputs. Finally, here is the fetch request to delete a guitar from the database.



									   Ruby on Rails
In the Ruby on Rails backend we are creating a persisting database for the frontend. In the controllers we are creating auctions and guitars using a serializer with a JSON render to convert the ruby object into a javascript object. In the routes.rb I’ve stated the resources for the guitars and auctions objects. In the database I’ve added an auction_id column to a guitar so that we can apply a guitar to an auction. 
