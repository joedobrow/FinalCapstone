# Final Capstone

Book Recommender using BERT NLP on scraped Blurbs

There are 5 notebooks involved in this project:

1. EDA -- Exploratory Data Analysis. Some plots and statistics on the data I am using

2. Blurb Scraping -- The scrapy code I used to scrape the blurb data

3. Blurb Cleaning -- A lot of cleaning was required on the blurbs that I scraped in order to be used. This includes using Bert-as-a-Service to get vector embeddings of each blurb

4. Parameter Tuning -- Running the model in different circumstances to find an optimal RMSE

5. Model Execution -- Functions to implement the recommender system, and utilizes optimal cleaned and processed data.


# PROJECT OVERVIEW

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
