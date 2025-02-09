**🔥 BlazeMap – Interactive Fire Spread Simulation 🔥**

BlazeMap is an interactive web application designed to simulate and predict the spread of fire in real time. Leveraging real-world weather and topographic data from multiple APIs, BlazeMap allows users to visualize how a fire might progress across a given landscape. Simply click on the map to set the fire's starting point, and watch the simulation play out with multiple scenario overlays.

## Features

- **Interactive Fire Simulation:**  
  Click on the map to set the fire's starting point and watch the fire spread in real time.

- **Scenario Visualization:**  
  Three overlays (green for best-case, yellow for neutral, and orange for worst-case) show different potential fire spread scenarios based on environmental conditions.

- **Real-Time Environmental Data Integration:**  
  BlazeMap fetches current weather (temperature, wind speed/direction, humidity, precipitation) and terrain data (slope, land cover) from various APIs and uses these parameters to compute the fire spread rate.

- **Dynamic Environmental Reasoning:**  
  The sidebar displays a detailed explanation of the environmental data used for the simulation. For example:  
  `Temp 22°C, Wind 2.61 m/s (Dir: 241°), Humidity 28%, Precip 0 mm, Slope 0.00%, Fuel: sparse, Land Cover: commercial.`

- **Nearby Resources:**  
  The map shows nearby firefighting resources such as fire stations and hydrants.

- **User Interface Controls:**  
  A time slider allows users to scrub through the simulation timeline, and a “Locate Me” button recenters the map on the user's location.

- **Responsive Design:**  
  BlazeMap is built to work across desktop and mobile devices.

## Mathematical Model

BlazeMap uses a simplified mathematical model based on **Rothermel’s equations**—a set of models widely employed by fire and forest management systems (including those developed by the US Forest Service Research and Development). The key aspects include:

- **Effective Spread Rate:**  
  The model starts with a base spread rate (in meters per time step) and adjusts it by applying multiplicative factors derived from weather and terrain parameters (e.g., temperature, wind speed and direction, humidity, precipitation, slope, and land cover). These adjustments are based on exponential modifiers that roughly mirror the behavior described by Rothermel’s model.

- **Elliptical Fire Front:**  
  Fire spread is modeled as an ellipse. Wind and slope factors elongate the ellipse in a specific direction. A recursive algorithm samples boundary points along this ellipse to draw the fire front on the map.

- **Scenario Multipliers:**  
  The simulation applies different multipliers for best-case, neutral, and worst-case scenarios to reflect the uncertainty and variability in fire behavior under different conditions.

This approach provides a balance between computational simplicity and visual realism, enabling real-time simulation without the full complexity of advanced fire behavior models.

 **Leaflet:** For interactive mapping and visualization.
- **JavaScript (ES6+):** Utilizes modern features such as arrow functions, Promises, and template literals.
- **HTML & CSS:** For the structure and styling of the web application.
- **Fetch API:** Native web API for asynchronous HTTP requests.
- **WeatherAPI:** Provides current weather data over HTTPS.
- **OpenElevation API:** Supplies elevation data for terrain analysis (accessed via a CORS proxy).
- **Overpass API:** Retrieves land cover and terrain features.
- **OpenCage Data:** Used for reverse geocoding to obtain addresses from coordinates.
- **CORS Proxy (Thingproxy):** Used to bypass cross-origin restrictions for APIs that do not support CORS.
- **Native DOM and Event APIs:** For interacting with and updating the user interface.

## Usage

1. **Set the Fire Starting Point:**  
   Click on the map to set the fire’s starting point and begin the simulation.

2. **View Fire Spread Scenarios:**  
   The simulation displays three colored overlays that show best-case (green), neutral (yellow), and worst-case (orange) fire spread scenarios.

3. **Time Control:**  
   Use the time slider to scrub through the simulation timeline and observe how the fire front evolves.

4. **Environmental Data Display:**  
   The sidebar shows real-time environmental data and a detailed “reasoning” explanation based on the current weather and terrain.

5. **Locate Me:**  
   Click the “Locate Me” button to recenter the map on your current location. This feature is especially helpful in real life because it allows users (including first responders and residents) to quickly gauge their proximity to a potential fire, aiding in timely evacuation or response decisions.

6. **Nearby Resources:**  
   The map marks nearby firefighting resources, such as fire stations and hydrants, to enhance situational awareness.

## How It Works

BlazeMap calculates the effective fire spread rate using a simplified model based on Rothermel’s equations—widely used by fire management systems. This model integrates real-world environmental data (weather and terrain) to adjust a base spread rate through multiplicative factors. Although the underlying simulation uses real-world units, the drawn fire front is scaled by a visual factor (the `displayScaleFactor`) to ensure it appears prominently on the map.

