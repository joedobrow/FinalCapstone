# Final Capstone

Book Recommender using BERT NLP on scraped Blurbs

There are 5 notebooks involved in this project:

1. EDA -- Exploratory Data Analysis. Some plots and statistics on the data I am using

2. Blurb Scraping -- The scrapy code I used to scrape the blurb data

3. Blurb Cleaning -- A lot of cleaning was required on the blurbs that I scraped in order to be used. This includes using Bert-as-a-Service to get vector embeddings of each blurb

4. Parameter Tuning -- Running the model in different circumstances to find an optimal RMSE

5. Model Execution -- Functions to implement the recommender system, and utilizes optimal cleaned and processed data.


# Project Overview

This doesn’t explain much of the WHY or my thoughts, just a bullet outline of the project. The ‘why’ is addressed more in the powerpoint.

https://docs.google.com/presentation/d/1iW6igOogAVr58uQi9FfgY0fs_O62Kxh5bgsa_M2OJOU/edit?usp=sharing

Goal: Build a book recommender
1. Conduct exploratory data analysis on my dataset
2. Scrape the ‘blurbs’ for each book in my dataset
3. Clean scraped books by matching them to the correct ISBN
4. Generate vector embeddings of the blurbs using BERT
5. Cluster the vector embeddings using K-Means
6. Use SVD to predict a user-item matrix where the items are clusters
7. Tune parameters of SVD to achieve a low RMSE
8. Compare to multiple different baseline RMSEs
9. Evaluate RMSE on ISBNs despite training on Clusters to get a real evaluation
10. Use the predicted matrix to find the highest rated clusters
11. Find the most popular books from the recommended clusters, and recommend them
12. Create a version of the model that is FAST so it can be used in real-time by a webapp or company that would use my product.


# Next Steps/Possible Improvements

1. 3/4 of the books were lost in the process of scraping blurbs and cleaning them and matching them to the correct book. The model would improve greatly with a fresh scrape. Other improvements to the data source would involve a more streamlined and consistent blurb cleaning process, since some of my algorithms are 'hacks' and only really work for this data. The data source I trained the model on is limited and 16 years old. Being able to implement this model into an existing book-related web service would improve the amount of data greatly

2. The BERT vector embeddings used were a simple arithmetic mean of the vectors for the all of the sentences in the blurb. The BERT model was also not pre-trained on any of my data and was simply 'out of the box.' In the future I would train the neural network model on the data that I have. It was just a little complicated and out of my expertise to do this, and BERT is known for being very powerful out of the box.

3. Languages have an undesired effect on the model. It is good at recommending German books to German readers, but is not able to recommend anything content-related within a language other than the primary language in the dataset: English. For example, a user that only reads French romance novels, would get recommended French sci-fi, as opposed to English romance novels. If I had enough data for other languages I could run seperate models... Or I could find translations of the blurbs, and just always recommend English books, and non-English readers could look for translated copies based on the recommendations.

4. There are tons of repeat books that have different ISBNs in the dataset. I should try to combine these.

5. Explore other clustering methods better and run more evaluations on the clustering. K-Means is intuitively a good model for this data, and is finding subjectively meaningful clusters, but other algorithms with different parameters could be explored.

6. More thorough parameter tuning would improve the model to having a better RMSE. However, a full gridsearch would require additional computer power and time. 

7. Other, more naive clustering methods should be considered and evaluated as baselines. For example, scraping the 'genre' of the book and clustering by that instead of BERT vectors is simpler and might provide better results. Clustering by Authors doesn't solve the sparsity problem very well since there are so many Authors still.

8. The model only predicts the 'best' books right now. For a book recommender, where the user very likely has not reported all of the books they have read, a system that recommends high quality, lesser known books is probably superior. I would like to incorporate more 'business-solution' functions to the final model.

9. Create a webapp to help show off this model and let people start getting recommendations!
