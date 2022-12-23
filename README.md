# ada-2022-project-adapeedia

## Data Story
Please visit our amazing website [here](https://faraldospau.wixsite.com/adapeedia) to get the most out of the story!

## Data Sets and Running the notebook
As the data exceeded Github's size limit constraints, we have uploaded a .zip of our data [here](https://drive.google.com/file/d/1JnCBDjjLFgyH-aWAudfuxixdQzEAczms/view?usp=sharing). After downloading this zip file and copying it to the directory containing this repository, you should uncompress it. Following this, you should have a `MovieSummaries` directory at the same level as `Project.ipynb`.

## What makes a movie successful?

### Abstract
Designing a successful movie is a hard task for all producers. Many logistic decisions should be made as there are numerous factors to consider: the runtime of the movie, the country of filmimg, the actors to choose, the language spoken, and many others. As movie productions have high budgets, such decisions can not be made by "trial and error". Fortunately, with the huge movie corpuses that are available nowadays, it is possible to explore the success of different combinations of these features and analyze the effect of each feature individually. And in this project, we aim at exploring these relations. In order to address this problem, we decided to quantify success according to the average rating and the profit that it gained. The goal will be to sensitively analyze and predict the best choice of movie logistics that will guide producers in their future movie productions.  

### Research Questions
* How do we define the success of a movie movie? 
* Are we able to predict the success of a movie given some variables?
* Which of the variables are important for predicting the success of a movie? 

## Analysis

### Data preprocessing

* We dropped some of the features that we considered duplicates of other information in the dataset due to the merging, or irrelevant fpr the aim of our analysis. The columns we dropped were: 'Freebase_movie_ID', 'primaryTitle', 'runtimeMinutes', and 'startingYear'.  
* We dropped the 'endYear' feature since 99% of rows were null values.  
* We checked to have unique entries in our dataset, such that when the 'wiki_movie_ID' was present more than once we kept only the one with highest 'numVotes'.  
* We dropped the values where the runtime was null.
* We dropped movies with budget or numVotes equals 0
* We checked for duplicates of the moxies with the wiki_movie_ID but there were no duplicates.

## Targets and Features
The outcome of the previous steps are the following entries in the datasets. 
### Success metrics
To define a consistent metric of success, we combined the **revenue** of a movie and the **averageRating** in the following way:
1) Standardize the **revenue** feature
2) To assign a weight for the **averageRating** of a movie, multiply this feature with the **logarithm** (base 10) of the **numVotes** feature
3) Standardize the resulting feature
4) Define the **success* metric as the average of the two standardized features
Mathematically, this is translated as:
$${success = {Stand(revenue) + Stand( \log(numVotes) * averageRating ) \over 2}} $$


### Features
* **Runtime**: The runtime in minutes of the movie. It's a floating point number.
* **Languages**: The languages in which the movie was broadcasted. It's a list of languages per each movie.
* **Countries**: The countries in which the movie was produces. It's a list of the coutries per each movie.
* **Genres**: The genres to which the movie has been categorized to. It's a list of genres per each movie, listed in order of relevance.
* **Year**: The year of production of the movie. It's provided as a string of day, month and year but we will include only the year as an integer.
* **titleType**: The categorization of the movie. Some examples: movie, tvmovie, short, tvepisode, etc.
* **isAdult**: True if the film was categorized for containing 18+ material. It's a binary variable.
* **dominant_gender**: True if female is the dominant gender among the character genders and False otherwise.
* **is_holidays**: True if the the movie was released 1 month before holidays and False otherwise.
* **IsFamousActor**: True if the movie contains at least one famous actor and false otherwise.
* **IsMajorProducer**: True if the producer is one of the major movie producers.
* **is_kill**: True if the word "kill" appears at least once in the plot summaries
* **Plot Summary**: A summary of the plot included in wikipedia per movie. In order to analyse this we will adopt the Standford CoreNLP processed summaries provided by the CMU Movie Summary Corpus in the supplements. In this way we will be able to detect which kind of content the movies contains and how this impacts the success.

## Visualization
In order to analyse the distribution and be more aware of how the data looks like, we plotted the features histrograms. We were able to understand that some metrics are normally distributed (as the average ratings) and some are highly skewed (as the number of votes) and therefore require a log transformation. Additionally, we plotted the top 20 languages, countries and genres and also some dynamic plots for the best genre and country per each year. Regression plots were also added to visualize the relation among features. Lastly, we displayed word clouds for each genre through a Latent Dirichlet Allocation after preprocessing the plot summaries (stemming, stopword removal, lemmatization).

### Organization
* Camille: 
* Hadi: pre-processing, metric formulation, ReadMe
* Silvia:
* Pau: Website (Data Story), some plotting, minor other code changes




