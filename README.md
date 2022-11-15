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
    ```
    baseURL = "https://maps.googleapis.com/maps/api/place/nearbysearch/json"

#search for the hotels

target_radius = 5000
target_type = "hotel"


# dictionary of parameters to update at each iteration 
parameters = {
    "type": target_type,
    "radius" :target_radius,
    "key": g_key
}

# use iterrows() to iterate through the rows in the DF
for index, row in hotel_df.iterrows():
    #grab the latitudes and longitudes from the columns in the DF
    latitude = row['Lat']
    longitude = row['Lng']
    
    # change location each iteration while leaving original params in place
    parameters["location"] = f"{latitude},{longitude}"
    
    
    # Use the search term: "Hotel" and our lat/lng
    base_url = "https://maps.googleapis.com/maps/api/place/nearbysearch/json"

    # make request and print url
    hotel_response = requests.get(base_url, params=parameters)
  

    # convert to json
    hotel_json = hotel_response.json()
    #pprint(hotel_json) # to check the indices of the hotel name 
    
 
    try:
        hotel_df.loc[index, "Hotel Name"] = hotel_json["results"][1]["name"]
        print(f"First hotel in {target_radius} meters is {hotel_json['results'][1]['name']}")
    except (KeyError, IndexError):
        print("Missing field/result... skipping.")
    
    print("--------------------------------------")
    
    ```
    
    
 ![Capture](https://user-images.githubusercontent.com/30300016/201991568-0f297218-2f7b-4954-aa3d-0e1b85d4bdad.JPG)



## Results: VacationPy
