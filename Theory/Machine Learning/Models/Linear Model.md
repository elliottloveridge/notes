# Linear Model

* A linear probability model (LPM) is identical to a [[Theory/Machine Learning/Regression|regression]] model expect for one key difference
	* Whereas the dependent ($y$) variable for a regression model is continuous, the dependent variable for an LPM is binary
* If we have one independent variable then our LPM is defined as;
	* $Y = B_0 + B_1X + u$
	* Where;
		* $Y$ is a binary response variable (dependent variable)
		* $X$ is the (single) independent variable
		* $u$ is the error term

## LPM Example
* Suppose $Y=1$ if a person is employed and 0 if they are not and $X$ is their years of experience
	* The LPM is defined as;
		* $Y = 0.4 + 0.07X$
* Zero years of experience would give a value of $y = 0.4$, meaning they have a 40% chance of employed
* For every year of experience, the likelihood that they are employed would go up by 7%

## Issues of LPMs
* From the above equation it is possible to have $Y > 1$ which is meaningless
* It assumes a linear relationship between the dependent and independent variable
	* Likely not true