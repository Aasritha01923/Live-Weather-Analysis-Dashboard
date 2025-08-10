# Live Weather Analysis Dash Board
Develop a Power BI Dashboard with WeatherAPI

Power BI is a fantastic tool for visualizing data and you can easily integrate live weather data into your reports too. In this File, you'll walk through the process of building a real-time weather dashboard powered by WeatherAPI, and then Add some Air Quality Index (AQI) indicators for a richer dashboard experience.


🎯 Why WeatherAPI?
WeatherAPI.com is a simple and powerful service that returns live, historical, and forecast weather data — perfect for Power BI. The data is available in JSON format, making it easy to process and transform.

🛠️ Prerequisites:

✅ A free or paid account on WeatherAPI.com

✅ Power BI Desktop installed

✅ Basic Power BI data model knowledge

🔑 Step 1: Get Your WeatherAPI Key

              1. Sign up at WeatherAPI.com, then copy your API key.
              
              2. You’ll use this key to authenticate API calls.

🌐 Step 2: Build the API URL

For current weather data, use:
                            https://api.weatherapi.com/v1/current.json?key=YOUR_API_KEY&q=CITY_NAME
                            

🧠 Step 3: Connect Power BI to WeatherAPI

            1. Open Power BI Desktop.
            
            2. Click Get Data → Web.
            
            3. Enter your WeatherAPI URL.
            
            4. Click OK.
            
🧹 Step 4: Transform the Data
Power BI will show a preview in the Power Query Editor:

            1. Expand the current record.
            
            2. Expand sub-records like condition or air_quality.
            
            3. Rename columns for clarity.
            
            4. Click Close & Apply.

📊 Step 5: Build Your Dashboard
Add:

✅ Cards for temperature, humidity, etc.

✅ Gauges for wind speed.

✅ Charts for daily variations.

🎨 Step 6: Styling & Interactivity

             1. Insert icons representing the current weather.
             
             2. Plot the map visual with city locations.
             
             3. Allow your users to select cities dynamically.

⚡ Step 7: Adding AQI Indicators with Reusable Measures
You can easily incorporate Air Quality Index (AQI) data into your report using the current.air_quality part of the WeatherAPI response.

Here’s a quick Power BI DAX pattern you can copy-paste and adapt to your needs:

🎨 Generic Template for AQI Color:(DAX)

AQI Color TEMPLATE =

VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.COLUMN_NAME]),0)

RETURN

SWITCH(

TRUE(),

AQI <= 50, "#43d946",

AQI <= 100, "#fff570",

AQI <= 150, "#ff9800",

AQI <= 200, "#d99343",

AQI <= 300, "#ff5b0f",

"#d95243"

)


💡 Simply copy this measure and replace COLUMN_NAME with the air quality column you want to check — for example:

pm2_5

co

no2

🎨 Generic Template for AQI Suggestion:(DAX)

AQI Suggestion = 

VAR AQI = SELECTEDVALUE('Current'[current.air_quality.pm10])

RETURN


SWITCH(

    TRUE(),
    
    AQI <= 50,  "Enjoy outdoor activities - the air is fresh and clean",
    
    AQI <= 100, "Air quality is acceptable; normal outdoor activity is fine",
    
    AQI <= 150, "Sensitive individuals should limit strenuous outdoor activity",
    
    AQI <= 200, "Reduce time spent outdoors; consider indoor exercise",
    
    AQI <= 300, "Avoid outdoor exertion; plan activities indoors",
    
    "Stay indoors as much as possible; use a mask if you must go out"
    
)


🎨 Generic Template for AQI Status:(DAX)

AQI Status TEMPLATE =

VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.COLUMN_NAME]),0)

RETURN

SWITCH(

TRUE(),

AQI <= 50, "Good",

AQI <= 100, "Moderate",

AQI <= 150, "Unhealthy for Sensitive",

AQI <= 200, "Unhealthy",

AQI <= 300, "Very Unhealthy",

"Hazardous"

)

✅ Again, just replace COLUMN_NAME with the pollutant of interest.


Finally, Your Dashboard will look like:   https://github.com/Aasritha01923/Live-Weather-Analysis-Dashboard/blob/main/Snapshot%20of%20Dashboard.jpg


💡 Handy hint:

Keep these generic DAX measures as templates so when you want to add AQI visualizations for new pollutants like so2, no2, or o3, you only need to copy-paste and tweak one column name.

    




🎉 Conclusion:

Integrating WeatherAPI with Power BI enables the creation of a dynamic weather dashboard featuring real-time data and custom AQI visualizations. Leveraging reusable DAX measures ensures the solution remains scalable, maintainable, and adaptable to evolving requirements.

Thanks for stopping by - hope this dashboard brightens your day like good weather does....! Made with love for data and a little obsession with the weather.

If this dashboard made you smile, my job here is done — and if you need help, I’m just a message away.....!

Happy dashboarding!🎨



