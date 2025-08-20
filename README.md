# Portfolio Optimization using Coherent Measures of Risk

## Overview
This project focuses on portfolio optimization using **Coherent Measures of Risk**, such as Conditional Value at Risk (CVaR) and Mean Semi Deviation at Risk (MAD). The goal is to construct an optimal portfolio by minimizing risk while maximizing expected returns, leveraging modern optimization techniques and financial risk modeling.

## Features
- **Implementation of Coherent Risk Measures:** Incorporates CVaR, Mean-Semideviation, and Mean-Variance models.
- **Data Processing:** Handles financial time-series data, computing returns.
- **Optimization Techniques:** Utilizes convex optimization  for portfolio allocation.
- **Backtesting Framework:** Evaluates the performance of optimized portfolios against historical data.
- **Efficient Computation:** Leverages libraries such as **NumPy, SciPy, and CVXPY** for performance-efficient calculations.

## Portfolio Optimization Models
### 1. **Mean-Variance Optimization (MVO)**
- Seeks to minimize **variance** while maximizing expected returns.
- Formulated as:
  $\[\min_w w^T \Sigma w \quad \text{subject to} \quad w^T r \geq \mu, \quad \sum w_i = 1, \quad w_i \geq 0\]$
  where:
  - **w** = portfolio weights
  - **r** = expected returns
  - **Σ** = covariance matrix of returns
  - **μ** = target return

### 2. **Mean-CVaR Optimization**
- Focuses on minimizing **Conditional Value at Risk (CVaR)**, which measures expected loss beyond a given quantile.
- Formulated as:
  $\[\max_w \mathbb{E}[w^T r] - \chi \cdot \text{CVaR}_\alpha(w) \quad \text{subject to} \quad \sum w_i = 1, \quad w_i \geq 0\]$
  where:
  - **CVaR_α(w)** is the expected shortfall at confidence level **α**.
  - **χ** is a risk aversion parameter balancing mean return and risk.



### 3. **Mean-Semideviation Optimization**
- Uses **semideviation** to capture downside risk below the mean return.
- Defined as:
  $\[\sigma_-(w) = {-\mathbb{E}[w^T r]  + \chi \frac{1}{N} \sum_{t=1}^{N} \max(0, R_t - \bar{R})}\]$
  where **R_t** is portfolio return at time **t** and **\bar{R}** is the mean return.

- Formulated as:
  $\[\min_w \sigma_-(w) \quad \text{subject to} \quad w^T r \geq \mu, \quad \sum w_i = 1, \quad w_i \geq 0\]$

### **Comparison Table**
| Model               | Risk Measure | Captures Downside Risk? | Computational Complexity |
|--------------------|-------------|-------------------------|-------------------------|
| Mean-Variance      | Variance     | ❌ No                   | ✅ Quadratic Programming |
| Mean-CVaR         | CVaR         | ✅ Yes                  | ✅ Linear Programming |
| Mean-Semideviation | Semideviation | ✅ Yes                  | ✅ Linear Programming |

## Installation
To set up the project, clone the repository and install dependencies:
```bash
git clone https://github.com/your-username/portfolio-optimization.git
cd portfolio-optimization
pip install -r requirements.txt
```



### Example Notebook
An interactive Jupyter Notebook is included to demonstrate portfolio optimization:
```bash
jupyter notebook simulation.ipynb
```

## Dependencies
- Python 3.x
- NumPy
- SciPy
- Pandas
- Matplotlib
- CVXPY

## Results and Visualization
- Portfolio weight distribution
- Performance metrics (Sharpe ratio, drawdown, etc.)
