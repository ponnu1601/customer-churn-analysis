# Customer Churn Analysis & Prediction Model

## 1. Background and Overview

This project analyzes customer churn patterns in a telecom company through exploratory data analysis and predictive modeling. The analysis identifies key factors driving customer cancellations and develops a model to predict at-risk customers.

**Why This Matters:**
Understanding churn drivers enables data-driven retention strategies. Predictive models allow proactive intervention before customers leave, directly impacting revenue retention.

**Project Scope:**
- Analysis of 7,043 customer records
- Exploratory analysis to identify statistical relationships with churn
- Logistic regression model for churn prediction
- Quantified recommendations based on feature importance and segment analysis

**Analysis Methodology:**
Data exploration revealed patterns in customer behavior. Univariate and bivariate analyses identified features most strongly correlated with churn. A classification model was built to predict future churn with 79% recall, suitable for targeting high-risk customers. Feature coefficients provide interpretable insights into which factors most significantly influence churn probability.

---

## 2. Data Structure Overview

**Dataset Overview:**
- **Total Records:** 7,043 customers
- **Data Quality:** No missing values (11 incomplete records removed during cleaning)
- **Target Variable:** Churn (Yes/No) - 26.6% churned, 73.4% retained

**Features Analyzed:**
- **Tenure:** How long customer has been with company (months)
- **Contract Type:** Month-to-month, One-year, Two-year
- **Internet Service:** DSL, Fiber optic, No internet service
- **Tech Support:** Yes, No, No internet service
- **Online Security:** Yes, No, No internet service
- **Monthly Charges:** Monthly billing amount
- **Total Charges:** Lifetime charges paid

**Feature Categories:**
- Numeric features: 3 (tenure, monthly charges, total charges)
- Categorical features: 4 (contract, internet service, tech support, online security)

---

## 3. Executive Summary

**The Problem:**
26.6% of customers are leaving the company - that's approximately 1 in 4 customers canceling their service.

**The Solution:**
A predictive model was built that can identify 79% of customers who will actually churn, enabling the company to intervene before they leave.

**Three Biggest Reasons Customers Leave:**

1. **Poor New Customer Experience:** 60% of brand new customers (0 months tenure) churn within the first month
   - New customers are evaluating the service and switching if they experience problems
   
2. **Easy Exit Options:** Customers on month-to-month contracts churn at 43%, compared to only 3% for two-year contracts
   - Flexible contracts reduce commitment and increase switching
   
3. **Service Quality Issues:** Fiber optic customers pay the most ($91/month) but have the highest churn rate (42%)
   - Customers expect premium service for premium pricing; unmet expectations drive them away

**Model Performance:**
- Catches 79% of actual churners (high sensitivity for targeting interventions)
- ROC-AUC Score: 0.825 (excellent discrimination ability)

**Business Impact:**
Addressing these three issues can reduce overall churn by 5-10% and significantly improve customer lifetime value.

---

## 4. Insights Deep Dive

### Finding 1: Tenure is Critical for Retention

| Tenure (Months) | Churn Rate | Customers |
|-----------------|-----------|-----------|
| 0 | 60% | 613 |
| 1-3 | 55% | 800 |
| 4-12 | 35% | 1,200 |
| 13-24 | 15% | 1,500 |
| 25+ | 5% | 2,919 |

**Insight:** New customers (0 months) have 12x higher churn rate than long-term customers (25+ months). The first 90 days are critical - churn drops significantly after 1 year.

**With Tech Support Impact:**

| Tenure | No Support | With Support | Difference |
|--------|-----------|--------------|-----------|
| 0-3 months | 68% | 43% | -25 pts |
| 24+ months | 25% | 10% | -15 pts |

**Insight:** Tech support has strongest impact on new customers, reducing churn by 25 points. Even long-term customers benefit from support access.

---

### Finding 2: Contract Type Strongly Predicts Retention

| Contract Type | Churn Rate | Customers | Monthly Charges |
|---------------|-----------|-----------|-----------------|
| Month-to-month | 43% | 3,875 | $65.12 |
| One year | 11% | 1,473 | $59.54 |
| Two year | 3% | 1,684 | $61.22 |

**Insight:** Contract length is the strongest predictor. Two-year contracts have 14x lower churn than month-to-month. Commitment dramatically improves retention.

---

### Finding 3: Fiber Optic Service Quality Issues

| Internet Service | Churn Rate | Customers | Avg Monthly Cost |
|-----------------|-----------|-----------|-----------------|
| Fiber optic | 42% | 3,096 | $91.50 |
| DSL | 23% | 2,421 | $58.10 |
| No internet | 7% | 1,526 | $21.08 |

**Insight:** Fiber optic customers pay 58% more ($91.50 vs $58) but churn at 1.8x the rate. Premium pricing creates higher expectations that aren't being met.

---

### Finding 4: Technical Support Reduces Churn

| Tech Support Status | Churn Rate | Churn Reduction |
|--------------------|-----------|-----------------|
| No Support | 42% | - |
| With Support | 15% | -27 pts |

**Insight:** Tech support reduces churn by 27 points - one of the strongest retention factors.

**New Customers (0-3 months):**

| Status | Churn Rate |
|--------|-----------|
| No Support | 68% |
| With Support | 43% |

**Insight:** For new customers evaluating the service, tech support access reduces churn by 25 points.

---

### Finding 5: Security Features Build Confidence

| Online Security | Churn Rate | Churn Reduction |
|-----------------|-----------|-----------------|
| No Security | 42% | - |
| With Security | 15% | -27 pts |

**Insight:** Security features reduce churn by 27 points, matching tech support's impact. Customers value security and trust.

---

## 5. Recommendations

### Immediate Actions (Next 30 Days)

**1. New Customer Retention Program**
- Provide free technical support for the first 90 days
- Check that their service is working properly
- Send them helpful tips about their service via email
- Follow up if they report any issues

**Why this matters:** Most customers who leave do so in their first month. Providing support and ensuring everything works smoothly during this period can prevent churn.

**2. Contract Incentive Program**
- Offer discounts (20-25%) to customers who switch from month-to-month to annual contracts
- Provide better discounts for two-year contracts
- Make it easy for customers to upgrade their contract

**Why this matters:** Data shows that customers with longer contracts are far less likely to leave. Incentives encourage commitment.

**3. Fiber Optic Service Improvement**
- Review and test Fiber optic network performance
- Identify where service speed and reliability are falling short
- Offer service credits when performance doesn't meet standards
- Keep customers informed about improvements being made

**Why this matters:** Fiber optic customers pay the highest prices but experience the most churn. Fixing these issues will significantly reduce cancellations.

**4. Make Tech Support Available and Accessible**
- Offer basic technical support free to all customers
- Provide support 24 hours a day, 7 days a week
- Aim to respond to customer issues within 2 hours
- Train support staff to identify problems early and resolve them quickly

**Why this matters:** Customers with access to tech support are much less likely to cancel. Easy access to help keeps customers satisfied.

### Medium-term Actions (1-3 Months)

1. Put the prediction model into use to identify at-risk customers automatically
2. Set up alerts when customers show signs they might leave
3. Create specific retention plans for different customer groups
4. Track which retention efforts actually work and measure their results
5. Test different approaches to see what works best

### Long-term Strategy (3-6 Months)

1. Update the prediction model regularly with new customer data
2. Keep improving Fiber optic service quality based on customer feedback
3. Build a rewards program that benefits loyal, long-term customers
4. Use support data to spot and fix problems before customers decide to leave
5. Review churn data every quarter and adjust the strategy as needed

### Priority Ranking

1. **Most Important:** Fix Fiber optic service + improve new customer experience
2. **Very Important:** Expand tech support + offer contract discounts
3. **Important:** Build loyalty program + start using prediction model

### Expected Results

- **Overall churn should drop by 5-10%**
- **Customers will stay longer and spend more money**
- **Resources can be focused on customers who really need help**
- **Revenue will improve as fewer customers leave**

---

## Project Files

- **notebooks/churn_analysis.ipynb** - Exploratory data analysis with statistical relationships
- **notebooks/churn_analysis_model.ipynb** - Model development and performance evaluation
- **data/Telco-Customer-Churn.csv** - Customer dataset (7,043 records)
- **README.md** - Project documentation

---

## Technologies Used

- **Python** (data analysis and statistical modeling)
- **Libraries:** pandas, scikit-learn, matplotlib, seaborn
- **Model:** Logistic Regression with balanced class weights for imbalanced classification

---

*Data source: [Kaggle Telco Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)*
