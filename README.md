The final model is in `pricing-challenge_final.ipynb` and my scratch work is in the other two notebooks.

Description:
- The model takes a weighted average of the bond's previous trades to output a prediction for the current trade
- First, the model goes through the previous trade and reclassifies multi-leg trades as a single trade, assinging the OAS of this multi-leg trade to the average dealer_dealer price if it exists and the average of all trades otherwise.
- An offset is applied to the previous OAS data based off of the different trade types
- Data points are weighted based off of the trade type and a categorization of the trade size
- Finally, the weighted average is applied on the new adjusted OAS and custom weighting of the given trade data.
- Parameters and the ideas behind the model were fit to the train set and the validation set was only used at the end for results

Accuracy:

Model Predictions:
- Mean Error: 3.396038
- Median Error: 1.882608
- Mean Bias: -0.503067
- Median Bias: -0.389449

Last Trade Benchmark:
- Mean Error: 3.818279
- Median Error: 1.923350
- Mean Bias: 0.575663
- Median Bias: 0.241350

More details can be found at the bottom of `pricing-challenge_final.ipynb`.

Discussion:

My model does not incorporate data about trade frequencies that can be deduced from the ts_diff_hrs column. I believe that some aspect of liquidity here has the potential to fit the weighting of the half life. I also did not really use the quantity data as I just had a naive check as to whether the value was larger than 1,000,000. I also did not check the for mean reverting/following tendencies of the trade price, which could be of use. 

If the data exists, I think market quotes and customer orders that did not get executed can be valuable. Market quotes give us an idea of prices that dealers are likely willing to trade at, and if we see orders in between the market spreads, we can have a idea of levels that are closer to dealer fair values. The simplest way to use the market quote data would be to maintain a midpoint of the quote prices and update this price as quoting levels change. It is also feasible to have more complex price modeling with more data about the volumes and depths of quotes. 

