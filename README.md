# Dynamic Trading with Predictable Returns & Transaction Costs
Quantitative Finance | Portfolio Optimization | Reinforcement Learning

Capstone Project — MS Financial Engineering  
Stevens Institute of Technology

This project implements the dynamic trading framework proposed by **Gârleanu & Pedersen (2013)** to study portfolio allocation under predictable returns and transaction costs. The analytical framework is extended with a **Reinforcement Learning (PPO)** trading agent to explore adaptive portfolio strategies.

---

## Research Objective

Evaluate whether **dynamic portfolio rebalancing** improves performance relative to classical static allocation strategies.

Key goals:

- Implement the **Gârleanu–Pedersen dynamic trading framework**
- Model signal persistence using **VAR(1)**
- Compare dynamic allocation against **Markowitz and Equal-Weight portfolios**
- Explore **Reinforcement Learning** as an adaptive trading strategy

---

## Dataset

The analysis uses widely studied empirical asset pricing datasets.

- Fama-French factor dataset (including the Momentum factor)
- 10 Fama-French Industry Portfolios

Period: **1963 – 2024**

---

## Methodology

The modeling pipeline consists of:

1. Factor-based return prediction using **Fama-French signals**
2. Signal persistence modeling using **VAR(1)**
3. Covariance estimation using **Ledoit-Wolf shrinkage**
4. Dynamic portfolio optimization with **transaction costs**
5. Reinforcement Learning trading agent using **PPO**

---

## Dynamic Trading Framework

The Gârleanu–Pedersen model determines how a portfolio should adjust over time when trading is costly.

Instead of instantaneously rebalancing to the frictionless Markowitz optimal portfolio, the strategy **gradually moves toward a target allocation ("aim portfolio")**, reducing excessive turnover and transaction costs.

The dynamic trading strategy follows the framework proposed by Gârleanu & Pedersen (2013).  
Instead of rebalancing fully to the optimal Markowitz portfolio each period, the portfolio
moves gradually toward a target allocation in order to control transaction costs.

The portfolio update rule can be expressed as:

x_{t+1} = (1 - κ) x_t + κ Aim_t

where:

- x_t = current portfolio weights
- Aim_t = target (Markowitz) portfolio based on expected returns
- κ = trading rate controlling how quickly the portfolio moves toward the target

This **partial adjustment mechanism** balances expected return against transaction costs and
reduces excessive portfolio turnover.

The target portfolio ("aim") is the frictionless optimal allocation:

Aim_t = Σ⁻¹ μ_t

where:

- μ_t = expected return vector
- Σ = covariance matrix of asset returns

---

## Key Techniques

- Dynamic Portfolio Optimization  
- Transaction Cost Modeling  
- Factor-Based Return Prediction  
- VAR(1) Signal Dynamics  
- Ledoit–Wolf Covariance Shrinkage  
- Reinforcement Learning (PPO)  
- Portfolio Backtesting

---

## Strategy Performance (Risk Aversion γ = 3)

| Strategy | Annual Return (%) | Volatility (%) | Sharpe Ratio |
|----------|------------------|---------------|--------------|
| Dynamic Strategy | 14.3 | 20.7 | 0.69 |
| Markowitz Portfolio | 10.4 | 13.0 | 0.80 |
| RL Strategy (PPO) | 14.1 | 21.7 | 0.65 |

The dynamic trading strategy achieves higher cumulative returns, while the Markowitz portfolio exhibits a higher Sharpe ratio due to lower volatility. The reinforcement learning strategy shows comparable performance.

---

## Key Findings

- Dynamic trading produces higher cumulative returns than static Markowitz allocation.
- Transaction cost modeling leads to more realistic trading behavior.
- Reinforcement learning provides comparable performance in adaptive portfolio allocation.

---

## Repository Structure

```
dynamic-trading-portfolio-optimization

data/
    dataset_fama_french_industry_returns.csv

report/
    dynamic_trading_capstone_report.pdf

presentation/
    dynamic_trading_capstone_presentation.pptx
```

---

## Tech Stack

- Python  
- NumPy  
- Pandas  
- CVXPY  
- Gymnasium  
- Stable-Baselines3  
- Matplotlib

---

## Reference

Gârleanu, N., & Pedersen, L. H. (2013).  
**Dynamic Trading with Predictable Returns and Transaction Costs**  
Journal of Finance.          
