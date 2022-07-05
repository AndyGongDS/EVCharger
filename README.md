# EV Chargers: Modelling for number of EV Chargers and Recommendations in Ontario

## Problem Statement
EV Station is a start-up company providing multi-type EV Chargers for all types of EVs on the market. The company has successfully installed over 10K EV Chargers over 10 states in the United States, and are looking to enter the Canadian EV charging market. EV Station data science team was consulted by the management team for estimating the Canadian market size. The management would like to investigate the estimated number of additional EV chargers needed currently in Canada, revenue for the company if they fill the gap, and how it will be needed in the next few years.

![Public EV Chargers in Ontario](https://editorials.autotrader.ca/media/wanlw3dd/ivy-charging-station-huntsville.jpg?anchor=center&mode=crop&width=1920&height=1080&rnd=132828516422770000)
*Photo 1. Public EV chargers in Ontario (source: https://www.autotrader.ca/editorial/20211201/level-3-ev-chargers-to-be-installed-along-ontario-s-hwy-400-and-401/)*

## Goal of the Study
The aim of this project is to study if there are any opportunities for the EV Station company to enter the Canadian EV Charging Market, especially for Ontario, through installing new Public EV Chargers, as the emerging trend of using Electrical Vehicles. The addition of EV chargers in Ontario will be estimated for the management team to study the feasibility of entering the Canadian Market.

## Dataset
The main dataset used in this study was retrieved and downloaded from a public data source [Electric Charging and Alternative Fuelling Stations Locator](https://www.nrcan.gc.ca/energy-efficiency/transportation-alternative-fuels/electric-charging-alternative-fuelling-stationslocator-map/20487#/find/nearest?fuel=ELEC&ev_levels=all). The website provides a visualization tool for users to locate public chargers in both the US and Canada. It also enables embedding and downloading for the original datasets for public uses.

## Modeling
After the exploratory data analysis, training and testing datasets were prepared to train machine learning models. The data set included the following features:
- Total ports: total ports that were installed in the states/provinces regardless of the port types.
- TESLA, NEMA, CCS, CHADEMO, J1772: total number of respective charging connectors in the states/provinces.
- 2020 EV Registration: EV registered in 2020.
- M_Pop: Million of population in the most recent census.
- B_GDP: Billion of GDP in 2021
- M_Reg_Cars: Million of cars registered, regardless of the types of cars (EV, PHEV, Fuel).
- M_Area, M_Land, M_Water: Million square meters for total area, land area, and water area.
- Country_CA (Binary): 1 is in Canada, 0 is in the US.
The Total Stations column is the target for modeling and prediction.

In the modeling process, a few approaches were tried to find the best fit for the model, including training-test split, cross validation, grid search and random search hyperparameter tuning.
The following models were fitted and validated: 
1. Linear Regression Model
2. Random Forest
3. XGBoost
4. RANSAC Linear
Each model’s performance was evaluated through mean absolute errors (MAE) and R2 scores. The RANSAC Linear model performs the best as it has the most R2 score and the lowest MAE. After a grid search cross validation process, the best-fit hyperparameters were chosen as the best model.
***RANSAC Model*** performs the best amoung the four models.

## Results
The actual charger number is ***1850***, and the ***predicted*** EV charger number is ***1894***.

## Scenarios
- The EV Registration number increase to 15K, the predicted number of chargers is 1901
- The EV Registration number increase to 30K, the predicted number of chargers is 1912
- The EV Registration number increase to 60K, the predicted number of chargers is 1933

The EV Registration number increases will not affect the number of stations a lot, which is very interesting. It also suggested that in the next a few years, there is no gap to fill for the EV Charging companies. Existing stations have been sufficient.

### Next Steps
1. We will explore not only provinces, but also cities in the dataset. 
2. If possible, we will be looking for data about home chargers.
3. We can also explore EV charger types, based on the EV types. 