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

  More details can be found in the `pricing-challenge-final.ipynb`


- Build a model in the `pricing-challenge.ipynb` notebook to predict a trade’s OAS based on the bond’s previous trades. Benchmark the accuracy of your model relative to the last trade model.
- Either in the notebook or in a separate doc, write a short (less than 1 page) description of how your model works.
- Include a short discussion of the shortcomings of the model and the dataset. What does your model not incorporate that you think might be important? What does the dataset not include that you think might be important? How would you use those additional data sources?
