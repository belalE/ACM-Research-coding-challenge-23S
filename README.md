# ACM Research coding challenge (Spring 2023) - Belal Elsiesy

For this challenge, I decided to explore a few of the example problems given. I had the following goals:
1. Finding the most common star type in the dataset
2. Exploring patterns and relationships between variables
3. Finding the properties most influential in classifying star type
4. Training a machine learning model to predict star type

## Problem 1: Finding the most common star type in the dataset
--- 
This problem was the most simple. Using pandas's groupby function, I could view the count of each star type, which I also visualized in a bar graph. Both of these showed that there was an even distribution of star types. Each of the six star types had 40 entries each, resulting in the 240 datapoints.

## Problem 2: Exploring patterns and relationships between variables
--- 
To explore patterns and relationships between variables in the dataset, I used an incredibly useful visualization, seaborn's pairplot. This plot, seen below, revealed interesting patterns between star type and absolute magnitude, luminosity, and radius. Also, it revealed strong correlations between absolute magnitude and temperature, luminosity, and radius. 

![Screenshot 2023-02-01 at 10 49 02 PM](https://user-images.githubusercontent.com/28294251/216234336-d5cbd1e2-4c87-4174-80bb-3a0322e8c64e.png)

To more accurately understand these relationship, I used pandas's corr() function to find the pearson correlation coefficient between the variables. This data, which I visualized in the below heatmap, confirmed the relationships shown in the pairplot. For example, look at the Pearson correlation coefficient between Absolute magnitude and :
- Star type: -0.96
- Luminosity: -0.69
- Radius: -0.61

![image](https://user-images.githubusercontent.com/28294251/216235369-c0b6e149-1847-41f3-9d8a-d61c473db345.png)


I further visualized these relationships with jointplots.

## Problem 3: Finding the properties most influential in classifying star type
--- 
To approach problem 3, I took a similar approach to tackling problem 2. I graphed the results of the corr() function to see which variables were most strongly correlated to star type. The graph is seen below. 

![image](https://user-images.githubusercontent.com/28294251/216235583-31820278-4650-4051-8054-dffc09392766.png)

The result of this analysis showed that absolute magnitude was the most influential on star type.

## Problem 4: Training a machine learning model to predict star type
--- 
To tackle this problem, I decided to use an artificial neural network for multiclass classification.
After performing the train test split, I prepared the data by dropping missing values and using an encoder to transform the categorical variables to integers decipherable by the neural network. Then, I created a model with 3 layers:
1. A ReLu input layer with 6 nodes for the 6 inputs
2. A ReLu hidden layer
3. A SoftMax output layer with 6 nodes for the 6 possible star type outputs

After training for 600 epochs, the model had 83.9% accuracy and a 75.0% validation accuracy. However, the loss, evaluated by the sparse categorical cross entropy function, fluctuated heavily, as seen in the graph below.

![image](https://user-images.githubusercontent.com/28294251/216237378-a8ff9cbb-7788-40c9-aaf2-7b65143165de.png)

The performance of the model was dissappointing, but I did not have time to adjust it or improve it due to the constraint of time. To improve performance, I could:
- Adjust the layers of the model
- Better prepare the data, as I had issues with the categorical data in string form
- Adjust the number of epochs 
- Implement cross validation, such as KFold cross validation
- Try different types of classifiers, such as a Decision Tree or Random Forest



