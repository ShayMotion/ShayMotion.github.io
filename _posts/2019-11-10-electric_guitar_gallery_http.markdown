---
layout: post
title:      "Electric Guitar Gallery"
date:       2019-11-10 12:51:07 -0500
permalink:  electric_guitar_gallery_http
---

A CLI Data Gem Project in Ruby

For my first portfolio project, I wanted to create something fun, personal and useful. My initial idea came from reading a blog about the "Top 100 Guitars Sold at Auction" which featured many famous guitars, the date it sold and the price it was sold for. 

After inspecting the backend of the website, I had realized that the HTML was very disorganized and would just over-complicate the project, especially with an overload of information which may affect the user experience ultimately.

So, in order to simplify the idea, I chose another website with less information and much easier div classes so that I may scrape the appropriate data to generate a simple program in Ruby that displays the Top 10 Electric Guitars, a decimal rating from 1.0-5.0, and a short summary reviewing each guitar, as displayed on the website below. 

https://www.guitarfella.com/best-electric-guitar/


Initially I had installed the Nokogiri and Open-URI gems so that I may scrape the data of the website. I had many obstacles on the way, such as noticing extra bits of the website's data which was appearing in my scraper class' results. I had done much research so that I may precisely capture each of the appropriate information extracted in between the HTML coding.

"Guitar Gallery" being the module, I wanted to create a separate "Guitar" class so I may describe the object to Ruby. It includes a name, rating and summary and the guitar object saves itself to an array of guitars.

The Command Line Interface includes a multitude of methods so that the user experience may be simple and clear. It opens by greeting the user and listing the 10 guitars available in the gallery, along with a method that correlates a number from 1-10 that the user will input into the interface which will match their selection. 

Once the user has chosen a guitar, they will be given the information of the guitar such as the name, decimal rating and summary which they then will be asked if they would like to view the information of another guitar. They will be given the choice of yes or no, if yes the program will repeat itself. If no, the program will bid farewell to the user. 

For me, the most rewarding part after a mountain of errors was finally seeing the project come alive. The "call" method was used to be the initiation method that starts up the program. By CDing into the project and entering bin/GuitarGallery the call method in the GuitarGallery console will run the program. You may clone the project from here: git@github.com:ShayMotion/cli9.git

In the future, I would connect the program with a guitar gallery on a website that includes pictures, and a more in-depth description of the guitars. Maybe some links to where they can purchase the guitar. But for now, I'm super happy to have created my very first program and look forward to building many more!
