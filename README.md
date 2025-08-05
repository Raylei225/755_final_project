<h1 align="center">755 Final Project: State-level Firearm Trend Prediction</h1>
<div align="center">   
    <img src="Image/FirearmTrendLogo.png" alt="Logo" width="200" height="200">
    <h5> Contributors </h5>
    <p> Yuyang Shen, Will Yin</p>
</div>

## What's This About?

This repository contains the final project for course of PSYCH-755: Environments and Tools for Large-scale Behavioral Data Science at University of Wisconsin at Madison. The project focuses on predicting state-level National Instant Criminal Background Check System (NICS) of firearm, which serves as the proxy of firearm sale trend, using neural network. Two types of neural network were applied in this project: long short term memory (LSTM) of recurrent neural network and customized deep learning neural network (in progress), the latter of which contains our focal predictor Google search trend (gtrend) and multiple other features.

## User Notice

This project is a tentative part of our Capstone project attempting to address our research question via different types of neural network. We DO NOT reconmmend any attempt to apply any pipelines in this repository in your own project as they are still in progress of development until further update. However, if you just want to try some of these files by yourself, you will need functional tensorflow (version 2.19.0 or newer) and compatible keras, and you may also need quarto if you want to render the qmd files. 

## Overview

`RNN.ipynb`: This file contains codes for time series prediction of NICS data using LSTM which is a variant of recurrent neural network. The original pipeline is from [https://github.com/nachi-hebbar/Time-Series-Forecasting-LSTM]. While the prediction seems decent for several state, the model fails for many states at the same time. This unsatisfying performance suggest that our collected NICS data may lack staionality, which is the desired characteristic for time series prediction, potentially influenced by other factors such as seasonality and other social factors. This possibility of other influential factors further confirms us to introduce additional features such as gtrend and other social factors when building the predictive model.

`data_cleaning.qmd`:
This markdown file contains codes for transferring our congregated time series data into wide format. The specific calculation for each column in the data is addressed in this file as well. 

`neural_network.ipynb`:
This file contains codes for building and applying deep learning neural network onto our wide format of data (`NN_wide_data.csv`). However, this file is still in progress of polishing as our data is not yet perfectly compatible with the current pipeline, resulting in a performance of 0 accuracy. We may consider using different pipelines or built of neural network in the future as the current one was originally used for visual learning.

## Data
This project only used publicly accessible data from government agencies, including data from 2013-9 to 2023-8.
### Target variable

<img src="Image/NICS-Logo_190104_102706.png" width="600" height="300">

`totals`: Total number of individuals who have gone through the FBI National Instant Criminal Background Check System (NICS)

### Features
`state`: The state of this data collected

`gtrend`: The Google trend data of the state

`date`: The data are collected by month; this column shows the month of the data collection in year-month-day format

`urban_pop_percent`: the percentage of urban population in the state

`rural_pop_percent`: the percentage of rural population in the state

`population`: The entire population of the state

`percent_in_poverty`: The percentage of the poverty population

`Median_income`: The median income of the state

`partisan_index_dem`: The proportion of the population who voted for the democratic party in the last two-year election.

`partisan_index_rep`: The proportion of the population who voted for the republican party in the last two-year election.

`percent_of_unemployed_poulation`: The percentage of unemployed population in the state


## Limitations & Contributions

* Predictive performance: performance for both time series prediction and deep layer neural network is not satisfying. We need better ways to either build our own model or implement existing networks to get better predictive performance
<be>

* Data cleanning: the current way of transferring our time series data into wide format is too straight resulting in a great decrease in the size of our data, which is also another potential contributing factor to poor prediction, and potentially loss of important information and patterns. We need additional ways to process and clean our data so that it can be better fitted into neural network pipelines.
<be>

* Debugging: the current codes are not bug-free. Warnings in `RNN.ipynb` and 0% accuracy in `neural_network.ipynb` both suggests the potential occurence of silent errors that could also deteriorate our prediction. 
<be>

* The target variable used the number of people who went through a background check every month as a proxy. Which may not represent the number of people who purchased the weapon since one person could purchase more than one weapon for their families or purchase a weapon from the secondary market/gun shows.





