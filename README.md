# Weather Forecasting Model Comparison

In this repository, I explore various time series forecasting models for weather prediction using one year of hourly data. The objective is to identify the model that achieves the lowest Mean Absolute Error (MAE) for December predictions among these classic approaches.

Note: some interesting model to add later is the prophet model, it's of course an old and maybe too simple model but combined to an XGBoost that tries to learn the residuals it might be very interesting.

Install all required packages:
   ```bash
   pip install -r requirements.txt
   ```

## Model Performance Summary

| Model                       | Training Time | MAE for 63rd Street Weather Station | MAE for Foster Weather Station | MAE for Oak Street Weather Station | Strengths                                           | Weaknesses                                           |
|-----------------------------|---------------|-------------------------------------|--------------------------------|------------------------------------|-----------------------------------------------------|------------------------------------------------------|
| **ARIMA**                   | 2.1s          | 5.97                                | 5.98                           | 5.67                               | - Simple and interpretable model                   | - Assumes linearity and stationarity                  |
|                             |               |                                     |                                |                                    | - Good for linear, seasonal data                   | - High error on complex patterns                      |
|                             |               |                                     |                                |                                    | - Fast training on small datasets                  | - Struggles with multivariate forecasting             |
| **CatBoost**                | 1.2s          | 2.59                                | 2.68                           | 2.31                               | - Fast and efficient training                       | - Moderate accuracy for complex sequences             |
|                             |               |                                     |                                |                                    | - Handles categorical and missing data well         | - Requires careful parameter tuning                   |
|                             |               |                                     |                                |                                    | - Resistant to overfitting                          | - Less interpretable than simpler models              |
| **Random Forest**           | 47.4s         | 0.41                                | 0.42                           | 0.40                               | - High accuracy and handles non-linearity           | - Long training time, memory-intensive                |
|                             |               |                                     |                                |                                    | - Robust to outliers and noisy data                 | - Limited long-term forecasting capabilities          |
|                             |               |                                     |                                |                                    | - Interpretable feature importance                  | - Prone to overfitting if not tuned                   |
| **XGBoost**                 | 1.3s          | 0.45                                | 0.45                           | 0.44                               | - Fast training and high scalability                | - Moderate accuracy on highly non-linear data         |
|                             |               |                                     |                                |                                    | - Robust and flexible                               | - Sensitive to overfitting on small datasets          |
|                             |               |                                     |                                |                                    | - Handles sparse and unstructured data              | - Parameter tuning can be complex                     |
| **Temporal Fusion Transformer (TFT)** | 13m25s | 0.66                                | 0.73                           | 0.66                               | - Captures complex temporal dependencies            | - Very long training time, requires GPU for speed     |
|                             |               |                                     |                                |                                    | - Suitable for multivariate and irregular data      | - High computational cost                             |
|                             |               |                                     |                                |                                    | - High accuracy for non-linear patterns             | - Large data requirement for optimal performance      |

The table above summarizes the performance of each model in terms of training time, MAE for each weather station, and key strengths and weaknesses.

---

This comparison highlights the trade-offs between model complexity, accuracy, and computational cost. Choosing the best model depends on the specific forecasting needs, such as the importance of accuracy versus the availability of computational resources and the nature of the data.
