
![ER_Hero width-1200 format-webp](https://github.com/user-attachments/assets/76b38df0-bbd7-4879-a82b-2cfd6f7913bc)

# Table of Contents
- [Project Overview](#Project-Overview)
- [Framework](#Framework)
- [Assumptions and Research](#Assumptions-and-Research)
- [Results and Conclusion](#Results-and-Conclusion)
- [References](#References)

References
# Project Overview
<p align="justify"> This project outlines the development of a predictive model for forecasting energy surpluses 24 hours in advance in Brighton, UK. 
  The model will enable a company to offer free electricity to local customers when excess energy is available. The goal is to ensure accurate predictions 
  while minimizing false positives, 
  as incorrect predictions could lead to unnecessary financial losses for the company.</p>

  # Framework

![Framework](https://github.com/user-attachments/assets/fb83d1c0-40e4-4cda-a959-4ffaf8f76239)

  This diagram represents a framework for a decision system to manage energy distribution from renewable sources (solar and wind power) to end users based on AI-driven predictions of energy surplus.

## Input Data

The input data for the model consists of several environmental and weather-related factors that influence energy production, particularly from solar and wind sources.

## Decision System

### AI Model

The development of a robust machine learning model follows a structured process consisting of the following key stages:

**Data Exploration and Preprocessing**  
Initial exploration and cleaning of the historical data, addressing missing values, outliers, and data normalization, ensuring the dataset is ready for model training, has been done in `Brighton_Data_Exploration.ipynb`.

**Model Training**  
Various machine learning models were trained to predict energy surpluses:
- LSTM (Long Short-Term Memory)
- CNN (Convolutional Neural Network)
- CNN-LSTM

**Model Evaluation**  
The models were evaluated based on the following performance metrics:
- Mean Squared Error (MSE)
- Accuracy
- Precision
- Recall
- False Positive Rate (FPR): Important for ensuring financial stability by minimizing incorrect predictions of surplus.

The notebooks `Brighton_Data_Exploration.ipynb` and `Brighton_modelling.ipynb` contain all the above information.

# Assumptions and Research

This project is based on three main categories of assumptions:

- Energy Calculation Assumptions
- Energy Generation and Consumption Assumptions
- Surplus Energy Calculation

## Energy Calculation Assumptions
**Solar Power**
The solar farm spans 125 acres, as recommended in [1]. It is assumed that there is no loss in power, and the entire area of the farm generates electricity.

**Wind Power**
Design factors that could impact power generation are not considered. The wind farm is equipped with 50 turbines, based on the average number of turbines in a typical wind farm [2].

## Generation and Consumption Assumptions
**Energy Generation Assumptions**

Data from the past three years in the UK [5] indicates that:

- Renewable energy generation is high at the beginning and end of the year.
- Renewable energy generation is relatively low during the 2nd and 3rd quarters.

**Energy Consumption Assumptions**

- Energy consumption increases in the 1st and last quarters.
- Energy consumption decreases in the 2nd and 3rd quarters.
- There is no surplus energy available in the 1st and last quarters due to high consumption.
- Potential surplus energy may occur in the 2nd and 3rd quarters due to lower consumption, despite high solar generation.

<div style="display: flex;">
  <img src="https://github.com/user-attachments/assets/a54ef9dc-bc21-4825-9fd0-1d62e923782b" width="400" />
  <img src="https://github.com/user-attachments/assets/a3419d33-f93b-4f13-9658-9e6f8fdd1e99" width="400" />
</div>

**Brighton Power Consumption**
According to the UK Government [6], the graph represents Brighton’s power consumption. Based on this data, Brighton's power consumption is estimated at 72 GWh annually.

In the UK, the cost of 1 kWh of electricity is £0.245 [7].

![3](https://github.com/user-attachments/assets/99c6d46f-be82-475e-83b6-76437a3feaab)

## Surplus of Energy

Brighton's annual power consumption is set at 72 GWh. Of this, 60% is allocated to the 1st and 4th quarters, while 40% is assigned to the 2nd and 3rd quarters. Hourly consumption is derived from monthly consumption, assuming constant use throughout the day for simplicity.

To determine surplus power, hourly consumption is subtracted from total generated power. A positive result indicates a surplus; a negative result indicates none.

To prevent grid overload during surplus periods, power is distributed 70% to residential users and 30% to industrial users. During surplus, residential users receive a limited amount of free electricity, with additional charges applied for overuse.

# Results and Conclusion
The Full Results of the the models are in `Brighton_modelling.ipynb` 

The system demonstrated high accuracy, precision, and recall, while maintaining low Mean Squared Error (MSE) and False Positive Rate (FPR) in predicting power surplus.

Although the model performs well in predicting solar power, it faces significant challenges in forecasting wind power. 
Due to these limitations, the model is not ready for deployment by May 2024. Improvements are needed to enhance accuracy and further reduce the FPR,
which could otherwise result in substantial financial losses.

We recommend deploying the model during the 1st and 4th quarters of the year, when the FPR is lower. This would allow for data collection on consumer
behavior and provide an opportunity to monitor system performance. Additionally, this period can be used to assess market trends and evaluate the revenue
potential from new users attracted by the free surplus electricity offering.

# References
[1] House of Commons Library. (2024, Feb. 12). Planning For Solar Farms [Online]. Available: https://researchbriefings.files.parliament.uk/documents/CBP-7434/CBP-7434.pdf

[2] USA FACTS. (2022, Aug. 25) How much US electricity comes from wind power? [Online]. Available: https://usafacts.org/articles/how-much-us-electricity-comes-from-wind-power/

[3] Penn State University. Wind Energy and Power Calculations [Online]. Available: https://www.e-education.psu.edu/emsc297/node/649

[4] A. Sarkar and D. K. Behera, (2012) “Wind turbine blade efficiency and power calculation with electrical analogy,” International Journal of Scientific and Research Publications, (2012).  

[5] UK Government, Department for Energy Security and Net Zero. (2023 Dec. 12). Energy Trends: December 2023 [Online]. Available: https://assets.publishing.service.gov.uk/media/6581bceffc07f300128d44d7/Energy_Trends_December_2023.pdf

[6] UK Government, Department for Energy Security and Net Zero. (2023 Dec. 12). Subnational total final energy consumption, UK, 2005 to 2021 [Online]. Available: https://assets.publishing.service.gov.uk/media/65117912bf7c1a0011bb4671/Subnational_total_final_consumption_2005_2021.xlsx

[7] ‘Average Cost of Electricity Per kWh in the UK 2024’, GreenMatch.co.uk. Accessed: Apr. 21, 2024. [Online]. Available: https://www.greenmatch.co.uk/average-electricity-cost-uk




