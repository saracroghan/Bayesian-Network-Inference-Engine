# Bayesian Network Inference Engine

This project is a Python implementation of a probabilistic inference engine for Bayesian Networks. It allows users to load network structures and conditional probability tables from BIF (Bayesian Interchange Format) files and perform inference using two primary algorithms: Variable Elimination and Gibbs Sampling.

## Project Overview

The engine provides a framework for representing Bayesian Networks as objects consisting of Nodes, Factors, and CPTs. It is designed to handle complex networks and provide accurate probability distributions for query variables, with or without observed evidence.

### Implemented Algorithms

* **Variable Elimination (VE)**: An exact inference algorithm that uses a min-degree heuristic for elimination ordering. It performs factor restriction based on evidence, factor multiplication, and marginalization to compute results.
* **Gibbs Sampling**: An approximate inference algorithm (Markov Chain Monte Carlo). It uses forward sampling for initialization and a Markov Blanket sampling method to generate states. The implementation supports burn-in periods and multiple runs to ensure convergence and average out results.

## Technical Components

* **Factor Class**: Manages probability tables, supporting operations such as factor multiplication and marginalization via cartesian products.
* **BayesNet and Node Classes**: Structures that maintain the network topology, including parent-child relationships and individual conditional probability tables.
* **BIF Integration**: Utilizes the pgmpy library to parse standard .bif files into the custom internal Bayesian Network structure.
* **Min-Degree Heuristic**: Optimizes the Variable Elimination process by selecting the variable appearing in the fewest factors to minimize the size of intermediate factors.

## Prerequisites

Before running the project, ensure you have the following dependencies installed:

* Python 3.x
* pgmpy
* itertools
* numpy
* csv
* os

You can install pgmpy using pip:
pip install pgmpy

## Repository Structure

* **InferenceEngine.py**: The main Python script containing the classes and algorithms.
* **networks/**: A directory containing sample .bif files (e.g., child.bif) used for testing the network structure.
* **results/**: The default output location for generated CSV reports.

## How to Run

The script is configured via a set of parameters located at the top of the file. Follow these steps to perform inference:

1. **Set Parameters**: Open the script and update the following variables in the configuration section:
   * **ALGORITHM**: Set to 've' for Variable Elimination or 'gibbs' for Gibbs Sampling.
   * **NETWORK_NAME**: Provide the path to your .bif file.
   * **REPORT**: List the names of the variables you wish to query, separated by semicolons.
   * **EVIDENCE**: Provide observed evidence in the format 'Variable=Value', separated by semicolons (e.g., 'LungCancer=Yes;Smoker=True').
   * **EVIDENCE_LEVEL**: A label used for the output filename (e.g., 'None', 'Low', 'High').

2. **Execute the Script**: Run the code block or script.
   python InferenceEngine.py

3. **Output**: The results will be exported as a CSV file following the naming convention: 
   {GROUP_ID}_{ALGORITHM}_{NETWORK_NAME}_{EVIDENCE_LEVEL}.csv

The CSV file contains the variable names, their domain values, and the calculated probability distributions.

## Authors
* Jada Zorn
* Sara Croghan
