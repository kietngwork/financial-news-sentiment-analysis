# 📊 Financial News Sentiment Analysis
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/bc726ad0-54d7-43b6-9123-909cc22cc8d3" />

## 1. Background & Overview

Financial markets react rapidly to news, but manually interpreting thousands of daily financial headlines is not scalable for analysts. Many analytics teams want to understand whether **news sentiment can explain or anticipate short-term stock price movement**, and whether segmentation by industry improves insight quality.

This project applies **data analytics, feature engineering, and model evaluation** techniques to assess the relationship between **financial news sentiment and daily stock price changes**. Rather than focusing purely on model complexity, the analysis emphasizes **data preparation, validation, interpretability, and business relevance**.

The study compares:
- A **general sentiment approach** applied across industries  
- **Industry-specific sentiment analysis** to test whether customization improves results  

Industries analyzed:
- Technology  
- Energy  
- Healthcare  
- Real Estate  
- Finance  
- Media & Entertainment  

**Core business question**  
Is one well-designed sentiment pipeline sufficient for analytics use, or does industry-level customization meaningfully improve insight quality?

## 2. Data Structure & Initial Checks

### Data Sources
- Financial news headlines (2018) sourced via Bloomberg  
- NASDAQ stock price data (Open, Close)

### Dataset Overview
- Original dataset: ~15.5M news records  
- Filtered to 2018 for computational efficiency and market stability  
- Final working dataset: ~697,000 records

### Key Fields
| Field | Description |
|---|---|
| Date | News publication / trading date |
| Stock_symbol | Company ticker |
| Headline | Financial news title |
| Sentiment_score | Numeric sentiment derived from NLP models |
| Price_Change | (Close − Open) / Open |

### Data Cleaning & Preparation
- Removed ~6% of rows with missing tickers  
- Standardized date formats and aligned trading days  
- Aggregated multiple headlines into **daily average sentiment per stock**  
- Assigned neutral sentiment on days with no news  
- Adjusted for non-trading days by rolling sentiment forward

## 3. Executive Summary

### Key Findings
- Financial news sentiment contains **measurable predictive signal**, but strength varies by model and industry
<img width="477" height="382" alt="Screenshot 2025-12-23 at 2 04 19 PM" src="https://github.com/user-attachments/assets/33e4578d-3f7e-49dd-9b2c-4b33b1ed712d" />

- A **general FinBERT-based sentiment model** performed consistently across most sectors
<img width="494" height="217" alt="Screenshot 2025-12-23 at 2 05 41 PM" src="https://github.com/user-attachments/assets/cc4f9820-9c74-4631-a9d1-090e5d0fc7b4" />

- Industry-specific tuning **did not always improve accuracy** and often increased overfitting
<img width="485" height="198" alt="Screenshot 2025-12-23 at 2 07 06 PM" src="https://github.com/user-attachments/assets/3875d219-65cb-436b-a90a-e1768c641074" />

- Media & Entertainment showed distinct behavior due to non-financial language patterns
<img width="481" height="239" alt="Screenshot 2025-12-23 at 2 09 56 PM" src="https://github.com/user-attachments/assets/239c60c5-803a-4c6e-92cc-17175ba2a8f6" />

For analytics teams, a **single general sentiment pipeline** is usually sufficient and more cost-effective. Industry-level customization should be applied **selectively**, not by default.

## 4. Insights Deep Dive
Models were evaluated using **interpretable, analyst-relevant metrics**, not just in-sample fit:

- Regression: MAE, RMSE  
- Classification: Accuracy, Precision, Recall, F1  
- Train vs Test comparison to detect overfitting  

| Approach | Insight |
|---|---|
| TextBlob + LSTM | Simple baseline, limited predictive power |
| BERT + LSTM | Strong training fit, weak generalization |
| **FinBERT + LSTM** | Best balance of accuracy and stability |

Higher model complexity does not guarantee better out-of-sample performance. Stability and generalization matter more for business analytics.

### Industry-Level Analysis

#### Cross-Industry (General Model)
- Stable performance across all sectors  
- Low train–test error gap  
- Best candidate for production analytics use  

#### Media & Entertainment
- Headlines driven by content releases and public sentiment  
- Less aligned with traditional financial language  
- Industry-specific modeling captured nuance more effectively  

#### Other Industries
- Technology, Energy, Healthcare, Finance, and Real Estate showed **minimal benefit** from specialization

## 5. Recommendations
1. **Start with a general sentiment pipeline**
   - Lower maintenance cost  
   - Easier validation  
   - Strong cross-industry performance  

2. **Apply segmentation selectively**
   - Use industry-specific tuning only when language patterns differ meaningfully  

3. **Improve features, not just models**
   - Combine sentiment with volume, volatility, or event-based indicators  

4. **Use sentiment as decision support**
   - Complementary signal, not a standalone trading system  
