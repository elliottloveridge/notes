# Deployment Patterns

## Common Examples
- Common deployment cases
	- New product/capability
		- Start with a small amount of traffic and gradually ramp up
	- Automate/assist with manual task
		- Shadow mode deployment
	- Replace previous ML system
		- Gradual ramp up with monitoring
		- Rollback
			- If the algorithm is not working then revert back to the previous method

## Types of Deployment Patterns
### Shadow Mode Deployment
- ML system shadows the human and runs in parallel
	- ML systems output not used for any decisions during this phase
		- Allows you to gather comparison data
			- Sampling allows you to decide whether to let ML system make decisions

### Canary Deployment
- This step comes after shadow mode when you have more confidence in the output of your model
- Roll out to a small fraction (5%) of cases
- Monitor system and ramp up traffic gradually

### Blue Green Deployment
- Used when replacing ML systems
- Blue is the old version (have this make decisions)
- Green is the new version
- Have a sudden switch between Blue/Green
	- Easy way to enable rollback if anything goes back

## Degrees of Automation
- With the above patterns you can think of systems existing on a scale between human only and full automation
	- Human only $\rightarrow$ Shadow mode $\rightarrow$ AI assistance $\rightarrow$ Partial automation $\rightarrow$ Full automation
		- AI assistance and Partial automation is known as *human in the loop* automation