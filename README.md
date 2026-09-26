# ⬡ Private Credit BDC Analytics Suite

A self-contained, browser-based analytics platform designed to monitor private credit portfolios, analyze multi-manager overlap, and track credit risk across major Business Development Companies (BDCs).

🔗 **Live Application:** [grishmagarg.github.io/bdc-credit-analytics](https://grishmagarg.github.io/bdc-credit-analytics/?utm_source=gemini)

*(Runs 100% client-side in your browser — zero installation, servers, or environment setup required.)*

---

## 📌 What Is This Project?

### The Context

Business Development Companies (BDCs) like Blackstone Private Credit Fund (BCRED), Apollo Debt Solutions (ADS), and Blue Owl Credit Income Corp (OCIC) originate and manage tens of billions in direct private loans. Every quarter, they disclose every portfolio asset in regulatory SEC filings known as the **Schedule of Investments (SOI)**.

These filings detail every held credit, including par amount, cost basis, carrying fair value, maturity, and investment class.

### The Analytical Challenge

For institutional allocators, investment committees, and risk surveillance teams:

* Disclosures span thousands of line items with conflicting naming styles across GPs for identical corporate borrowers.
* Computing shared debtor exposure and co-investment concentrations across multiple mega-cap funds requires cumbersome, manual spreadsheet mapping.
* Spotting valuation divergence—where one GP marks a shared borrower down while another keeps it carried near par—is slow and prone to error.

### What This Dashboard Delivers

This suite ingests and standardizes multi-quarter SOI data directly in the browser to deliver:

1. **Multi-Fund Overlap Intelligence:** Pinpoints co-invested credits held by $\ge 2$ funds, calculating total Fair Value, Par exposure, and single-borrower portfolio weightings.
2. **Pairwise Overlap Heatmaps:** Computes bidirectional $N \times N$ matrices tracking shared asset concentration across any pair of funds (by Fair Value % and position count).
3. **Level 3 Debt Impairment Surveillance:** Evaluates stressed and non-performing debt positions across customizable valuation bands ($\le 70\%$, $\le 80\%$, $\le 90\%$ of cost) benchmarked as a percentage of total assets.
4. **Cross-Manager Pricing Divergence:** Tracks quarterly Fair Value-to-Par trajectories to detect early warning credit distress and marking dispersion.

---

## ⚡ 10-Second Quickstart (Zero-Download Live Run)

You do not need to download files or configure an environment. Run the entire platform live with one click:

1. **Open the App:** Navigate to **[grishmagarg.github.io/bdc-credit-analytics](https://grishmagarg.github.io/bdc-credit-analytics/?utm_source=gemini)**.
2. **Load Sample Data:** Click the **⚡ Load Sample Data** button in the header/upload panel. The app automatically fetches and populates pre-structured multi-quarter datasets (~11,000+ total loan positions across 10 flagship BDCs) directly into memory.
3. **Scan & Analyze:** Click **⊙ Scan Files & Detect Funds** to populate the comparative analytics engine.

---

## 🧭 Exploring the Analytical Modules

Once the data is scanned, navigate through the suite using the top tab bar:

### 1. 🔍 Overlap Analysis

* **How to use:** Select 2 to 5 funds from the dropdowns, confirm your **Primary Quarter**, and click **Analyze Overlaps**.
* **What you see:** A unified balance sheet view displaying every shared borrower, combined exposure, and color-coded **Fair Value / Par %**:
* 🔴 **< 90%:** Stressed positions / marked below par.
* 🟡 **90% – 100%:** Watchlist / performing near par.
* 🟢 **> 100%:** Premium / PIK accumulation.
* **Summary KPI Cards:** Instant metrics on overlapping names, total overlap Fair Value, divergent marks ($>5\text{ pp}$ spread), and single-borrower portfolio concentrations.



### 2. 📊 Overlap Matrices

* **How to use:** Select any quarter and click **Run Overlap Matrices**.
* **What you see:** Dynamic relative heatmaps quantifying bilateral portfolio overlap across three lenses:
1. Fair value overlap as a % of row fund
2. Number of overlapping companies
3. Overlapping companies as a % of row fund portfolio count



### 3. 🛡️ Level 3 Debt Surveillance

* **How to use:** Select funds, toggle target quarters, define threshold bands (defaults: $\le 70\%$, $\le 80\%$, $\le 90\%$ of cost), and click **Run Level 3 Debt**.
* **What you see:** Aggregates cumulative stressed debt exposure expressed as a percentage of total fund assets across consecutive quarters, tracking asset-quality deterioration over time.

### 4. 📈 Pricing Trend & Valuation Chart

* **Pricing Trend:** Tracks quarter-over-quarter drift ($\Delta$) in loan marks across the peer group to spotlight deteriorating assets.
* **Valuation Chart:** Select any individual borrower from the global universe and up to 10 funds to view multi-quarter line charts comparing how each manager values the credit over time.

---

## 📁 Uploading Custom SOI Data

You can also evaluate your own proprietary or non-BDC portfolio files. Click **↓ Download Template** to download a standardized format. The platform requires only six standard columns:

* `BDC Name` — Name of the credit vehicle/fund
* `Normalize Name` — Clean company/borrower name (legal suffixes stripped)
* `Industry` — Industry or sector classification
* `Par Amount ($M)` — Par/notional value in millions
* `Cost ($M)` — Cost basis in millions
* `Fair Value ($M)` — Carrying fair value in millions

*(A single workbook can contain multiple funds—the system parses and separates them automatically).*

---

## 🔒 Security & In-Browser Processing

* **100% Client-Side Execution:** All parsing, entity normalization, and matrix computations run locally in your browser memory via SheetJS (`xlsx.js`) and Chart.js.
* **Zero Data Transmission:** No uploaded files, portfolio holdings, or calculated values are ever sent to, processed by, or stored on an external server.
