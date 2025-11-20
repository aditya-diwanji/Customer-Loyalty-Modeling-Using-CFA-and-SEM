# Customer-Loyalty-Modeling-Using-CFA-and-SEM

This repository contains a full Confirmatory Factor Analysis (CFA) and Structural Equation Modeling (SEM) pipeline built to uncover latent behavioral drivers in a 2,239-record customer dataset.

The project identifies three key latent constructs — **Spending**, **Engagement**, and **Promotion Sensitivity** — and validates them using robust statistical diagnostics.

---

## 📌 Project Objectives

- Implement a **CFA + SEM workflow** to analyze customer purchase and campaign behavior.  
- Estimate and validate **latent variables** using observed indicators.  
- Evaluate model fit using **RMSEA, CFI, TLI, SRMR**, and **modification indices**.  
- Improve model stability by addressing **cross-loadings**, **variance scaling issues**, and **multicollinearity**.  
- Generate **latent factor scores** for downstream behavioral insights or segmentation.

---

## 📂 Dataset

- **Observations:** 2,239 customers  
- **Features include:**  
  - Purchase amounts (Wines, Fruits, Meat, Sweets, Gold)  
  - Purchase channels (Store, Web, Catalog)  
  - Campaign responses (AcceptedCmp1–5, Response)  
  - Demographic & behavioral variables  

---

## 🧠 Latent Constructs

### **1. Spending**
Indicators:  
`MntFishProducts`, `MntSweetProducts`, `MntMeatProducts`, `MntGoldProds`, `MntFruits`, `MntWines`

### **2. Engagement**
Indicators:  
`NumStorePurchases`, `NumWebPurchases`

### **3. Promotion Sensitivity**
Indicators:  
`AcceptedCmp5`, `Response`, `AcceptedCmp4`, `AcceptedCmp3`, `AcceptedCmp1`

All factor loadings were **statistically significant**.

---

## 🧪 Methodology

- **Estimation Method:** MLR (Robust Maximum Likelihood)  
- **Standard Errors:** Huber–White robust  
- **Fit Evaluation:**  
  - RMSEA (Robust & Scaled)  
  - CFI, TLI  
  - SRMR  
  - Chi-square & Hoelter’s N  
- **Model Refinement:**  
  - Modification Index analysis  
  - Resolved cross-loading issues  
  - Fixed non-positive definite covariance warnings  
  - Improved discriminant validity and factor separation  

---

## 📈 Key Results

- All latent constructs demonstrated **strong reliability and convergent validity**.  
- Fit indices improved after addressing cross-loadings and high-MI relationships.  
- Final model produced **stable factor scores** usable for segmentation, clustering, or predictive modeling.

---

## 📁 Files in This Repository

| File | Description |
|------|-------------|
| `CFA Customer Analysis.pdf` | Full jamovi output including CFA, SEM, fit indices, and modification indices |
| `model_code.R` (optional) | SEM/CFA specification using `lavaan` |
| `README.md` | Project overview |

---

## 🧾 Example Model Specification (lavaan)

```r
model <- '
  Spending =~ MntFishProducts + MntSweetProducts + MntMeatProducts +
               MntGoldProds + MntFruits + MntWines

  Engagement =~ NumStorePurchases + NumWebPurchases

  PromotionSensitivity =~ AcceptedCmp5 + Response + AcceptedCmp4 +
                         AcceptedCmp3 + AcceptedCmp1

  Spending ~~ Engagement
  Spending ~~ PromotionSensitivity
  Engagement ~~ PromotionSensitivity
'
