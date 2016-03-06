Budget Pacing for Targeted Online Advertisements at LinkedIn by Deepak Agarwal et al. KDD 2014.

**Linkedin
- Agarwal et al. suggests that DSPs can pace based on probablistic throttling (throw out a portion of auctions)
- Argues that modifying bids as suggested in Mehta et al. is not a good mechanism for pacing, because of reserve prices in SSPs
- Forecasts eligible traffic for a campaign offline, f_i,t denotes the cumulative # impressions at time t
- Computes a_i,t based on f_i,t and f_i,T, where a_i,t is the budget to be spent before time t
- The traffic to a campaign is controlled via p_i,t / Pass Through Rate (0 is to pass on everything, 1 is to take on every eligible auction)
- Every 1 minute, adjust p_i,t based on a naive update rule:
	* if spend_i,t <= a_i,t, p_i,t = p_i,t-1 * (1 + 0.1)
	* if spend_i,t >  a_i,t, p_i,t = p_i,t-1 * (1 - 0.1)
- Defends an adjust rate of 10% for 2 reasons:
	1. Too hard to come up with an accurate value / noisy
	2. Budget spend curve is not smooth
- Slow start, p_i,0 starts low (~ 10% ) to prevent overspending early on
- Fast finish, exhaust budget within 22 hours, because forecasted impressions not accurate
