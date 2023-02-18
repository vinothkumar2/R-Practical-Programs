
# Machine Learning with R

## Root node attribute selection for Decision Trees using information gain

### Code




```r
# Load the necessary libraries
library(MLmetrics)
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
model <- rpart(Species ~ ., data=train, method="class", parms=list(split="information"))

# Plot the decision tree
rpart.plot(model, main="Decision Tree - Iris Dataset", under=TRUE, faclen=0)

# Make predictions on the testing set
predictions <- predict(model, test, type="class")
actual <- test$Species

# Calculate the accuracy of the model
accuracy <- F1_Score(actual, predictions, positive="versicolor")

# Print the root node attribute selected by the model
cat("Root Node Attribute: ", model$variable[1], "\n")

# Print the accuracy of the model
cat("Accuracy: ", round(accuracy, 2), "\n")


```

## Explanation 

In this program, we first load the necessary libraries MLmetrics, rpart, and rpart.plot. We then load a sample dataset (iris dataset in this case) on which we want to build the decision tree.

We split the data into training and testing sets using the sample function. We use 70% of the data for training and 30% for testing.

We then use the rpart function to build the decision tree model, specifying the dependent variable (Species in this case) and all the independent variables (. in this case). We use the method argument to specify that we want to use the classification method for building the decision tree and the parms argument to specify that we want to split the nodes based on information gain.

Next, we use the rpart.plot function to visualize the decision tree. We pass in the model object as an argument, and specify some optional parameters to customize the appearance of the plot.

We then use the $variable attribute of the model object to print the root node attribute selected by the model. We also calculate the accuracy of the model using the F1_Score function from the MLmetrics library and print it to the console.

In this example, the root node attribute selected by the model is Petal.Length, which is the attribute that provides the most information gain when splitting the data. The model has an accuracy of 0.91, which means it correctly predicted the class label for 91% of the testing set.
## Screenshots

![App Screenshot](https://user-images.githubusercontent.com/68177619/219874799-d0171b51-0950-42b8-a364-eceb4b22fe74.png?text=App+Screenshot+Here)

