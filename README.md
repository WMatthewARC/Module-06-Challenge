# Module-06-Challenge | python-api-challenge

#### Background
Whether financial, political, or social—data's true power rests in its ability to answer questions definitively. So, let's take what you've learned about Python requests, APIs, and JSON traversals to answer a fundamental question: "What's the weather like as we approach the equator?"
Now, we know what you may be thinking: "Duh. It gets hotter ..."
But, if pressed, how would you prove it?



## Part 1 : WeatherPy

The first requirement is to create a series of scatter plots to showcase the following relationships:
* Temperature (F) vs. Latitude
* Humidity (%) vs. Latitude
* Cloudiness (%) vs. Latitude
* Wind Speed (mph) vs. Latitude

### * Temperature (F) vs. Latitude

* ![NorthLinearRegression](https://user-images.githubusercontent.com/30300016/201977058-a0bd1746-700d-4545-a5c9-cad4fc812909.JPG)
* ![SouthLinearRegression](https://user-images.githubusercontent.com/30300016/201977070-6d13a251-cdbc-4f6a-a3cd-e2f0212c25cf.JPG)

### * Humidity (%) vs. Latitude

* ![NorthHemivsHumidity](https://user-images.githubusercontent.com/30300016/201981591-457a0bb6-cbea-4451-bae9-8204e6592c2f.JPG)
* ![SouthHemivsHumidity](https://user-images.githubusercontent.com/30300016/201981677-34e95385-393e-42df-a7ff-54eedf949c22.JPG)


### * Cloudiness (%) vs. Latitude

* ![NorthHemivsClouds](https://user-images.githubusercontent.com/30300016/201981841-1fa8e2fd-e884-4e72-9341-ebfdb69ac13c.JPG)
* ![SouthHemivsClouds](https://user-images.githubusercontent.com/30300016/201981860-bd4a1f38-d228-4a14-8b3d-07166de24656.JPG)

### * Wind Speed (mph) vs. Latitude

* ![NorthHemivsWind](https://user-images.githubusercontent.com/30300016/201981985-1dcbf551-f1b2-4000-a695-c2142540fa01.JPG)
* ![SouthHemivsWind](https://user-images.githubusercontent.com/30300016/201981957-b7af0909-9a88-412d-91b9-e28883e56512.JPG)


## Results: WeatherPy

* Cities closer to the 20 latitudes skew higher temperatures on avg.
* Humidity can be found in many latitudes.
* While the highest wind speed can be found between -60 and - 40 Latitude, Latitude alone does not seem to be an indicator of high wind speed.

---------------------------------------------------------------------------------

## Part 2: VacationPy
Now, let's use your skills working with weather data to plan future vacations. Use Jupyter-gmaps and the Google Places API for this part of the assignment.

* Create a heat map that displays the humidity for every city from Part 1
* Narrow down the DataFrame to find your ideal weather condition
* Use Google Places API to find the first hotel for each city located within 5,000 meters of your coordinates
* Plot the hotels on top of the humidity heatmap, with each pin containing the Hotel Name, City, and Country


### * Create a heat map that displays the humidity for every city from Part 1
  * ![heatmap](https://user-images.githubusercontent.com/30300016/201990786-606066b8-ccfe-4652-a3d6-0dc5aff53a2a.png)


### * Narrow down the DataFrame to find your ideal weather condition
      # Filter cities by Max Temp between 70 and 80, Humidity less than 51%, and Cloudiness < 30%
      ideal_cities_df = city_data_df[(city_data_df["Max Temp"]<81) & (city_data_df["Max Temp"]>70) & (city_data_df["Humidity"]<51) & (city_data_df["Cloudiness"]<30)]
      ideal_cities_df
      
      
### * Use Google Places API to find the first hotel for each city located within 5,000 meters of your coordinates
    
  * ![Capture](https://user-images.githubusercontent.com/30300016/201991568-0f297218-2f7b-4954-aa3d-0e1b85d4bdad.JPG)


### * Plot the hotels on top of the humidity heatmap, with each pin containing the Hotel Name, City, and Country

  * ![hotalmap](https://user-images.githubusercontent.com/30300016/201992305-4db6d957-55dc-4db5-8cff-9cfb04ad4de5.png)



## Results: VacationPy
That was alot to get this list that meet this of hotals that meet this ideal weather condtion. 

      Kamenskaya Oosh
      Avenue A Realty Ltd Brokerage
      Avenue A Realty Ltd Brokerage
      Avenue A Realty Ltd Brokerage
      Hotel Laguna
      Μεταλλευτικές Εγκαταστάσεις Στρατωνίου / Stratoni Mining Facilities
      Shazam Atm
      Zags
      Silk Road Hotel Termez
      Lodja, Republica Democrática do Congo
      Budget House
      ISGN - Chibuto (Higher Institute of Business Management
      Hotel Avenida
![image](https://user-images.githubusercontent.com/30300016/201992876-8b7734d5-474c-474d-b290-f0c4066d95cd.png)



