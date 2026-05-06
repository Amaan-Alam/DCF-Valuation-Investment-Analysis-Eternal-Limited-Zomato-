# **Eternal Limited (formerly Zomato) – DCF Valuation Model**

## <u>Executive Summary</u>
This repository contains a comprehensive three-scenario Discounted Cash Flow (DCF) valuation of **Eternal Limited** (NSE: ETERNAL, formerly Zomato). The model derives the intrinsic equity value per share as of **5 May 2026** using the Free Cash Flow to Firm (FCFF) methodology over a 10‑year explicit forecast (FY26E–FY35E) and a Gordon Growth terminal value.

**Key Result:**  
- **Probability‑weighted implied share price:** ₹157.84 (vs. current market price of ₹251.00)  
- **Weighted upside/(downside):** –37.1% → **Recommendation: SELL**  

The market appears to price in an optimistic scenario that is significantly above the model’s probability‑blended intrinsic value.

## <u>File Structure</u>


## *Model Architecture & Methodology*

The valuation follows a standard **FCFF → Enterprise Value → Equity Value** framework:
1. Segment‑level revenue and margin projections for Food Delivery, Hyperpure (B2B), Quick Commerce (Blinkit), Going Out, and Others.
2. Derivation of unlevered free cash flows (NOPAT + D&A – Capex – Δ NWC).
3. Discounting explicit period FCFFs at the case‑specific WACC.
4. Adding a terminal value (Gordon Growth Model) discounted back to the valuation date.
5. Adjusting for net debt (debt – cash) to arrive at equity value; dividing by shares outstanding gives the implied price per share.

The model is built in three parallel, independent scenario engines: **Base**, **Optimistic**, and **Pessimistic**, each with its own set of drivers.

### *1. Key Drivers & Assumptions*
Each scenario is governed by a distinct set of growth, margin, and capital‑efficiency assumptions. The most critical inputs are:

| Assumption | Base | Optimistic | Pessimistic |
|------------|------|------------|-------------|
| Quick Commerce (Blinkit) revenue CAGR (FY25‑35) | ~39% | ~48% | ~27% |
| Hyperpure (B2B) revenue CAGR | ~30% | ~38% | ~21% |
| Food Delivery revenue CAGR | ~14% | ~17% | ~10% |
| Blinkit terminal EBITDA margin | 15.0% | 19.0% | 11.0% |
| Hyperpure terminal EBITDA margin | 5.0% | 7.0% | 3.0% |
| Total revenue CAGR (FY25‑FY35) | 27.3% | 35.7% | 19.6% |
| FY35E Consolidated Adj. EBITDA margin | 14.0% | 19.9% | 11.0% |

Other key drivers:  
- **Share‑based payment expense** declines gradually as a % of revenue.  
- **Capex intensity** decreases from 5.5% to 3.5% of revenue over the forecast.  
- **NWC investment** is modelled as a % of incremental revenue.  
- **Effective tax rate** ramps from 0% to the statutory 25.17% over the forecast.

### *2. Discount Rate (WACC)*
WACC is built from a CAPM‑based cost of equity and after‑tax cost of debt, weighted by target capital structure:

**Cost of Equity:**  

$$
\text{Cost of Equity} = R_f + \beta \times \text{ERP}
$$

**WACC Formula:**  

$$
\text{WACC} = (E/V) \times \text{Cost of Equity} + (D/V) \times \text{After-tax Cost of Debt}
$$


| Parameter | Base | Optimistic | Pessimistic |
|-----------|------|------------|-------------|
| Risk‑free rate ($R_f$)  | 7.00% | 7.00% | 7.00% |
| Equity Risk Premium (ERP) | 6.75% | 6.75% | 6.75% |
| Levered Beta ($\beta$) | 0.90 | 0.75 | 1.10 |
| Cost of Equity | 12.40% | 12.06%* | 14.43% |
| After‑tax Cost of Debt | 6.73% | 6.73% | 6.73% |
| Debt weight (D/V) | 0.85% | 0.85% | 0.85% |
| **WACC** | **13.02%** | **12.02%** | **14.36%** |

*(Note: The Optimistic cost of equity in the model yields 12.02% WACC after weighting; the exact cost of equity rounds slightly differently due to internal cell precision – the final WACC is correct as per model.)*

### *3. Terminal Value*
Terminal value is calculated using the **Gordon Growth Model** applied to the final year’s FCFF (FY35E) grown at the perpetual rate:


$$ \text{Terminal Value} = \frac{\text{FY35E FCFF} \times (1 + g)}{\text{WACC} - g} $$


| Scenario | Terminal Growth ($g$) | Terminal Value (₹ Cr) | PV of Terminal Value (₹ Cr) |
|----------|--------------------------|-----------------------|----------------------------|
| Base | 5.0% | 1,72,186 | 50,629 |
| Optimistic | 6.0% | 5,71,743 | 1,99,782 |
| Pessimistic | 4.0% | 29,702 | 9,750 |

Terminal value dominates total Enterprise Value (typically 60–80%), making the valuation highly sensitive to both WACC and the perpetual growth rate.

## <u>Key Outputs</u>

### *Scenario Valuation Bridge (INR Crores)*
| Valuation Component | Base | Optimistic | Pessimistic |
|---------------------|------|------------|-------------|
| PV of Explicit FCFF | 17,974 | 58,700 | (645) |
| PV of Terminal Value | 50,629 | 1,99,782 | 9,750 |
| **Enterprise Value** | **68,603** | **2,58,482** | **9,105** |
| Less: Total Debt | (2,045) | (2,045) | (2,245) |
| Plus: Cash & Investments | 16,806 | 16,806 | 16,806 |
| **Equity Value** | **83,364** | **2,73,243** | **23,866** |

### *Per‑Share Results*
| Scenario | Implied / Share (₹) | Upside / (Downside) | Probability Weight |
|----------|---------------------|---------------------|-------------------|
| Base | 87.61 | –65.1% | 40% |
| Optimistic | 287.17 | +14.4% | 35% |
| Pessimistic | 25.08 | –90.0% | 25% |
| **Probability‑Weighted** | **157.84** | **–37.1%** | **100%** |

**Investment Rule:** BUY if weighted upside ≥ +15%, HOLD if 0% to +15%, REDUCE if –15% to 0%, SELL if < –15%.  
→ Current recommendation: **SELL**

*The active scenario toggle in the Excel model is set to **Optimistic** (hence the Cover sheet shows BUY), but the probability‑weighted view drives the final signal.*

## <u>Sensitivity Analysis</u>
The model includes two‑way data tables (Sheet: **Sensitivity**) that illustrate how the Base‑case implied share price changes with variations in **WACC** and **terminal growth rate**, and with **WACC** and **terminal EBITDA margin**.

**Key observations:**  
- A 100 bps increase in WACC (from 13% to 14%) reduces the Base‑case implied price by ~13%.  
- A 100 bps increase in terminal growth (5% → 6%) raises the price by ~9%.  
- To justify the current market price of ₹251, the market must assume a WACC below 11%, a terminal growth rate above 7%, or a terminal EBITDA margin well above 18% — all well outside the Base‑case corridor.

## <u>How to Use the Model</u>
1. **Switch the Active Scenario:**  
   - Open `Eternal.xlsx`, go to the **Summary** sheet.  
   - Change cell **F5** to `1` (Base), `2` (Optimistic), or `3` (Pessimistic).  
   - The **DCF**, **Sensitivity**, and **Cover** sheets recalculate instantly.

2. **Customize Probability Weights:**  
   - On the **Summary** sheet, adjust cells **B45** (Base), **D45** (Optimistic), and **F45** (Pessimistic).  
   - Ensure the sum equals 100% (cell B46 checks this). The weighted equity value and implied per share update automatically.

3. **Flex Assumptions:**  
   - Go to the **Assumptions** sheet.  
   - Edit the case‑specific growth and margin drivers in the lower section (rows 56–107). The **Scenarios** sheet picks them up via the toggle.  
   - Alternatively, change inputs directly in the **Scenarios** sheet for a quick over‑ride (not recommended for permanent changes).

4. **Interpret Sensitivity Tables:**  
   - The **Sensitivity** sheet uses Excel Data Tables. After changing inputs, ensure they are recalculated (press `F9` if needed). The interpretation notes at the bottom guide the user on what combinations justify the current market price.

## <u>Sources & References</u>
- Eternal Limited (formerly Zomato) Annual Reports FY22–FY25  
- NSE/BSE filings  
- Management commentary (Q4 FY26)  
- Brokerage and industry research  
- Risk‑free rate: 10‑year Indian G‑Sec as of valuation date  




*Disclaimer: This model is prepared for educational and analytical purposes only. It does not constitute investment advice, a recommendation, or a solicitation to buy or sell any security. All projections are based on subjective assumptions and may differ materially from actual outcomes*
