# Weather-API-Data-Visualization

🌦️ PowerBI-WeatherAPI-Dashboard
Live Weather & AQI Dashboard in Power BI using WeatherAPI
This project integrates WeatherAPI.com with Power BI to create an interactive dashboard that displays live weather data, AQI levels, and air quality recommendations using reusable DAX measures.

📌 Features
🌍 Real-time weather data (temperature, humidity, wind speed, etc.)

📊 AQI visualization with dynamic colors, suggestions, and status indicators

🗺️ City selection and map plotting

🔄 Scalable DAX templates for multiple pollutants (PM2.5, CO, NO2, SO2, O3)

🛠️ Prerequisites
✅ A free or paid account on WeatherAPI.com

✅ Power BI Desktop installed

✅ Basic knowledge of Power BI data modeling

🔑 Step 1: Get Your WeatherAPI Key
Sign up at WeatherAPI.com

Copy your API key — used to authenticate requests

🌐 Step 2: Build the API URL
Example for current weather data:

bash
Copy
Edit
https://api.weatherapi.com/v1/current.json?key=YOUR_API_KEY&q=CITY_NAME
Replace:

YOUR_API_KEY → Your API key

CITY_NAME → Target city name

🧠 Step 3: Connect Power BI to WeatherAPI
Open Power BI Desktop

Go to Get Data → Web

Enter your API URL

Click OK

🧹 Step 4: Transform the Data
Expand the current record in Power Query

Expand nested fields like condition and air_quality

Rename columns for clarity

Click Close & Apply

📊 Step 5: Build Your Dashboard
Add:

✅ Cards for temperature, humidity, etc.

✅ Gauges for wind speed

✅ Line charts for daily variations

✅ Filters/Slicers for city selection

🎨 Step 6: Styling & Interactivity
Add weather icons based on conditions

Plot city coordinates on a map

Use dynamic AQI colors and suggestions

⚡ Step 7: Adding AQI Indicators (DAX Templates)
You can visualize air quality from current.air_quality using these reusable DAX templates.
Just replace COLUMN_NAME with pollutants like pm2_5, co, no2, etc.

🎨 AQI Color Template
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

🎨 AQI Suggestion Template
AQI Suggestion TEMPLATE =
VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.COLUMN_NAME]),0)
RETURN
SWITCH(
TRUE(),
AQI <= 50, "Air is clean and healthy",
AQI <= 100, "Acceptable air quality, stay active",
AQI <= 150, "Sensitive groups should reduce outdoor time",
AQI <= 200, "Limit prolonged outdoor exertion",
AQI <= 300, "Avoid outdoor activity if possible",
"Stay indoors, wear a mask if outside"
)

🎨 AQI Status Template
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


💡 Quick Tip
Keep these templates in your report

Replace COLUMN_NAME for new pollutants

Reuse them for multiple AQI visuals easily

🎉 Conclusion
By combining WeatherAPI and Power BI, you can build a dynamic, real-time weather dashboard enriched with AQI insights and custom DAX-driven visuals.
This approach is scalable, maintainable, and interactive for end-users.

🏷️ Tags
Power BI WeatherAPI Dashboard Air Quality DAX Data Visualization
