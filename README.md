# The Bias-Variance Tradeoff: Choosing How Flexible a Model Should Be

## Objective

In this lab, I wanted to understand how the complexity of a polynomial model affects its bias, variance, and ability to make accurate predictions on new data.

## Methodology

- Generated simulated data with a known true curve and used 200 fresh samples to measure bias squared and variance across six polynomial degrees.
- Compared training error and held-out error across polynomial degrees 1–15 using 2,000 new observations.
- Used 5-fold cross-validation to find the polynomial degree with the lowest average prediction error and compared how much the results varied across folds.
- Used nested cross-validation to see whether selecting the lowest CV error gives an accurate estimate of performance on new data.
- Created a function called `kfold_mse()` to calculate cross-validation error for different polynomial degrees and numbers of folds, including 10-fold CV.
- Explored double descent by fitting higher-degree polynomials and comparing their training and held-out errors.

## Key Findings

- **Bias and variance:** At degree 5, variance was 0.0180, compared to 0.0994 at degree 15. This showed me that increasing model complexity can make predictions less consistent.
- **Held-out error:** Degree 5 had the lowest held-out error among the degrees tested.
- **Cross-validation:** 5-fold CV selected degree 4 with an MSE of 0.1401, while the held-out data selected degree 5.
- **Nested cross-validation:** The estimated MSE was 0.2070, compared to the lowest 5-fold CV MSE of 0.1401. This showed me that choosing the model with the lowest CV error can make its performance look better than it actually is.
- **Fold consistency:** Degrees 4 and 5 had relatively small differences in error across folds, suggesting more consistent predictions.
- **10-fold CV:** I created the function to compare degrees 4 and 5 using 10 folds, but I haven't recorded the final MSE values yet.
- **Double descent:** With a degree-40 polynomial, training MSE was 0.0650 while held-out MSE was 155.1553. In the higher-degree experiment, held-out error increased dramatically before decreasing again as model complexity increased.

## Conclusion

Overall, this lab helped me understand why a more complicated model isn't always better. While increasing the polynomial degree can reduce bias, it can also increase variance and make predictions worse on new data. I also learned that cross-validation is useful for choosing a model, but even its lowest error can be overly optimistic. I would still start with a simpler model and use cross-validation to decide whether adding more complexity is worth it.
