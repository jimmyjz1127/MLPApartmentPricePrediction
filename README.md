# ML Apartment Pricing Dataset Regression Task
## Author : James Zhang (jimmyjz1127)

This project aims to implement a number of approaches for the regression task of predicting housing prices for a given dataset.
The following are implemented:  
1) Data Pre-processing pipeline containing feature pruning, imputation strategies, numerical standardization, one-hot encoding, dimension reduction
2) A number of regression models using Scikit-Learn 
3) A fully connected feedforward muli-layer perceptron using PyTorch
4) Evaluation 

## Dataset 
|Feature|Description|
|---|---|
|`category`|string indicating type of housing (e.g `housing`, `apartment`)|
|`title`|title of listing on realestate site|
|`body`|description of listing on realestate site|
|`amenities`|series containing list of amenities (e.g `Dishwasher,Refrigerator`)|
|`bathrooms`|number of bathrooms|
|`bedrooms`|number of bedrooms|
|`currency`|type of currency (e.g `usd`)|
|`fee`|`yes` or `no` for whether a fee is associated with listing|
|`has_photo`|`thumbnail`, `yes`,`no`|
|`pets_allowed`|series of pets allowed (e.g `dog,cat`)|
|`price`|The response variable - pricing of listing|
|`price_display`|string version of price|
|`price_type`|indicates method of payment (e.g `monthly`)|
|`square_feet`|number indicating square footage|
|`address`|address of listing|
|`cityname`|name of city where listing is located|
|`state`|US state code for listing|
|`latitude`|latitude coordinate for listing|
|`longitude`|longitude coordinate for listing|
|`source`|the listing site|
|`time`|time that listing was made|

## Data Preprocessing Steps 
1) The following features were dropped :  
    1) `id`
    2) `title`
    3) `body`
    4) `currency`
    5) `price_display`
    6) `address`
2) The following series type features were split and one-hot encoded 
    1) `amenities`
    2) `pets_allowed`
    3) `category`
3) The `cityname` feature which had a large cardinality was removed and replaced with a ordinal value (0,1,2) indicating whether the average `price` for that city is under 1000, between 1000-2000, or above 2000
4) The `state` attribute was replaced by regions such as `Mid_Atlantic`, `E_N_Central`
5) The numerical features were all standardized
6) The remaining non-numerical features were all one-hot encoded or binarized where appropriate 