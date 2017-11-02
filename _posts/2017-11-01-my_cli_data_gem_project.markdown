---
layout: post
title:      "My CLI Data Gem Project"
date:       2017-11-02 02:20:31 +0000
permalink:  my_cli_data_gem_project
---

For my first project, I wanted to test my knowledge and decided to ask my husband what application he would be interested in utilizing. As a starter, he wanted an application that would be able to inquire stock information. 

I questioned him on what information people would be most interested in as a potential investor. The list consisted of the securities’ current price, open price, previous close price, 52-week low-high range, historical price chart, related news articles and description of the company. 

I did research on different websites to see which site would be the least difficult to scrape, followed by the planning on how the CLI should work. I wanted the user to be able to input the stock ticker and then see a menu from where they can choose the information they want to see.  Next, I gave thought into providing the user the capability to continue inquiring other stocks without having to exit and reenter the program. The application is also built to provide the user a list of related news articles from which they can freely select and read. 

I thought about how I wanted to design the classes and have them interact with one another. I created four classes, which consisted of cli, article, stock and scraper. In the scraper class, it creates a new stock object with a collection of attributes whose values are provided from the scraped data. My cli class can utilize this information to provide the user on what they want to reference. Also, to validate the ticker symbol; a stock ticker data text file was created to check to see if there is a match. 

Scraping the data was a bit challenging. I went over previous labs on the scraping section and googled further information to figure out how to obtain the correct data. Watching the videos listed under resources several times helped a lot with completing this project. It also helped to talk about the issues I was having. I would talk to my husband who has no programming background about the problems that would occur and as I am talking about it, come to a realization on what I had to do to fix it while he is left with a blank look on his face. 

After doing this project, I feel like I have a better understanding of object oriented programming. This is the first time I was challenged to create an application from an idea. This experience was very rewarding and encouraging.

