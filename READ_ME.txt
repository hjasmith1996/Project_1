Read me:

With this project, I am scraping data to compare the local weather to stock exchanges market cap and trade volume. Perhaps some sort of non-trivial correlation can be found. This project succeeds in getting a wealth of data for the weather and a sizable amount regarding the stock markets.

The first part of the project is concerned with choosing what locations to gather the data of the weather from. Obviously, weather occurs globally, so I had to trim the locations down. I chose to select the locations which are where the world’s largest stock exchanges are located. This will give me a direct relationship from the locality of the weather to the locality of the stock market. 

Wikipedia gives a list of the most popular stock markets by market share. This is however only an up-to-date list. It only gives me the data for the most recent month. To look for information on previous months, I will have to check the history of edits for the page. Editors would update the list to the most recent values at the time, so searching for data this way is quite reliable. 

With the program, I go to the page showing all the edits and expand the list so it shows information of 500 edits. I was only able to scrap to edits going back towards 2017 as the format of the page changes significantly after this. I don't even go this far back anyway, as I ran into a few bugs here. I went back a year. The wealth of data comes later where the location is linked to the month. This would lead to almost 4000 scrapings of the weather page. The list of list here is exported to a CSV which would be cleaned later. 

I find the list of the edits and click on each link one by one. This each time takes me to the actual wikipedia page. Here I collect information from each row of the table. This includes the ranking of the stock exchange, its name, its location (which is extremely important). It is the most effective method to also scrap information of the row’s monthly trade volume and market cap now. This information is all stored in a list of two entry lists. The innermost list has the month and year combination as the first entry and the dictionary containing all the scrapped information for that month in the second entry.  

The next thing I did was put all of my locations into a non duplicating list. When we are scraping the weather website, we can edit the url to go to a specific location by inputting its key. This is a prelude to the next part where we find all the keys. To find all the locations we use severely for loops contained inside each other. This searches our collection of data in every place where the locations can be inserted. They are then added to a regular list of locations if the location has not been added already. 

Now we can move on to the next part which involves putting all of these locations into the search bar of the weather page. We will use selenium to go to the page and find the key from the URL. Some tricks are used with selenium involving waiting at certain areas for pages to load and search results to appear. I also wait for longer periods than originally stated if links were found to not contain the keys we were scraping for. Some locations listed as cities in the wikipedia page do not lead me to the correct location in the weather page using this method. This includes Hong Kong and Mexico City. These expectations were dealt with on an individual basis. 

A new dictionary is created here with a one to one link of the locations and the location keys. I have called this a matching dictionary as it exists to give me easy access to every location key instantly. 

The way I have collected data means that I have correlated each month-year combination to a lot of locations (around 18 each). Another dictionary like the one we had before is needed that explicitly links the two without duplication. This was completed quite quickly by unpacking the list of dictionaries we originally scrapped with. 

I will now do my main web scraping on the weather website. For each month and location combination, I will go through all the days of that month in that location. The URL was edited by me to lead directly to the weather for that day in that location. Most of the relevant data is scraped from this page including the condition of the rain fall each hour of the day. Since this is qualitative data, I will find the modal average to give the day an average condition in this respect. This is to be done later. 

Having my list of lists, we can export it to a csv file. 
