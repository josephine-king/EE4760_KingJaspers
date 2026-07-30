# Probabilistic Sensor Fusion

Implementation of probabilistic state-estimation and sensor-fusion algorithms, including **particle filters, extended and unscented Kalman filters, Gaussian processes, distributed Kalman filtering, and decentralized GP hyperparameter optimization**.

Developed as part of the **EE4760 Probabilistic Sensor Fusion** course at TU Delft.

## Overview

This repository contains a series of implementations exploring probabilistic methods for estimating the state of dynamic systems from noisy and distributed measurements.

The assignments progress from single-agent nonlinear state estimation to **multi-agent distributed estimation and optimization**, with applications including indoor localization, magnetic-field mapping, and target tracking.

## Topics

### 1. Particle Filtering

A particle filter is implemented to estimate the position of an agent moving through an indoor environment.

The agent uses:

* A motion model based on noisy position increments
* Noisy magnetometer measurements
* A pre-existing magnetic-field map modeled by a Gaussian process

The particle filter estimates the agent's 3D position from these nonlinear measurements and is compared against dead reckoning.

### 2. Extended and Unscented Kalman Filters

The same magnetic-field localization problem is addressed using two nonlinear Kalman-filtering approaches:

* **Extended Kalman Filter (EKF)**
* **Unscented Kalman Filter (UKF)**

Both methods combine the motion model with nonlinear magnetometer measurements to estimate the agent's position.

This assignment provides a comparison between linearization-based and sigma-point approaches to nonlinear Bayesian estimation.

### 3. Gaussian Process Regression

Gaussian process regression is used to learn a **magnetic-field map** from spatially distributed measurements.

The learned GP model provides the nonlinear measurement function used in the localization assignments.

### 4. Distributed Kalman Filtering

A distributed state-estimation problem is considered in which a network of fixed anchors collaboratively estimates the position of a maneuvering target.

Each anchor measures the target's noisy radial distance and can communicate only with its neighboring anchors. The nonlinear range measurements are reformulated into a linear state-space model, after which a **distributed Kalman filter** is used for collaborative estimation.

The system demonstrates how agents can combine local measurements and limited neighbor-to-neighbor communication to estimate a common target state.

### 5. Decentralized GP Hyperparameter Learning

The final assignment extends Gaussian-process regression to a distributed multi-agent setting.

GP hyperparameters such as the signal variance and kernel length scale are learned by distributing the data across multiple agents. Rather than performing one centralized optimization, the agents solve local optimization problems and communicate over a network.

A **proximal ADMM (pxADMM)** algorithm is implemented to coordinate the local optimizations and recover a solution approaching the centralized optimum.

## Methods at a Glance

| Assignment | Problem                                        | Main Method                 |
| ---------- | ---------------------------------------------- | --------------------------- |
| 1          | Indoor localization with magnetic measurements | Particle Filter             |
| 2          | Nonlinear magnetic-field localization          | EKF & UKF                   |
| 3          | Magnetic-field mapping                         | Gaussian Process Regression |
| 4          | Multi-agent target tracking                    | Distributed Kalman Filter   |
| 5          | Distributed GP hyperparameter learning         | Proximal ADMM               |

## Repository Structure

```text
├── assignment1_students/
│   ├── assignment1_30.ipynb
│   ├── GP.py
│   ├── helper.py
│   ├── linAlg.py
│   └── processedData/
│
├── assignment2_students/
│   ├── assignment2_30.ipynb
│   ├── GP.py
│   ├── helper.py
│   ├── linAlg.py
│   └── processedData/
│
├── assignment3_students/
│   ├── assignment3_students.ipynb
│   ├── GP.py
│   ├── helper.py
│   └── linAlg.py
│
├── assignment4_students/
│   ├── assignment4_students.ipynb
│   ├── helper.py
│   ├── linAlg.py
│   ├── multiagent_tracking.png
│   └── tracking_data.npz
│
└── assignment5-students/
    └── assignment5-students/
        ├── assignment5-student.ipynb
        ├── artificial_gp_field.mat
        └── utils.py
```

## Context

Developed as part of **EE4760 Probabilistic Sensor Fusion** at TU Delft.

The course focuses on implementing and evaluating probabilistic sensor-fusion methods for practical estimation problems, including nonlinear filtering, Gaussian processes, and distributed estimation.
