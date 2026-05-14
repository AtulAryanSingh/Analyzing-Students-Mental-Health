# International Student Mental Health Analysis

![Mental Health Illustration](mentalhealth.jpg)

## 📌 Project Overview
Does going to university in a different country affect your mental health? In 2018, a Japanese international university surveyed its students to examine the correlation between studying abroad, social connectedness, acculturative stress, and depression. 

This project uses **PostgreSQL** to analyze the survey data, specifically focusing on international students to determine if the length of stay is a contributing factor to their mental health metrics. 

## 🗂️ Dataset Description
The analysis is based on the `students.csv` dataset, which includes demographic information, language proficiency, and diagnostic scores for various psychological metrics. 

**Key Variables Analyzed:**
* `inter_dom`: Types of students (International or Domestic)
* `stay`: Length of stay (in years)
* `todep`: Total score of depression (PHQ-9 test)
* `tosc`: Total score of social connectedness (SCS test)
* `toas`: Total score of acculturative stress (AS test)

## 🛠️ Tech Stack
* **Database:** PostgreSQL
* **Environment:** Jupyter Notebook (`notebook.ipynb`)
* **Language:** SQL

## 🔍 Methodology & Key Queries
The core analysis involves filtering the dataset to isolate international students (`inter_dom = 'Inter'`) and aggregating their mental health scores grouped by their length of stay. 

**Core SQL Query:**
```sql
SELECT 
    stay, 
    COUNT(*) AS count_int, 
    ROUND(AVG(todep), 2) AS average_phq, 
    ROUND(AVG(tosc), 2) AS average_scs, 
    ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
