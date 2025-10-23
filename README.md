# 💎 Diamond Dataset Analysis: Power BI Technical Documentation

## 1. Project Objective and Data Architecture

This documentation details the implementation of a Power BI dashboard designed to perform granular analysis on the Diamond Dataset. The primary objective was twofold: to establish core market benchmarks and to perform **Anomaly Detection** regarding the traditional pricing hierarchy of the 4Cs (Carat, Clarity, Color, Cut).

**Data Model:** The project relies on a flat data model optimized for performance in Power BI. All calculations are handled via DAX measures to ensure flexibility.

## 2. Technical Implementation and DAX Utility

### A. Key Performance Indicators (KPIs) Implementation
The top four cards provide immediate market status.

| KPI | DAX Formula Utility | Strategic Utility |
| :--- | :--- | :--- |
| **Average of price** ($6.35K) | `AVERAGE('Diamond Data'[Price])` | Sets the baseline expectation for transaction value. |
| **Max of price** ($19K) | `MAXX('Diamond Data', 'Diamond Data'[Price])` | Identifies the highest price point, crucial for outlier examination in the scatter plot. |

### B. Average Price by Clarity (Bar Chart)
**Implementation:**
* **Visual:** Clustered Bar Chart.
* **Axes:** X-Axis: `Clarity` (Categorical), Y-Axis: `AVERAGE('Diamond Data'[Price])`.
**What it Reveals (Anomaly):** This chart is the project's centerpiece for **disproving the IF clarity hypothesis**. The visualization immediately highlights that **VS2** and **VS1** grades lead the average price metrics, directly challenging the assumption that IF (Internally Flawless) must be the most expensive. This informs **Pricing Strategists** to focus on true market demand points rather than academic perfection.

### C. Average Diamond Price by Color (Donut Chart)
**Implementation:**
* **Visual:** Donut Chart.
* **Values:** Slices are generated using `SUM('Diamond Data'[Carat])`.
* **Legend:** `Color` (G, H, I, J, E, F).
**What it Shows (Inventory & Sourcing):** By visualizing the total *carat weight* (volume) rather than just the *count* of diamonds, this visual guides **Sourcing Teams** to understand which colors (G and H) constitute the largest supply chain volume, optimizing procurement efficiency.

### D. Diamond Distribution by Cut (Bar Chart)
**Implementation:**
* **Visual:** Bar Chart.
* **Values:** `COUNTROWS('Diamond Data')`.
**What it Shows (Market Accessibility):** This provides a quick read on the market's abundance, showing that **Premium** and **Good** cuts are the most frequently traded segments, guiding inventory decisions on high-volume items.

### E. Carat vs. Price Relationship (Scatter Plot)
**Implementation:**
* **Visual:** Scatter Plot.
* **Axes:** X-Axis: `Carat`, Y-Axis: `Price`.
**What it Demonstrates (Model Validation):** This foundational chart validates the core **linear correlation** in diamond pricing (price increases with carat). Its critical utility lies in **visual outlier confirmation**, helping Data Science teams to review data points that fall far outside the trend line (e.g., extremely high-priced, low-carat stones) before building predictive models.

## 4. Strategic and Scientific Impact

The dashboard successfully serves as a robust BI tool, using visual evidence to:
1.  **Challenge Hypotheses:** Disproving the perfect clarity (IF) pricing theory.
2.  **Guide Investment:** Pointing toward high-demand, high-value segments (VS2, VS1, G/H colors).
3.  **Confirm Data Quality:** Using the scatter plot to visually check the data's integrity and correlation.
