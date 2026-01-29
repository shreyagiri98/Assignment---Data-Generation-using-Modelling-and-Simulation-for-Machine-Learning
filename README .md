# Assignment: Data Generation using Modelling and Simulation for Machine Learning

**Name:** Devansh Wadhwani  
**Roll No:** 102303631  

## Overview
This project demonstrates the generation of synthetic data using a **discrete-event simulation (DES)** and subsequent analysis using various Machine Learning models. We simulated a **Call Center** environment to study the relationship between staffing levels, service times, and customer wait times.

## Methodology

### 1. Simulation Setup (SimPy)
We used the `simpy` library in Python to model a Call Center as an **M/M/c queue**:
- **Arrival Process**: Customers arrive according to a Poisson process (exponential inter-arrival times).
- **Service Process**: Support time is exponentially distributed.
- **Resources**: Calculate the impact of number of employees on wait times.

**Parameters:**
- **`Num_Employees`** (Integer): Random selection between 1 and 10 agents.
- **`Avg_Support_Time`** (Float): Average time an agent takes to resolve a query (20 - 60 mins).
- **`Customer_Interval`** (Float): Average time between customer calls (1 - 10 mins).

**Output Variable:**
- **`Avg_Wait_Time`**: The average time a customer waits in the queue before being served.

### 2. Data Generation
We executed the simulation **1000 times**. In each run, we randomly sampled the input parameters from their defined ranges and recorded the resulting `Avg_Wait_Time`. This resulted in a dataset (`simulation_data.csv`) with 1000 rows.

### 3. Machine Learning Analysis
We trained **10 different regression models** to predict `Avg_Wait_Time` based on the three input parameters.
- **Data Split**: 80% Training, 20% Testing.
- **Preprocessing**: Standard Scaling was applied to features.
- **Evaluation Metric**: R2 Score (Coefficient of Determination) and RMSE (Root Mean Squared Error).

## Results
The following table summarizes the performance of all models, sorted by R2 Score:

| Model             |    RMSE |   R2 Score |
|:------------------|--------:|-----------:|
| Gradient Boosting | 25.7817 |   0.8637 |
| KNN               | 27.3871 |   0.8462 |
| Random Forest     | 27.4004 |   0.8461 |
| Extra Trees       | 28.2158 |   0.8368 |
| Linear Regression | 32.6232 |   0.7818 |
| Ridge             | 32.6282 |   0.7817 |
| Lasso             | 32.7568 |   0.7800 |
| AdaBoost          | 33.0509 |   0.7761 |
| SVR               | 35.5247 |   0.7413 |
| Decision Tree     | 37.1777 |   0.7166 |

### Best Model
The **Gradient Boosting Regressor** achieved the highest accuracy with an **R2 Score of 0.8637**. This indicates that the non-linear relationship between queueing parameters and wait time is best captured by boosting ensemble methods.

## Files
- `102303631_Assignment5.ipynb`: Jupyter notebook containing the code.
- `simulation_data.csv`: The generated dataset.
- `generate_data.py`: Script used to run the SimPy simulation.
- `README.md`: Project documentation.
