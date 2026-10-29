# AI-Powered Predictive Maintenance & Resource Optimizer for Industrial Laundry Machinery

Final project for the Building AI course.

## Summary

This project develops an AI solution to monitor commercial laundry equipment (such as the XGQ-160FQ washer-extractor and steam boilers) using IoT sensor telemetry. It detects early mechanical anomalies, predicts component breakdown, and optimizes water, steam, and electrical energy consumption. Building AI course project.

## Background

Commercial and industrial laundry plants operate heavy-duty washing and finishing machinery around the clock. Unexpected equipment downtime leads to significant operational losses and delays in client deliveries (hotels, hospitals, and garment sectors).

* **Frequent Unscheduled Breakdowns:** Bearing wear, motor stress (VFD faults), and pneumatic valve failures often cause sudden production stops.
* **Resource Wastage:** High energy usage (steam, electricity, and water) without dynamic optimization increases carbon footprint and utility bills.
* **Personal Motivation:** Having observed large-scale plant operations, preventing machine downtime and saving operational costs through early failure prediction can transform plant management.

## How is it used?

The system collects real-time sensor streams from washer-extractors, boilers, and dryers (vibration, motor current, operating temperatures, and steam pressure levels). 

* **Primary Users:** Plant maintenance engineers, floor supervisors, and operations managers.
* **Deployment Context:** Industrial laundry facilities, hotel central laundries, and textile processing units.
* **Actionable Alerts:** Maintenance alerts are automatically generated on an interactive dashboard and sent via mobile notifications before mechanical failures cause complete stoppages.

```python
# Conceptual anomaly score detection demo
import numpy as np

def calculate_anomaly_score(vibration_rms, motor_temp, steam_pressure):
    # Baseline weights derived from machine baseline profiles
    weights = np.array([0.45, 0.35, 0.20])
    features = np.array([vibration_rms, motor_temp, steam_pressure])
    
    # Linear combination with Sigmoid activation for risk probability
    z = np.dot(weights, features) - 3.5
    failure_probability = 1.0 / (1.0 + np.exp(-z))
    return failure_probability

# Example reading from an XGQ-160FQ washer unit during high extraction spin
prob = calculate_anomaly_score(vibration_rms=4.2, motor_temp=85.0, steam_pressure=0.55)
print(f"Predicted Component Failure Risk: {prob * 100:.2f}%")# laundry-ai-predictive-maintenance
