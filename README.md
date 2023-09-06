[<img src="https://img.shields.io/badge/R-Data Analytics and ML-important.svg?logo=R">](<LINK>)

<h1 align="center" style="font-size:60px;">Sentiment-Analysis-on-Hotel-Reviews-and-Hybrid-Recommender-for-customers</h1>

# Technologies
<img src="https://www.r-project.org/Rlogo.png" width="50"></img>

# Prerequistes
* Install [R](https://www.r-project.org/) & [R studio](https://posit.co/products/open-source/rstudio/)

# How to run the code ?
* Extract the `datasets.rar` file.
* Open the `code.Rmd` file with R studio
* Search the following code lines and give the correct file paths of the datasets as per your system configuration.
```r
dhotel<-read.csv("D:\\6th sem materials\\Data Analytics\\hotel_reviews.csv")
dcovid<-read.csv("D:\\6th sem materials\\Data Analytics\\covid19.csv")
```
* Click on the Knit option in R studio to get a markdown version of the project along with output.
# Aims
A markdown version of the project can be observed in `code.html`. It includes the following objectives:

#### 1. To perform sentiment analysis on hotel reviews in order to understand the inclination of customers towards a particular service
* Extracting [TFIDF](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) feature from hotel reviews
* Assigning labels to numerical hotel ratings (positive, neutral and negative)
* Supervised sentiment analysis using multinomial [naive bayes](https://en.wikipedia.org/wiki/Naive_Bayes_classifier) (x = tfidf feature, y = hotel ratings)
* Dimensionality reduction of TFIDF using [SVD](https://en.wikipedia.org/wiki/Singular_value_decomposition) followed by [SVM](https://en.wikipedia.org/wiki/Support_vector_machine) on reduced data
* Since SVM gives greater accuracy, this is used to predict sentiment of entire dataset
* Using predicted sentiment, get top 5 reviews of each sentiment by calculating the cosine similarity from their corresponding centroids
#### 2. To map geospatial data of these hotels to check if they fall within Covid-19 containment clusters and using the current location of the customer generate the shortest route to the hotel and check the top-rated hotels with shortest distance
* Plot covid locations and hotel locations on US map
* Apply [DBSCAN clustering](https://en.wikipedia.org/wiki/DBSCAN) to covid locations, then predict in which clusters the hotels are
* Find [k nearest neighbors](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm) from hardcoded target hotel
* Using geocoding, find target user's coordinates
* From user coordinates, calculate [haversine distance](https://en.wikipedia.org/wiki/Haversine_formula) to reach similar hotels as the target hotel
#### 3. To generate hotel recommendations from user profile and hotel reviews
* Using a regressive [neural network](https://en.wikipedia.org/wiki/Neural_network), model hotel ratings dependent on tfidf feature and get [residual sum of squares](https://en.wikipedia.org/wiki/Residual_sum_of_squares) when estimating on test data
* Normalize the test dataset predictions. Get the threshold user rating by multiplying user profile vector (1 to 5 scores) and test dataset predictions. Set a minimum error.
* For every instance in the test dataset, calculate difference between that prediction and threshold user rating. If it is less than the minimum error, add it to the recommended hotels list.
