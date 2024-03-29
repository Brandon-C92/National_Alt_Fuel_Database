# Exploring A National Database of Available Alternative Fuel Stations and Locations of the United States of America
# SPC Brandon Cooke, USARMY
A interactive map with current Alternative fuel stations with locations on an interacive Folium map that can be localized or drag-and-dropped into a web browser along with data analytics of the types of fuel stations throughout the US.

![image](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/04a3cfc5-3734-41b1-85b0-1566e030a57e)

About the Open Energy Data Initiative (OEDI)
OEDI is a centralized repository of high-value energy research datasets aggregated from the U.S. Department of Energy’s Programs, Offices, and National Laboratories. Built to enable data discoverability, OEDI facilitates access to a broad network of findings, including the data available in technology-specific catalogs like the Geothermal Data Repository and Marine Hydrokinetic Data Repository.

OEDI is powered by OpenEI, an energy information portal sponsored by the U.S. Department of Energy and developed by the National Renewable Energy Laboratory in support of the Open Government Initiative to make energy data transparent, participatory, and collaborative.
# Data Description

Alternative fueling stations are located throughout the United States and Canada, and their availability continues to grow. The Alternative Fuels Data Center (AFDC) maintains a website where you can find alternative fueling stations near you or on a route, obtain counts of alternative fueling stations by state, view maps, and more.

The most recent dataset available for download here provides a "snapshot" of the alternative fueling station information for compressed natural gas (CNG), ethanol (E85), propane/liquefied petroleum gas (LPG), biodiesel (B20 and above), electric vehicle charging, hydrogen, and liquefied natural gas (LNG), as of July 29, 2021.

![image](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/bdf71031-6720-4408-a080-4ef091c9cbc0)


# Capstone 1 Goals
- Visualize interacive map displaying Fueling Locations all around the US.
- Find out what the most common types of alternative fuels available at these stations are.
- Find out if certain types of alternative fuels more prevalent in specific cities or areas.
- and expand my general knowlege of Python

# Data Visualization
I first wanted to know how many stations were created, and when they started being produced.
- But to do that I had to transfrom the data into a readable format:

 <img width="1092" alt="Screenshot 2024-03-27 at 5 32 03 PM" src="https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/423b6646-1bde-4a5b-9fd7-e7357d130783">
 
This dataset was completley unorganized, as you can tell the State column was filled with street addresses, the Zip column was directions to the station, and the Station Phone number was actually the state abbreviation.

Once I did some Data Analysis and data transformation:

<img width="1092" alt="Screenshot 2024-03-27 at 5 14 58 PM" src="https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/ae413955-542c-4c44-a68a-1107173a2f5f">

I was able to grab certain values and asssign them to the correct columns and also added a geopoint, to allow for easier plotting on maps in the future. I turned the csv file from a Pandas Dataframe into a GeoPandas Dataframe.

From There:

I created a temporal line graph to showcase the creation of alternative fuel stations thoughout the years.

![Time_analysis_of_stations](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/dae167c2-f1bc-4bf2-aa91-d1fda60b24f6)

Fig 1. The number of unique staion openings in the dataset, over time.

Next, I created additional graphs to fine tune when those stations were created by month and day of week.

![New_stations_open_by_month](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/8ae1121d-e67d-4dfa-87c7-75afd934f52b)

Fig 2. The number of unique staion openings in the dataset, over time by month.

At this point I was getting down to the nitty -gritty and displaying what day of the week the stations were opened.
![Stations_opened_by_day_week](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/f96dcdc2-8b82-415c-a922-f91e822ba43d)

Fig 3. The number of unique staion openings in the dataset, over time by day of week.

After that I wanted to look at the aggregate of differnt availible fuels in the dataset.

![Pie_chart_of_fuel](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/a84be3ad-2761-4576-a9da-91f79acb24c7)

Fig 3. The number of unique Fuel Types in the dataset.

For the next part, I wanted to find out what states had alternate fuel stations, if any at all, and which state had the most.

![#_alt+stations_by_state_horz_bar](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/087abc72-920c-45f6-8cef-d32db2df177b)

Fig 4. A graph of states that have the most Alt Fuel Stations in the dataset.

Again I looked at what Fuel Types were most prevalent , but also corrobrateing them with the year they opened.

![Heatmap_Fuel_by_Year](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/d42a763f-32d0-45bd-8f30-bb03f1e5a17f)

Fig 5. A heatmap of states that have the most Alt Fuel Stations in the dataset, along with the year they appeared.

Once I figured out with different methods which fuel type was the most prevalent, and where they were, I wanted to narrow it down to a city as to which one had the most Alt Fuel Stations. This bar graph simply displays that Los Angeles is the city with the most stations.

![Top_10_citys_most](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/be882ad2-34bb-47aa-808d-b5f754e2cac2)

Fig 6. A bar graph with the total ammount of stations by city.

Since we have all of our statiscical analysis done, I went and started to configure the data and figure out what the distances were between stations. I then too another route with how to measure the data with the geodesic python library to see if I could get a different result. Figure 7 calculates the pairwise distances between each pair of fuel stations based on their longitude and latitude coordinates and then visualizes the distribution of these distances using a histogram. In the second graph the distances are calculated based on the longitude and latitude coordinates stored into a diffent Dataframe as well, but it's processed in a different manner.

![Distacnes_bet_stations](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/9aaae136-89a3-46e9-8307-dd1bd5c3a0bc)

![SMALL DISTANCE](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/853a0167-54f6-40f0-858b-f544504dfea9)

Fig 7 and 8. A histogram bar chart with values that denote the distances to fuel stations based on a sample of data (x1000 becasue of data size vs computational power).

From there, after getting all that statistical data, it was time to move on to the MVP. I created a visual, interactive Folium map that you can view on a webpage. It's similar to using Google Maps or other online mapping services. However, with Folium, you can create your own customized maps with different features and layers.
I took in the refined dataframe and published it with folium to show fuel stations all around the United States.
As stated before the dataset was so large (56800 rows of data), that local analysis on this Mac Book Pro wasn’t capable processing this dataset completely.

This folium map is the point map displaying a sample of fuel stations across the US.

![CPT2403291101-644x4331-ezgif com-optimize](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/27c7ab00-acab-49b2-a1d6-e433e10dc73c)

Fig 9. A interactive map displaying a sample of point data containing points, station info, fuel type, and address. (x1000 becasue of data size vs computational power).

This folium map is a Heatmnap that shows the denity of stations in an area.

![CPT2403291122-716x402-ezgif com-optimize](https://github.com/Brandon-C92/National_Alt_Fuel_Database/assets/161045627/43520c16-5551-404d-89ad-a0e530088b26)


Fig 10. A interactive Heatmap displaying a sample of point data showing the density of fuel stations pertaiing to loactions on the map. (x1000 becasue of data size vs computational power).


# Future Considerations:

I want to, based on trending analysis and proper data collection gather relevant data including factors such as population density, transportation infrastructure, regulatory policies, historical fuel consumption, station adoption rates, etc. I would want to perform a predictive model for forecasting future demands for alternative fuels or the possible prediction of the likelihood of station adoption.
