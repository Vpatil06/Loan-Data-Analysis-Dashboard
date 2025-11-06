# Loan-Data-Analysis-Dashboard
Power BI dashboard analyzing loan approval patterns.
# 💳 Loan Data Analysis Dashboard – Power BI Project

## 📘 Overview
This project analyzes loan application data to identify the major factors influencing loan approvals.  
Using **Power BI**, an interactive dashboard was created to visualize approval trends, applicant profiles, income distribution, and credit history effects.  
The dataset consists of **614 loan applications** with multiple applicant and loan attributes.

---

## 🧰 Tools & Technologies Used
- 🟡 **Power BI** – for dashboard and visual analysis  
- ⚙️ **DAX (Data Analysis Expressions)** – for calculated measures and KPIs  
- 📊 **Microsoft Excel / Python** – for initial data cleaning  
- 💻 **GitHub & LinkedIn** – for project sharing and documentation  

---

## 📂 Dataset Information
**Dataset:** `loan-dataset.csv`  
**Number of Records:** 614  

**Key Columns:**
- `Loan_ID` – Unique identifier for each application  
- `Gender`, `Married`, `Education`, `Self_Employed`  
- `ApplicantIncome`, `CoapplicantIncome`, `LoanAmount`, `Loan_Amount_Term`  
- `Credit_History`, `Property_Area`, `Loan_Status`  

---

## 🧮 Data Preparation
- Kept `Loan_ID` for identification and drillthrough.  
- Created calculated columns:
  - `TotalIncome = ApplicantIncome + CoapplicantIncome`  
  - `EMI = LoanAmount / Loan_Amount_Term`  
- Handled missing values:
  - Categorical → filled with **mode**  
  - Numeric → filled with **median**  
- Missing `Credit_History` replaced with **1 (good history)**.  
- Missing `Loan_Amount_Term` replaced with **360 months**.

---

## 📊 Dashboard Components
### **KPIs**
- Total Loans  
- Approved Loans  
- Approval Rate (%)  
- Average Loan Amount  
- Median Applicant Income  

### **Visuals**
- 🥧 Loan Status Distribution (Approved vs Rejected)  
- 📊 Approval Rate by Property Area  
- 🎓 Loan Status by Education  
- 💰 Income vs LoanAmount (Scatter Plot)  
- 📈 Loan Amount Distribution (Histogram / Column Chart)  
- 🧠 Key Influencers (AI Visual)  
- 🧾 Detailed Table with Loan_ID, LoanAmount, Income, Status  

### **Filters (Slicers)**
- Gender, Married, Education, Self_Employed, Credit_History, Property_Area, Loan_Status  

---

## 🎨 Dashboard Theme
- **Approved:** 🟩 Green `#27AE60`  
- **Rejected:** 🟥 Red `#C0392B`  
- **KPIs / Neutral:** 🔵 Blue `#3498DB`  
- **Background:** Light Grey `#F8F9F9`  
- Layout: Top KPIs, Left Filters, Center Visuals, Right Tables and Influencers.

---

## 📈 Key Insights
- ✅ **Approval Rate:** ~69% of total loan applications were approved.  
- 💳 **Credit History:** The most influential factor in approvals.  
- 🎓 **Education:** Graduates were more likely to receive approvals.  
- 🏡 **Property Area:** Semiurban applicants had the highest approval rate.  
- 💰 **Income vs Loan:** Higher incomes generally linked to larger loan approvals.  

---

## ⚙️ DAX Measures Used
```DAX
Total Loans = COUNTROWS('loan-dataset')
Approved Loans = CALCULATE([Total Loans], 'loan-dataset'[Loan_Status] = "Y")
Approval Rate = DIVIDE([Approved Loans], [Total Loans], 0)
Avg Loan Amount = AVERAGE('loan-dataset'[LoanAmount])
Median Applicant Income = MEDIAN('loan-dataset'[ApplicantIncome])
Total Income = SUMX('loan-dataset', 'loan-dataset'[ApplicantIncome] + 'loan-dataset'[CoapplicantIncome])
