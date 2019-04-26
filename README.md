# INFO 6210 Ski Resort Recommend

JIAYUE XU /
LIN SHI /
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
 ![1](https://user-images.githubusercontent.com/46548277/56830387-351a1280-6834-11e9-9407-a5aa17a65b7b.jpg)
 
2. Ski resort information from Twitter
From Kaggle, we can get all the ski resort names, use these names as Twitter names to search location of ski resorts, followers and so on. 

Some ski resort name may not have Twitter name, so when we run the code, we need ignore error and continue running.
 
![2](https://user-images.githubusercontent.com/47193601/56831327-becadf80-6836-11e9-9fc3-bc53683a2428.png)
•	Resort_twitter(table in mysql)

![3](https://user-images.githubusercontent.com/47193601/56831347-cc806500-6836-11e9-91fc-b0a0cc2694d5.png)
 

3. Consumer information from Instagram
We use ski resort name got from Kaggle as hashtag and we use instaloader to get users’ information those post posts in specific hashtags. In order to simplify data, we just extract those who posts during 24 hours and get posts likes, post comments and so on.

Some ski resort name may not have hashtag, when we run the code, we need ignore error and continue running.  Some ski resort as hashtags may not have posts during 24 hours, so we will get empty list in our table, we need drop it and finally create a whole table.
 
![4](https://user-images.githubusercontent.com/47193601/56831377-e752d980-6836-11e9-9d74-831fec9f3d4c.png)

•	Inshashtag
 ![5](https://user-images.githubusercontent.com/47193601/56831388-e9b53380-6836-11e9-9a3f-ecd27db031c6.png)

4. Ski resort information from google map
When we get ski resort name, we need input these names to google map, but these ski resort name may not the accurate name in google map. Therefore, the first step, we need add ski resort after every ski resort name. Then we use these names to get longitude and latitude.

The result of format we get from google map API is string, we need exchange it to list.
![6](https://user-images.githubusercontent.com/47193601/56831391-ec178d80-6836-11e9-9549-652bb585edbe.png) 
•	resorts_googleinfo
![7](https://user-images.githubusercontent.com/47193601/56831393-ede15100-6836-11e9-8ad5-021f37c1591d.jpg) 


5. Ski resort information from Dark Sky website
When we get all the longitude and latitude from Google map API, we put it to the Dark Sky website. Then we will get all information like cloud cover, humidity, pressure and so on. 

However, in order to do normalization, we need divide all information to 8 tables.
![8](https://user-images.githubusercontent.com/47193601/56831401-f5a0f580-6836-11e9-898c-2fc8700d4d8f.png) 

•	cloudcover

![9](https://user-images.githubusercontent.com/47193601/56831404-f76ab900-6836-11e9-893d-bea424e64f7e.jpg)

•	humidity

![10](https://user-images.githubusercontent.com/47193601/56831416-018cb780-6837-11e9-9536-1dbcdf3adaca.jpg) 

•	pressure

![11](https://user-images.githubusercontent.com/47193601/56832811-f471c780-683a-11e9-89e3-715f7ae88916.jpg) 

•	temperature_max

![12](https://user-images.githubusercontent.com/47193601/56832815-f76cb800-683a-11e9-81d4-1c1cb8c440a9.jpg) 

•	temperature_min

![13](https://user-images.githubusercontent.com/47193601/56832817-f9367b80-683a-11e9-9169-674d33c462d1.jpg) 

•	visibility

![14](https://user-images.githubusercontent.com/47193601/56832819-fb98d580-683a-11e9-99be-e70043c8b214.jpg) 

•	windspeed

 ![15](https://user-images.githubusercontent.com/47193601/56832824-fd629900-683a-11e9-8b3e-7fdd239f7418.jpg)

III. ER Diagram

![16](https://user-images.githubusercontent.com/47193601/56832832-ff2c5c80-683a-11e9-87db-cb7e8aa6deb4.png)


IV. Code with Documentation

https://github.com/howardxjy/info6210_project_team_Cerberus 


V. News and Trend
We just extract those consumers information from Instagram who post posts during 24 hours in 500 hashtags, everyday we will get total about 1000 posts to MySQL and we have get 5000 posts till today.

And same situation, we extract weather information from Dark sky website during 7 days. Every 7 days, we will update the information in database.

![17](https://user-images.githubusercontent.com/47193601/56833939-115bca00-683e-11e9-86f1-d07e68ced0ac.jpg)

![18](https://user-images.githubusercontent.com/47193601/56833946-1456ba80-683e-11e9-93cd-035258737db4.jpg)

![19](https://user-images.githubusercontent.com/47193601/56833952-16207e00-683e-11e9-91d5-0611b6f5e965.jpg)


VI. Use case to answer those question
•	What are people saying about me(somebody)?
Usecase_1: Find all the posts with a special hashtag or context?

![20](https://user-images.githubusercontent.com/47193601/56832873-15d2b380-683b-11e9-8047-91123083dcde.jpg)
 
•	How viral are my posts?
Usecase_2: Find the ins user with the most posts’ likes?
•	Who should I be following?
Usecase_3: Find someone all posts who have the most posts’ likes.

![21](https://user-images.githubusercontent.com/47193601/56832875-18350d80-683b-11e9-82b1-c3a4ae6a84d7.jpg)

•	What posts are likely to be interesting to me?
Usecase_4: Find all the posts with a particular hashtag and many comments?

![22](https://user-images.githubusercontent.com/47193601/56832901-271bc000-683b-11e9-9fcf-315f328dfa38.jpg) 

•	What post are like mine?
Usecase_5: Find all the posts give a positive comment to the ski resort?

![23](https://user-images.githubusercontent.com/47193601/56832907-28e58380-683b-11e9-8728-0f9e554a4604.jpg)

•	What users post like me?
Usecase_6: Find all the user post between 22:00 between 23:00?

![24](https://user-images.githubusercontent.com/47193601/56832909-2aaf4700-683b-11e9-944a-d6226bca6bb5.jpg) 

•	What topics are trending in my domain?
Usecase_7: Find the most popular resorts’ name based on Instagram likes?

![25](https://user-images.githubusercontent.com/47193601/56832911-2d11a100-683b-11e9-87d8-781b56f3a935.jpg)

•	What keywords/hashtag should I add to my post?
Usecase_8: Add the most likely hashtag to “Abenaki” into my post caption?

![26](https://user-images.githubusercontent.com/47193601/56832917-2edb6480-683b-11e9-950b-549eb583596b.jpg) 

•	Should I follow somebody back?
Usercase_9: Find the consumer who has the most Instagram posts likes for one particular ski resort

![27](https://user-images.githubusercontent.com/47193601/56834095-7c0d0580-683e-11e9-8462-32761effd586.jpg)

VII. Fuzzy search

1. Synonyms 
When we extract users’ posts from Instagram, we will also get many synonyms hashtag cause they are included in those posts. Therefore, we use fuzzywuzzy library to classify those hashtags and select the most matching hashtag as the synonymous hashtags

![28](https://user-images.githubusercontent.com/47193601/56832929-33078200-683b-11e9-9560-6ac7bedddc1d.jpg) 

2. Mis-spellings
When users search a ski resort name, maybe they have a wrong spelling. We need correct them and create a table to update all possible mis-spelling.
 
![29](https://user-images.githubusercontent.com/47193601/56834105-8202e680-683e-11e9-91b1-79054907f0a0.jpg)
 

3. Semantic information
When users post posts, they maybe have many hashtags, those irrelevant hashtags are Semantic information.
 
![30](https://user-images.githubusercontent.com/47193601/56834112-85966d80-683e-11e9-9eaa-8ff60745a97e.jpg)

VIII. Results
We create a database about all ski resort information and then we write code in python to connect our database. Beside we write function to help users to find ideal ski resort. For example, if customers input location they want to go and the ticket price they can afford, they will find all information from our database to recommend some ski resort and customers can choice one of they like.  
Case1 price and location
 
 ![31](https://user-images.githubusercontent.com/47193601/56834114-87603100-683e-11e9-96a1-99996ef68513.jpg)
 
Case2: state and altitude
 

![32](https://user-images.githubusercontent.com/47193601/56834120-8929f480-683e-11e9-9ef9-58965ed3b1c0.jpg) 

IX. Conclusion and Difficulties
We create a database and python as the bottom of the website we connected to the database. Then we write switch case to call database. Therefore, when user search information, we will call function to extract the information they want.

However, the most difficult thing is that we don’t know how to use Django to create a website. There are have not enough time to learn by ourselves this library. So, it’s clearly what we need to do in future. We need use Django to create a website such as search engine and so on. 

X. Citation (90% By Ourself , 10% By The Citation)
1. Kaggle: https://www.kaggle.com/beaubellamy/ski-resort
2. Instagram API: https://instaloader.github.io/index.html
3. Twitter API: https://developer.twitter.com/en/docs.html
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


