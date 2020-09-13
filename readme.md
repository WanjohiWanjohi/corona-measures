
## Problem Statement
In late 2019 , the spread of the corona virus was limited to the Asias and only became a matter of gloabla precedence in February 2020. The spread of the disease has been managed by the imposition of different measures by different governments towards maintaining social distancing. In the implementing of these measures, it is important to find out which ones bear the most result in slowing down the infection rate and which measures could be done away with a change point analysis to quantify the impact of policy interventions to slow the spread of COVID-19


## Objective

For the week of 10th August , it is the goal of this project to find the possible number of infected persons given the different policies implemented by the Senegalese government.

The change points considered prior are :

    - 10/03/2020 : All learning and religious instituions shut down
    - 16/03/2020: Travel ban declared both locally and externally
    - 31/03/2020: Declaration of a national state of emergency


## Tools and Methods used

1.  The SIR model uses the Susceptible-Infected-Recovered rate where the susceptible population reduces as the number of those infected increase ( an inverse relationship). 
There are four parameters to be estimated in the SIR model from data: 
    - transmission rate β
    - diagnosis rate ρ 
    - the initial population size I0 when time (t) = 0 (t=0)
    - variance q=1/τ for the noise distribution in the data.

    More information about the SIR model can be found in this paper by John Dehning et all (2020) here: https://science.sciencemag.org/content/sci/369       /6500/eabb9789.full.pdf

2. PyMC3 - a standard Bayseian modelling package in Python. More information about the PyMC3 modelcan be found here : https://docs.pymc.io/notebooks/api_quickstart.html

3. Markov Chain Monte Carlo Sampling : PyMC3 samples in multiple chains, or independent processes.In this case we use it as a simulation technique that can be used to find the posterior distribution and to sample from it. Thus, it is used to fit a model and to draw samples from the joint posterior distribution of the model parameters.

3. Bayesian Modelling & Inference: Bayesian models are founded on the Bayes theorem 
    (![Image of Bayes Theorem](https://wikimedia.org/api/rest_v1/media/math/render/svg/87c061fe1c7430a5201eef3fa50f9d00eac78810)  
    
    In Bayesian inference, the event B is fixed in the discussion, and we wish to consider the impact of its having been observed on our belief in various possible events A. In such a situation the denominator of the last expression, the probability of the given evidence B, is fixed; what we want to vary is A. Bayes's theorem then shows that the posterior probabilities are proportional to the numerator. 

    In this case the fixed variable (B) is the implemented policy.
 


## Limitations and Challenges

According to Weston C. Rada  et all (https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7104073/), the limitations of the SIR model are  :

A linkage between the transmission rate β and the diagnosis rate ρ .  The linkage between two or more parameters implies the following: 
        - the best-fit parameter values are effectively not unique 
        - there is a continuum of parameter values that cause the model to fit the data approximately equally as well. 
        This phenomenon is often referred to as **nonidentifiability** in the modeling literature.
        The linkage between β and ρ reflects the dependency of the transmission rate and the case-infection ratio, and hence the scale of the epidemic. This               nonidentifiability is the reason for the wide variability in published model predictions of COVID-19 epidemic.
        **Solution**: Our fitting procedure using Bayesian inference and the affine invariant ensemble Markov chain Monte Carlo algorithm was able to achieve this objective.
        
        
## Conclusions
