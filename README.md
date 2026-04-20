# drought-index-calculation
Python project for calculating a simple drought index using rainfall anomalies
# Drought Index Calculation

This project uses Python to calculate a simple drought index based on rainfall anomalies. It demonstrates basic skills in time-series analysis, environmental data processing, and visualisation.

## What the project does
- Loads a CSV file with daily or monthly rainfall values
- Calculates long-term mean rainfall
- Computes rainfall anomalies
- Generates a simple drought index (negative anomaly = drought)
- Plots rainfall and drought index for easy interpretation

## Tools used
- Python
- Pandas
- NumPy
- Matplotlib

## How to run
1. Install the required libraries:
2. Run the script:

## Why I built this
I have worked with hydrological and climate datasets in my engineering career. This project shows how I can apply Python to calculate a simple drought index, which is useful for monitoring water scarcity, planning abstractions, and supporting drought management decisions.
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load dataset (replace with your own CSV if needed)
df = pd.read_csv("rainfall_data.csv")

# Ensure correct types
df["date"] = pd.to_datetime(df["date"])
df = df.sort_values("date")

# Calculate long-term mean rainfall
long_term_mean = df["rainfall"].mean()

# Calculate anomalies
df["anomaly"] = df["rainfall"] - long_term_mean

# Simple drought index (negative anomaly = drought)
df["drought_index"] = df["anomaly"]

# Plot rainfall
plt.figure(figsize=(12, 6))
plt.plot(df["date"], df["rainfall"], label="Rainfall (mm)")
plt.axhline(long_term_mean, color="orange", linestyle="--", label="Long-Term Mean")
plt.xlabel("Date")
plt.ylabel("Rainfall (mm)")
plt.title("Rainfall and Long-Term Mean")
plt.legend()
plt.grid(True)
plt.show()

# Plot drought index
plt.figure(figsize=(12, 6))
plt.plot(df["date"], df["drought_index"], label="Drought Index")
plt.axhline(0, color="red", linestyle="--", label="Zero Line")
plt.xlabel("Date")
plt.ylabel("Drought Index (mm)")
plt.title("Simple Drought Index (Rainfall Anomalies)")
plt.legend()
plt.grid(True)
plt.show()
date,rainfall
2024-01-01,5
2024-01-02,0
2024-01-03,12
2024-01-04,3
2024-01-05,4
2024-01-06,0
2024-01-07,1
2024-01-08,2
2024-01-09,0
2024-01-10,8
