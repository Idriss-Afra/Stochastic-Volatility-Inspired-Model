# Stochastic Volatility Inspired Model

A quantitative finance repository focused on constructing the equity implied volatility surface under the **Stochastic Volatility Inspired (SVI)** model.

This project calibrates the **SVI parameterization** to market implied volatilities while enforcing practical no-arbitrage conditions across strikes and maturities.

---

## Repository Structure

```text
Stochastic-Volatility-Inspired-Model/
├── Stochastic Volatility Inspired Model.ipynb
└── MarketData/
    ├── CAC40_MarketData_12022025.csv
    └── EURIBOR6M_ZCRates_12022025.csv
```

---

## Project Overview

This notebook focuses on fitting the **equity implied volatility surface** using the **SVI model**.

For each expiry, the model represents total implied variance as a function of log-moneyness through five parameters:

* **a** — overall variance level
* **b** — wing slope intensity
* **rho** — skew asymmetry
* **m** — horizontal shift
* **sigma** — local curvature scale

The workflow includes:

* SVI slice-by-slice calibration
* constrained optimization of the five SVI parameters
* butterfly arbitrage checks
* calendar arbitrage checks
* parameter bounds for numerical stability
* smart initial guess construction for calibration efficiency

---

## Arbitrage Constraints

The notebook is not limited to fitting market quotes. It also checks that the calibrated surface remains consistent with standard no-arbitrage conditions.

### Butterfly Arbitrage

For each expiry slice, the calibration verifies that the implied total variance curve is free of **butterfly arbitrage**, meaning the associated risk-neutral density remains non-negative across strikes.

### Calendar Arbitrage

Across maturities, the notebook verifies that total variance is **non-decreasing with expiry**, preventing **calendar spread arbitrage**.

---

## Market Data

The `MarketData/` folder includes:

* `CAC40_MarketData_12022025.csv` — market option data used for the SVI calibration
* `EURIBOR6M_ZCRates_12022025.csv` — zero-coupon rates used for discounting and forward-related calculations

Users can replace the sample input files with their own market data, provided that the CSV files keep the same structure as the ones included in `MarketData/`.
To run the notebook correctly, the current column layout and overall file format must be respected.

---

## Example Output

**CAC40 Implied SVI Volatility Surface**:

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/8c9b39fa-abfc-46d5-9c9e-42a2f34f53d5" />

**CAC40 Implied SVI Total Variance Surface**:

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/5484ab76-0bcc-4a2a-97e7-62f8a1576ea7" />

---

## Best use case

Use this notebook when working with **equity option market data** and building a **smooth, arbitrage-free implied volatility surface** under the SVI framework.

---

## How to Use

Clone the repository:

```bash
git clone https://github.com/Idriss-Afra/Stochastic-Volatility-Inspired-Model.git
cd Stochastic-Volatility-Inspired-Model
jupyter notebook
```

Then open:

* `Stochastic Volatility Inspired Model.ipynb`

---

## Author

**Idriss Afra**
