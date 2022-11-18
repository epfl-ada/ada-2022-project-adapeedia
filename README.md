# ada-2022-project-adapeedia
## What makes a movie successful?

### Abstract
The question that this project will try to answer is: what makes a movie successful? In order to adress this problem we decided to quantify success according to the average rating of the movie and its revenue. The goal will be to sensitively predict which would be the best choices in order to maximize this success features for the future next movie being produced.  
Furthermore, we will analyse the tabular data included in the CMU Movie Summary Corpus  inoder to take into consideration features as the runtime of the the movie, the languages in which it was produces, the countries in which it was produces, year, movie genre and type. Other analysis we plan to do is some text analysis on the plot summaries in order to detect which category of words and scenes are more appealing to the public. Additionally, the analysis will be carried out on the character actor in order to detect if some character is more influential then other on the success metrics.  
Eventually, we want to compare the outcomes of the two analysis (the one based on the revenue and the one based on the average ratings) in order to provide a detailed dicussion about the prediction.

### Success metrics

#### Revenues
Revenues per movie in US dollars.
Therefore, we proceeded in order to obtain a revenue analysis oriented dataset. However, since the revenues information is not included per each movie, the dataset will shrink to ~10k samples as this feature has a lot of missing values.

#### Average ratings
The average ratings are recorded in a scale of [0,10].
It was possible to access the movie ratings by downloading from the IMDB website the datasets containing information about the second indicator or success " average ratings" whhich complements the original CMU one. This resulted in a dataset of ~50k samples, all containing a rating value. However, in order to have a sensible indicator about the ratings we decided to only consider movies with a minimum vote count (for example 20) and make the analysis more credible, additionally, this will not affect our data size drastically.

### Feature analysis
The feature we will include in our analysis are:

#### Runtime
The runtime in minutes of the movie. It's a float number.

#### Languages
The languages in which the movie was broadcasted. It's a list of languages per each movie.

#### Countries
The countries in which the movie was produces. It's a list of the coutries per each movie.

#### Genres
The genres to which the movie has been categorized to. It's a list of genres per each movie, listed in order of relevance.

#### Year
The year of production of the movie.

#### titleType
The categorization of the movie. Some examples: movie, tvmovie, short, tvepisode, etc.

#### isAdult
True if the movide was categorized for containing 18+ material. 

#### Actor's score 
We will assign to each of the actors a score according to the prizes they won in their acting career. The scoring will be given according to this order of significance:
* Oscars winned
* Golden Globe
* Palme d'Or
*

#### Actor age in the movie
Included in the CMU dataset there is the age of the actor when filming the movie.

#### Plot Summary
A summary of thhe plot included in wikipedia per actor. In order to analyse this we will adopt the Standford CoreNLP processed summaries provided by the CMU Movie Summary Corpus in the supplements. In this way we will be able to detect which kind of content the movies contains.





