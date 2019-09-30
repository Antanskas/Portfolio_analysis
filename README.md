# Portfolio_analysis, VaR simulations
* ## Idea ![](https://github.com/Antanskas/Portfolio_analysis/blob/master/repository_images/idea.png)
  * Analyse given investment portfolio which is consist of call, put options, shares. Simulate various VaR models, answer to essential questions.
* ## Environment ![colab img](https://github.com/Antanskas/Portfolio_analysis/blob/master/repository_images/colab.png)
  * Google colaboratory server
  * Python 3
* ## Dataset ![](https://github.com/Antanskas/Portfolio_analysis/blob/master/repository_images/books.png)
  * Excel table with stock prices, volatilities, portfolio info
* ## Models ![](https://github.com/Antanskas/Portfolio_analysis/blob/master/repository_images/model.png)
  * Variance-covariance VaR
  * Historical VaR simulation
* ## Questions ![](https://github.com/Antanskas/Portfolio_analysis/blob/master/repository_images/questions.png)
  * **Question 1:**
    * **What was the portfolio value on the 19th April 2013?**  
    Answer:  
      Portfolio value on 2013-04-17 is 202681.84
    * **To which risk factors is the portfolio most sensitive?**  
    Answer: 
      As we see for Calls Delta is near 1 and for Puts - near to 0. It means that for Calls changing of underlying assets affects Call's    values the same way (underlying assets raises for 1 leads to raise calls for 1 as well). For Puts, changes of underlying assets      affects Puts values poorly (puts values remains more or less the same). Having mostly Calls, shares and only 2 Puts in whole          portfolio, option behaves like the underlying security as shares does in terms of price changes. Overall - portfolio is sensitive    for underlying asset price changes. Mean Delta value is 0.77 which tells that in average portfolio value changes in 0.77xchanges      speed.
      Also we can notice, Gamma values for whole portfolio subjects tend to be close to 0 what tells us that Delta doesn't tend to change when underlying security changes in price. Deltas tend to keep same values - big for Calls which leads for keeping portfolio sensitive for changes in underlying asset prices. Mean Gamma value is 0.00000000679 that is ~ 0.
      Theta values, which represents how time affects option values, for Puts are big positive(but only two Puts in whole portfolio) and for Calls (majoroty of assets in whole portfolio) - small negative. In the other hand mean Theta value is 22.29 which is an indicator that even majority of assets are calls and shares, for puts time means a lot and overall portfolio is sensitive for time.
      Vega tells how volatility of price gonna change or how option price changes while implied volatily changes as well. For all the options in portfolio Vega values are really small what means that changes in implied volatility impacts portfolio value in a really small step as well.They are all small positive values which tells that if implied volatility raises, portfolio value raise reallly small as well and vice versa. So implied volatility isn't a factor to which portfolio is really sensitive. Mean Vega value is 0.009.
      Rho measures the sensitivity of an option to a change in interest rate. As we see from Rho values that only Puts has big absolute Rho values (big negatives) which says that changes in interest rates affects Puts values in the oposite direction (if interest rates decreases then Put values increases and vice versa). For Calls Rho values are really small positives, nearly close to 0 which means that changes in interest rates really poorely affects Call option values. Even majority of options are calls, mean Rho value is -9.70 which says that when interest rate increases portfolio value decreases by 9.7 points.

      Resume: Overall it seems that underlying asset price (stock price) plays biggest role for portfolio changes (Delta). Secondary comes time or Theta, and thirdy - interest rate or Rho. Portfolio is most sensitive for these parameters by the same order.
  * **Question 2:**
    * **At which date would the portfolio suffer the largest loss?**  
    Answer:  
    Date when portfolio value was lowest (biggest loss) is: 2012-09-19
    ![](https://github.com/Antanskas/Portfolio_analysis/blob/master/plots/portfolio_values_over_time.png)
    * **How much did the risk factor move on that date?**  
    Answer:  
    Since day before minimal portfolio value day till minimal portfolio value day, average Greek risk factors decreased by:
      * Delta: 1.226139e-05
      * Gamma: -1.171564e-08
      * Theta 1.213072e+00
      * Vega -8.488840e-03
      * Rho -6.748304e-04
   * **Question 3:**
     * **What would be variance-covariance Value at Risk of the portfolio for 1 day horizon and confidence interval: 99%?**  
     Answer:  
     Variance-covariance VaR for 1 day horizon and confidence==99% is -2.101 %
     ![](https://github.com/Antanskas/Portfolio_analysis/blob/master/plots/portfolio_value_changes_histogram_vc.png)
   * **Question 4:**
     * **What would be historical simulation Value at Risk of the portfolio for 1 day horizon and confidence interval: 99%?**  
     Answer:  
     Historical VaR for 1 day horizon and confidence==99% is -2.531 %
     ![](https://github.com/Antanskas/Portfolio_analysis/blob/master/plots/portfolio_value_changes_histogram_hist.png)
   * **Question 5:**
     * **How would you test if variance-covaraince VaR is adequatelly measuring the risk?**  
     Answer:  
     I would compare variance-covariance VaR with historical VaR
     * **Is the model performance acceptable?**  
     Answer:  
     Comparing variance-covariance VaR simulation and historical VaR simulation values with confident==99% difference is 0.43% what is around 16% and 20% of both VaR values and with confident==95% difference between these two VaR simulations is even smaller - 0.164%, what is around 11% and 12% of both VaR values. Using both VaR simulations we took actual historical data so in both ways if we assuming that value should be distributed with normal distribution both variance-covariance and historical VaRs should be similar and we got that. Does the model perform is acceptable is hard to tell, it depends on the standarts company has.
