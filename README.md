# Regional Cuisine Classifier


## Motivation


We wanted to see if there was a way to classify different recipes’ cuisine types by region, just by taking in a list of ingredients.
Our goal was to create a model in which by inputting ingredients in a function, it will give an output of which possible region the ingredients belong to.
Companies such as Yelp, GrubHub and Seamless can use this type of model to help classify food based on ingredients or dish name.

-----------
## Sources:

We web scrapped the following websites for recipe ingredients. All scrapped ingredients had a tag of which region it belongs to:

[BBC Food](https://www.bbc.com/food/cuisines), and [Epicurious](https://www.epicurious.com/cuisine/)

-----------

## EDA of our DataFrames:

DataFrame Head: This just shows the top five rows of our dataframe. Cuisine is our Target (y) variable while recipe_ingredients is our independent variable.

<img width="644" alt="screen shot 2019-01-09 at 10 06 07 pm" src="https://user-images.githubusercontent.com/41834786/50943615-3416ce00-145b-11e9-9649-cf4b19f29713.png">

Below is a bar graph showing all features used and how many recipe each feature had. They are relatively evenly distributed, with low class imbalance

<img width="893" alt="screen shot 2019-01-09 at 10 06 30 pm" src="https://user-images.githubusercontent.com/41834786/50943887-375e8980-145c-11e9-9f7e-2e550a1b207a.png">

And lastly, a sample of word cloud showing how unique each region recipe ingredients are:

<img width="904" alt="screen shot 2019-01-09 at 10 06 45 pm" src="https://user-images.githubusercontent.com/41834786/50943976-9de3a780-145c-11e9-99ed-801c8371176c.png">

-----------

## Cleaning Up the Data

After EDA, we cleaned up our data. This meants get rid of common stop words that are already in the NLP English Corpus, in addition to punctuations and additional common words that show up in all recipes, such as units of measurements.
After cleaning, we looked at the bi-gram as many recipe ingredients such as oil has another word paired with it that may make it uniue to a region.

<img width="697" alt="screen shot 2019-01-09 at 10 22 38 pm" src="https://user-images.githubusercontent.com/41834786/50944134-34b06400-145d-11e9-8af7-51044f3e1152.png">

-----------
## Data Analysis


Then we looked at a ROC/AUC (Reciever Operating Characteristics/ Area Under Curve):

<img width="653" alt="screen shot 2019-01-09 at 10 26 10 pm" src="https://user-images.githubusercontent.com/41834786/50944234-97a1fb00-145d-11e9-970c-14914ce61ce6.png">

Here is the SVM Confusion Matrix that showed how well our model predicted correctly. Vertical is the actual target and horizontal is the prediction. While there are some incorrect predictions, they also appear to share many common recipe based on regional and/or cultural similarities 


<img width="698" alt="screen shot 2019-01-09 at 10 29 01 pm" src="https://user-images.githubusercontent.com/41834786/50944351-02ebcd00-145e-11e9-8a97-4e1e9fe49476.png">

-----------

## Model Results

We made multiple models with multiple GridSearch CV parameters to get the best model possible. After multiple model run and hyper parameter tuning we found that Random Forest tuned with GridSearch works best.
Our model predicts with a nearly ~70% accuracy. Given that this is a multiclass classification model based on text data, this is excellent. If one were to pick a region based on recipe ingredients, their accuracy would be 100 divided by the numbers of classes we are trying to predict. So it is 100/14 which is 7.14%.
Here is a basic picture of all our model and their accuracy score. All actual work can be found in the Final_Compiled notebook file

<img width="544" alt="screen shot 2019-01-09 at 10 34 09 pm" src="https://user-images.githubusercontent.com/41834786/50944508-b359d100-145e-11e9-9461-9676db4f55e3.png">


Thank you for reading.



