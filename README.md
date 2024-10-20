# Property-Price-Prediction-Sao-Paulo

#### [Pre process](https://colab.research.google.com/github/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/imoveis_preprocess.ipynb)
- Anonymize data (extract URL information)
- Rename files abd field names

## [Data Preparation](https://colab.research.google.com/github/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/imoveis_data_preparation.ipynb)
- Exploration data
- Clean null and inconsistent data
- Clean some outliers
- Data conversions
- Data encodes (except text `title`)

## [Linear Regressions](https://colab.research.google.com/github/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/imoveis_linear_regression.ipynb)
- Apply different Linear Models (only numeric fields are used for price estimation)
  - Simple linear model
  - Log numeric (`price`, `area_util`) 
  - With Log numeric + iteracions
  - All cases are filtered with significant regression coefs.
- **Best result**

| Model                   | R2	 | RMSE	      | MAE	      | MedAE	    | MAPE |
|-------------------------|------|------------|-----------|-----------|------|
| Linear log, inter (all) |	0.63 | 402047.49  | 210913.13	| 127497.35 |**0.22**|

<br>
<br>
<img src="https://github.com/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/figures/imoveis_results_linear_regressions.png?raw=true" width="680">

## [ML Models Selection](https://colab.research.google.com/github/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/imoveis_select_ML_models.ipynb)
- Apply and select from different Linear Models (only numeric fields are used for price estimation)
- **Best results**

| Model                   | R2	 | RMSE	      | MAE	      | MedAE	    | MAPE |
|-------------------------|------|------------|-----------|-----------|------|
| Gradient Boosting (all)     |	0.99 | 71283.11	  | 50316.73	| 35095.12	| 0.07 |
| **Random Forest     (all)**	| 0.96 | 130296.62	| 88421.16	| 57367.88	|**0.10**|
| K-Nearest Neighbors (all)	| 0.67	| 375741.02	| 260570.99 | 	172230.00	| 0.31 |

3 Best results are showed. Decision trees give MAPE = 0, but with large overffiting, thus was excluded here. Linear Regression regressions and their variants (Ridge Regression, HuberRegressor etc.) give better results than K-Nearest Neighbors, but ~0.30. They are also excluded here since a better result, ~0.22, was obtained berfore with linear regression with log transformation and iteractions. Random Forest was selected, despite a little small MAPE than Gradient Boosting because it shows better results (RMSE) in test data (here, results are over all data). 

## [RandomForest: numeric + Yolo](https://colab.research.google.com/github/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/imoveis_ML_best_model_numeric_yolo.ipynb)
- Apply RandomForestRegression: numeric fields and Yolo detected objects are used for price estimation)

- **Best result**

| Model                   | R2	 | RMSE	      | MAE	      | MedAE	    | MAPE |
|-------------------------|------|------------|-----------|-----------|------|
| RF Num + Yolo (all)	| 0.98	| 95801.03	| 57979.46	| 30782.84	| **0.07** |




