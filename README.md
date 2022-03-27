# Product-Recommnder-System for online stores.
Product Recommender for online stores.
Capstone Project
Data Science Career Track, Springboard
Thanks to mentor Julian Jenkins III

</br>How online stores can help customers to buy the right product from their millions of products,so that online retailers can retain the customer from going elsewhere and see yearly increase in their average order value. Build a recommendation system so that customers can get the right product with personalized info.
</br>Online stores show millions of products to the customer from their catalog. Choosing the correct product for their needs is becoming difficult because of so much information.Since customers are more likely to buy based on personalized recommendations, management has decided to go for a recommendation system so that they can retain the customer and hence increase yearly product sales.
#### Data Source
In this project recommendation model is built based on electronics products of Amazon,based on the ratings.The dataset here is taken from the below website.
Source - Amazon Reviews data (http://jmcauley.ucsd.edu/data/amazon/links.html) 
</br>The repository has several datasets. For this case study, I am using the Electronics dataset.
#### Sample review dataset:
This dataset includes reviews (ratings, text, helpfulness votes), product metadata (descriptions, category information, price, brand, and image features), and links (also
viewed/also bought graphs). And has 1689188 records.
</br>"reviewerID": "A2SUAM1J3GNN3B",
</br>asin": "0000013714",
</br>"reviewerName": "J. McDonald",
</br>"helpful": [2, 3],
</br>"reviewText": "I bought this for my husband who plays the piano. He is having a wonderful time playing these old hymns. The music is at times hard to read because we think the book was published for singing from more than playing from. Great purchase though!",
</br>"overall": 5.0,
</br>"summary": "Heavenly Highway Hymns",
</br>"unixReviewTime": 1252800000,
</br>"reviewTime": "09 13, 2009"
</br>Data set had 1m+ rows and with no null values. out of 17 features only 4 features viz.,'reviewerId', 'productId', 'ratings','timestamp' are considered.Various types of
distribution are looked at to get a better understanding of data.
#### Summary of data set
</br>Number of reviews: 1365131
</br>Number of unique reviewers = 1036895
</br>Number of unique products = 35192
</br>Average rating score: 4.046
Insights
#### Product Ratings:
Products were rated with discrete numbers 1,2,3,4,5. Most of the reviews rated 5. Here is the actual numbers Single Reviewer rated more than 50 times. This shows customers are buying many productsfrom this store. Here is the top 5 number of times the reviewer has given the ratings.
![image](https://user-images.githubusercontent.com/87315447/160265771-f5673acb-e2b8-49d8-b202-5f587b50c511.png)
#### Popular products
The top 5 most popular product are -
</br>B007WTAJTO with ratings 14162
</br>B0019EHU8G with ratings 12274
</br>B003ELYQGG with ratings 11611
</br>B0012S4APK with ratings 5606
</br>B0001FTVEK with ratings 5324
</br>Here is the distribution
![image](https://user-images.githubusercontent.com/87315447/160265792-2eb5906b-6d22-4fbc-b5a0-a9e9e2e9dea9.png)
#### Total Review Number based on years -
Number of reviews was maximum in the year 2013.Looks there were hardly ratings done on
products till 2002 and slowly started from 2003.
</br>2013 with ratings 513513
</br>2014 with ratings 346501
</br>2012 with ratings 223490
</br>2011 with ratings 128834
</br>2010 with ratings 67371
#### Unique customer per year:
</br>2010 with customer 61782
</br>2011 with customer 115009
</br>2012 with customer 192277
</br>2013 with customer 414734
</br>2014 with customer 288186
There were a total of 1151618 unique customers visited between 1999 to 2014. Year 2013 has seen the maximum number. Here is the visual distribution
![image](https://user-images.githubusercontent.com/87315447/160265827-8d8124d4-e4df-402f-98bd-037bc4feea37.png)
#### Unique Products per year
</br>2010 has seen 7002 products
</br>2011 has seen 11177 products
</br>2012 has seen 17387 products
</br>2013 has seen 26257 products
</br>2014 has seen 24322 products
</br>2013 has seen the more products.From the plot looks there were not many products till2005.
![image](https://user-images.githubusercontent.com/87315447/160265836-829ea8a5-a9f8-4195-88c2-584d0bc317c1.png)
From 1999 to 2004, not many reviews were given, maybe customers were buying less product, or reviews and ratings were not that significant for product purchase.
#### Model Selection :-
</br>Surprise Package :http://surpriselib.com/
#### References
</br>Documentation :https://surprise.readthedocs.io/en/latest/
</br>Installation: http://surpriselib.com/
</br> Git hub : https://github.com/NicolasHug/Surprise
There are a lot of different packages available to build a recommender system. For this one,I'm using the Surprise package. Surprise has many different algorithms built in.It provides various ready-to-use prediction algorithms such as baseline algorithms, neighborhood methods, matrix factorization-based ( SVD, PMF, SVD++, NMF), and many others. Also, various similarity measures (cosine, MSD, pearson…) are built-in.In this case, I need to load in a custom dataset to use with Surprise. According to the
documentation, we need to make sure our data frame has three columns: the user ids, the item ids, and the ratings. Additionally, we'll need to specify the rating scale. In our case,users have used the ratings discretely from 1 to 5. I'm also going to split the data into training and testing data using the Surprise package
</br>With the Surprise library, I used below algorithms BaselineOnly:Algorithm predicting the baseline estimate for a given user and item.
</br>KNNBaseline:A basic collaborative filtering algorithm taking into account a baseline rating.
</br>NMF:A collaborative filtering algorithm based on Non-negative Matrix Factorization.
</br>Co-clustering:A collaborative filtering algorithm based on co-clustering.
</br>SVD:When baselines are not used, this is equivalent to Probabilistic Matrix Factorization, it is as popularized by Simon Funk during the Netflix Prize
Metrics used are rmse and mae. And here is the result.
![image](https://user-images.githubusercontent.com/87315447/160265912-5cce40b4-566c-42ed-b309-e9006715eca2.png)
</br>BaselineOnly algorithm has given the best rmse. So I used this model to get the product recommendation based on ratings.
#### Top 10 best predictions
![image](https://user-images.githubusercontent.com/87315447/160265923-afb036ff-2506-4e45-b42a-d1e8a1c66cc1.png)
The above are the top 10 best Predictions. The product 'B000HGHMF8','B000IF51UQ' and 'B0028E1E2Y' are rated best with ratings 4.
#### Top 10 worst predictions
![image](https://user-images.githubusercontent.com/87315447/160265929-ee44879e-c241-400c-ac83-7544e0fbd03e.png)
Cross checking with productId B007WTAJTO, this has predicted rating 4.89 and 10k reviewers rated this.
![image](https://user-images.githubusercontent.com/87315447/160265938-73dced20-df08-4023-8cce-9f5465de3dcb.png)
#### Conclusion:
There are many ways to build and improve this recommender system. I couldn't use k-NN algorithms from the Surprise package, as it needs more memory, nor could I complete it on google colab. Using more tuned parameters I did some basic cross validation to select the best parameters. To improve the recommendations, tune these parameters and make sure that the algorithm is serving the best recommendations possible with the data available.
