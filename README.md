# World_Weather_Analysis

## Project Overview
We've created the PlanMyTrip App which intakes user input for the temperature ranges for their vacation and returns an itinerary for a trip to cities with hotels that fall into the requested range. Using the Open Weather Maps API and Google Maps API we created an mock itineraru using the PlanMyTrip app script.

## Resources:
Data Source: Open Weather Map API, Google Maps API, WeatherPy_database.csv, WeatherPy_vacation.csv

Software: Python 3.7.6, Jupyter Notebook, Matplotlib, Numpy, Pandas, Citipy, Requests & datetime modules

## Analysis
Generating the vacation itinerary for a mock use of the PlanMy Trip app is as follows:

### Identifying cities and weather
First, we created a list of cities and found the local weather for those cities.
1. Using numpy's random function we created a set of 2000 random latitude and longitude lines.
2. Using citpy's nearest_city function we associated 749 of the latitude and longitude pairs to cities around the world.
3. Using Open Weather Map's API we attributed the current weather of the cities found by the citipy module and placed the data in a dataframe (See Picture 1.1) and exported to a csv file.

**Picture 1.1: Example Open Weather Map API dataframe**
![Example Open Weather Map API dataframe](https://github.com/joshuanallen/World_Weather_Analysis/blob/213c6a863406eff220e8b60886146fb5e0300147/city_data_df.png)

### Plotting cities within user's desired temperature range
Next, we imported the above list of cities and their current weather to isolate those that fall within the user's requested temperature range.
1. We imported the city data with the Open Weather Map data into a dataframe. Then we isolated those that fell within the user's input for ideal temperature range (70-85 degrees Farenheit in this example).
2. Using the Google Maps API we pulled in the closest hotel within 5000m of the coordinates for cities that fall within the set temperature range.
3. The qualifying cities with hotel data is exported to csv file
4. Using gmaps module we plotted the cities with hotels in range on a world map. (See Picture 2.1)

**Picture 2.1: Example map with city and hotel info within user input temperature range**
![Example map with city and hotel info within user input temperature range](https://github.com/joshuanallen/World_Weather_Analysis/blob/213c6a863406eff220e8b60886146fb5e0300147/Vacation_Search/WeatherPy_vacation_map.png)


### Creating a travel itinerary
Finally, we use the created list of hotel and city data within the desired tempoerature range to select destinations and create a travel itinerary.
1. We imported the qualified city and hotels into a dataframe
2. Using Gmaps module we plotted the cities with a marker layer on a world map
3. We identified four cities within travel range of each other to build a travel itinerary and created tuples for the latitude and longitude pairs.
4. Using Gmaps directions layer we plotted driving directions to create a round trip itinerary to the four identified cities. (See Picture 3.1)

**Picture 3.1: Example map with travel itinerary driving route**
![Example map with travel itinerary driving route](https://github.com/joshuanallen/World_Weather_Analysis/blob/213c6a863406eff220e8b60886146fb5e0300147/Vacation_Itinerary/WeatherPy_travel_map.png)

5. Using the gmaps marker layer we plotted the four derstination cities on a map populated with the hotel, city, and weather information. (See Picture 3.2)

**Picture 3.2: Example map with travel itinerary city and hotel info**
![Example map with travel itinerary city and hotel info](https://github.com/joshuanallen/World_Weather_Analysis/blob/213c6a863406eff220e8b60886146fb5e0300147/Vacation_Itinerary/WeatherPy_travel_map_markers.png)

## Conclusions
Using the Open Weather Map API and Google Maps API we were able to create a mock travel itnerary for a user looking to vacation in four cities within a desired temperature range.

### Limitations of current script and future improvements
The current script is limited to a manual selection of 4 cities within reasonable travel distance. Additionally, the gmaps module limits travel options to driving, bicycling, and walking. 

To improve the functionality of our script we whould add the ability to have the user identify an area in which they would like to travel as an additional filter and apply that geolocation automatically filter and find four relevant cities within those parameters
