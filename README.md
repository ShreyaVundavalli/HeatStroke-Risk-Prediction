# Heatstroke Risk Prediction System

Real-time heatstroke risk prediction system that combines real time vitals, environmental data, and deep learning–based time-series forecasting to generate proactive, interpretable risk alerts.

---

## Overview

The system ingests physiological vitals (body temperature, heart rate, SpO₂) from IoT sensors and fuses them with weather data (ambient temperature, humidity, solar radiation) to estimate heatstroke risk on a 0–100% scale. A Temporal Fusion Transformer (TFT) model forecasts future vital trends, while a custom risk engine converts predictions into intuitive risk levels.

---

## Architecture

- **Data Acquisition Layer**: ESP32 + sensors (DHT11, DS18B20, pulse oximeter) stream vitals and environment readings at fixed intervals.  
- **Processing & Forecasting Layer**:  
  - Python + Flask backend for preprocessing, TimeGAN-based augmentation, and TFT inference.  
  - Risk score computed using weighted vitals and environmental factors, smoothed over a moving window.  
- **Risk Analysis & Visualization Layer**:  
  - Node.js communication server for WebSocket updates.  
  - React frontend with Chart.js to display live vitals, predicted trends, and color-coded risk indicators.

**Figure 1 – System Architecture**  
![System Architecture](https://github.com/user-attachments/assets/0a595827-f8d0-4f6a-8940-5f50ce98095c)

**Figure 2 – Flow of Prediction**  
![Flow of Prediction Diagram](https://github.com/user-attachments/assets/04f9beb0-cc6e-4ffb-b520-f0a74df6af07)

---

## Key Features

- Real-time multivariate time-series forecasting with Temporal Fusion Transformer.  
- Synthetic sequence generation using TimeGAN to handle sparse or missing sensor data.  
- Trend-aware risk scoring formula that combines body temperature, heart rate, humidity, solar radiation, and SpO₂ into a normalized 0–100 risk score.  
- Web dashboard showing:
  - Live vitals  
  - Actual vs. predicted curves  
  - Heatstroke risk percentage and alert bands  

**Figure 3 – Live Vitals**  
![Live Vitals](https://github.com/user-attachments/assets/d7ebe92b-3e4f-4189-84fa-45038b76f706)

**Figure 4 – Risk Assessment Dashboard**  
![Risk Assessment Dashboard](https://github.com/user-attachments/assets/046aab1e-642c-4f2a-92fd-bd9536f4733e)

---

## Tech Stack

| Category      | Technologies |
|--------------|-------------|
| **Backend**  | Python, Flask, TimeGAN, Temporal Fusion Transformer (TFT) |
| **Frontend** | React, Chart.js |
| **Middleware** | Node.js (communication server, WebSockets) |
| **Hardware** | ESP32, DHT11, DS18B20, pulse oximeter, LCD display |

---

## How It Works (High Level)

1. Sensors send vitals and environment readings to the backend at regular intervals.  
2. Data is cleaned, normalized, and optionally augmented with TimeGAN to fill gaps.  
3. TFT consumes past windows and known covariates to forecast short-term vital trajectories.  
4. A risk engine converts current and forecasted values into a percentage risk score and class (Low / Moderate / High).  
5. The frontend subscribes over WebSockets and updates charts and risk indicators in real time.  

**Figure 5 – Model Performance Metrics**  
![Performance Metrics](https://github.com/user-attachments/assets/7665f6ac-c9c4-47e3-9090-1506f173a671)

---

## Demo

** End-to-End System Demo Video**  
[Watch Demo Video](https://github.com/user-attachments/assets/22d06996-4803-4901-bfd0-5c3a1b3423c3)
