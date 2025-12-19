# Data Centric AI

**Research Area:** Data-Centric Machine Learning, Vision-Language Models

## Key Contributions

- Analyzes information bottleneck in activation functions
- Proposes methods for learning from re-purposed and synthetic data
- Addresses data scarcity through creative data utilization

## 1. Information Bottleneck in Activation Functions

- **ReLU vs tanh:** ReLU has minimal information bottleneck compared to tanh
- **Problem:** Final layer still uses double-sided sigmoid, losing information
- **Solution:** Remove double-sided activation functions to reduce information bottleneck

## 2. Learning from Re-Purposed Data

**Goal:** Build Region-LVLM with regional understanding capabilities

**Challenge:** No direct region-caption paired datasets available

**Solution:**
- Found existing data where annotators described images while moving mouse cursor
- Re-purposed this data by processing mouse trajectories as region annotations
- Demonstrates using data from different tasks when target data is unavailable

## 3. Learning from Synthetic Data

**Problem:** Models poorly understand text negation; existing datasets contain meaningless negations

**Solution:** Generate synthetic data with meaningful negation examples

## 4. Industry Application: Amazon CreativeX

**Context:**
- Large companies can build dedicated teams for ad creation
- Small businesses lack resources to create creative assets

**Mission:** Help small businesses generate advertising assets through AI-powered tools

## Conclusions

Data-centric approaches offer practical solutions when ideal training data is unavailable—through re-purposing existing datasets, generating synthetic data, or reducing architectural information loss.
