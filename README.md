# Will-My-Flight-Be-Delayed-

This repo contains the work I did for my second individual project at Metis. In this project, I built and evaluated classification models towards predicting flight delays from flight schedule (on-time performance) and weather features at origin and destination airports and which features contributed to these delays. The [FAA definition](https://www.bts.dot.gov/explore-topics-and-geography/topics/airline-time-performance-and-causes-flight-delays) of a flight delay is associated with arrival delay -- any flight that arrives at the gate at least 15 minutes past its scheduled arrival time is delayed. I focused on flights departing from the three primary airport serving the New York City metropolitan area (EWR, JFK, and LGA).

I collected [Airline On-Time Performance Data](https://www.transtats.bts.gov/Tables.asp?DB_ID=120&DB_Name=Airline%20On-Time%20Performance%20Data&DB_Short_Name=On-Time) for all flights from 2016 through 2018 Q1, and daily weather data for 2016 through 2018 Q1 from specified weather stations from the [NOAA Global Historical Climate Network Daily (GHCND)](https://www.ncdc.noaa.gov/ghcn-daily-description). I also collected itinerary-level data from passengers for 2016 through 2018 Q1 from the [Origin and Destination Survey](https://www.transtats.bts.gov/Tables.asp?DB_ID=125&DB_Name=Airline%20Origin%20and%20Destination%20Survey%20%28DB1B%29&DB_Short_Name=Origin%20and%20Destination%20Survey) and used the [Airports API](https://github.com/ryanburnette/airports-api) to get latitude/longitude for the airports in my final dataset.

The files contained in this repo (and more specifically, the basic workflow for their use) is as follows:
1. Use Selenium to download and unzip .zip files of flight schedule and itinerary data (in .csv format) in the following notebooks:  
* **AOTP_Scrape.ipynb**, for monthly Airline On-Time Performance data
* **DB1B_Scrape.ipynb**, for monthly Origin and Destination Survey data

2. Read in and prepare downloaded flight schedule and itinerary data in the following notebooks:
* **AOTP_Read.ipynb**, for the Airline On-Time Performance data
* **DB1BCoupon_Read.ipynb**, for the Origin and Destination Survey data

3. Use data prepared in **AOTP_Read.ipynb** to gather latitude/longitude for each airport under consideration using the notebook **LatLongRead.ipynb**.

4. Use data prepared in **AOTP_Read.ipynb** and **DB1B_Read.ipynb** to perform feature engineering to estimate the ratios of business passengers on flight routes under consideration using the notebook **DB1BCoupon_FeatureEng.ipynb**.

5. Read in and prepare weather data (manually collected), and then merge with flight schedule data prepared in **AOTP_Read.ipynb** using the notebook **AddWXData.ipynb**.

6. Put together and prepare all data for modeling using **FinalDataCompiltaion.ipynb**.

7. Build, evaluate and select classification models using the notebook **All_Data_All_Models.ipynb**. 
