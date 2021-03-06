# covid-ml-project
**Predicting countries' covid indicators using LSTM RNNs**

Includes preprocessing data from ourworldindata, design and training of an LSTM RNN using tf.keras, and visualization of predicted results. The data is predicted based on 7-day rolling averages of new deaths and cases per million people, territory population and median age

Juan Andrés Toro
2021-04-27
___
## Steps
### Data gathering
- Get countries' covid data from Our World in Data https://covid.ourworldindata.org/data/owid-covid-data.csv
- Get US state covid data from nytimes github https://raw.githubusercontent.com/nytimes/covid-19-data/master/rolling-averages/us-states.csv
- Gett US state populations and median age from wikipedia
- Concatenate all territory data to obtain a dataset of covid indicators for all relevant countries and US territories

### Data exploration
- Examine columns and their respective NA value percentage
- Plot histograms for numerical variables
- Plot scatter matrix to observe correlations

### Data preprocessing
- Define relevant columns and specify sequential (date dependent) and non-sequential columns
- Target column is defined as new_deaths_smoothed_per_million in order to keep territories where there is enough relevant data
- Truncate the data so all data is from 2020-04-01 onwards
- Group by territory name, keep only those territories which fit certain conditions (same number of reports as the USA, less than 20% NaN values, less than 20% 0 deaths, has population and median age data, has at least 100 unique values reported for deaths)
- Preprocess territory data, scaling values and imputing NaNs
- Plot both cases and deaths for all territories selected
- Define preprocessing function for prediction

### Window based LSTM 
- Concatenate all territories and generate train, validation, and test sequences using Keras' TimeSeriesGenerator
- Select number of days to look back
- Train two layer LSTM network
- Evaluate model loss on train, validation, and test datasets

### Predictions
- Choose a territory name, n (days forward to predict), n_past (days in the past to predict in order to compare with real results)
- Choose a column to display (0=deaths, 1=cases)
- Plot predictions

### Predict colombian departments COVID-19 indicators
- The model has never been trained on Colombian department data
- Import data, preprocess it, choose territory name to predict and plot predictions
___
## Results and plots
![image](https://user-images.githubusercontent.com/82002486/129951045-56523198-d9ba-49a6-80e7-574c43d9d016.png)
![image](https://user-images.githubusercontent.com/82002486/129951083-c6f10246-dc18-4961-86db-575f9b6e0421.png)
![image](https://user-images.githubusercontent.com/82002486/116830146-b4eabe00-ab6d-11eb-969f-1fa62242080c.png)
![image](https://user-images.githubusercontent.com/82002486/116830155-c03de980-ab6d-11eb-9540-ddbdff0c24df.png)
___
**Juan Andrés Toro**

**2021-04-27**
