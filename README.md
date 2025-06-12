# Bayesian Skew-Normal Black-Litterman Model

This repository implements a Bayesian extension of the Black-Litterman model using **skew-normal priors** and **Metropolis-Hastings sampling** to infer posterior distributions over expected returns and optimal portfolio weights. The model captures **asymmetric investor beliefs**, enhancing traditional Black-Litterman portfolios with richer uncertainty modeling.

---

## 📌 Features

- **Skew-normal prior** on market-implied expected returns
- **Skew-normal likelihood** on subjective views (e.g., SPY = 7%)
- Metropolis-Hastings MCMC for full posterior inference
- Posterior mean and credible intervals for:
  - Expected returns (`μ`)
  - Optimal weights (allowing shorting)

---

## 📁 Files

| File                      | Description                                         |
|---------------------------|-----------------------------------------------------|
| `BlackLitterman_Skewed.R` | Main R script implementing the model                |
| `README.md`               | Project documentation                               |

---

## 🧠 Model Details

Let:

- $\mu \sim \text{SN}(\mu_{\text{mkt}}, \tau \Sigma, \alpha_0)$ 
  (prior on expected returns)

- \( P\mu \sim \text{SN}(q, \Omega, \alpha_1) \)  
  (investor views with skewness)

Then the posterior is:
\[
\pi(\mu \mid \text{data}) \propto \text{SN}(\mu; \mu_{\text{mkt}}, \tau \Sigma, \alpha_0) \cdot \text{SN}(P\mu; q, \Omega, \alpha_1)
\]

The model supports:
- Skewed priors and views
- Analytical prior + view formulation
- MCMC estimation using Metropolis sampling

---

## 📈 Assets and Views

- Tickers: `SPY`, `TLT`, `QQQ`, `GLD`, `EEM`
- Prior: Implied market equilibrium returns
- Views: Customizable via matrix `P`, targets `q`, and skewness `α₁`

---

## ⚙️ How to Run

### 1. Install dependencies:
```r
install.packages(c("quantmod", "dplyr", "xts", "moments", "lubridate", "MASS", "sn"))
