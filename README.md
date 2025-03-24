📊 Diabetes Readmission Analysis (1999–2008)

🚀 Project Overview

This project analyzes 10 years (1999–2008) of inpatient diabetic encounters from 130 US hospitals to explore the factors influencing readmissions, particularly those occurring within 30 days. The goal is to identify trends and drivers behind short-term readmissions to improve care quality and reduce costs.

Tech Stack : 

🐍 Python (Google Colab) – for preprocessing & feature engineering  
📊 Power BI – for interactive data visualizations

---

📚 Dataset Summary

- Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008)  
- Study Reference: [Hindawi - Biomedical Research International](https://www.hindawi.com/journals/bmri/2014/781670/tab1/)  
- Size: 100,000+ diabetic patient encounters  
- Period: 1999–2008  
- Features: 50+ variables including demographics, labs, medications, diagnoses, procedures, and readmission info  

Inclusion Criteria:
- Inpatient diabetic encounters  
- Length of stay: 1–14 days  
- At least 1 lab test and 1 medication administered  

---

🧪 Python Preprocessing (Google Colab)

✅ Steps Performed

1. **Data Inspection**  
   - Explored record count and column data types  
   - Checked distribution of `readmitted` and `discharge_disposition_id` values  

2. **Binary Target Creation**  
   - Created `Output_Readmission` column where  
     `1 = readmitted within 30 days`,  
     `0 = otherwise`

3. **Missing Value Handling**  
   - Replaced `'?'` with `NaN`  
   - Filled missing values in `race`, `payer_code`, `medical_specialty` with `"NA"`

4. **Feature Engineering**  
   - Grouped 73 medical specialties into top 10 + `"Other"`  
   - Dropped low variance features (e.g., `examide`, `citoglipton`)  
   - Identified ID columns (e.g., `admission_type_id`, `discharge_disposition_id`) as categorical  

5. **Export for Dashboarding**  
   - Cleaned dataset downloaded for use in Power BI  

---

📊 Power BI Dashboards

1️⃣ Emergency Admissions vs Readmission

**Question**: Are emergency admissions more likely to result in <30-day readmissions?

**Visuals**:
- Bar chart: Admission Type vs Readmission  
- KPI card: Emergency Readmission Rate  
- Trend line: Readmission by Admission Type

---

2️⃣ Discharge Disposition Impact

**Question**: How does the discharge type influence readmission likelihood?

**Visuals**:
- Bar chart: Discharge Disposition vs Readmission  
- Donut chart: `<30`, `>30`, and `No` Readmission breakdown  
- Slicer: Filter by disposition type  

---

3️⃣ Medications, Procedures & Visit Frequency

**Question**: Do lab tests, medications, or visit types affect readmission?

**Visuals**:
- Scatter plots and bar charts comparing:
  - `num_lab_procedures`, `num_medications`, `number_emergency`, `number_inpatient`  
- KPIs for average visits and procedures by readmission status  

---

4️⃣ Specialty-Based Readmissions

**Question**: Which medical specialties see the highest patient readmission rates?

**Visuals**:
- Bar chart: Top 10 Specialties by Patient Count  
- Pie chart: Readmission Rate by Specialty  
- Table: Specialty × Discharge × Readmission Breakdown  

---

📌 Key Insights

- **Emergency admissions** had the highest rate of <30-day readmissions  
- Most patients discharged to **home** had high readmission volumes  
- **Internal Medicine** and **Emergency/Trauma** specialties showed higher readmission patterns  
- Patients with more medications and lab tests were **more likely to be readmitted**

---

🔮 Future Enhancements

- Build a machine learning classifier to predict readmission risk  
- Use `diag_1`, `diag_2`, `diag_3` fields for ICD code grouping 
