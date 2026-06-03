Global Immunization Analytics Dashboard (1997–2024)

📊 Project Overview
An end-to-end Power BI business intelligence solution engineered to track, model, and visualize global vaccination coverage data across nearly three decades. This project transforms raw, fragmented public health data into an interactive executive tracking system—demonstrating advanced data modeling (Star Schema), ETL optimization via Power Query, and executive mobile-responsive design.

📈 Executive KPI Baselines
Global Average Coverage: ~87.5% (Calculated via optimized average aggregations)

Vaccines Tracked: 16 unique vaccines (Accurately capturing multi-dose series including Ipv1, Ipv2, and pol3 via distinct counts)

Global Scope: 195 unique countries monitored

🛠️ Data Architecture & Modeling
A core focus of this project was migrating away from a brittle flat-file structure to implement an optimized, high-performance Star Schema. Normalizing the data model ensures rapid query performance, eliminates data redundancy, and guarantees clean DAX context evaluation.

Plaintext
                  ┌───────────────┐
                  │  Dim_Country  │
                  └───────┬───────┘
                          │ 1
                          │
                          │ *
┌───────────────┐   * ┌───┴────────────┐ * ┌─────────────────┐
│  Dim_Vaccine  ├───══► Fact_Vaccination ◄══─┤    Dim_Date     │
└───────────────┘ 1   └────────────────┘   1 └─────────────────┘
Centralized Fact Table: Fact_Vaccination captures granular, yearly immunization coverage percentages across global territories.

Dimension Tables: Dim_Country, Dim_Vaccine, and Dim_Date are connected via strict 1:N (one-to-many) unidirectional relationships to protect filter context integrity.

Data Integrity via Power Query (M): Cleaned complex multi-dose naming conventions, handled missing data anomalies, and filtered out blank entries to guarantee reporting accuracy.

🔢 Core DAX Measures
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
🚀 Analytics Experience & UI/UX Design
Desktop Analytics Experience
The desktop interface is built on a professional 16:9 widescreen layout featuring a dark blue corporate header banner and an intuitive analytical flow:

3-Card KPI Control Panel: Positioned at the top left for instant macro-level insight.

Dynamic Geographic Tracking: An integrated World Map for spatial distribution analysis and regional hot-spotting.

Trend & Ranking Analysis: A historical Line Chart paired with a Clustered Bar Chart to instantly identify top and bottom-performing nations.

Deep-Dive Interactive Filters: Features a dedicated Vaccine Dropdown Slicer (with blank values programmatically removed via Basic Filtering) and a Year Slider for cross-highlighting.

📱 Executive Mobile-First Optimization
To support field stakeholders and executives on the move, the entire dashboard was refactored for mobile devices. All 10 native page elements were reorganized into a clean, single-column vertical scrolling experience that retains full interactive capabilities without layout distortion.

🛠️ Tech Stack & Advanced Competencies
Power BI Desktop: Star schema architecture, explicit DAX engineering, and cross-filtering optimization.

Power Query (M): ETL pipeline design, schema normalization, and data type validation.

UI/UX Design: Corporate color theory, visual hierarchy layout engineering, and mobile-first responsive design.

📂 Repository Structure
Plaintext
├── wuenic_input_to_pdf.xlsx                                    # Raw data source file used for ETL
└── /assets/                                                    # Documentation assets
    ├── desktop_dashboard.jpg
    ├── interactive_analysis.jpg
    ├── mobile_layout.jpg
    └── data_model_schema.jpg
🔒 Note on Source Files: The interactive .pbix project file is withheld publicly to protect proprietary design architecture, but is fully available upon request for interview and professional evaluation purposes.
