# Bayesian Network Inference Engine: Test Cases and Solutions

This document provides a set of standardized test cases to verify the performance and accuracy of both the **Variable Elimination (VE)** and **Gibbs Sampling** implementations. These cases cover a range of network sizes and complexity levels.

## Testing Setup

To run these tests, ensure your `NETWORK_NAME` parameter points to the correct location of the `.bif` files and adjust the configuration variables in the main script as indicated for each case.

---

## 1. Child.bif (Medical Diagnosis)
**Network Size:** 20 Nodes
* **Query Variable (REPORT)**: `Disease`
* **Evidence (EVIDENCE)**: `BirthAsphyxia=yes;LowerBodyCP=yes`
* **Evidence Level**: `High`
* **Scenario**: Diagnostic inference where observed physical symptoms are used to predict the underlying disease.
* **Expected Result**: The probability for `CongenitalHeartPPD` or `LungDisease` should increase significantly compared to their prior probabilities. Both algorithms should show strong agreement on the distribution.

## 2. Alarm.bif (Emergency Medicine Monitoring)
**Network Size:** 37 Nodes
* **Query Variable (REPORT)**: `Anaphylaxis`
* **Evidence (EVIDENCE)**: `BP=low;HR=high`
* **Evidence Level**: `High`
* **Scenario**: Monitoring vital signs to detect rare but critical medical events.
* **Expected Result**: While the prior probability of `Anaphylaxis` is extremely low, the combination of low blood pressure and high heart rate should cause a sharp spike in its probability.

## 3. Insurance.bif (Vehicle Insurance Risk)
**Network Size:** 27 Nodes
* **Query Variable (REPORT)**: `PropCost`
* **Evidence (EVIDENCE)**: `Age=Adolescent;RiskAversion=Adventurous;VehicleYear=Older`
* **Evidence Level**: `High`
* **Scenario**: Assessing financial risk (Property Cost) based on driver demographics and vehicle age.
* **Expected Result**: This high-risk combination should shift the `PropCost` distribution away from "Ten" or "Hundred" and toward the "Thousand" or "Million" categories.

## 4. Win95pts.bif (Windows 95 Print Troubleshooter)
**Network Size:** 76 Nodes
* **Query Variable (REPORT)**: `PrntApp`
* **Evidence (EVIDENCE)**: `DskSpsFree=low;NetSrv=not_responding`
* **Evidence Level**: `Medium`
* **Scenario**: Troubleshooting software failures based on system resource states.
* **Expected Result**: This is a large network used to test the efficiency of the **Min-degree heuristic**. The result should show a high probability of application-level printing errors (`PrntApp=No`).

---

## Verification Guide

### Exact Inference (Variable Elimination)
* **Normalization**: Ensure the sum of probabilities for the query variable domain equals exactly
