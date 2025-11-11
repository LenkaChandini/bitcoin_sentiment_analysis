# bitcoin_sentiment_analysis
bitcoin_sentiment_analysis

## 🧠 Junior Data Scientist – Trader Behavior Insights  
### 📊 Bitcoin Market Sentiment vs Trader Performance  

---

### 📁 Project Overview
This project analyzes how **Bitcoin market sentiment (Fear/Greed Index)** influences **trader performance** using historical trade data from **Hyperliquid**.  
The goal is to uncover hidden trading patterns, understand behavioral trends, and identify how emotions like fear and greed impact market profitability.  

---

### ⚙️ Datasets Used
1. **Historical Trader Data (Hyperliquid)**  
   - Columns: `account`, `symbol`, `execution_price`, `size`, `side`, `time`, `start_position`, `event`, `closedPnL`, `leverage`, etc.  

2. **Bitcoin Market Sentiment Dataset**  
   - Columns: `Date`, `Classification (Fear/Greed)`  

---

### 🧩 Step-by-Step Analysis Pipeline

#### 1️⃣ Data Loading and Cleaning
- Imported essential Python libraries: `pandas`, `numpy`, `seaborn`, `sklearn`, etc.  
- Standardized column names to lowercase and underscores.  
- Converted timestamps and date columns to proper datetime format.  
- Ensured numeric conversions for trade metrics (`execution_price`, `closed_pnl`, etc.) and verified data completeness.

---

#### 2️⃣ Feature Engineering: Daily Performance Aggregation
Since the sentiment data is daily, trade data was aggregated at the daily level to create comparable metrics:
- **daily_pnl** → Total daily profit and loss  
- **trade_count** → Number of trades per day  
- **win_rate** → Ratio of profitable trades to total trades  

---

#### 3️⃣ Data Merging and Sentiment Scoring
Merged **daily performance data** with **sentiment data** by trading date.  
Mapped sentiment categories to numeric scores for quantitative analysis:  

| Sentiment | Score |
|------------|--------|
| Extreme Fear | 0 |
| Fear | 25 |
| Neutral | 50 |
| Greed | 75 |
| Extreme Greed | 100 |

---

#### 4️⃣ Exploratory Data Analysis (EDA) and T-Test
- Analyzed performance across sentiment levels.  
- **Average Daily PnL during Fear:** \$8,458.56  
- **Average Daily PnL during Greed:** \$4,416.04  
- **T-Test Result:** P-value = 0.093 → Difference not statistically significant at 5% level.  

---

#### 5️⃣ Statistical Analysis: Correlation
- Negative correlation between sentiment score and performance metrics:  
  - **daily_pnl:** -0.15  
  - **win_rate:** -0.17  
- Suggests **contrarian performance** — traders perform better when fear dominates.  
- 30-day rolling correlation visualization shows the dynamic relationship over time.  

---

#### 6️⃣ Trader Segmentation (K-Means Clustering)
Segmented traders into **three behavioral clusters**:  

| Cluster | Description | Avg PnL | Avg Win Rate | Avg Trade Count |
|----------|--------------|----------|----------------|----------------|
| 1 | Best Performance | \$800k | 88.6% | — |
| 0 | High Volume, Moderate PnL | — | — | 12k |
| 2 | Low Performance | \$64k | 47% | — |

---

#### 7️⃣ Predictive Modeling
Built a **Logistic Regression model** to predict next-day profitability (`next_profitable`) using:
- Sentiment score  
- Trade count  

Used **TimeSeriesSplit** for chronological cross-validation.  
✅ **Model Accuracy:** 77%  

---

### 📈 Key Insights
- Traders perform **better during Fear** market phases — a contrarian trend.  
- Sentiment and trade volume are reliable indicators for short-term performance prediction.  
- Clear segmentation helps identify trader types and risk behaviors.  

---

### 🧮 Tech Stack
- **Languages:** Python  
- **Libraries:** pandas, numpy, seaborn, matplotlib, scikit-learn, scipy  
- **Tools:** Jupyter Notebook, Excel, GitHub  

