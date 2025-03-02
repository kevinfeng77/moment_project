Description:
- The model takes a weighted average of the bond's previous trades to output a prediction for the current trade
- First, the model goes through the previous trade and reclassifies multi-leg trades as a single trade, assinging the OAS of this multi-leg trade to the average dealer_dealer price


- Build a model in the `pricing-challenge.ipynb` notebook to predict a trade’s OAS based on the bond’s previous trades. Benchmark the accuracy of your model relative to the last trade model.
- Either in the notebook or in a separate doc, write a short (less than 1 page) description of how your model works.
- Include a short discussion of the shortcomings of the model and the dataset. What does your model not incorporate that you think might be important? What does the dataset not include that you think might be important? How would you use those additional data sources?
