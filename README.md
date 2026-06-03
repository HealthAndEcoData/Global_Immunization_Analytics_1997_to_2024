Global Immunization Analytics Dashboard (1997–2024)

📊 Project Overview
An end-to-end Power BI business intelligence solution engineered to track, model, and visualize global vaccination coverage data across nearly three decades. This project transforms raw public health data into an interactive executive tracking system, demonstrating advanced data modeling (Star Schema), ETL optimization, and mobile-responsive design.

📈 Executive KPI Baselines
Global Average Coverage: ~87.5% (Calculated via optimized average aggregations)

Vaccines Tracked: 16 unique vaccines (Accurately capturing multi-dose series including Ipv1, Ipv2, and pol3 via distinct counts)

Global Scope: 195 unique countries monitored

🛠️ Data Architecture & Modeling
A key focus of this project was moving away from a flat-file structure to implement an optimized, high-performance Star Schema. This ensures rapid query performance and clean DAX calculations.

                  ┌───────────────┐
                  │  Dim_Country  │
                  └───────┬───────┘
                          │ 1
                          │
                          │ *
┌───────────────┐   * ┌───┴────────────┐ * ┌─────────────────┐
│  Dim_Vaccine  ├───══► Fact_Vaccination ◄══─┤    Dim_Date     │
└───────────────┘ 1   └────────────────┘   1 └─────────────────┘
Centralized Fact Table: Fact_Vaccination captures granular, yearly coverage metrics.

Dimension Tables: Connected via 1:N (one-to-many) relationships to Dim_Country and Dim_Vaccine lookup tables.

Data Integrity via Power Query (M): Cleaned complex multi-dose naming conventions, handled missing data, and filtered out blank entries to guarantee reporting accuracy.

⚙️ Tech Stack & Advanced Skills
Power BI Desktop: Star schema architecture, advanced DAX measures, and cross-filtering optimization.

Power Query (M): ETL pipeline architecture, schema normalization, and data type validation.

UI/UX & Responsive Design: Corporate color theory, 16:9 widescreen layout, and mobile-first refactoring.

🔢 Core DAX Measures & Calculations
To ensure performance optimization and precise aggregations across the star schema, explicit DAX measures were constructed rather than relying on implicit/default fields.

1. Global Average Coverage
Calculates the historical baseline anchor across global performance cards.

Code snippet
Global Average Coverage = 
AVERAGE( 'Fact_Vaccination'[Coverage_Percentage] )
2. Unique Vaccines Tracked
Optimized distinct count logic to accurately capture multi-dose series variations (e.g., Ipv1, Ipv2, and pol3) across the dimension lookup.

Code snippet
Vaccines Tracked = 
DISTINCTCOUNT( 'Dim_Vaccine'[Vaccine_Name] )
3. Monitored Countries
Dynamically evaluates the active scope of geographic regions represented in the current context.

Code snippet
Countries Monitored = 
DISTINCTCOUNT( 'Dim_Country'[Country_Name] )
🚀 Desktop Analytics Experience
The desktop interface is built on a professional 16:9 widescreen layout featuring a dark blue corporate header banner and an intuitive analytical flow:

3-Card KPI Control Panel: Instant high-level macro metrics.

Dynamic Geographic Tracking: A World Map for spatial distribution analysis.

Trend & Ranking Analysis: A historical Line Chart paired with a Clustered Bar Chart to identify top and bottom-performing nations.

Deep-Dive Interactive Analysis
Includes a dedicated Vaccine Dropdown Slicer (with blank values programmatically removed via Basic Filtering) and a Year Slider for granular, state-level cross-highlighting.

📱 Executive Mobile-First Optimization
To support field stakeholders and executives on the move, the entire dashboard was refactored for mobile devices. All 10 native page elements were reorganized into a clean, single-column vertical scrolling experience that retains full interactive capabilities without layout distortion.

📂 Repository Structure
Global Immunization and Vaccine Tracking 1997 to 2024.pbix — Complete interactive Power BI report file.

wuenic_input_to_pdf.xlsx — Raw data source file used for ingestion and transformation.

/.jpg assets — Includes 4 high-resolution interface screenshots (Desktop, Interactive Analysis, Mobile Layout, and Data Model Schema) utilized for documentation.
