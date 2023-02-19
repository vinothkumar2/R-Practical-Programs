
# Machine Learning with R

## Data and Text classfication using K Means Algorithm


### Code




```r
library(cluster)

# Load the data
data(mtcars)

# Choose columns to cluster
cols_to_cluster <- c("mpg", "disp", "hp", "wt", "qsec")

# Perform normalization on selected columns
mtcars_norm <- scale(mtcars[,cols_to_cluster])

# Set number of clusters
k <- 3

# Run k-means clustering
kmeans_model <- kmeans(mtcars_norm, centers = k)

# Print cluster assignment for each data point
cat("Cluster assignments:\n")
cat(kmeans_model$cluster, sep = "\n")

# Print cluster centers
cat("\nCluster centers:\n")
print(kmeans_model$centers)

# Print mean values for each cluster
cat("\nMean values for each cluster:\n")
for (i in 1:k) {
  cat("Cluster ", i, ":\n")
  mean_vals <- colMeans(mtcars[kmeans_model$cluster == i, cols_to_cluster])
  print(mean_vals)
}


```

## Explanation 

This program loads the mtcars dataset, selects columns to cluster, and performs normalization on the selected columns. The program sets the number of clusters to be 3, and runs the k-means algorithm on the normalized data. The program then prints the cluster assignment for each data point, the coordinates of the cluster centers, and the mean values for each cluster.


## Screenshots

![image](https://user-images.githubusercontent.com/68177619/219945751-25b76d96-2d85-4096-b163-52ab3d4c0996.png)


## Created by

- [@vinothkumar](https://github.com/vinothkumar2/)
