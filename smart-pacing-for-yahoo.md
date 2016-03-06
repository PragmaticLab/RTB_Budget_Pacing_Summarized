Smart Pacing for Effective Online Ad Campaign Optimization by Jian Xu et al. KDD 2015.

** Yahoo
- Xu et al. summaries 2 main approaches to pacing:
	1. bid modification (Mehta et al.)
	2. probablistic throttling (Agarwal et al.)
- Uses probablistic throttling for 3 reasons:
	1. directly influences budget spend, until bid modification
	2. SSP reserve prices make bid modification hard
	3. decouples pacing from bid calculation
- Formulates pacing as a primal dual problem:
	find r_i to minimize Performance (P)
	s.t. C = B, omega(C,B) <= e
	B is budget for time slot, C is actual spend, e is allocated slack
	uses RMSE as omega in this paper
- Find offline p_i = Pr(action | Req_i, Ad), the action rate
- Group similarly responding ad requests into the same group, called a layer, where members of each layer have a group throttle rate
- Each layer has the following: 1. pacing rate 2. priority
	* priority is based on how high p_i is
- Layers that correspond with high P_i / action rate will enjoy a low throttle rate, and vise versa
- Adjust pacing rate of each layer periodically based on the residuals from time [0, t), calculated by sum(B_t - C_t)
^ a form of adaptive controller (I think it's a feedforward one)
- Hints that a moderate number of layers performs best, because:
	1. statistics for each layer becomes insignficant when # layers is high
	2. execess number of layers strain system bandwidth
- Categorizes the proposed method as an adaptive controller, and the method introduced in Agarwal et al. a conventional feedback controller.
- Shows a lower eCPC compared to Agarwal et al. because the Linkedin one has fluctuations around the curves
