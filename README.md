## Movie Database ETL

This repository is an updated version of an ETL project that a team and I created to use as a database to create a web-app using a RESTful API. The data is set up for a relational database like SQL, but we opted for a noSQL database in MongoDB.

The initial data we used was simply too large to fit in a github repository, as it contained millions of entries that through some cleaning, we managed to move into a fewer than 10,000 total entries in order to be usable with our deployment platform Heroku.

The links to the initial data (sourced from imdb) can be found at the following links 

    Names of actors and actresses https://datasets.imdbws.com/name.basics.tsv.gz

    The titles of productions - https://datasets.imdbws.com/title.basics.tsv.gz

    Number of votes and average ratings - https://datasets.imdbws.com/title.ratings.tsv.gz

    Primary cast members and credited production roles - https://datasets.imdbws.com/title.principals.tsv.gz

## The Transform Process

These data sets contain a huge amount of information, but was in need of some cleaning to work in the context of our project.

First, we started by cleaning the data of various incomplete entries, may sported the text "\N" which indicates a user inputting data and hitting the "enter" key to move on to the next line. We also filtered out "N/A" values in the same line.

![principles-data](Images\PrincipalsData.png)

In need of further shortening, we removed all rows from the principals dataset if they did not contain the words "actor, actress or director," as many rows simply didn't have proper entries in the "category" column and we were mostly interested in making a tool to see statistics around those three roles.

We also cut out all television shows from the list in order to hit our total cap.

Finally, after merging all of our filtered-down data frames together we were left with over 1 million rows, and had to make one final cut. We took only the entries for movies that had recieved 90,000 ratings or more, which left us with about 9,100 rows to be loaded into MongoDB.

![final-data](Images\PrincipalsData.png)