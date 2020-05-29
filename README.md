# Movie Analysis Project

DSC NYC Flatiron Module 1 Project:
By: **Jason Drummond** & **Daniel Cho**

## Introduction

For this project we explored the film industry. We collected data on over 3300+ top revenue generating movies from movies databases such as Box Office Mojo and TMDB in order to analyze and provide recommendations for Microsoft looking to break into the film industry. This data contained information on financial metrics, production, genre, MPAA Rating and much more.

From here we posed 4 questions we wanted to focus our analysis:
 1. Is it the right time for Microsoft to enter the movie industry?
 2. What companies will Microsoft be competing against?
 3. What audience should we target to generate the most revenue?
 4. Which genre are currently the biggest box office draws? Profitability/Budeting?
 
## Files in this Repository
 * Data Collection API & Web Scrape.ipynb - Merging Web Scrape from Box Office Mojo & API from TMDB
 * Data Cleaning.ipynb - Cleaning the data of merged Data Frame
 * Data Visualizations.ipynb - Creating visuals and analyzing the data to provide our recommendations
 * PNG Visuals - Folder contained png files of all of our data visualizations
 * final_movie_data.csv - CSV file containing the merged data from our data collection
 * cleaned_final_movie_data.csv - CSV file containing the cleaned and edited data used for our analysis

## Built with Libraries
**Data Collection**
 * Pandas
 * Requests
 * Json
 * Time
 * BeautifulSoup

**Data Cleaning & Visualization**
 * Pandas
 * Matplotlib
 * Seaborn
 
## Data Collection
A quick review of Box Offie Mojo, TMDB, IMDB & Rotten Tomatoes revealed that that collecting data from the first two sources would be the best course of action. We deemed with the organized format of Box Office Mojo web scrapping using BeautifulSoup would be the best tool. Because of TMDB's API friendly user interface we utilized Json & Requests to do our API pull. We ulitmately were able to combine these two sets of film data along their IMDB movie ids.

**Web Scraping**

We identified the webpages, from Box Office Mojo, which would allow us to scrape as much data as possible and compiled them in to a list. These webpages corresponded to the top 1000 movies in each MPAA Rating Category, (G, PG, PG-13, R). We created a few functions that loop through the list of Urls and gather all data displayed on the page for each movie. Most importantly each URL in the list had multiple pages we would need to search through making it a need to extract that information from the "Soup" to iterate over them and continue on to the next URL in the original list.

When the function was done looping through all of the webpages we would get a list of movie details and the IMDB id for each movie. A Pandas DataFrame was created with this information and the IMDB id's were then used to gather even more information on the movies we scraped from the web.

**API**

We used TMDB for our API pulls. TMDB was a great resource for API as they had an easy to use interface and clear parameters of what we were able to access. The first step was requesting an API Key from TMDB in order access the data and using the libraries JSON & Requests. We identified that using an API pull for movie details gave us the most relevant data. 

Taking the list of imdb ids from the web scrape were able to access additional data from TMDB that included metrics ranging from budget, genre, production company & countries, etc. A Pandas DataFrame was also created for TMDB data. We then joined the two dataframes together again under the common imdb id to put everything into one workable dataframe.

Lastly we exported the dataframe to a .csv file for future access and to begin working on our data cleaning.

## Data Cleaning

Our first step in cleaning our data was importing our .csv file and pandas. A lot of time was dedicated to removing unnecessary columns, rows, null values and any extreme outliers. We added additionally columns to help organize genre and production data. Additionally we streamlined our financial numbers to be under the same format. Lastly, some of the revenue numbers from TMDB were missing or incorrect so we filtered out those movies to prevent any skews in our data. Finally, we exported the cleaned dataframe again to a new .csv file for future access and to start our data visualizations.

## Data Visualizations

We used a combination of matplotlib and seaborn visualizations to portray our analysis and findings. We used a variety of graphs ranging from bar graphs, line graphs, swarmplots, regression charts, and combo charts. These visualizations were all created to help answer our project questions and provide recommendations.

## Analysis
To address our first question we found that the movie industry has been showing strong steady growth year by year shown in the bar graph below. Since the 2000's worldwide movie revenue for top performing films has grown by a multiple of 2.5x. Therefore we believe that Microsoft is in a prime position to enter the movie industry.

![](PNG%20Visuals/yearly_movie_revenue_growth.png)

The movie industry has a few big players that dominate the blockbuster movies. The bar chart below highlights the top 10 revenue generating production studios of all time. Universal, Disney and Paramount are the top 3. As one of the largest corporations in the world, Microsoft has the unique ability to compete with the biggest players.

![](PNG%20Visuals/top_revenue_producing_studios_all_movies.png)

After establishing that the movie industry is fast growing we wanted to investigate what audience should be targeted. MPAA rating (G, PG, PG-13, R) helps us better understand the general demographic of movie goers. In the line chart below it illustrates the dramatic growth of PG-13 movies since it's creation in the 1980's. Prior to 2000, PG & R films dominated the industry. At the start of the 21st century, the creation of blockbuster PG-13 movies grew bu a multiple of 2.5x. We can determine that PG-13 is the audience that Microsoft should be targeting.

![](PNG%20Visuals/Mpaa_Rating_by_year.png)

This swarm plot further illustrates the revenue driving ability that PG-13 movies have. Many movies in all ratings have been able to achieve a revenue total ranging from $100-$300 million. However, it is PG-13 that have had the most success in reaching the highest box office totals of 1B+ further illustrating that PG-13 should be the focus for Micorsoft.

![](PNG%20Visuals/Movie_Rev_by_rating.png)

Understanding that PG-13 should be our target audience we wanted to understand how different genres perform under this rating. Action, Sci-fy and Adventure drive the most revenue on average per movie, but also have the highest budgets. On the other hand the Horror and Music have the lowest budgeting while also driving decent revenue per movie.

![](PNG%20Visuals/Avg_dollar_figs_genre.png)

Diving deeper within the PG-13 cateogry we focused on the Action and Horror genres. No surprise that Marvel Studios is the top production studio for Action with Avatar and Star Wars being the best overall performing movies. Horror as illustrated in the plot graph is far and away the most profitable (total profit/total revenue) genre generating an average 81% profit off of total revenue. 

![](PNG%20Visuals/PG13_Analysis.png)

## Recommendations
 * The movie industry has grown over 2.5x since the 21st century and Microsoft is in a prime position to break into the market.
 
 * We recommend targeting the PG-13 audience as this MPAA rating has also grown 2.5x over the past 20 years, leading to a greater chance of producing a blockbuster movie.
 
 * We would target genres that provide low risk to reward ratio. The Horror, Adventure, Fantasy, and Crime genres would fit into this Category, with Horror being the top performer.
 
 * To produce the highest revenue generating movies we recommend creating PG-13 Action movies, but be prepared to compete against big players like Marvel & Universal in a over saturated Action genre.
 
## Limitations and Further Exploration
**Limitations**

The biggest limitation to the market right now is the spread of Covid-19, which has the ability to disrupt the movie industry. Can theater chains survive long term? Will more and more people stream movies?

**Further Exploration**

First we would like to explore a larger dataset to see if particular Actors or Directors can help boost revenue.

We would also like to collect data from a focus group to see if there would be interest in making a movie based of a Microsoft IP-e.g., current video game series

## Presentation 

https://docs.google.com/presentation/d/1R7RFa1d1OMULlJ5Qd99jdSjU2P2ujZpYLzHTpL9EhDk/edit#slide=id.p
