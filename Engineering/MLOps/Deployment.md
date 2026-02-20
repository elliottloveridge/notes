# Deployment

## Challenges

### ML Challenges
- Concept drift and Data drift
	- What if your data distribution changes after your model has been deployed?
	- *Concept drift is a change in the desired mapping from $x \rightarrow y$*
		- Predicting house prices
			- Price of a given house changes due to economic changes
	- *Data drift is a change in your data distribution $x$*
		- People start building a different style of house

#### Common Data
- Training
	- Purchased data - historical user data with transcripts
- Testing
	- Data from a few months ago
- Live
	- Data can change gradually or due to a sudden shock
		- E.g. credit card fraud models at the start of Covid pandemic caused sudden changes to spending patterns

### Software
- Prediction service takes queries $x$ and outputs predictions $y$

#### Potential Issues
- Realtime predictions or batch predictions?
	- How quickly do you need the answer
- Where does your prediction service run?
	- Cloud vs Edge/Browser
		- Edge systems can work locally
- Compute resources
	- CPU/GPU/memory
		- What can you afford?
- Latency/throughput (QPS - queries per second)
	- In software engineering, often want an answer within 500ms
- Logging
	- Storing meta data and data for retraining
- Security and privacy