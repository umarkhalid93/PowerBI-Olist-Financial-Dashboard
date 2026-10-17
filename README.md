# PowerBI-Olist-Financial-Dashboard
Enterprise-grade Power BI financial dashboard (Soll-Ist-Vergleich) with Azure SQL backend, advanced DAX, and RLS.
# Enterprise Financial Dashboard (Soll-Ist-Vergleich)

## Project Overview
An enterprise-grade Power BI financial dashboard built on top of the Olist e-commerce dataset. Designed to German enterprise reporting standards, featuring a robust "Soll-Ist-Vergleich" (Target vs. Actual) variance engine, optimised DAX, and strict data governance.

## Architecture & Tech Stack
* **Backend:** Azure SQL Database 
* **Frontend:** Power BI Desktop
* **Data Modelling:** Star Schema (Fact: `vw_olist_orders_cleaned`, Dimensions: `DimDate`, etc.)
* **Validation:** SQL Server Management Studio (SSMS)

## Key Technical Implementations
1. **Advanced DAX Engine:** Engineered a YoY variance matrix handling strict data cutoffs and missing chronological context using nested `ISBLANK()` and `SAMEPERIODLASTYEAR` logic.
2. **Performance Optimisation:** Dashboard rendering evaluated via DAX Studio / Performance Analyser. Core matrix visuals execute in **< 350ms**, well below the 500ms enterprise benchmark.
3. **Advanced UX:** Built a collapsible application-style filter pane utilising Selection groups, Bookmarks (unlinked from data context), and Action triggers to maximise canvas real estate.
4. **Data Governance:** Implemented Row-Level Security (RLS) filtering to restrict user data access based on organisational roles (e.g., Logistics Managers restricted to "delivered" status).
5. **SQL Backend Audit:** 100% data integrity verified. Power BI frontend Total Revenue (27,183,287.40 €) mathematically tied out to the Azure SQL backend via aggregation query:
   `SELECT SUM(CAST(price AS FLOAT)) AS SQL_Total_Revenue FROM Olist_Items_CSV;`
