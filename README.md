# HR Attrition Analytics — Executive Dashboard (Power BI)

**Why it matters:** Replacing employees is expensive. I built a compact Power BI dashboard that shows *where* and *when* attrition spikes, and what to investigate next.

**Tools:** Power BI, DAX  
**KPIs:** Attrition Rate, Total Employees, Avg Monthly Income  
**Slicers:** Department, Gender, OverTime

<img src="https://github.com/user-attachments/assets/36803710-1310-4f17-a8d3-d681c8475664" alt="Dashboard" width="1298" height="730" />


---

## Business Questions
1) What’s the overall **Attrition Rate**?  
2) Which **Departments / Job Roles** lose the most people?  
3) How does attrition vary by **Age band** and **Tenure (Years at Company)**?  
4) Is there a relationship between **OverTime / Income** and attrition?

## Headline Insights (IBM sample data)
- Overall **Attrition ≈ 16%**.  
- **R&D and Sales** lead in attrition **counts**.  
- Risk is highest in **early tenure (0–3 years)**.  
- **OverTime = Yes** correlates with higher attrition.  
- Lower **Monthly Income** bands show higher attrition.

> Dataset: IBM HR Analytics (public, synthetic).

## What I built
- KPI header (Attrition Rate, Total Employees, Avg Monthly Income)  
- Attrition by **Department** and **Job Role × Gender**  
- Attrition by **Age band** (Young, Mid-level, Experienced, Senior)  
- Attrition by **Tenure** (YearsAtCompany binned/grouped)

## Core DAX
```DAX
Total Employees = DISTINCTCOUNT('HR'[EmployeeNumber])
Attrition Count = CALCULATE([Total Employees], 'HR'[Attrition] = "Yes")
Attrition Rate  = DIVIDE([Attrition Count], [Total Employees])
Avg Monthly Income = AVERAGE('HR'[MonthlyIncome])
