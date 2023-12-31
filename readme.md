# Option pricing methods

This package aims to provide 4 different methods to estimate the price of options.

The estimators don't allow to set all the parameters but just accept a stock, in the constructor, and then evaluate the price of an option of that stock.
This lead to be able to estimate real world data, but doesn't allow to create custom environment with fake option price, volatility etc. etc.

Instead the estimator takes the last prices (for the period of these prices go to the "setting parameter" section) of the stock and computes volatility and drift of the stock.

The 4 model to estimate the price of an option are:
- binomial model
- monte carlo simulation
- black-scholes formula
- bootstrap

At the moment dividends are just ignored.

## Setting paramter
The only (financial) parameter that should be set is the annual risk free rate. As a default it is set to 0.04 in the super class of the estimator, so it's not a compulsary argument in the
estimate methods.

Another parameter that can be set is the period that the estimators take into consideration in order to calculate the volatility and drift of the stock. Also this parameter is set
in the superclass of the estimators and its default value is six months. If we want to change it we should set the estimate method parameter *periodForPrices* to a value of the *Period* 
enumeration that is defined in utilities.

### Monte Carlo and Bootstrap estimators
For the Monte Carlo and Bootstrap estimators there are another couple of customizable parameter in the *estimate* method:

- <ins>numberOfSimulations</ins>: the number of simulations of the asset price that are run to evaluate the option price
- <ins>showSimulationPaths</ins>: plot a chart with the paths of the stock prices for each simulation

## American option
For american options, a method has been implemented in the binomial estimator (*estimateAmericanOption*). In all the other methods we suppose to work with european options.