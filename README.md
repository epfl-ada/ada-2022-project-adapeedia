# ada-2022-project-adapeedia
## What makes a movie successful?

### Abstract
The question that this project will try to answer is: what makes a movie successful? In order to adress this problem we decided to quantify success according to the average rating of the movie and its revenue. The goal will be to sensitively predict which would be the best choices in order to maximize this success features for the future next movie being produced.
Furthermore, we will analyse the tabular data included in the CMU Movie Summary Corpus  inoder to take into consideration features as the runtime of the the movie, the languages in which it was produces, the countries in which it was produces, year, movie genre and type. Other analysis we plan to to is some text analysis on the plot summaries. The goal is to detect which category of words and scenes are more appealing to the public.
Eventually, we want to compare the outcomes of the two analysis (the one based on the revenue and the one based on the average ratings) in order to provide a detailed dicussion about the prediction.

### Proceedure

Firstly, it was possible to access the movie ratings by downloading IMDB datasets containing information about the movies including it's average rating on the platform. Therefore, we proceeded in order to obtain a revenue analysis oriented dataset. However, since the revenues information is not included per each movie, the dataset will shrink to ~10k samples as this feature has a lot of missing values.
This is the reason why the second indicator or success "ratings" was included. In this step the IMDB dataset including the ratings complements the original one. This resulted in a dataset of ~50k samples, all containing a rating value. However, in order to have a sensible indicator about the ratings we decided to only consider movies with a minimum vote count (for example 20) and make the analysis more credible, additionally, this will not affect our data size drastically.



