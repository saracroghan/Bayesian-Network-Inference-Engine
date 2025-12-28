# Bayesian Network Inference Engine

This project is a Python-based probabilistic inference engine for Bayesian Networks. It allows users to load network structures and conditional probability tables (CPTs) from BIF (Bayesian Interchange Format) files to perform inference using both exact and approximate algorithms.

## Project Overview

The engine provides a framework for representing Bayesian Networks as objects consisting of Nodes, Factors, and CPTs. It handles complex networks and provides probability distributions for query variables given specific evidence.

### Implemented Algorithms

* **Variable Elimination (VE)**: An exact inference algorithm that uses a min-degree heuristic for elimination ordering. It performs factor restriction based on evidence, factor multiplication, and marginalization.
* **Gibbs Sampling**: An approximate inference algorithm using Markov Chain Monte Carlo (MCMC). It utilizes forward sampling for initialization and Markov Blanket sampling to generate states. The implementation supports burn-in periods and multiple runs to average results.

## Technical Components

* **Factor Class**: Manages probability tables and supports operations like factor multiplication and marginalization.
* **BayesNet and Node Classes**: Maintain the network topology, parent-child relationships, and conditional probability tables.
* **BIF Integration**: Uses the `pgmpy` library to parse standard `.bif` files into the custom internal network structure.
* **Min-Degree Heuristic**: Optimizes Variable Elimination by selecting the variable appearing in the fewest factors to minimize intermediate factor sizes.

## Prerequisites

Ensure you have the following dependencies installed:

* Python 3.x
* pgmpy
* itertools
* numpy

You can install the primary dependency via pip:
`pip install pgmpy`

## Repository Structure

* **InferenceEngine.py**: The main Python script containing the classes and algorithms.
* **test_cases.md**: A detailed document containing standardized parameters and scenarios for Child, Alarm, Insurance, and Win95pts networks.
* **networks/**: A directory where your `.bif` files should be stored.

## How to Run

The script is configured via parameters at the top of the file. Follow these steps to perform inference:

1. **Set Parameters**: Update the following variables in the configuration section of the script:
   * **ALGORITHM**: Set to 've' for Variable
