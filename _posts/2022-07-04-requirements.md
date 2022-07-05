---
toc: true
layout: post
description: Requirements
categories: [markdown]
title: Requirements
---
# Requirements

Folgende Requirements wurden nach den SOPHISTEN Regeln für Frunch Infinity 2.0 definiert:
- Functional:
  - When the Turbofan dataset is imported within the Streamlit app, the application must fully recognize all variables and values of the dataset
  - When the user accesses the application, a choice of available datasets is presented on the user interface
  - If a selection of different datasets is provided in the app, the corresponding dataset must be imported in the data folder of the Frunch      Infinity Gitlab repository
  - When the user runs the "Free Lunch" function (Auto Machine Learning process) within the application, the pipeline must be able to prepare the selected dataset for model training
  - When the selected dataset is passed to the pipeline, the pipeline has to be able to remove missing values
  - When the selected dataset is passed to the pipeline, the pipeline must be capable of scaling the relevant features
  - Once the pipeline has preprocessed the selected data set, several statistical models should be trained on the data to make the training results comparable
  - When the training of the models is completed, a table with the model results must be displayed within the user interface
  - If errors occur while running the Frunch function, the errors should be visible on the app's interface to facilitate the debugging for app-developers


- Technological

- Quality of Service


- User Interface:
  - If the user starts the app, they have to be able to select a data set from an available list.
  - When the models finish the training a summary table must be created showing all results of the models.
  - When the user is starting the free lunch function and any errors occur from the code, those erros should be displayed via the app to the user for debugging. 

- Requirements related to other results

- Requirements for activities

## hier UML Diagramm der zentralen Komponenten einfügen
