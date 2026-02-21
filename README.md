# NBA-Shot-Prediction-Model
Neural network pipeline that predicts outcome of NBA shot attempts.

## Overview

This project trains a neural network to classifies the outcome of NBA shot attempts (make or miss) using historical shot data from the 2013–2023 seasons. The model currently achieves **70% prediction accuracy**, given the position of the shot on the court and the team in possession of the ball.

Potential applications include real-time sports prediction markets, where shot-level probability estimates could provide a meaningful edge.

## Pipeline

### 1. Data Collection
Shot data was scraped from [basketball-reference.com](https://www.basketball-reference.com/) for all NBA seasons from 2013 to 2023, using an adapted version of the [shotChart](https://github.com/theccalderon/shotChart) scraping framework.

### 2. Preprocessing & Feature Engineering
Raw shot data required significant cleaning and transformation before it could be fed into a model:

- **Cleaning:** Removed units from numeric fields, converted data types to model-compatible formats
- **Feature Engineering:** Derived new features including the score of both the attacking and defending teams at the time of each shot
- **Encoding:** Applied one-hot encoding to categorical variables (players and teams) to produce numeric feature vectors

### 3. Feature Selection
An extensive iterative feature selection process was used to identify the most predictive features out of 20+ candidates. The final model uses the **best 3 features**, selected to balance predictive power with model simplicity and generalizability.

### 4. Model Training
The NN was trained from scratch to classify shot outcomes. The final model predicts shot makes and misses with **70% accuracy**, using shot location on the court and the team in possession as inputs.

## Results

| Metric | Value |
|---|---|
| Prediction Accuracy | 70% |
| Seasons Covered | 2013–2023 |
| Features Used (final) | 3 (selected from 20+) |

## Future Work

The long-term vision is a real-time shot prediction pipeline that runs during live NBA broadcasts:

- **Image Classifier:** Train a computer vision model to extract shot location and team possession from a single frame of an NBA broadcast
- **End-to-End Pipeline:** Feed the image classifier's output directly into the shot prediction model, removing the need for manual data entry
- **Live Application:** Build a proof-of-concept app that overlays real-time shot outcome probabilities during a broadcast, updating semi-continuously as play develops

## Sources

- [basketball-reference.com](https://www.basketball-reference.com/) — Source for all shot data
- [shotChart by theccalderon](https://github.com/theccalderon/shotChart) — Adapted for scraping 2013–2023 season data
