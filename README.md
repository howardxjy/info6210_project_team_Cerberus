# INFO 6210 Ski Resort Recommend

JIAYUE XU
LIN SHI
RUOLAN LIAO

Abstract
People like ski but select a good ski resort is a very struggling thing because there are too many factors for customers to decide. This project gathers all information about ski resort including ticket price, ski facility, weather of its city, number of customers per year and so on from 3 social medias to create a database and then we write a function. When customer insert their requirement on our database, we can extract useful information to recommend fitful ski resorts to them.
Keywords
Ski resort, database, function, social media, recommend

I. Introduction
Skiing is a popular sport in the United States. Most people would like to the ski resort to spending vacations with their families. However, there are many choices for them to choose a good ski resort, like weather, location, hill heights, and so on, that all these factors will affect their skiing time. 

Besides, people go to vacation may not only for skiing purpose, they maybe still interested in different scenes and views in the same city.  Looking for a good vacation place including ski resorts seems to be a task which involve bunch of research works. People even need to check the weather forecast for each of dream resort. 

As a result, we want to build a database about all information about ski resorts and other kind of information for the cities, weather forecast, scenes and so on. The database will help people evaluate the comprehensive destination that satisfies ski purpose. It helps people to make a better choice.
 
II. Data Resource
1. Ski resort information from Kaggle
We get ski resort information from Kaggle, but it includes other countries’ ski resort information excepted to the America. So we need classify ski resorts those in the USA.
•	ski_resort_usa
 
 
2. Ski resort information from Twitter
From Kaggle, we can get all the ski resort names, use these names as Twitter names to search location of ski resorts, followers and so on. 

Some ski resort name may not have Twitter name, so when we run the code, we need ignore error and continue running.
 

•	Resort_twitter(table in mysql)

 

3. Consumer information from Instagram
We use ski resort name got from Kaggle as hashtag and we use instaloader to get users’ information those post posts in specific hashtags. In order to simplify data, we just extract those who posts during 24 hours and get posts likes, post comments and so on.

Some ski resort name may not have hashtag, when we run the code, we need ignore error and continue running.  Some ski resort as hashtags may not have posts during 24 hours, so we will get empty list in our table, we need drop it and finally create a whole table.
 

•	Inshashtag
 

4. Ski resort information from google map
When we get ski resort name, we need input these names to google map, but these ski resort name may not the accurate name in google map. Therefore, the first step, we need add ski resort after every ski resort name. Then we use these names to get longitude and latitude.

The result of format we get from google map API is string, we need exchange it to list.
 
•	resorts_googleinfo
 


5. Ski resort information from Dark Sky website
When we get all the longitude and latitude from Google map API, we put it to the Dark Sky website. Then we will get all information like cloud cover, humidity, pressure and so on. 

However, in order to do normalization, we need divide all information to 8 tables.
 

•	cloudcover
 
•	humidity
 
•	pressure
 
•	temperature_max
 
•	temperature_min
 
•	visibility
 
•	windspeed
 

III. News and Trend
We just extract those consumers information from Instagram who post posts during 24 hours in 500 hashtags, everyday we will get total about 1000 posts to MySQL and we have get 5000 posts till today.

And same situation, we extract weather information from Dark sky website during 7 days. Every 7 days, we will update the information in database.

 
 
 

IV. Use case to answer those question
•	What are people saying about me(somebody)?
Usecase_1: Find all the posts with a special hashtag or context?
 
•	How viral are my posts?
Usecase_2: Find the ins user with the most posts’ likes?
•	Who should I be following?
Usecase_3: Find someone all posts who have the most posts’ likes.
 
•	What posts are likely to be interesting to me?
Usecase_4: Find all the posts with a particular hashtag and many comments?
 
•	What post are like mine?
Usecase_5: Find all the posts give a positive comment to the ski resort?
                   
•	What users post like me?
Usecase_6: Find all the user post between 22:00 between 23:00?
 
•	What topics are trending in my domain?
Usecase_7: Find the most popular resorts’ name based on Instagram likes?
 
•	What keywords/hashtag should I add to my post?
Usecase_8: Add the most likely hashtag to “Abenaki” into my post caption?
 
•	Should I follow somebody back?
Usercase_9: Find the consumer who has the most Instagram posts likes for one particular ski resort
 

V. Fuzzy search
1. Synonyms 
When we extract users’ posts from Instagram, we will also get many synonyms hashtag cause they are included in those posts. Therefore, we use fuzzywuzzy library to classify those hashtags and select the most matching hashtag as the synonymous hashtags
 

2. Mis-spellings
When users search a ski resort name, maybe they have a wrong spelling. We need correct them and create a table to update all possible mis-spelling.
 

3. Semantic information
When users post posts, they maybe have many hashtags, those irrelevant hashtags are Semantic information.
 


VI. Results
We create a database about all ski resort information and then we write code in python to connect our database. Beside we write function to help users to find ideal ski resort. For example, if customers input location they want to go and the ticket price they can afford, they will find all information from our database to recommend some ski resort and customers can choice one of they like.  
Case1 price and location
 
Case2: state and altitude
 

VII. Conclusion and Difficulties
We create a database and python as the bottom of the website we connected to the database. Then we write switch case to call database. Therefore, when user search information, we will call function to extract the information they want.

However, the most difficult thing is that we don’t know how to use Django to create a website. There are have not enough time to learn by ourselves this library. So, it’s clearly what we need to do in future. We need use Django to create a website such as search engine and so on. 

VIII. Citation
1. Kaggle: https://www.kaggle.com/beaubellamy/ski-resort
2. Instagram API: https://instaloader.github.io/index.html
3.Twitter API: https://developer.twitter.com/en/docs.html
4. Google map API: https://developers.google.com/maps/documentation/maps-static/intro
5. Weather API: https://rapidapi.com/darkskyapis/api/dark-sky?utm_source=google&utm_medium=cpc&campaign=1755331082&keyword=dark%20sky%20api&gclid=CjwKCAjwtYXmBRAOEiwAYsyl3E0gIvlOFxfTBLunnM7PgWco4SrEjF8P_3YfVcp60wT77yQoh_zYWxoCRHgQAvD_BwE

MIT License
	

	Copyright (c) 2019 Jiayue Xu, Lin shi, Ruolan Liao
	

	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:
	

	The above copyright notice and this permission notice shall be included in all
	copies or substantial portions of the Software.
	

	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
	SOFTWARE.


