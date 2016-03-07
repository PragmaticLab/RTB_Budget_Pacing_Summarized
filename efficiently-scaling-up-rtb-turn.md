From 0.5 Million to 2.5 Million: Efficiently Scaling up Real-Time Bidding by Jianqian Shen et al. ICDM 2015.

- Shen et al. proposes a hierarchical allocation to distribute bid requests and a logistic sigmoid to further filter bid requests
- each request can be hierarchically allocated based on features (e.g. device, publisher)
	- example hierarchy:
		1. publisher 1
			2. site 1
				3. device 1
				3. device 2
			2. site 2
				3. device 1
				3. device 2
		1. publisher 2
			2. site 1
				3. device 1
				3. device 2
			2. site 2
				3. device 1
				3. device 2
- each leaf node wants R_t requests, so a hierarchical filtering system is created, where each node has selection rate theta_i
- theta_i is a threshold for each request's utilization score, which is an estimation of how likely this request is useful
- Shen et al. proposes a logistic sigmoid to compute the utilization score, for 4 reasons:
	1. higher utilization gets higher score
	2. the "S" shape of sigmoid ensures score is in a limited range
	3. normalized
	4. relatively easy to balance exploration vs exploitation
