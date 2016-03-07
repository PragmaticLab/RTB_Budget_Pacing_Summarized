Real Time Bid Optimization with Smooth Budget Delivery in Online Advertising by Kuang-Chih Lee, Ali Jalali, Ali Dasdan. ADKDD 2013.

** Turn
- Lee et al. explains a solution to smooth budget delivery
- The paper comes up with a method to divide budget B into (b1..bt) and an ad selection algorithm to maximize actions/events from ads
- Budget allocation solution:
	- creates a spend plan for each campaign
	- divide day into t slots; length of slot chosen to minimize variance of impression price for each campaign
	- characterize the quality of impressions (e.g. CTR) for each slot as p_x
	- bx in b1..bt is equal to p_x / sum(p_x)
	- Tries to spend more on time slots that gives higher actions (e.g. CTR)
	- Pacing rate for each slot is calculated based on bx (how much we want to spend) and Rx (total traffic seen by DSP)
- Ad selection algorithm:
	- Given budget, win rate and bid price, we know how many impressions we want, say X
	- From historical data, we construct a gaussian model of CTR or AR
		- From this guassian, we know how many impressions with high CTR / AR are going to come
		- We pick a threshold Tau, so that we can buy approx. X impressions
	- When ad comes into system, CTR / AR probability is calculated from statistical model
	- We bid on ads that have probability greater than Tau
- This paper also address dynamc CPM campaigns, by utilizing adaptive pacing rates
- The main flaw of the ad selection algorithm is that it doesn't take account of competition within set{Ad_1..Ad_m}
