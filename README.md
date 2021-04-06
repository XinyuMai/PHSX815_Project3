# PHSX815_Project3: Orbit Stability Simulation of Planetary systems

## Project Description
Similar to project 1 and 2, we will simulate an idealized planetary system with the Sun at the center, corresponding to orbital parameters samples from Beta distribution. We implement the Hill stability Criterion \cite{Chambers:1996} \cite{Gladman:1993} to calculate fractional orbital separation for examination of stability of two bodies system. The difference in this project is that the model parameter we are interested in will be estimated using simulated data from the experiment. 


In the last project, We closely examime two hypotheses:
* Hypothesis H0: probability of stable systems assuming model parameters alpha_{0} = 0.5, beta_{0}=0.5
* Hypothesis H1: probability of stable systems assuming model parameters alpha_{1} = 3.0, beta_{1}= 3.0

Note: alpha and beta are two shape parameters of beta distribution.

## This repository contains several types of programs:
* python/ `Random.py`, `OrbitSim.py`, `MinimizeSim.py`, `MySort.py`
* `data/` contains output data
* `plots/` contains output plots

## Code Usage 

In this project, we can implicitly specify non-default values for the probability of stable outcome (like a coin toss experiment) by specifying two model parameters alpha_{0} and beta_{0}. 

Begin with `OrbitSim.py`, it will call from random class, samples from beta distribution by \\alpha and \\beta to calculate \\delta_critical. Then numeriacally calculate the probability of being stable and pass to bernoulli probabaility distribution. A result of stable or unstable outcome is simulated by specifying number of systems and number of experiments you wish to evaluate. This program will generate simulated stable/untable systems indicating as '0' ot '1' and pipe it to a text file. 

	*  Options can be called from the command line with the -h 
	*  eg: `python3.8 python/OrbitSim.py -a 0.5 -b 0.5 -Nsystem 100 -Nexp 10000 -output H0.txt `
	*  -a alpha value
	*  -b beta value
	*  -output [filename]  name of file for hypothesis

Next step, we will use the text file data (fixed), analyze the simulated data to find the value of \\alpha and \\beta that maximizes L(alpha, beta|X) (the data is ”fixed” in an experiment).

* `python3.8 python/SimAnalysis.py -a0 0.5 -b0 0.5 -a1 3.0 -b1 3.0 -input0 H0.txt -input1 H1.txt`


