
# Machine Learning with R

## Bagging, Boosting applications using Regression Trees


### Code




```r
# Load required libraries
library(rpart)
library(randomForest)
library(gbm)
library(MASS)

# Load Boston Housing dataset
data(Boston)

# Split data into training and test sets
trainIndex <- sample(1:nrow(Boston), 0.7*nrow(Boston))
train <- Boston[trainIndex, ]
test <- Boston[-trainIndex, ]

# Fit regression tree model
tree_model <- rpart(medv ~ ., data=train)

# Bagging
bag_model <- randomForest(medv ~ ., data=train, ntree=500)

# Boosting
boost_model <- gbm(medv ~ ., data=train, n.trees=500, interaction.depth=4, shrinkage=0.01)

# Make predictions on test data
tree_pred <- predict(tree_model, newdata=test)
bag_pred <- predict(bag_model, newdata=test)
boost_pred <- predict(boost_model, newdata=test)

# Evaluate model performance
tree_rmse <- sqrt(mean((tree_pred - test$medv)^2))
bag_rmse <- sqrt(mean((bag_pred - test$medv)^2))
boost_rmse <- sqrt(mean((boost_pred - test$medv)^2))

cat("RMSE for regression tree:", tree_rmse, "\n")
cat("RMSE for bagging:", bag_rmse, "\n")
cat("RMSE for boosting:", boost_rmse, "\n")




```

## Explanation 

In this example, we load the Boston Housing dataset, which contains information about houses in the Boston area and their median values. We split the data into training and test sets, and then fit a regression tree model to the training data. We then apply bagging and boosting to the data using the randomForest and gbm functions, respectively, and make predictions on the test data. Finally, we evaluate the model performance using the root mean squared error (RMSE).
## Screenshots

![App Screenshot](https://user-images.githubusercontent.com/68177619/219874799-d0171b51-0950-42b8-a364-eceb4b22fe74.png?text=App+Screenshot+Here)

