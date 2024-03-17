# CryptoClustering

## Prepare the Data

I used the `StandardScaler()` module from `scikit-learn` to normalize the data from the CSV file.

I created a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

## Find the Best Value for k Using the Original Scaled DataFrame

I used the elbow method to find the best value for k using:

- a list with the number of k values from 1 to 11.
- an empty list to store the inertia values.
- a for loop to compute the inertia with each possible value of k.
- a dictionary with the data to plot the elbow curve.
- I plotted a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

I found that the the best value for k is 4.

## Cluster Cryptocurrencies with K-means Using the Original Scaled Data

I used the following steps to cluster the cryptocurrencies for the best value for k on the original scaled data:

- I initialized the K-means model with the best value for k.
- I fitted the K-means model using the original scaled DataFrame.
- I predicted the clusters to group the cryptocurrencies using the original scaled DataFrame.
- I created a copy of the original data and add a new column with the predicted clusters.
- I created a scatter plot using hvPlot:
1. Set the x-axis as "PC1" and the y-axis as "PC2".
2. Color the graph points with the labels found using K-means.
3. Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

##Optimize Clusters with Principal Component Analysis

Using the original scaled DataFrame, I performed a PCA and reduced the features to three principal components.

I retrieved the explained variance to determine how much information can be attributed to each principal component and then found out the total explained variance of the three principal components.

I created a new DataFrame with the PCA data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

## Find the Best Value for k Using the PCA Data

I used the elbow method on the PCA data to find the best value for k creating

- a list with the number of k-values from 1 to 11.
- an empty list to store the inertia values.
-  a for loop to compute the inertia with each possible value of k.
- a dictionary with the data to plot the Elbow curve.
- I plotted a line chart with all the inertia values computed with the different values of k to identify the optimal value for k visually.

The best value for k using the PCA data is still 4.

## Cluster Cryptocurrencies with K-means Using the PCA Data

- I initialized the K-means model with the best value for k.
- I fitted the K-means model using the PCA data.
- I predicted the clusters to group the cryptocurrencies using the PCA data.
- I created a copy of the DataFrame with the PCA data and added a new column to store the predicted clusters.
- I created a scatter plot using hvPlot:
1. Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
2. Color the graph points with the labels found using K-means.
3. Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

## Observations

The PCA features incorporated in the clusters have significantly lower inertia values than the original features. As a result, the values within each cluster are much closer to each other, making it easier to distinguish between them than the original data. The PCA plot can also better isolate the two outliers, celsius-degree-token and ethlend. Despite losing 10% of the data, the clusters still contained the same coins, with coins like tezos and iota being much closer to the other cluster. The results were accurate even with the missing data.
