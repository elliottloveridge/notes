# Monitoring

- ML deployment is an iterative process
	- Uses performance analysis

### Dashboards
- Decide what key metrics to monitor
	- What could go wrong
- Server load
- Diffraction of non-null outputs
- Fraction of missing input values

- Common practice to set an alarm at a given threshold for metrics you are tracking
	- Adapt these over time

#### Metrics
##### Software
- Memory
- Compute
- Latency
- Throughput
- Server load

##### Input
- Number of missing values
- Average input volume (speech recognition)

##### Output
- Number of times a user redoes a search
- Number of null returns
- CTR (click-though rate)

## Model Maintenance
- Manual retraining
	- Most common vs automatic retraining