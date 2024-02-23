# Observer Pattern
- The observer pattern is one of the most commonly used design patterns
	- Keeps objects in the know when something they *care about* happens
- Defines a **one-to-many dependency** between objects so that when one object changes state, all of its dependent are notified and updated automatically
- It is related to the Publish-Subscribe pattern
## Subject and Observer Objects
- The subject object manages some important data
- When data in the Subject changes, the observers are interested
	- Automatic update/notification
- The observers have subscribed to (registered with) the Subject to receive updates when the Subject's data changes
- Observers can ask to be added and removed as observers
	- *Think of it like subscribing to a mailing list*
		- You get new mail when subscribed and can also unsubscribe at any point
### Example Structure
![](Observer%20Pattern.png)
## Example: Weather-O-Rama
- You have been provided with a WeatherData object that gets the latest weather conditions from the Weather Station (see below)
![](Weather-O-Rama.png)
- You will need to adapt the WeatherData object so that it knows know how to update the display
- You will also need to implement three different display elements:
	- Current conditions (shows the three device readings)
	- Weather statistics
	- Forecast
### WeatherData Object
- The WeatherData object contains the following methods:
	- `get_temperature`
	- `get_humidity`
	- `get_pressure`
	- `measurements_changed`
		- Whenever WeatherData gets updated weather values, this method gets called
- We know that the WeatherData class has getter methods for the three measurement values
- Therefore, *the task is to alter `measurements_changed` so that it updates the three displays*
### Goal
- Whilst we have the above goal we should remember the one constant in software development - change
	- We expect more than three displays in the future so why not build in expandability
		- Allow other users to add (or remove) as many display elements as they want to the application
![](WeatherData%20Classes.png)
