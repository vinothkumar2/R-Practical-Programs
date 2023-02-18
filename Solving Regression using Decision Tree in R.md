
# Machine Learning with R

## Solving Regression Using Decision Trees

### Code




```r
# Load the necessary libraries
library(rpart)
library(rpart.plot)

# Load the dataset (using the cars dataset for demonstration)
data(cars)

# Build the decision tree model
model <- rpart(dist ~ speed, data=cars, method="anova")

# Plot the decision tree
rpart.plot(model, main="Decision Tree - Cars Dataset", under=TRUE, faclen=0)

# Use the model to make predictions on new data
new_data <- data.frame(speed=c(20, 40, 60))
predictions <- predict(model, new_data)

# Print the predictions
print(predictions)

```

## Explanation 

In this program, we first load the necessary libraries rpart and rpart.plot. We then load a sample dataset (cars dataset in this case) on which we want to build the decision tree.

We then use the rpart function to build the decision tree model, specifying the dependent variable (dist in this case) and the independent variable (speed in this case). We use the method argument to specify that we want to use the ANOVA method for building the decision tree.

Next, we use the rpart.plot function to visualize the decision tree. We pass in the model object as an argument, and specify some optional parameters to customize the appearance of the plot.

Finally, we use the predict function to make predictions on new data. We create a new data frame new_data with some values for the speed variable, and use the predict function to make predictions based on the decision tree model. We print the predictions to the console using the print function.

## Screenshots

![App Screenshot](https://user-images.githubusercontent.com/68177619/219874799-d0171b51-0950-42b8-a364-eceb4b22fe74.png?text=App+Screenshot+Here)

## Author

- [@vinothkumar](https://github.com/vinothkumar2/)
