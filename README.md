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
- Apply different Linear Models, only numeric fields are used for price estimation 
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
<img src="https://github.com/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/figures/imoveis_results_linear_regressions.png?raw=true" width="640">

## [ML Models Selection](https://colab.research.google.com/github/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/imoveis_select_ML_models.ipynb)
- Apply and select from different Linear Models (only numeric fields are used for price estimation)
- **Best results**

| Model                   | R2	 | RMSE	      | MAE	      | MedAE	    | MAPE |
|-------------------------|------|------------|-----------|-----------|------|
| Gradient Boosting (all)     |	0.99 | 71283.11	  | 50316.73	| 35095.12	| 0.07 |
| **Random Forest     (all)**	| 0.96 | 130296.62	| 88421.16	| 57367.88	|**0.10**|
| K-Nearest Neighbors (all)	| 0.67	| 375741.02	| 260570.99 | 	172230.00	| 0.31 |

3 Best results are showed. Decision trees give MAPE = 0, but with large overffiting, thus was excluded here. Linear Regression regressions and their variants (Ridge Regression, HuberRegressor etc.) give better results than K-Nearest Neighbors, but ~0.30. They are also excluded here since a better result, ~0.22, was obtained berfore with linear regression with log transformation and iteractions. Random Forest was selected, despite a little small MAPE than Gradient Boosting because it shows better results (RMSE) in test data (here, results are over all data). 

## [RandomForest: numeric features](https://colab.research.google.com/github/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/imoveis_ML_best_model_numeric.ipynb)
- Apply RandomForestRegression, only numeric fields are used for price estimation

- **Best result**

| Model                   | R2	 | RMSE	      | MAE	      | MedAE	    | MAPE |
|-------------------------|------|------------|-----------|-----------|------|
| RF Numeric Fields (all) |	0.98 | 95300.42	| 57290.74 |	29912.10 |**0.07** |

<br>
<br>
<img src="https://github.com/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/figures/imoveis_results_ML_numeric.png?raw=true" width="640">

## [RandomForest: numeric + Yolo](https://colab.research.google.com/github/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/imoveis_ML_best_model_numeric_yolo.ipynb)
- Apply RandomForestRegression, numeric fields and Yolo detected objects are used for price estimation
- **Best result**

| Model                   | R2	 | RMSE	      | MAE	      | MedAE	    | MAPE |
|-------------------------|------|------------|-----------|-----------|------|
| RF Num + Yolo (all)	| 0.98	| 95801.03	| 57979.46	| 30782.84	| **0.07** |

<br>

| nr | Feature |	Mutual Information |
|----|---------|---------------------|
| 1	 | condominio	| 1.082172 | 
| 2	 | area_util	| 1.080046 | 
| 3	 | tipo_Padrão| 	1.042260 | 
| 4	 | **sink**	| 0.983158 | 
| 5	 | banheiros	| 0.944558 | 
| 6	 | quartos	| 0.902648 | 
| 7	 | iptu	| 0.878083 | 
| 8	 | vagas_na_garagem	| 0.835178 | 
| 9  | location	| 0.815770 | 
| 10 | 	**chair**	| 0.791374 | 
| 11 |	**toilet** |	0.788386 |
| 12 |	**potted plant** |	0.599620 |
| 13 |	**bed**	| 0.576171 |
| 14 |	**tv**	| 0.571253 |
| 15 |	**couch**	| 0.565151 |

The use of Yolo objects detected in the images as predictors does not appear to bring any significant gain to price estimation compared to the model that uses only numerical predictors. Despite this, several detected objects show a significant gain in information, and among the 15 attributes with the highest gain, 7 objects are objects detected in the images. This suggests that this approach may be potentially useful, although it seems necessary detect more relevant objects to the real estate advertising scenario, in addition to those identified as standard by Yolo.

<br>
<br>
<img src="https://github.com/Rogerio-mack/Property-Price-Prediction-Sao-Paulo/blob/main/figures/imoveis_results_ML_numeric_yolo.png?raw=true" width="640">


