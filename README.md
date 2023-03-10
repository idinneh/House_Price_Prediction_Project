# House Price Prediction Project
## Overview
As our final project, we have decided to predict house prices using historical data and machine learning. We chose this topic because the housing market is widely talked about, especially since the start of the COVID-19 pandemic. We also chose this topic because the housing market affects all of us in one way or another. Our analysis will help to answer two questions: how accurately can a model predict the sale price of a house and what are the most important features that can impact the price of a house? 

[Link to Tableau Dashboard](https://public.tableau.com/app/profile/sandra.nwokolo/viz/Final_project_16758302638690/FinalprojectDashboard?publish=yes)

**Dataset**
- There are two datasets being used for this analysis: data on houses with their prices sold in Seattle, Washington, USA between August and December 2022 from Kaggle, and data on all houses in the United States with their zip codes and coordinates.
- The data on houses with their prices sold contains both training and testing data with columns 'beds', 'baths', 'size', 'size_units', 'lot_size', 'lot_size_units', 'zip_code', and 'price'. The target column is 'price' and the other columns are the features.
-  Fortunately, the data we found on Kaggle is well-structured (**link**: https://www.kaggle.com/datasets/samuelcortinhas/house-price-prediction-seattle). 
-  The main challenge we faced while choosing the dataset is that we could not find data on the topics we found most interesting, and the data we were able to find was complex and required a lot of cleaning. Therefore, we searched for data that was reasonably easy to work with. While our dataset only contained data spanning 5 months ending in Decemeber 2022, we wanted to use it as this was very recent and can give us good insights. 
-  For our second dataset, we were able to extract the coordinates for the houses in Seattle from Excel (**link**: https://www.listendata.com/2020/11/zip-code-to-latitude-and-longitude.html). Using VLOOKUP, we found the corresponding coordinates (???lat???, ???lon???) from the second dataset to the Zip Code in the first dataset (testing and training files)

|ERD | 
| ------------- |
|![Screenshot 2023-02-01 200225](https://user-images.githubusercontent.com/111667387/216205791-3c5a0304-c405-4f45-b89c-d5e62632f306.jpg)|

| Final DataFrame | 
| ------------- |
|![Dataset](https://user-images.githubusercontent.com/111667387/215643247-da31c70f-86f3-4714-892b-ab6897e44dec.jpg)|


| Training File Data Types | Testing File Data Types |
| ------------- | ------------- |
| ![Datatypes 1](https://user-images.githubusercontent.com/111667387/215642689-87ad7c05-c850-4c8f-a192-e4f9667e257f.jpg)|![Datatypes 2](https://user-images.githubusercontent.com/111667387/215642736-b5fdb394-d9c9-40ec-9f32-da7410c99c73.jpg)|

**Tools & Technologies**
- Visualization: Tableau, Seaborn, Matplotlib, Flask
- Data Analysis: Jupyter Notebook, Excel
- Algorithms: Linear Regression, Random Forest Regression, k-Nearest Neighbours (k-NN)

**Project Status**: We have built several machine learning models and determined that the linear regression model is the best model to use as it had the lowest number of errors. We also built an interactive dashboard in Tableau.

## Results
**Visualization** 
|Pairplot: Using pairplot in Seaborn, out of the 5 plots generated, we can see that the increase in price is most strongly influenced by the increase in house size. Similar but weaker relationships are also seen between price and the number of beds as well as price and the number of baths. In addition, we can see that prices for different lot sizes varies indicating that other factors such as location may be playing an important role.| 
| ------------- |
|![pairplot ](https://user-images.githubusercontent.com/111667387/216508451-b7abbdb8-8d8d-4d73-aa21-b97dda9207f8.jpg)|
|**Barplot**: Using barplot in Seaborn, we were able to illustrate how house prices vary signficantly depending on the zip code. We can see that houses in zip codes 98109 and 98168 are the priciest. On the other hand, houses with zip codes 98199 and 98146 are the cheapest. Zipcodes was also ranked number 1 on our list of feature importance.| 
|![barplot](https://user-images.githubusercontent.com/111667387/216508256-d0984b54-c87d-4558-9f6b-42f0be5e341c.jpg)|
|**Heatmap**: Using heatmap in Seaborn, our map showed that the number of beds and house size are the most positively correlated followed by size and price and then baths and size. Conversely, the most negatively correlated factors are beds and lot size followed by zip code and price and then baths and lot size. We believe some of these correlations are inaccurate which indicates that there may be some issues with our dataset.| 
|![heatmap](https://user-images.githubusercontent.com/111667387/216514150-2dc4e59f-eeef-4daa-9f07-6b6b1f008e75.png)|

**Model #1: Linear Regression** 
|Our linear regression model performed poorly overall with a model train score of 0.21 and test score of 0.13. The mean absolute error (MAE) was also very high with a score of 306819.77 and a root mean squared error (RMSE) of 553.91. While we are not satisfied with these scores, we achieved our goal of building a simple functioning model. We now plan to use scaling, adding more features, and trying different models to determine the best model to use. | 
| ------------- |
|![model evaluation ](https://user-images.githubusercontent.com/111667387/216739702-19e791bb-6dee-4c4e-802f-dd9a6b530009.png)|



**New Models with Added Features**

In the second notebook, we made the changes below to see if it could help improve the data of our model:

**1.** We combined the data of the test and train dataframe in order to create our own split for the model. 

![combined_df](Static/Images/combined_df.png)

**2.** We added new features to our data set like the Average Income per Household and Population in each zip code. We also dropped the following features that were not needed for our model: Lot Size Units, Size Units, Coordinates, National Rank, and City.

**3.** We scaled the x values of the dataset.

![scaled_x](Static/Images/scaled_x.png)
            

Using our second notebook with added features, we trained three models: Linear Regression, Random Forest, and KNN Regression. The Linear Regression model showed the lowest number of errors among the three.

|Linear Regression model: the model score is 24%. It is still poor but there is a slight improvement compared to the result of our first model. The mean absolute error (MAE) was roughly 274821.3 and the root mean squared error (RMSE) was roughly 1019983.08.| 
| ------------- |
|![lr_model_cb](Static/Images/lr_model_cb.png)|


|Random Forest model: the mean absolute error (MAE) was roughly 294627.4 and the root mean squared error (RMSE) was roughly 542.80.| 
| ------------- |
|![random_forest_cb](Static/Images/random_forest_cb.png)|
            


|KNN Regression model: the mean absolute error (MAE) was roughly 500116.05 and the root mean squared error (RMSE) was roughly 707.19.| 
| ------------- |
|![kn_reg_cb](Static/Images/kn_reg_cb.png)|
            

            
            



## Summary 
Overall, we consider our final project to be a success as we worked well as a team and used various tools and resources to build a model and present our findings. We initially built a functioning linear regression model, but it had poor results as the mean absolute error (MAE) was 306820. To improve this model, we combined and then split the test and train dataframe, added and dropped features, and scaled our dataset. Using the updated dataframe and dataset, we tested the linear regression, random forest, and KNN regression models. Our test results showed that the linear regression model had the lowest MAE (274821) which is a modest improvement from our inital linear regression model. We also found that the most important feature is the zip code followed by the house size. In addition, we created different diagrams to gain better insights on our data. Lastly, we created an interactive dashboard that tells a story on our model. 
