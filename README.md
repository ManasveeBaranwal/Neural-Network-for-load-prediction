🇮🇳 India Electricity Load Forecasting: A Comprehensive Guide

Welcome to the India Load Forecasting Repository! This project contains advanced machine learning and deep learning models for predicting India’s electricity demand. The primary notebook—Neural_network_based_model_for_load_prediction.ipynb—explores and compares 11 forecasting methods across 5 Indian regions:
	•	Northern Region
	•	North Eastern Region
	•	Eastern Region
	•	Southern Region
	•	Western Region

The models are trained on historical hourly data from 2018–2023 and scale up to 2030 projections (~340 GW peak and ~2400 BU energy demand).

⸻

🧠 Why Load Forecasting Matters

Load forecasting is critical for India’s grid because it:
	•	Ensures reliable power supply
	•	Enables cost-efficient generation
	•	Helps integrate intermittent renewables
	•	Supports policy decisions by CEA, grid operators, and NITI Aayog

2030 Targets:
	•	Peak Demand: ~340 GW
	•	Total Energy: ~2400 BU

India’s demand is influenced by urbanization, EV growth, cooling loads, and renewable volatility—making accurate forecasts vital for grid reliability.

⸻

📊 Dataset Overview
	•	Source: Excel files (e.g., Hourly_Load_Data_2018_2022_LeapFixed.xlsx, India_2023_Hourly_Load_Data.xlsx)
	•	Content: Hourly load data (MW) for 5 regions from 2018–2023
	•	Annual Data: CSV containing yearly peak and energy targets
	•	Features: Up to 22 per region (lags, rolling stats, FFT harmonics, annual values)
	•	Train/Test:
	•	Train: 2018–2021
	•	Validation: 2022
	•	Test: 2023

⸻

🧪 The 11 Methods Explored

1. LSTM + SARIMAX Hybrid
	•	SARIMAX forecasts monthly trends
	•	LSTM learns short-term daily patterns
	•	Daily results are scaled to match SARIMAX’s monthly energy totals

2. SARIMAX + Statistical Profile
	•	Purely statistical method
	•	Monthly SARIMAX predictions disaggregated into hourly values using historical hourly profiles
	•	Highly explainable and lightning-fast

3. SARIMAX Backtesting Engine
	•	Validates the SARIMAX forecast by checking its accuracy on unseen data (2022/2023)
	•	Ensures trust before projecting to 2030

4. Hybrid Validation Engine
	•	Measures accuracy (MAPE, RMSE, R²) for both 2022 and 2023
	•	Compares hybrid predictions to real-world values

5. XGBoost + FFT Features
	•	ML model using 32 handcrafted features including FFT harmonics
	•	Achieves ~3.5% MAPE with high speed and interpretability

6. Sub-Sampled LSTM
	•	Uses 4-hour interval data instead of 1-hour
	•	Faster training with only slight accuracy loss

7. CNN-LSTM Hybrid
	•	CNN extracts shape patterns
	•	LSTM retains temporal memory
	•	MAPE ~1.6%

8. Ensemble CNN-LSTM
	•	Averages predictions from multiple CNN-LSTM runs
	•	Reduces variance and improves robustness

9. Tuned CNN-LSTM + Weather
	•	Uses temperature and humidity as additional inputs
	•	Grid search optimizes model parameters
	•	Achieves ~1.0% MAPE

10. Country-Level Metrics
	•	Aggregates metrics across all regions to give national statistics
	•	Enables India-wide planning reports

11. Final Ensemble Model
	•	Combines all tuned CNN-LSTM runs with weather
	•	R² ≈ 0.999 and MAPE < 1.5% on 2023

⸻

📘 Notebook Guide

The core notebook—Neural_network_based_model_for_load_prediction.ipynb—is organized with these demo cells:
	•	Cell 1: Demonstrates Method 1 (LSTM + SARIMAX)
	•	Cell 2: Demonstrates Method 2 (SARIMAX + Profile-Based Disaggregation)

Other methods (3–11) are implemented across other scripts and notebooks in the repository.

⸻

📈 Key Results

Best accuracy by region on 2023 test data:
	•	Northern: MAPE ~1.6%, R² ~0.988
	•	Southern: MAPE ~1.5%, R² ~0.970
	•	Western: MAPE ~1.3%, R² ~0.964
	•	Eastern: MAPE ~1.5%, R² ~0.975
	•	North Eastern: MAPE ~1.9%, R² ~0.982

India-wide average:
	•	MAPE ~1.2%
	•	R² ~0.998

⸻

🔍 Insights & Learnings
	•	Hybrid models perform best when combining long-term (SARIMAX) and short-term (LSTM/CNN) strengths
	•	FFT-based features add meaningful seasonal/cyclical patterns
	•	Weather inputs improve summer predictions and AC-driven spikes
	•	Validation against 2023 is essential to ensure future reliability
	•	CEA scaling constraints keep 2030 forecasts grounded in policy

⸻

🇮🇳 Indian Use Cases
	•	Grid balancing and renewable forecasting
	•	Power purchase planning
	•	Load dispatch optimization
	•	Policy support for NITI Aayog, MoP, and CEA
	•	EV integration and solar ramping response
