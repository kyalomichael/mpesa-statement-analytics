# M-Pesa FinTech Analytics: End-to-End Data Pipeline & BI Architecture 📊🏦

An enterprise-grade data engineering and business intelligence project that transforms unstructured mobile money data (M-Pesa transaction statements) into a structured relational database schema and interactive analytical dashboards.

## 🛠️ Tech Stack & Architecture
* **Data Extraction & ETL:** Power Query / Excel (Parsing multi-nested, erratic PDF reporting layers)
* **Database Management System:** SQL Server (SSMS) (Schema staging, data type validation, relational modeling)
* **Business Intelligence & Analytics:** Power BI (Star-schema modeling, advanced DAX time-intelligence)

---

## 💡 Core Strategic Takeaways (From 11,000+ Transactions)
1. **The Overdraft Velocity:** A striking **37%** of all transactional interactions were automated Fuliza overdraft triggers utilized to cover short-term liquidity gaps.
2. **Commercial Dominance:** B2B/B2C transactions (Paybills and Till numbers) heavily dominate peer-to-peer transfers, making up **65%** of total outgoing cash flow.
3. **Weekend Spending Cadence:** Transaction velocity sharply peaks on Thursday and Friday evenings around 7:00 PM, generating a rapid transactional loop averaging a new transaction every **43 minutes**.

---

## 🚀 Data Pipeline Breakdown

### 1. Ingestion & Transformation (Power Query)
* Overcame PDF layout complexities to isolate unstructured text strings.
* Standardized messy transaction descriptions into distinct dimensions.
* Separated core transaction principals from dynamic transactional fees.

### 2. Relational Staging (SQL Server)
The data was migrated into an RDBMS (`Mpesa_Analytics`) to ensure strict schema enforcement and query performance. 

```sql
-- Sample Validation Query Used in Staging
SELECT TOP (1000) 
    [Receipt_No],
    [Completion_Time],
    [Details],
    [Paid_In],
    [Paid_Out]
FROM [Mpesa_Analytics].[dbo].[mpesa_clean]
WHERE [Receipt_No] IS NOT NULL;
