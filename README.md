# homework-unsupervised_ML

This code is a homework to begin unsupervised machine learning. 

## Type of data
Unsupervised machine learning is to pass data to an algorithm (model) to categorize, or we also call to cluster. There are two kinds of data for the algorithm to process, one is continuous numeric, such as price, volume; one is representiative tokens, such as type, ID. 

## The algorithm (model)
The example algorithm (model) we use is K-Means, which takes a pandas dataframe to assign a cluster label to each row (data point), so that the "cluster center" (centroid) is the arithmetic mean of all the points belonging to the cluster. We need to determine and pass the number of clusters (k) to the algorithm. 

## Preprocess data
Since the natural data would land in various number ranges, for example in this work, the crypto currencies price changes in 24 hours can be 1/365 of that in 1 year, obviously a mean mixing up the two does not make much sense. Therefore we want to preprocess the data to put them in scale.

Also with the representative token type, we should not assign random numbers to represent, as the numbers would be joining the calculation of the mean. Hence we also preprocess this type, to make each token a column in the data frame, containing 0/1 as "switch" value. Pandas get_dummies can do this.

## Measure
K-Means model adds up the square of every data point's distance to the centroid, called inertia as one of the two measurements. Naturally, the less k and less inertia, the data is better categorized. 

Since the more k, the less inertia, and k is passed to the model, it is our job to find a balance point to cluster the data as well as possible.

## Reducing data dimensions
With our purpose to categorize cryptos' performance, even with the cluster label assigned, it would still be difficult to interpret the result using plot, as there are multiple dimensions involved, and we can only show two or three dimensions at a time.

PCA (Principal Component Analysis) is an algorithm to convert multi-dimensions (columns) numbers into fewer dimensions (n_component), while preserve the dynamics of the data to a certain level, measured by "explained variety ratio".

## Techniques
The python lib we use is scikit-learn. 
* sklearn.preprocessing: StandardScaler - used to put continuous numeric data in scale
* sklearn.decomposition: PCA - convert high dimensional data to lower dimension
* sklearn.cluster: KMeans - the unsupervised machine learning model. 
* Other alternative ways based on similar ideas: Birch, AgglomerativeClustering, and more in [scikit-learn](https://scikit-learn.org/stable/modules/clustering.html#overview-of-clustering-methods) are not presented in this work

## Steps
1. Read the [csv file](Resources/crypto_market_data.csv) into a panda dataframe
2. Scale the column numbers fit_transform
3. Try 1 to 10 k, plot the "elbow" curve to find a best k
4. Use the best k to fit and plot KMeans clusters
5. Using PCA to convert the 7-column (dimension) to 3-column (3 components)
6. Find the best k on the PCA dataframe in the same way as 3
7. Use the best k to fit and plot KMenas clusters
8. Compare the outcomes between 7-dimension data and the PCA 3-component data
9. Conlusion: PCA gives a better KMeans result

## References

[scikit-learn StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html)

[scikit-learn Preprocessing Data](https://scikit-learn.org/stable/modules/preprocessing.html#preprocessing-scaler)

[Pandas concat function](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.concat.html)

[scikit-learn Python Library](https://scikit-learn.org)