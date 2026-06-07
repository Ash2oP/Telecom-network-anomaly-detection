# Telecom-network-anomaly-detection
# 5G Telemetry & Real-Time Network Anomaly Detection API

An asynchronous, high-throughput backend data pipeline designed to ingest simulated 5G network telemetry logs and deploy a machine learning model to detect real-time latency spikes, packet loss, and cell tower node anomalies. 

This project bridges Telecom Signal/Network concepts with Applied Data Engineering and Machine Learning.

---

# The Problem:

Traditional rule-based threshold alerts fail by raising false alarms during peak traffic hours. This pipeline implements an unsupervised or semi-supervised learning to dynamically track network health.

---

## Tech Stack & Architecture

*   **Language:** Python
*   **Data Manipulation:** Pandas, NumPy
*   **Machine Learning:** Scikit-Learn
*   **Backend Framework:** FastAPI
*   **Database & Storage:** PostgreSQL
*   **Containerization & Deployment:** Docker, Uvicorn

---

## Project Architecture

1. **Telemetry Generation:** A multi-threaded simulation script generates synthetic 5G call detail records (CDRs) and network node metrics (Signal-to-Interference-plus-Noise Ratio (SINR), Reference Signal Received Power (RSRP), packet loss %, and round-trip latency logs), mimicing real world signal degradation.
2. **Ingestion Layer:** FastAPI endpoints receive high-concurrency JSON streaming logs asynchronously to prevent server blockages.
3. **ML Inference Pipeline:** These ingested streams then pass through a pre-trained Scikit-Learn pipeline. The model categorizes the network performance into `Normal`, `Degraded`, or `Anomalous (Critical Node Failure)`.
4. **Data Persistence:** Raw telemetry and the predictions are structured and committed to a local PostgreSQL database using batch queries.

---

## Execution Roadmap

### Phase 1: Data Modeling & EDA
*   Design the synthetic 5G metrics dataset simulation scripts.
*   Perform rigorous Exploratory Data Analysis (EDA) using Pandas, Matplotlib, and Seaborn to visualize distributions, correlation matrices, and signal degradation patterns.
*   Commit the initial exploratory Jupyter notebooks to the `/research` directory.

### Phase 2: Model Training & Core API
*   Train, tune, and evaluate the Scikit-Learn anomaly detection models.
*   Build the core FastAPI endpoints.
*   Integrate PostgreSQL database schemas for structured metrics retention.

### Phase 3: Stress Testing & Containerization
*   Set up asynchronous worker queues to handle heavy data loading simulation.
*   Containerize the app stack using Docker Compose for a single-command local setup.

---
