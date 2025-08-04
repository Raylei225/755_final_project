# 755 Final Project: State-level Firearm Trend Prediction

## Predict state-level background check number (NICS) of firearm via neural network

This repository contains the final project for course of PSYCH-755: Environments and Tools for Large-scale Behavioral Data Science at University of Wisconsin at Madison. The project focuses on predicting state-level NICS of firearm, which serves as the proxy of firearm sale trend, using neural network. Two types of neural network were applied in this project: long short term memory (LSTM) of recurrent neural network and customized deep learning neural network (in progress), the latter of which contains our focal predictor Google search trend (gtrend) and multiple other features. 

## User Notice

This project is a tentative part of our Capstone project attempting to address our research question via different types of neural network. We DO NOT reconmmend any attempt to apply any pipelines in this repository in your own project as they are still in progress of development until further update. However, if you just want to try some of these files by yourself, you will need functional tensorflow (version 2.19.0 or newer) and compatible keras, and you may also need quarto if you want to render the qmd files. 

## Overview

`RNN.ipynb`: 
This file contains codes for time series prediction of NICS data using LSTM which is a variant of recurrent neural network. The original pipeline is from [https://github.com/nachi-hebbar/Time-Series-Forecasting-LSTM]. While the prediction seems decent for several state, the model fails for many states at the same time. This unsatisfying performance suggest that our collected NICS data may lack staionality, which is the desired characteristic for time series prediction, potentially influenced by other factors such as seasonality and other social factors. This possibility of other influential factors further confirms us to introduce additional features such as gtrend and other social factors when building the predictive model.

`data_cleaning.qmd`:
This markdown file contains codes for transferring our congregated time series data into wide format. The specific calculation for each column in the data is addressed in this file as well. 

`neural_network.ipynb`:
This file contains codes for building and applying deep learning neural network onto our wide format of data (`NN_wide_data.csv`). However, this file is still in progress of polishing as our data is not yet perfectly compatible with the current pipeline, resulting in a performance of 0 accuracy. We may consider using different pipelines or built of neural network in the future as the current one was originally used for visual learning.

## Limitations & Contributions

* Predictive performance: performance for both time series prediction and deep layer neural network is not satisfying. We need better ways to either build our own model or implement existing networks to get better predictive performance

* Data cleanning: the current way of transferring our time series data into wide format is too straight resulting in a great decrease in the size of our data, which is also another potential contributing factor to poor prediction, and potentially loss of important information and patterns. We need additional ways to process and clean our data so that it can be better fitted into neural network pipelines.

* Debugging: the current codes are not bug-free. Warnings in `RNN.ipynb` and 0% accuracy in `neural_network.ipynb` both suggests the potential occurence of silent errors that could also deteriorate our prediction. 