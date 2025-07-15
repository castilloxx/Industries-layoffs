# 📊 Layoffs Data Analysis Project

## Project overview
This project is a **full SQL-based data cleaning and exploratory data analysis (EDA)** on a global layoffs dataset. It showcases my skills in **data cleaning, transformation, analysis, and deriving actionable insights** using MySQL.

---

<img width="1366" height="768" alt="Screenshot (3)" src="https://github.com/user-attachments/assets/d0432587-8e62-409b-9bee-cdb7879b2b68" />


## 🗂️ Dataset Overview

The dataset contains information about company layoffs, including:

- **Company name**
- **Location**
- **Industry**
- **Total laid off**
- **Percentage laid off**
- **Date**
- **Stage**
- **Country**
- **Funds raised (in millions)**

---

## ⚙️ Tools Used

- **MySQL (Data Cleaning & Analysis)**
- **Tableau (dashboard and visualization)**

---

## 🔧 Project Workflow

1. **Data Cleaning**
   - Checking for and removing duplicates
   - Standardized data entries (company names, industry, country)
   - Converted dates to appropriate date format
   - Handled NULL or blank values

2. **Data Transformation**
   - Created staging tables to safely clean data
   - Populated missing industries using self joins

3. **Exploratory Data Analysis (EDA)**
   - Analyzed total layoffs by:
     - Company
     - Industry
     - Country
     - Year and Month
   - Checked for the maximum total laid off and percentage laid off
   - Identified companies with a 100% total laid off
   - Identified companies, industriies, stage and countries with highest laid off
   - Identified the months with the highest laid off
   - Calculated rolling total layoffs over time
   - Identified the laid off of each company year by year

4. **Data visualization**
   - Layoffs by industry
   - Layoffs % distribution
   - Top 10 companies by layoffs
   - Layoffs by countries
   - Layoffs vs funding
   - Layoffs overtime

---

## 📊 Tableau Dashboard Preview

🔗 [View Dashboard on Tableau Public](https://public.tableau.com/app/profile/favour.chukwudozie.ndu.arinze/viz/Tableaulayoffsstagingdashboard/Dashboard1)

## 💡 Key Insights

- The **highest number of layoffs** was recorded by major tech companies.
- **Industries most affected** include Tech, Retail, and Crypto.
- **Peak layoff periods** align with global economic slowdowns and industry downturns.

---

## 📝 SQL Highlights

Here are examples of analytical queries used:

```sql
SELECT stage, SUM(total_laid_off)
FROM layoffs_staging2
GROUP BY stage
ORDER BY 2 DESC;

WITH ROLLING_TOTAL AS
(
SELECT SUBSTRING(`date`, 1,7) AS `MONTH`, SUM(total_laid_off) AS total_off
FROM layoffs_staging2
WHERE SUBSTRING(`date`, 1,7) IS NOT NULL
GROUP BY `MONTH`
ORDER BY 1 ASC
)
SELECT `MONTH`, total_off, SUM(total_off) OVER(ORDER BY `MONTH`) AS rolling_total
FROM rolling_total;
```

## Recomendtions

- Industries like Tech and Crypto need stronger financial strategies.
- Businesses should train workers to take on different roles if needed.
- Countries with many layoffs should review their job policies.
- Companies should watch economic trends to prepare early.
