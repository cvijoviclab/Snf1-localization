This folder contains files fore input into monolix: 

mx_005_glucose: 0.005% glucose
mx_2_glucose: 2% glucose
mx_2_glycerol: 2% glycerol



simulations were done in monolix version 2023R1

steps in monolix:

after initializing a new project and opening the respective csv file in monolix, following steps should be taken:  

1. data selection: 
	data information: select continuous
	add. covariates: select none

	assign the following columns: 
		ID -> ID
		recovery_time -> TIME
		observation -> OBSERVATION ( this is the normalized and bleach corrected intensity measured in the bleached nucleus)

2. structural model: 

insert:

DESCRIPTION:

[LONGITUDINAL]
input={ I0,A1, tau}

EQUATION:
I = I0+ A1*(1-exp(-tau*t))

OUTPUT:
output = {I}


3. initial estimates

leave inital values unchanged:
	population distribution parameters: 	population = 1 for every parameter
						std. deviation = 1 for every parameter


	Residual error parameters: 		a = 1
						b = 0.3
						c = 1


4. statistical model & tasks: 
	Tasks:	population parameters: 	burn-in phase: 5 iterations
						exploratory phase: 	auto stop criteria enabled
									max number of iterations 500
									min number of iterations 150
									stepsize exponent 0
									simulated annealing enabled
									decreasing rate( var. res. errors)  0.95
									decreasing rate( var. indiv. param.)  0.95
						smoothing phase: 	auto stop criteria enabled
									max number iterations 200
									min number of iterations 50
									stepsize exponent 0.7

		enable EBEs: 	max number of iterations: 200
				tolerance: 0.000001

		enable conditional distributions: MCMC convergence assessment: 
							interval length : 50
							disable max iterations limit
							relative interval width 0.05
							simulated parameters per individual 10

		enable plots and set towards preference


	Observation model: 
			Type, observation ID, Name and prediction are defined in the data and structural model tab
			error model: 	proportional
			distribution: normal

	Individual model: 
			Parameters set via structural model
				distribution for each parameter: lognormal
				random effects enabled
				correlation disabled

--> run the model

afterwards run the tasks:
	standard errors: 	min number of iterations: 50
				max numer of iterations: 200

	likelihood: 		monte carlo size: 10000
				degrees of freedom of t- distribution: fixed, 5
			
		

		
																	