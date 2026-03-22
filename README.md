# Quantum Portfolio Optimizer — Day 12

<div align="center">

![IBM Quantum](https://img.shields.io/badge/IBM%20Quantum-052FAD?style=flat-square&logo=ibm&logoColor=white)
![Qiskit](https://img.shields.io/badge/Qiskit-6929C4?style=flat-square&logoColor=white)
![Yahoo Finance](https://img.shields.io/badge/Yahoo%20Finance-720E9E?style=flat-square&logoColor=white)
![Python 3.10](https://img.shields.io/badge/Python%203.10-1a1a2e?style=flat-square&logo=python&logoColor=4fc3f7)
![Day 12](https://img.shields.io/badge/Day%2012-Complete-4fc3f7?style=flat-square)
![Day 13](https://img.shields.io/badge/Day%2013-Streamlit%20App-00ff88?style=flat-square)

</div>

<br/>

<div align="center">
<i>Part of the IBM Quantum 20-Day Learning Sprint · VIT Chennai</i>
</div>

---

## Overview

This notebook applies **QAOA (Quantum Approximate Optimization Algorithm)** to real-world portfolio optimization using live stock data from Yahoo Finance. It compares the quantum approach against the classical Markowitz model on four major tech stocks.

| Method | Approach | Best Portfolio | Score |
|--------|----------|---------------|-------|
| Classical Markowitz | Continuous weights | AAPL 60% · GOOGL 22% · AMZN 18% | Sharpe 2.31 |
| QAOA | Binary selection | GOOGL alone | 0.5784 |

---

## The Problem

Given a set of assets, find the allocation that maximizes returns while minimizing risk.

```
Classical (Markowitz):
  maximize  w^T·μ - q·w^T·Σ·w
  subject to: Σwᵢ = 1, wᵢ ≥ 0

QAOA (binary):
  select which stocks to include
  |1⟩ = buy · |0⟩ = skip
  2^N combinations explored in superposition
```

---

## Data

Real daily closing prices from Yahoo Finance — 2023.

| Stock | Annual Return | Role |
|-------|-------------|------|
| AAPL | 46.24% | Stable growth |
| GOOGL | 50.14% | High growth |
| MSFT | 49.69% | Balanced |
| AMZN | 63.29% | Best performer |

```
Period       : 2023-01-01 to 2024-01-01
Trading days : 250
Source       : Yahoo Finance (yfinance)
```

---

## Results

### Classical Markowitz

```
Optimal weights:
  AAPL  :  60.39%
  GOOGL :  21.82%
  MSFT  :   0.00%  ← excluded
  AMZN  :  17.79%

Expected return :  50.57%
Portfolio risk  :  19.75%
Sharpe ratio    :   2.3079
```

### QAOA Top Solutions

```
Portfolio              Count   Score
──────────────────────────────────────
AAPL+GOOGL+MSFT+AMZN    754   0.4991
AAPL+GOOGL+AMZN         163   0.5073
GOOGL+AMZN               10   0.5314
GOOGL alone               —   0.5784  ← best score
```

---

## Tech Stack

```python
qiskit              >= 2.0.0
qiskit-aer          >= 0.17.2
qiskit-algorithms   >= 0.3.0
yfinance            >= 0.2.0
scipy               >= 1.10.0
matplotlib          >= 3.7.0
numpy               >= 1.24.0
pandas              >= 2.0.0
```

---

## Setup

```bash
git clone https://github.com/Akhila707/IBM-Quantum-FoundationsDay12.git
cd IBM-Quantum-FoundationsDay12
pip install -r requirements.txt
jupyter notebook
```

---

## Project Structure

| Path | Description |
|------|-------------|
| `notebooks/01_quantum_portfolio.ipynb` | Main experiment notebook |
| `results/stock_performance.png` | Stock price history + returns |
| `results/portfolio_comparison.png` | Markowitz · QAOA · convergence |
| `data/stock_prices.csv` | Downloaded prices (gitignored) |

---

## Sprint Progress

```
Day 01  ──  ✅  Qiskit setup · Hello Quantum
Day 02  ──  ✅  Superposition · Entanglement
Day 03  ──  ✅  Gates deep-dive · Grover's
Day 04  ──  ✅  VQE · COBYLA optimizer
Day 05  ──  ✅  QAOA · MaxCut
Day 06  ──  ✅  Quantum Error Mitigation · ZNE
Day 07  ──  ✅  Real IBM hardware · ibm_torino
Day 08  ──  ✅  QSVM · ZZFeatureMap
Day 09  ──  ✅  VQC · Variational Classifier
Day 10  ──  ✅  Project 1 · QML Classifier · MNIST
Day 11  ──  ✅  Quantum-Safe Cryptography · LWE
Day 12  ──  ✅  Quantum Portfolio · QAOA · real stock data
Day 13  ──  ✅  Project 2 · Streamlit app · deployed
·
·
Day 20  ──  ·   Final push · 
```

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Akhila707-181717?style=flat-square&logo=github)](https://github.com/Akhila707)
&nbsp;·&nbsp;
[![IBM Quantum](https://img.shields.io/badge/IBM%20Quantum-052FAD?style=flat-square&logo=ibm&logoColor=white)](https://quantum.ibm.com)

</div>
