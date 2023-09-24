# White-Wine-Quality-Classification
Predict the quality of a given wine based on the selected features, including data preparation techniques.

Utilized data preparation techniques such as data descriptors, data scaling, outliers handling and missing data to aid in feature selection. 
The selected features were used for a classification task to predict the quality of a given wine based on the selected features. 

**Data Description:**

As seen from the info() and describe() functions, we have a significant number of missing data in the first 3 columns. The columns 'fixed acidity', 'volatile acidity' and 'citric acid' each have 513 missing values, this amounts to 10% of missing data. Our dataset is also not free of outliers, especially the columns 'residual sugar','free sulfur dioxide' and 'total sulfur dioxide'. The other columns do have outliers but they are not as comparable to the above 3 columns.

**Data Distribution:**
As seen from the histogram below and the description above, we can infer the distribution of the data among multiple features. Most wines have **fixed acidity** between 5.5(g/dm^3) - 7.5(g/dm^3). In terms of **volatile acidity**, majority of the data lies between 0.1 and 0.4. The **citric acid** has most of the data in the 0.3 range. Most wines have **residual sugar** at 2(g/dm^3) and has a max outlier at 65.8. Most wines have **chlorides** at 0.03(g/dm^3) - 0.06(g/dm^3) and there are some outliers. **pH** looks to have a normal distribution of data **alcohol** has a pretty average distribution across the value range and most of it is around 9.5%. **density** is concentrated in the range of 0.99 to 1.00. **free sulfur dioxide** has a wide distribution from 0 to 100 and some significant outlier value of 289. **total sulfur dioxide** is distributed in the range of 40 to 200, with significant outlier values upto 440 and **sulphates** are significantly concentrated at 0.4(g/dm^3) and 0.5(g/dm^3).
**quality** is our target variable and 5,6,7 are the most prominent values and is imbalanced.


## Data Scaling

Here we visualize the effects of data scalers on our input features using boxplot. The scalers used are MinMaxScaler, MaxAbsScaler, RobustScaler.

We use **MinMaxScaler** as it redistributes the data to a smaller scale, in this case (0 to 1) as seen below, also as we have removed/handled outliers and missing data, this scaler is more suitable

**MaxAbsScaler** it is considered as it does not change the distribution shape and also it works better as we have handled the outliers before hand

**RobustScaler** it is more inline with our interquartile approach of scaling and also it can handle existing outliers. This scaler is used in case if there are outliers existing in the data.

## Handling missing data and outliers

In order to do the missing data and outlier handling, we will make use of our original data frame **White_Wine**.
Here to handle missing data we will consdier using ffill(forward filling).

And to handle outliers we will make use of the interquartile range, as it will not extrapolate our outliers.

**Classification Task**

Here we will make use of **Random Forest classifier and KNN Classifer**, as they provided the best performance among other methods exectued (SGD and SVC). Also we will make use of **f1_weighted** as the metric of choice, in our case the target variable (**quality**) is imbalanced in nature. This can be seen by the histogram plotted to visualize the data distribution, in such a scenario **f1_weighted** will provide a model that is more reliable and not overfitting.

## Feature Selection

As defined at the start of our project, we consider the **quality** column as our target variable. 
Also we will make use of the forward and backward selection under the Wrapper approach of feature selection. We have chosen this approach, as it is robust and allows for using a range of learning algorithms. This will help us in determining the best approach to successfully complete our classification task.


