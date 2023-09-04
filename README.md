# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The primary goal of this project is to perform Statistical Modelling using Python by extracting bike data from CityBikes API service for any city of our choice and retrieve different point of interests close to these bike stations retrieved using the CityBikes API. For retrieving the POI data we would collect data from the FourSquare API and Yelp API. This project also involves comparison between the above mentioned API's from which more valuable / meaningful data can be retrieved. Also, come up with a Statistical Model to intrepret the retrieved results. The purpose behind this project is to put our best ability of Python learning, understanding of the Pandas framework , plotting using Python and have hands on the statistical modelling python packages to make ourselves familiar

## Process

### Configuration and Initial Set up
To begin with I took a clone of the **Statistical-Modelling-with-Python** repository from LHL's git repos and started familiarizing on the assignments.md file
Also, ensured the correct naming standards are followed upon for the repository and also frequent code commits are made for avaoiding code loss


### Explore the CityBike / foursquare/ yelp API's
<n> During this process, I did explore the citybike API/ foursquare API and Yelp API using Postman. </n>
<n> I did navigate to the citybike API and did hit the API endpoints both: </n>
**http://api.citybik.es/v2/networks** and 
<n> **http://api.citybik.es/v2/networks/networkid** .</n>
<n> After this initial exploration of the API, I did finalize my city of exploration to be Vancouver Canada and cover the POI's within 1000 mile radius from the mentioned city. </n>
<n> As part of this step I did generate the API keys for foursquare and Yelp Fusion API </n>

### citybike API data 
As part of this I have to populate the citybike.ipynb notebook. I did hit the second API endpoint which was specific with the networkid as below:
http://api.citybik.es/v2/networks/mobibikes - mobibikes was the name of the station in Vancouver.
The output from the API would be stored in the format of JSON.
Also, as next step, I did parse the JSON output to input the same into Pandas dataframe. Most important part of this parsing is, we need to figure out which are the essential fields that we need to parse
from the JSON to our dataframe. I did spend a quality time, as this would be the base for my entire project, as part of the next steps, we need to join the dataframes of citybike with the POI that we would
be retrieving from following foursquare and yelp API's . The output is stored in the local as .csv file and the same is attached along with other artifacts

### foursquare API data
<n>I did import the necessary python packages for working further on this and other API's </n>
<n> This step requires to hit the API endpoint to retrieve the POI for the foursquare API. I did pass the value of the location of the city that I have used as a param to the API endpoint.
This is one of the Pro of the foursquare API, where you can search the near by POI based on the latitude and longitudes or by passing the city name. Once the desired response is achieved using the GET function,
I did store the output as a JSON and parsed the JSON for each latitude and longitude from the citybike API output dataframe which is retrieved from the .csv file as a dataframe in the prerequisite step before hitting the foursquare API. Based on the output parsed the foursquare JSON output and loaded them into a pandas dataframe. The output is also stored as a .csv file and retrieved for later use in joining the data frames. This is available in the yelp_foursquare_EDA.ipynb

### yelp API data
<n> This step requires to hit the API endpoint to retrieve the POI for the Yelp Fusion API. I did pass the value of the location of the city that I have used as a param to the API endpoint.
This is one of the Pro of the Yelp API, where you can search the near by POI based on the latitude and longitudes or by passing the city name. Once the desired response is achieved using the GET function,
I did store the output as a JSON and parsed the JSON for each latitude and longitude from the citybike API output dataframe which is retrieved from the .csv file as a dataframe in the prerequisite step before hitting the Yelp API. Based on the output parsed the Yelp JSON output and loaded them into a pandas dataframe. The output is also stored as a .csv file and retrieved for later use in joining the data frames.
This is available in the yelp_foursquare_EDA.ipynb

### Joining data and provide visualization
Further the data from the citybikes API / foursquare API and Yelp API converted to a pandas dataframe using the .csv file and they were joined to get the desired output.
I did provide histogram visualization/ box plot and heat map for the final data frame which was the joined output of all the API dataframes. The data was further checked for any duplicates and sorted accordingly


### Set up SQLite Database
The joined data which is part of the finally merged dataframe was then imported into the SQLite database **statmoddel_python_poi**. The shapes of the dataframe and their data types were assesed as part of this excercise. Also couple of SQL queries were executed as part of this excercise in VSCode and ensured that the dataframes are loaded properly into the tables. The above step and this step could be found in the 
joining_data.ipynb file.

### Compute Regression Models
This was the interesting plot of the project. The merged dataframe is checked for 'Nan' values, duplicates and the outliers are elimiated and the Regression models are applied on the data.
I did perform OLS regression model on the derived data. During this process, i did figure out there is a strong correlation between the slots, no_of_bikes (free bikes) and empty slots.
Also, figured out there is a very weak regression that exists between latitude/ longitude and rating of the POI. The detailed explanations and corresponding model data is available as part of the **model_building.ipynb** notebook

## Results
I did figure out based on the categories that we choose the API results are retrieved. In this project, during my exploration process I did use the categories of Travel and Transportation. These categories has less data in Foursquare but there were precise and crisp POI data available with yelp API. So I would infer for this category selection Yelp API did provide me more data when compared to that of foursquare and had rating data provided for each of the POI based on our search. But when the same excercise was performed for the categories of Restaurant/ ATM's/ Park, there was more data available with less dupes from foursquare and yelp had very less POI data for ATM's and Parks. Hence I could arrive at the conclusion, that based on the categories that we decide to use for the API data generation the POI data from the corresponding API's would vary. Also, the modeling part of this project gave me very thoughful insights and outcomes how the discrete variable X varies with the continous variable Y.

## Challenges 
As part of the project following challenges were faced:
1. Less API POI data for several categories from foursquare/ yelp API's
2. Per day Limit was throwing off as we had to iterate the API results for all the bike co-ordinates within the bike station
3. Had hard time during the process of joining data. Had to round the lat and long so that we get effective dataset for the modelling
4. As part of Modelling, had issues in configuring and understanding the OLS components and deriving the right conclusions
5. There were nulls, Nan values and duplicates to be handled before modelling was employed
6. Also, there were outliers that need to be consider removing for achieving good regression models
7. Had to parse the JSON for each lat & long and store the outputs
8. Though the visualizations were simple, but the effort and process behind each of these outputs were huge and time taking

## Future Goals
If i had time, I would have explored further few other categories that could provide more API POI data. Also would end up converting the regression models to classification models and derive at more insights from the data available
