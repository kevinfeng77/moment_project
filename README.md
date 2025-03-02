# Pricing Challenge Final Model

The final model is contained in [`pricing-challenge_final.ipynb`](pricing-challenge_final.ipynb), while my scratch work is available in the two additional notebooks.

---

## Description

- **Weighted Average Prediction:**  
  The model computes a weighted average of the bond's previous trades to predict the current trade's value.

- **Trade Reclassification:**  
  - Multi-leg trades are reclassified as a single trade.
  - The OAS for these trades is assigned as:
    - The average dealer_dealer price if it exists.
    - Otherwise, the average of all trades.

- **Offset Application:**  
  An offset is applied to the previous OAS data based on different trade types.

- **Data Weighting:**  
  Data points are weighted according to:
  - The trade type.
  - A categorization of the trade size.

- **Prediction Calculation:**  
  The weighted average is applied on the newly adjusted OAS using custom trade data weights.

- **Model Training and Validation:**  
  Parameters and underlying ideas were tuned on the training set. The validation set was used solely for evaluating final results.

---

## Accuracy

### Model Predictions

- **Mean Error:** 3.396038
- **Median Error:** 1.882608
- **Mean Bias:** -0.503067
- **Median Bias:** -0.389449

### Last Trade Benchmark

- **Mean Error:** 3.818279
- **Median Error:** 1.923350
- **Mean Bias:** 0.575663
- **Median Bias:** 0.241350

*More details can be found at the bottom of [`pricing-challenge_final.ipynb`](pricing-challenge_final.ipynb).*

---

## Discussion

- **Trade Frequency Data:**  
  The model does not currently incorporate trade frequency information (as seen in the `ts_diff_hrs` column). I believe that liquidity aspects reflected in this data could potentially influence the half-life weighting.

- **Quantity Data:**  
  The model employs a basic check for trade quantities (whether the value exceeds 1,000,000). There is room for improvement by refining how quantity data is used.

- **Price Dynamics:**  
  I have not yet explored the mean-reverting or trend-following tendencies of the trade price, which might provide additional predictive power.

- **Additional Data Sources:**  
  If available, incorporating market quotes and customer orders (that did not get executed) could be valuable.  
  - **Market Quotes:**  
    Offer insight into the prices dealers are willing to trade at.
  - **Order Data:**  
    Orders within market spreads may help estimate levels closer to the dealer's fair value.

  The simplest approach to using market quote data would be to maintain a running midpoint of quote prices, updating as quoting levels change. More advanced methods could involve complex price modeling that accounts for volumes and quote depths.

---
