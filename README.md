# Best Location To Rent An Apartment in Toronto, Ontario, Canada

## Introduction 

In this project, I will try to find an optimal location to rent an apartment in Toronto. I will try to apply the data science techniques to discover the utmost neighborhoods in the city of Toronto based on the following criterias:

 * Number of groccery stores.
* Number of parks	
* Number of coffee shops	
* Number of resturants	
* Number of transit stops	
* Crime rates	
* Average price of rentals 

This project mostly targets the newcomers to the city of Toronto, who are not familiar with the neighborhoods of Toronto.

## Data

I decided to use the following data sources for the defined criterias:

* [https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M](https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M): which corresponds to the neighborhoods of Toronto

* [http://cocl.us/Geospatial_data](http://cocl.us/Geospatial_data): This data source contains the coordinates of each postal code. Therefore, its corresponding neighborhoods.
* **Foursquare API**: to explore each neighborhood.
* [https://www.kaggle.com/brahmdata/major-crime-indicators201419-toronto-police](https://www.kaggle.com/brahmdata/major-crime-indicators201419-toronto-police): The location of any crime that happened in Toronto from 2014 till 2019.
* [https://www.kaggle.com/rajacsp/toronto-apartment-price](ttps://www.kaggle.com/rajacsp/toronto-apartment-price): The address and the rent of each available apartment in Toronto.

## Methodology

Toronto has 140 neighborhood. However, I didn't have access to all of their coordinates. As a result, I used the postal codes as an identifier for the neighborhoods and assign the coordinates of the postal codes to the neighborhood it covers. So I will start by preprocessing the data by doing the following steps:

1. Retreiving the postal codes of Toronto. Removing the ones with no assigned boroughs.
2. Assigning the coordinates of each postal code.
3. Exploring the number of Grocery Stores, Pharmacies, Parks, Coffee Shops and	Resturants in a neighborhood by using the **Foursquare API**.
4. Calculating the number of transit stops in each neighborhood.
5. Fetching the crime rates of 2019 for each neighborhood.
6. Computing the average price of a 1-bedroom apartment in each neighborhood.
7. Creating the dataframe of the above information.

The result dataframe should have the following information:
`Neighborhood, Grocery Stores,	Pharmacies,	Parks,	Coffee Shops,	Resturants,	Stops,	Crimes,	Price`

Now, for analyzing the constructed dataframe, I use the weighted score of each column for the neighborhood but before that I normalize my data in each column. The score of a neighborhood is calculated by the following formula:

`Grocery Stores	+ Pharmacies + Parks + Coffee Shops + Resturants + Stops+( -3 *Crimes ) + (1 - Price)`

You'll notice that the higher the crime rate and the rental price is in a neighborhood, the less the score will be but the score is more biased towards the safer neighborhood.

## Results

I have found the following locations, the best areas to rent a one bedroom apartment:

Neighborhood | Grocery Stores |	Pharmacies | Parks | Coffee Shops | Resturants | Stops | Crimes | Price
------------ | ------------- | ----------- | ------| ------------ | ---------- | ---------- | ---------- | ----------
Enclave of M5E | 0 | 2 | 2 | 14 | 23 | 9 | 511 | 2412.500000
Design Exchange | 0 | 1 | 0 | 18 | 25 | 4 | 297 | 1250.000000
Victoria Hotel | 0 | 0 | 1 | 19 | 32 | 19 | 828 | 2427.142857
Berczy Park | 0 | 2 | 1 | 5 | 13 | 24 | 487 | 2393.750000
Underground city | 0 | 0 | 0 | 18 | 30 | 3 | 351 | 1892.857143
St. James Town | 1 | 1 | 2 | 11 | 21 | 29 | 2654 | 1993.608696
Toronto Islands | 0 | 0 | 2 | 16 | 13 | 16 | 1303 | 2335.373134
Christie | 4 | 0 | 2 | 4 | 2 | 110 | 2358 | 1733.900000
Thorncliffe Park | 1 | 1 | 1 | 1 | 4 | 67 | 1109 | 1200.000000
Central Bay Street | 0 | 0 | 1 | 14 | 19 | 26 | 1713 | 1916.263158

## Discussion

For finding the above result, I normalized my data and then computed the weighted average. However, the weight of each criteria depends on the importance of it to an individual. Therefore, with other weights, we might get a different results. Also, the above result are for one bedroom apartments. The result are different based on the number of bedrooms, since the price is different.

## Conclusion 

In this project, I compared different locations and neighborhoods in Toronto based on different criteria and found the above locations the best places to rent one-bedroom apartments. 
