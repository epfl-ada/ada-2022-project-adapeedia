# ada-2022-project-adapeedia
## What makes a movie successful?

### Abstract
The question that this project will try to answer is: what makes a movie successful? In order to address this problem we decided to quantify success according to the average rating, and the revenue that it produced. The goal will be to sensitively predict which would be the best choices in order to maximize these success features for the future next movie being produced.  
Furthermore, we will analyse the tabular data included in the CMU Movie Summary Corpus in order to take into consideration features as the runtime of the the movie, the languages and countries in which it was produced, release year, movie genre and type.
Eventually, we want to compare the outcomes of the two analysis (the one based on the revenue and the one based on the average ratings) in order to provide a detailed dicussion about the prediction.

## Analysis

### Dataset preparation
There are the steps we made in order to have the datasets we will need for the analysis.  
* We used the movies dataset from the CMU Movie Summary Corpus in order to have a revenue analysis oriented dataset. However, since the revenues information is not included per each movie, the dataset will shrink to ~10k samples as this feature has a lot of missing values.  
* In order to have the ratings oriented dataset we downloaded from the IMDB website the datasets containing information about the second indicator or success " average ratings" which complements the original movies one. This resulted in a dataset of ~50k samples, all containing a rating value.  

### Data preprocessing

Since the analysis we did is divided in two objective, also the. preprocessing is divided in two parts, the one addressing the average ratings and the one addressing the revenues of the movies.
With regards to the average ratings oriented dataset, these are the preprocessing steps we did:  
* We dropped some of the features that we considered duplicates of other information in the dataset due to the merging, or irrelevant fpr the aim of our analysis. The columns we dropped were: 'Freebase_movie_ID', 'primaryTitle', 'runtimeMinutes', and 'startingYear'.  
* We dropped the 'endYear' feature since 99% of rows were null values.  
* In order to have a sensible indicator about the ratings we decided to only consider movies with a minimum vote count (for example 20) and make the analysis more credible, additionally, this will not affect our data size drastically.  
* We checked to have unique entries in our dataset, such that when the 'wiki_movie_ID' was present more than once we kept only the one with highest 'numVotes'.  
* We standardized the 'numVotes', 'revenues', and 'runtime' columns.  

For the revenue oriented dataset instead we:
* We dropped the values where the runtime and the year was null.
* We checked for duplicates of the moxies with the wiki_movie_ID but there were no duplicates.
* We transformed the revenues linearly by dividing thier amount for 10^6.

## Targets and Features
The outcome of the previous steps are the following entries in the datasets. 
### Success metrics
* **Revenues**: Revenues per movie in US dollars.
* **Average ratings**: The average ratings are recorded in a scale of [0,10].

### Features
* **Runtime**: The runtime in minutes of the movie. It's a floating point number.
* **Languages**: The languages in which the movie was broadcasted. It's a list of languages per each movie.
* **Countries**: The countries in which the movie was produces. It's a list of the coutries per each movie.
* **Genres**: The genres to which the movie has been categorized to. It's a list of genres per each movie, listed in order of relevance.
* **Year**: The year of production of the movie. It's provided as a string of day, month and year but we will include only the year as an integer.
* **titleType**: The categorization of the movie. Some examples: movie, tvmovie, short, tvepisode, etc.
* **isAdult**: True if the film was categorized for containing 18+ material. It's a binary variable.
* **Plot Summary**: A summary of the plot included in wikipedia per movie. In order to analyse this we will adopt the Standford CoreNLP processed summaries provided by the CMU Movie Summary Corpus in the supplements. In this way we will be able to detect which kind of content the movies contains and how this impacts the success.

## Visualization
In order to analyse the distribution and be more aware of hhow the data look like we plotted the features with respect to the success target metrics. 
We were able to understand that some metrics are normally distributed (as the average ratings) and some are highly skewed (as the number of votes) and therefore require a log transformation. Additionally we plotted the average runtime accoding to each category of titleType in order to deeply understand their categorical differences.  
Furthermore, we plotted the top 20 languages, countries and genres according to the ratings and, separately, the revenues.
Lastly, we plotted some dynamic plots for the best genre and country per each year. We did this plots for both the revenues and ratings analysis in order to capture a trend which depended on the year.

## Future Steps
In the next Milestone we will find the most suitable model in order to predict which are the characteristics which mostly impact the revenues and the ratings. This analysis will be done separately, and then combined through a sensible discussion about the results.






