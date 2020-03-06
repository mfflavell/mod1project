# Film Analysis Project
Flatiron Module 1 Media Project
Rajeev Panwar & Frank Flavell

# Project Overview & Business Case

Scenario: Microsoft is interested in entering the movie business to establish the company as a leader in film production capabilitues and to gain additional profits.  We have been tasked with gathering and analyzing movie data to provide the company with insights and recommendations.  We aim to answer the following questions:

*  Is this a good time to enter the film industry?
*  What is a realistic budget range for a blockbuster film?
*  What genres are the most profitable?
*  What factors correlate the most with profitability and could be used as a proxy?
*  What companies would be Microsoft's main competitors?

# Approach

Our process had 5 parts:
*  Review of available data on sites like IMDB, Box Office Mojo, TMDB, and Rotten Tomatoes.
*  Web scrapping Box Office Mojo for film financials using a Python Jupyter Notebook and Beautifulsoup.
*  API requests to TMDB for film details using Requests.
*  Cleaning and analyzing the data using Pandas.
*  Visualizing our insights using Seaborn.

# Review of Data Sources

After reviewing the available film data online, we determined that Box Office Mojo and TMDB would be the easiest sources for our project.  Box Office Mojo has a relatively simple user interface compared to its parent site, IMDB, and provided much of its data in the form of tables perfect for web scrapping.  And TMDB has a very developer friendly API section where we could request an API key and browse the many ways we could access their data.  Of all the sites, Rotten Tomatoes was the most difficult to access with a sluggish API and a complex user interface making it difficult to obtain ratings from the html.

# Gathering Data Using Web Scrapping

We identified the pages containg the data we needed on Box Office Mojo and copied and pasted the URLs into our Python Jupyter Notebook.  We imported Beautifulsoup to import the html 'soup' and parsed it according to specific html tags.  We then iterated over the html code to isolate the exact data points we needed and organized that data into a list of lists.  We repeated the process for each webpage and eventually combined our lists together into one big list of data.  We turned that list into a Pandas dataframe to clean it up.

One of the key data points we obtained was the IMDB ID for each movie, which we could use to obtain more details for each movie through the TMDB API.

# Gathering Data Using API Requests

Using a list of IMDB IDs for all of the movies we had scrapped from Box Office Mojo, we made 1,000 API requests using the Request package.  We were able to automate the process using a for loop to iterate over the list of IMDB IDs and insert each unique ID into the API request URL.  Each request resulted in a json file with a dictionary containing the details of each movie.  All of the dictionaries were compiled into a master list.

We turned this list of dictionaries into a Pandas dataframe and completed some cursory cleanup before merging the Box Office Mojo dataframe with the TMDB dataframe using a join on the IMDB IDs.

We then exported the dataframe to a .csv file so we could access it in the future and make several backups.

# Cleaning the Data using Pandas

We spent many hours cleaning the data using Pandas Dataframes and Series to prepare it for analysis.  We removed or updated Null values.  Some columns contained a collection of data in each row so we extracted the data we needed from each collection and created new columns.  We completed this process for film genre and production companies.  We also changed the datatypes of many columns so we could make calculations and comparisions acorss columns.

# Analysis using Pandas and Seaborn

We used many DataFrame methods to analyze the data including .describe, .groupby, and .apply.  We created new columns for profitability and other calculations.  Then we made new dataframes to answer our guiding questions and then visualize our analysis using Seaborn graphs and charts.

# Findings

We determined this is a good time to enter the movie business.  from 1970, which had one high grossing film, to 2017, which had over 50, there is a positive trend in the opportunity for blockbuster films.

![Number of Blockbusters per Year](https://github.com/Frankafka/mod1project/blob/master/Number%20of%20Blockbuster%20by%20Year.png)

We identified the ideal film budget for one film is $40 million dollars.  The ability to make more in profits did increase if the budget was more than $40 million, but so did the risk of not achieving profitability.

![Ideal Budget Plot by Profitability](https://github.com/Frankafka/mod1project/blob/master/Profitability%20and%20Budget.png)

We found that the most profitable genres are Action, Adventure, Comedy and Animation.  Three of these genres rely heavily on CGI (computer generated imagery) and special effects that require a great deal of technological competence.  Definitely an opportunity for Microsoft.

![Most Profitable Genres](https://github.com/Frankafka/mod1project/blob/master/Profitability%20by%20Genre.png)

We determined the factor most correlated with profitability was foreign gross revenue over the lifetime of the film.  Domestic lifetime gross revenue at the box office often lead to breaking even financially, but the revenue from abroad lead to profitability.

![Profitability Correlation](https://github.com/Frankafka/mod1project/blob/master/Microsoft%20Profitability%20Correlation.png)

We found that Walt Disney, Marvel Studios, Universal Pictures, and Paramount would be Microsofts main competitors, especially in the most profitable genres.

![Most Profitable Competitors](https://github.com/Frankafka/mod1project/blob/master/Most%20Profitable%20Competitors.png)


# Recommendations

We recommend...
*  Microsoft enter the film industry to leverage their competitive advantage in technology.
*  Invest between $120 to 160 million per film within the action, adventure, animation, and comedy genres.
*  Focus on stories that will have an international appeal and build global strategic partnerships to ensure international distribution.
*  Focus on stories that can sustain multiple films in a collection.
*  Conduct a detailed competitive analysis of Walt Disney, Marvel Studios, Universal Pictures, and Paramount and develop a talent aquistition strategy to attract some of their employees to join Microsoft.
