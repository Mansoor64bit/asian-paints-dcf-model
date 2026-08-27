# Asian Paints Ltd — DCF Valuation Model

A Discounted Cash Flow (DCF) valuation model for **Asian Paints Ltd** (India's largest decorative paints company), built using the **Free Cash Flow to Firm (FCFF)** method. The model derives its own growth rate from ROIC and reinvestment history, builds a peer-based WACC, and outputs an intrinsic value per share against the current market price.

> 📊 Intrinsic value per share: **₹432.42** vs current market price of **₹2,839** (see [Notes](#notes--things-to-double-check) below for an important caveat on this number).

---

## 📁 What's in this repo

| File | Description |
|---|---|
| `Asian_Paints_DCF_Valuation_Model.xlsx` | The full Excel model — historical financials, WACC, growth, and DCF tabs. |
| `report/Asian_Paints_DCF_Valuation_Report.docx` | A written summary report (Word doc) walking through the methodology, key numbers, and conclusions. |
| `screenshots/` | PNG snapshots of the key tabs of the model, for quick viewing without opening Excel. |

---

## 🧮 What's inside the Excel model

The workbook has 8 tabs:

1. **HistoricalFS** – 10-year historical income statement, FY2017–FY2026, plus LTM.
2. **Raw FS** – Underlying balance sheet and cash flow source data.
3. **Intrisic Growth** – ROIC and Reinvestment Rate calculations used to derive the "intrinsic" growth rate.
4. **WACC** – Peer-comparable beta, cost of equity, cost of debt, and final WACC build-up.
5. **Rm** – Historical Indian equity market returns (used to derive the equity risk premium).
6. **Raw Beta Peers** – Peer company beta inputs.
7. **DCF** – The core valuation: FCFF forecast, terminal value, and equity value per share.
8. **Data Sheet** – Supporting raw data.

## 📈 Key outputs at a glance

| Metric | Value |
|---|---|
| Forecast period | FY2027F – FY2031F |
| Base year EBIT (FY2026) | ₹6,129.5 Cr |
| Expected growth (5-yr median intrinsic growth) | 23.54% |
| Terminal growth rate | 5.38% |
| WACC | 16.69% |
| Terminal Value | ₹78,689 Cr |
| Value of Equity | ₹41,661 Cr |
| **Intrinsic value per share** | **₹432.42** |
| Current market price | ₹2,839 |

## 🛠 How to use

1. Download `Asian_Paints_DCF_Valuation_Model.xlsx` and open it in Excel (or Google Sheets / LibreOffice).
2. Start at the **HistoricalFS** tab to see the base financials.
3. Check **Intrisic Growth** and **WACC** tabs to see how the growth rate and discount rate are built.
4. The **DCF** tab pulls everything together into the final valuation, and includes a built-in sensitivity table (WACC vs terminal growth).
5. All blue-font cells are hardcoded inputs/assumptions; black is formula-driven; green links to another sheet.
6. Read `report/Asian_Paints_DCF_Valuation_Report.docx` for a plain-English walkthrough with charts and commentary.

## 📝 Notes / things to double-check

This model was reviewed while packaging it for this repo, and a couple of things are worth flagging honestly rather than glossing over:

- **PV of FCFF summation:** the equity bridge on the DCF tab currently picks up only the *last* forecast year's discounted cash flow (cell `H11`) instead of the sum of all five years. Summing all five years would raise the intrinsic value to roughly **₹560–₹565/share** — still well below the market price, but worth fixing in the sheet for accuracy (cell `C26`, `DCF` tab).
- **Growth rate vs recent trend:** the 23.5% near-term growth assumption is a historical 5-year median. Actual sales growth was much lower in FY2024 (2.9%) and negative in FY2025 (-4.5%), so it may be worth testing a more conservative growth case.
- **Terminal value weight:** the terminal value makes up roughly 90%+ of total enterprise value, so small changes in WACC or terminal growth swing the output a lot — use the sensitivity table on the DCF tab to stress-test this.

None of this is a "fix" applied to the file — the model has been left exactly as uploaded. These are flagged for transparency so anyone using the model knows what to check first.

## ⚠️ Disclaimer

This is an educational financial model, not investment advice. Figures are based on historical company filings and the model author's own assumptions. Do your own research or consult a licensed financial advisor before making investment decisions.

---
*Built with a standard FCFF (Free Cash Flow to Firm) DCF framework: historical analysis → ROIC-driven growth → peer-based WACC → 5-year explicit forecast → Gordon Growth terminal value → equity bridge.*
