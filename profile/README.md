# MindsEye

Machine learning with EEG brainwaves and pupil diameter to infer real-time productivity, supported by a backend for live data and a frontend for visualizing and competing with friends.

---

## Overview

MindsEye is a neuroscience-driven application that combines EEG brainwave data and eye-tracking measurements to estimate focus levels in real time.  
The system enables users to participate in competitive productivity sessions with friends, visualized through a responsive web dashboard.

---

## Key Features

| Category | Description |
|-----------|-------------|
| Machine Learning | XGBoost model trained on EEG and pupil data to infer productivity levels. |
| EEG and Pupil Tracking | Integrates Muse EEG headset and MediaPipe iris tracking for synchronized brain and eye data collection. |
| Backend | FastAPI-based server handling ML inference, data storage, and WebSocket communications for live competitions. |
| Frontend | React-based interface that visualizes focus scores, leaderboards, and personal statistics. |
| Calibration | Each user runs a personalized calibration session to establish baseline focus levels. |
| Real-time Competition | Users can connect with friends in live sessions and compare focus scores as they work. |

---

## Architecture



frontend/ → React app for EEG streaming, visualization, and interaction
backend/ → FastAPI service for data handling, prediction, and live communication
models/ → Machine learning models (XGBoost) and preprocessing scripts


**System Flow**
1. The frontend captures EEG and pupil data.
2. Data is streamed to the backend via API requests.
3. The backend uses a calibrated XGBoost model to infer productivity.
4. Predictions are broadcast to all connected clients.
5. The frontend visualizes productivity levels and competition results in real time.

---

## Frontend

Built with **React**, the frontend collects EEG and pupil data, visualizes real-time focus levels, and manages live competition sessions through **WebSockets**.  
It includes calibration, competiton data, and productivity trend views.

### Backend

Developed using **FastAPI**, **PocketBase**, and **WebSockets**, the backend handles data ingestion, model inference, and live synchronization between users.  
It exposes endpoints for calibration, prediction, and session management powered by the trained **XGBoost** model.

## Machine Learning

- **Algorithm:** XGBoost regression/classification  
- **Inputs:** EEG channels (AF7, AF8, TP9, TP10) and pupil diameters (left/right)  
- **Output:** Productivity score between 0 and 100  
- **Calibration:** Each user establishes an individual baseline before competition  
- **Adaptation:** Model recalibrates periodically to adjust to signal drift

---

## Tech Stack

| Layer | Tools |
|--------|--------|
| Frontend | React, WebSockets |
| Backend | FastAPI, Python, XGBoost, asyncio |
| Database | PocketBase / SQLite |
| ML / Data | XGBoost, NumPy, Pandas |
| Data Input | Muse EEG, MediaPipe Iris Tracking |
| Hosting | Render (backend), Vercel (frontend) |

---

