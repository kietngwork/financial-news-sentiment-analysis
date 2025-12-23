# 📊 Financial News Sentiment Analysis

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
