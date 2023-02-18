
# Machine Learning with R

## Solving classfication using Decision Trees

### Code




```r
# Load the necessary libraries
library(rpart)
library(rpart.plot)

# Load the dataset (using the iris dataset for demonstration)
data(iris)

# Split the data into training and testing sets
set.seed(123)
split <- sample(1:nrow(iris), 0.7*nrow(iris))
train <- iris[split,]
test <- iris[-split,]

# Build the decision tree model
model <- rpart(Species ~ ., data=train, method="class")

# Plot the decision tree
rpart.plot(model, main="Decision Tree - Iris Dataset", under=TRUE, faclen=0)

# Make predictions on the testing set
predictions <- predict(model, test, type="class")
actual <- test$Species

# Calculate the accuracy of the model
accuracy <- sum(predictions == actual) / length(actual)

# Print the accuracy of the model
cat("Accuracy: ", round(accuracy, 2), "\n")



```

## Explanation 

In this program, we first load the necessary libraries rpart and rpart.plot. We then load a sample dataset (iris dataset in this case) on which we want to build the decision tree.

We split the data into training and testing sets using the sample function. We use 70% of the data for training and 30% for testing.

We then use the rpart function to build the decision tree model, specifying the dependent variable (Species in this case) and all the independent variables (. in this case). We use the method argument to specify that we want to use the classification method for building the decision tree.

Next, we use the rpart.plot function to visualize the decision tree. We pass in the model object as an argument, and specify some optional parameters to customize the appearance of the plot.

We then use the predict function to make predictions on the testing set. We pass in the model object and the testing set, and specify the type of prediction we want (class in this case). We then compare the predicted class labels with the actual class labels to calculate the accuracy of the model.

Finally, we print the accuracy of the model to the console.
## Screenshots

![App Screenshot](https://user-images.githubusercontent.com/68177619/219881064-34581361-702d-4dc8-af83-cd7e9192dbee.png)


## Created by

- [@vinothkumar](https://github.com/vinothkumar2/)
