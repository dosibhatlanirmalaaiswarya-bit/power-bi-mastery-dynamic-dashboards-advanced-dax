# **Power-BI-Mastery-Dynamic-Dashboards-Advanced-DAX**  

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://app.powerbi.com/view?r=eyJrIjoiNTQ0YTllMGItMjUxNi00ZDdiLThmZmUtMGQxNWI4ODdkMGExIiwidCI6IjY3NmQ5MDg1LTQzMjMtNDc2NS1iZTVjLWNjMDdlMTEyMTA5MiJ9)
[![DAX](https://img.shields.io/badge/DAX-Advanced%20Calculations-orange?style=for-the-badge)]()
[![Azure](https://img.shields.io/badge/Azure-Cloud%20Integration-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)]()

---

## 📊 Project Overview  

This project showcases an **Advanced Power BI Sales Dashboard**, incorporating **dynamic bookmarks, complex DAX calculations, and interactive storytelling techniques** to analyze business sales performance. Designed to **track key financial metrics**, the dashboard provides insights for both **executive-level decision-making** and **operational-level performance analysis**.  

---

## 🎯 Live Dashboard Preview  

🔗 **[Click here to view the Interactive Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNTQ0YTllMGItMjUxNi00ZDdiLThmZmUtMGQxNWI4ODdkMGExIiwidCI6IjY3NmQ5MDg1LTQzMjMtNDc2NS1iZTVjLWNjMDdlMTEyMTA5MiJ9)**

### Dashboard Screenshots

#### 📈 Executive Summary View
<img width="1780" height="965" alt="image" src="https://github.com/user-attachments/assets/8b02e3f4-f04b-4f3f-a9e7-067d2253999e" />

---

## 🏢 Industry Use Case  

Sales performance analysis is critical for organizations looking to **optimize revenue, monitor trends, and enhance strategic decision-making**. This project applies **best practices in business intelligence (BI) and data visualization** to provide actionable insights into **YoY growth, customer satisfaction, and profitability**.  

---

## ✨ Key Features & Functionalities  

### 🎯 Executive-Level Insights  
| Feature | Description |
|---------|-------------|
| **YoY Growth Analysis** | High-level growth trends using `REMOVEFILTERS()` to ensure business-wide visibility |
| **Gross Sales & Profit KPIs** | Key financial indicators with comparisons to historical performance |
| **Customer Satisfaction Score** | Aggregated customer feedback displayed dynamically |

### 📊 Operational-Level Insights  
| Feature | Description |
|---------|-------------|
| **Monthly & Yearly Trend Analysis** | Performance tracking over time, responding to slicer selections |
| **Dynamic Bookmarking** | Interactive navigation for seamless storytelling |
| **DAX-Based Performance Metrics** | Calculated measures for in-depth analysis of sales trends |

### 🔢 Advanced DAX Calculations  
- **Dynamic YoY Growth:**  
   - **Executive View:** Business-wide perspective ignoring slicer filters  
   - **Operational View:** YoY growth influenced by user-selected filters  
- **Customer Satisfaction Score:** Aggregating satisfaction ratings dynamically  

---

## 🛠️ Technologies & Tools Used  

| **Technology** | **Purpose** |  
|---------------|------------|  
| ![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black) | Data visualization & dashboard development |  
| ![DAX](https://img.shields.io/badge/DAX-Advanced-orange?style=flat) | Advanced calculations & KPIs |  
| ![Power Query](https://img.shields.io/badge/Power%20Query-ETL-green?style=flat) | Data transformation & cleansing |  
| ![SQL](https://img.shields.io/badge/SQL-Database-blue?style=flat&logo=microsoftsqlserver) | Data extraction & preprocessing |  
| ![Azure](https://img.shields.io/badge/Azure-Cloud-0078D4?style=flat&logo=microsoftazure) | Cloud integration & data storage |  
| ![Excel](https://img.shields.io/badge/Excel-Analysis-217346?style=flat&logo=microsoftexcel) | Initial dataset review & structuring |  

---

## 📁 Project Structure  

```bash
📦 Power-BI-Mastery-Dynamic-Dashboards-Advanced-DAX
├── 📂 Data/                    # Contains raw & cleaned data files
├── 📂 PowerBI/                 # Power BI .pbix file with reports
├── 📂 DAX/                     # Custom DAX scripts & calculations
├── 📂 Screenshots/             # Dashboard previews & insights
│   ├── Executive_Dashboard.png
│   ├── Sales_Performance.png
│   ├── Storytelling_View.png
│   └── Operational_Metrics.png
└── 📜 README.md                # Documentation (this file)
```

---

## 💻 DAX Code Snippets  

### YoY Growth - Executive Level  
```DAX
Executive YoY% Dynamic = 
VAR _LatestYear = 
    CALCULATE( MAX( CalendarTable[Year] ), ALL( CalendarTable ) )

VAR _PreviousYear = _LatestYear - 1

VAR _Current12MonthSales = 
    CALCULATE(
        Measures_Sales[Total Sales], 
        CalendarTable[Year] = _LatestYear,
        REMOVEFILTERS( CalendarTable )
    )

VAR _Previous12MonthSales = 
    CALCULATE(
        Measures_Sales[Total Sales], 
        CalendarTable[Year] = _PreviousYear,
        REMOVEFILTERS( CalendarTable )
    )

VAR _Result =
    IF(
        NOT(ISBLANK(_Previous12MonthSales)), 
        (_Current12MonthSales - _Previous12MonthSales) / _Previous12MonthSales, 
        BLANK()
    )

RETURN _Result
```

### Customer Satisfaction Score
```DAX
Customer Satisfaction Score = 
VAR _TotalResponses = 
    CALCULATE( COUNTROWS( SatisfactionTable ), ALL( SatisfactionTable ) )

VAR _WeightedScore = 
    SUMX( SatisfactionTable, SatisfactionTable[Rating] * SatisfactionTable[Weight] )

RETURN 
    DIVIDE( _WeightedScore, _TotalResponses, 0 )
```

---

## 🚀 How to Use This Project  

1. **Clone the Repository**  
```bash
git clone https://github.com/dosibhatlanirmalaaiswarya-bit/Power-BI-Mastery-Dynamic-Dashboards-Advanced-DAX.git
```  

2. **Open Power BI Desktop and Load the `.pbix` File**  

3. **Explore the Dashboard & Interact with Slicers**  

4. **Review DAX Scripts for Advanced Insights**  

---

## 📚 Key Learnings & Takeaways  

✅ Understanding **YoY Analysis** at both executive and operational levels  
✅ Building **Interactive Power BI Dashboards** with bookmarks & storytelling  
✅ Writing **Optimized DAX Measures** for business performance analysis  
✅ Using **REMOVEFILTERS vs ALL in DAX** for strategic reporting  
✅ Implementing **Dynamic KPI Cards** with conditional formatting  
✅ Creating **Drill-through pages** for detailed analysis  

---

## 🎯 Target Audience  

| Audience | Value Proposition |
|----------|-------------------|
| **Data Analysts & BI Professionals** | Learn advanced Power BI techniques & DAX patterns |
| **Recruiters & Hiring Managers** | Evaluate Power BI skills with a practical case study |
| **Businesses & Clients** | Gain insights into sales trends & data-driven decision-making |

---

## 🤝 Connect With Me  

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Aiswarya_Dosibhatla-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/Aiswarya)
[![GitHub](https://img.shields.io/badge/GitHub-dosibhatlanirmalaaiswarya--bit-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/dosibhatlanirmalaaiswarya-bit)
[![Email](https://img.shields.io/badge/Email-Contact_Me-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:nirmalaaiswaryadosibhatla@gmail.com)

📍 **Location:** Dallas, TX  
📱 **Mobile:** +1 940-977-2944

---

## ⭐ If you find this project useful, don't forget to star this repository!  

---

## 💡 Final Thoughts  

This project **bridges the gap between executive-level and operational analytics**, offering insights into how **advanced Power BI dashboards** can drive **business decisions with data**.  

The implementation demonstrates real-world scenarios I've encountered while:
- Processing **10M+ daily records** at Musigma Business Solutions
- Creating **Global Consolidated Power BI dashboards** tracking KPIs across **40 regions**
- Reducing **reporting time by 40%** through optimized DAX and data modeling

Looking forward to your feedback and contributions!

---

## 👩‍💻 About the Maintainer

<img src="https://avatars.githubusercontent.com/u/241822760?v=4" width="120" align="left" style="margin-right: 20px; border-radius: 50%;">

**Aiswarya Dosibhatla**  
*Data Analyst & ETL Architect*

Experienced Data Analyst with **3+ years** of professional experience in data analysis, ETL development, and business intelligence. Proficient in **Python, SQL, Power BI, Snowflake**, and cloud platforms including **Azure and AWS**. 

Delivered actionable insights improving reporting accuracy by **25%**. Expertise in designing dashboards, automating workflows, and optimizing data pipelines to enhance operational efficiency. Strong capability to translate business requirements into data-driven solutions for strategic initiatives.

<br clear="left"/>

### 🛠️ Technical Expertise

| Category | Skills |
|----------|--------|
| **Programming** | Python, R, SQL, Shell Scripting |
| **Data Engineering** | Azure Data Factory, Databricks, Apache Spark, Delta Lake |
| **BI & Visualization** | Power BI (Advanced DAX), Tableau, Excel Analytics |
| **Cloud Platforms** | Microsoft Azure, AWS, GCP |
| **Databases** | Snowflake, PostgreSQL, MySQL, SQL Server |
| **Methodologies** | Agile, Scrum, Medallion Architecture |

### 🎓 Education

| Degree | Institution | Timeline |
|--------|-------------|----------|
| **M.S. Information Systems & Technology** | University of North Texas, Denton, TX | Aug 2023 – May 2025 |
| **B.Tech Information Technology** | Jawaharlal Technological University, India | Jul 2016 – Aug 2020 |

### 🏆 Professional Achievements

- 🥇 Attained **3 Spot Awards** for exceptional performance at MuSigma
- 📊 Processed **10M+ daily records** with ETL pipelines achieving **99.9% uptime**
- 📈 Reduced reporting time by **40%** through dashboard optimization
- 👥 Led Agile teams of **8 members** with **100% on-time project completion**

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).

---

<p align="center">
  <b>⭐ Star this repo if you found it helpful! ⭐</b>
</p>

<p align="center">
  Made with ❤️ by <a href="https://github.com/dosibhatlanirmalaaiswarya-bit">Aiswarya Dosibhatla</a>
</p>
