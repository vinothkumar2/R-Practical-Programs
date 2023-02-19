
# Machine Learning with R

## Data and Text classfication using Neural Network


### Code




```r
library(neuralnet)
library(caret)
library(tidyverse)

# Load the iris dataset
data(iris)

# Preprocess the data
x <- iris[, 1:4]
y <- as.numeric(as.factor(iris$Species))
y <- ifelse(y == 1, 1, 0)  # Set "setosa" as the positive class
data <- cbind(x, y)

# Split the data into training and testing sets
set.seed(123)
training.samples <- data$y %>% createDataPartition(p = 0.8, list = FALSE, times = 1)
training <- data[training.samples, ]
testing <- data[-training.samples, ]

# Train the neural network model
model <- neuralnet(y ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = training, hidden = c(3, 2), linear.output = FALSE)

# Make predictions on the testing set
predicted <- predict(model, testing[, 1:4])
predicted <- ifelse(predicted > 0.5, 1, 0)

# Compute the accuracy of the model
accuracy <- sum(predicted == testing$y) / nrow(testing)

# Print the accuracy of the model
print(paste0("Accuracy: ", accuracy))

```

## Explanation 

In this program, we first load the iris dataset and preprocess the data by setting "setosa" as the positive class and combining the features and labels into a single data frame. We then split the data into training and testing sets using the createDataPartition function from the caret package. We train a neural network model on the training set using the neuralnet function from the neuralnet package. Finally, we make predictions on the testing set and compute the accuracy of the model.


## Screenshots

![App Screenshot](https://user-images.githubusercontent.com/68177619/219874799-d0171b51-0950-42b8-a364-eceb4b22fe74.png?text=App+Screenshot+Here)

