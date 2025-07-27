# MC_PowerBi_Project
# Saudi Commercial Records OpenData Dashboard - Power BI

An interactive Power BI report analyzing Saudi commercial records by capital, time, record type, and legal status.

## Key Insights
- Total capital (main & branch)
- Record count by region, city, and month
- Average capital per region
- Monthly registrations (2023-Q1 focus)
- Record types and legal classifications

## File
- `MC_Project.pbix`: Main Power BI report

## Preview

![Dashboard Screenshot](Screenshot Of Project)
![Dashboard Screenshot](Screenshot Of Project2)


## DAX Measures Used

```DAX
-BranchCapital = CALCULATE(SUM(Fact_Registrations[Capital]), Dim_CR_Type[CR_Type] = "فرعي")
.
.
-TotalCapitalinReagion = CALCULATE(SUM(Fact_Registrations[Capital]), Dim_Region[Region_Name]= Dim_Region[Region_Name])
.
.
-CR of City = CALCULATE(SUM(Fact_Registrations[Capital]), Dim_City[City_Name] = "الرياض")
.
.
-CR_Type_Percentage :=
DIVIDE(
    COUNT(Fact_Registrations[CR_Number]),
    CALCULATE(COUNT(Fact_Registrations[CR_Number]), ALL(Dim_CR_Type))
)

