# ACM Research coding challenge (Fall 2022)

This semester's challenge is especially open-ended. [Here is a dataset](https://www.kaggle.com/datasets/chancev/carsforsale) on Kaggle called "CarsForSale". It contains data scraped from the online car marketplace Cars.com. Each row contains 25 pieces of information about a car's listing, such as its price, year, model, and color.

The challenge is to do *something interesting* with the data. Can you find a pattern, answer a question, or create a visualization? In case nothing comes to mind, here are some ideas, with varying complexity:

- What qualities about a car do buyers seem to value the most?
- Make a graph to visualize the most popular car models over time.
- What colors of cars are most expensive?
- Do different brands try to appeal to people looking for different things?
- Come up with your own algorithm to figure out how good of a deal a listing is and compare it to the one in the dataset (`DealType`).
- Use [cluster analysis](https://en.wikipedia.org/wiki/Cluster_analysis) to group the cars into categories.
- How do people's taste in cars differ between states?
- Train a machine learning model to predict some aspect of a car based on other information from its listing.

However, we strongly encourage you to come up with your own problem to solve!

You can use any programming language, framework, or library you want, but we recommend [creating a notebook in Kaggle](https://www.kaggle.com/docs/notebooks) and using Python. This will run in your browser, interlaces code with documentation, allows you to import the CarsForSale dataset easily by pressing the "Add data" button, and gives you access to Python's high-quality, high-level libraries for working with data. [Learn more about data science in Python.](https://www.w3schools.com/datascience/ds_python.asp)

## How to submit your solution

1. [Create a  **public**  fork of this repository](https://docs.github.com/en/get-started/quickstart/fork-a-repo) and name it  `ACM-Research-coding-challenge-22F` (click the "Fork" button in the top right).

2. Replace this README file with a description ([written in Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/about-writing-and-formatting-on-github)) of your solution. Regardless of your success, describe the problem you set out to solve and how you did it. Split it up into sections with headers, and, if relevant, include figures.

3. Make sure to include all relevant files in your fork. If you made the project in a Kaggle notebook, click **File** → **Download Notebook** to download it as an `.ipynb` file.

4. You may have to "clone" the fork you made to edit files locally on your computer and "push" them to GitHub. Learn how to do that [here](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository).

4. Submit the link to your fork in this [form](http://apply.acmutd.co/research-coding-challenge).

## No collaboration policy

**You may not collaborate with anyone on this challenge.** You _are_ allowed (and encouraged) to use internet documentation. If you use existing code (either from Github, Stack Overflow, or other sources), **please cite your sources in the README**.

## Timing

Please don't spend too long on this project: **30 to 60 minutes** is reasonable. It's okay to put more time into your submission than that, but we don't expect you to get that much done; we really don't want this challenge to be a burden!

If you're *completely new* to this kind of project, however, it will likely take you more than an hour. This is a *densely useful* project to go through (you will learn a lot), so we believe this is justified.

## Assessment criteria

Submissions will be evaluated holistically, in combination with the rest of your application. We will consider your effort, use of external resources, how you approached the problem, and presentation, among other considerations.

## Support and questions

Feel free to ask for clarifications in the #research-qna channel in the [ACM UTD Discord server](https://discord.gg/nJxRdKdG4d)! You can also directly message Roman Hauksson on Discord: `RomanHauksson#3458`.

## Description and Solution

1. **First Approch:**<br>
&emsp;This car sales dataset is interesting. When analyzing the data, I found many interesting patterns. When filtering the null data from the dataset, I noticed ‘DealType’ had 222 null data. Looking at those 222 data points, I thought I could create a model to predict the deal type. However, I ran into many problems. The model performed poorly under three techniques - Sklearn’s linear regression model, Sklearn’s SVM, and Python’s XGBoost. There were many problems with the dataset. For instance, the uneven distribution of the data made it very difficult to train a model. So, I took a step back and plotted the correlation matrix. DealType had very little correlation with the other features. 
2. **Final Solution:**<br>
&emsp;Even though the first approach didnt lead to anything I anticipated, there was new and compelling information about the datset. Six features positively and strongly correlated to Consumer Ratings. These six features are Comfort Rating, Interior Design Rating, Performance Rating, Value For Money, Exterior Style Rating, and Reliability Rating. I analyzed this correlation by plotting the Consumer Ratings feature weights and importance. As expected, the six most contributing features were the same as the correlation matrix. I then separated the dataset to use these six features to predict the consumer rating. I used a linear regression model, an SVM, and XGBoost, where all three performed very well, providing high accuracy results.<br>
&emsp;My next thought was how this correlation would affect other features. So, I looked at the Price feature. From the correlation matrix and important feature visual, there seemed to be a correlation between price and consumer rating. So I trained a model with all the features to predict the price of the car. Then I trained the model with the six features (Comfort Rating, Interior Design Rating, Performance Rating, Value For Money, Exterior Style Rating, and Reliability Rating, and without the consumer rating) and a model with just consumer rating (and with the six features). <br>
&emsp;Since these six features have a strong correlation to another feature, I wanted to see if there would be a difference without one of them. There is a minimal difference with and without the feature consumer rating in predicting price values, as shown in the demonstration. <br>
&emsp;Many example notebooks on Kaggle using this dataset filter and clean the data. These notebooks delete features like Stock# and VIN as they provide little information about the price. Since Consumer Rating is a compilation of six other features, Consumer Rating could be considered unnecessary information. This idea requires more analysis but should be considered when using this dataset.<br>

## Source
-https://www.kaggle.com/code/ekasabrol/cars-for-sale-clean-encode-classifier (for data cleaning) <br>
-https://www.kaggle.com/code/abhishekamishra/samplenotebook (for sklearn's feature importances) <br>
