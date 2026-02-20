# ML Lifecycle

- The ML lifecycle comprises the work required to take an ML model from idea to production

## Parts of the Lifecycle

### Scoping
- Define the project

### Data
- Define data and establish baseline
- Labelling and organising the data

### Modeling
- Select and train a model
- Perform error analysis
	- This is an iterative process so you may go back to the model training, data, or scoping steps

### Deployment
- Deploy in production
- Monitor and maintain system
	- Often again requires going back to data or model training steps

### Example
#### Speech Recognition

- **Scoping**
	- Decide you want to work on a speech recognition problem
	- Define key metrics
		- Accuracy, latency, throughput
			- Throughput is how many queries per second you can handle
	- Estimate resources and timeline
- **Data**
	- Is the data labeled consistently?
		- "Um... today's weather" or just "Today's weather"
	- How much silence before and after each clip?
	- How do you perform volume normalisation?
		- Sometimes within the same audio clip
- **Modeling**
	- *Code* (algorithm/model)
		- Hyperparameters
	- *Data*
		- In academia, the data is often fixed (model/hyperparameters are not)
		- For product teams, model is often fixed (focusing on optimising the data/hyperparameters)
	- Error analysis
- **Deployment**
	- *Production Deployment*
		- Mobile phone (edge device)
			- An edge device connects a local system to a WAN (the internet)
			- This mobile phone has local software and a microphone
				- Uses a VAD (voice activity detection) module
		- Send the audio clip via an API to a prediction server in the cloud
			- Returns the transcript and search results (if you are doing voice search)
				- This is then displayed using Frontend code on the mobile phone
	- *Monitor and maintain system*
		- Say a younger audience started to use this software
			- Model would not perform as well with different voices
				- Concept/data drift

## Problems
- Problems with releasing an ML algorithm
	- Concept/Data drift
		- Your 'test' dataset changes over time for any given reason
	- A production ML project is not just the ML model
		- ~5-10% of the total work is the proof of concept model
		- You also have;
			- Data Collection
			- Data Verification
			- Feature Extraction
			- Monitoring
			- Others...