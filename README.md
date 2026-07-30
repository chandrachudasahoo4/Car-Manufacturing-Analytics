# 🚗 Car Manufacturing Dataset – Data Cleaning & Transformation Project

## 📌 Project Overview

This project simulates a real-world **Car Manufacturing Company** where data is collected from multiple enterprise systems such as:

- Product Lifecycle Management (PLM)
- Bill of Materials (BOM)
- Manufacturing Execution System (MES)
- IoT Sensors
- Supplier Management System
- Warranty Management
- Quality Inspection System

The purpose of this project is to perform **industry-level Data Cleaning and Data Transformation** using Python and Pandas to improve manufacturing analytics, traceability, production quality, and operational efficiency.

---

# 📂 Project Structure

```
Car-Manufacturing-Dataset/
│── production_events.csv
│── quality_inspection.csv
│── sensor_readings.csv
│── supplier_master.csv
│── bom_master.csv
│── work_orders.csv
│── tool_master.csv
│── calibration_master.csv
│── operator_master.csv
│── warranty_claims.csv
│── README.md
```

---

# 🎯 Business Use Case

An automotive OEM integrates data from:

- Manufacturing Execution System (MES)
- Product Lifecycle Management (PLM)
- Bill of Materials (BOM)
- IoT Sensor Network
- Supplier Master
- Quality Inspection
- Warranty Claims

However, inconsistent timestamps, invalid sensor readings, duplicate production events, inconsistent supplier information, and poor defect logging affect:

- Overall Equipment Effectiveness (OEE)
- First Pass Yield (FPY)
- Product Traceability
- Warranty Analysis
- Recall Risk
- Production Planning

This project cleans and transforms raw manufacturing data into analytics-ready datasets.

---

# 📁 Dataset Description

## 1. production_events.csv

Contains production events recorded from assembly lines.

Example Columns

- Event_ID
- VIN
- Work_Order
- Model
- Line
- Station
- Timestamp
- Part_Number
- Supplier_Code
- Operator_ID
- Tool_ID
- Shift
- BOM_Status

---

## 2. quality_inspection.csv

Contains quality inspection reports.

Example Columns

- Inspection_ID
- VIN
- Defect_Code
- Defect_Status
- Inspection_Result
- Inspector_ID
- Inspection_Source

---

## 3. sensor_readings.csv

Contains machine sensor data.

Example Columns

- Sensor_ID
- Timestamp
- Torque
- Temperature
- Pressure
- Humidity
- Machine_ID

---

## 4. supplier_master.csv

Supplier information.

Example Columns

- Supplier_Code
- Supplier_Name
- City
- Country
- Supplier_Type
- Quality_Rating
- On_Time_Delivery
- PPM_Defects

---

## 5. bom_master.csv

Bill of Materials information.

---

## 6. work_orders.csv

Production work orders.

---

## 7. tool_master.csv

Torque tool information.

---

## 8. calibration_master.csv

Calibration schedule and correction factors.

---

## 9. operator_master.csv

Operator information.

---

## 10. warranty_claims.csv

Vehicle warranty claims.

---

# 🧹 Data Cleaning Tasks (1–10)

## 1. Line and Station Standardization

- Remove leading/trailing spaces
- Convert to uppercase
- Standardize naming conventions

Example

```
ga-1
 GA-1
Ga-1

↓

GA-1
```

---

## 2. Timestamp Normalization

Convert timestamps into standard datetime format.

Example

```
2026/03/10 06:70

↓

2026-03-10 07:10
```

---

## 3. Part Number Normalization

- Uppercase
- Remove spaces
- Validate against BOM

Example

```
123-abc

↓

123-ABC
```

---

## 4. Torque Parsing

Convert torque values into Numeric (Nm).

Example

```
45 Nm
45.0
45

↓

45.0 Nm
```

---

## 5. Temperature Conversion

Convert all temperatures into Celsius.

Example

```
85F

↓

29.4°C
```

---

## 6. Defect Normalization

Normalize values such as

- NA
- None
- OK
- Reject
- Repair

into standard categories.

---

## 7. VIN Validation

- Validate VIN format
- Remove spaces
- Mask VIN before exporting

Example

```
XX123456789

↓

XXXXXXX6789
```

---

## 8. Supplier Code Standardization

Normalize supplier codes and merge with supplier master.

Example

```
sup-09

↓

SUP-09
```

---

## 9. Duplicate Production Events

Remove duplicate records using

```
VIN
Station
Timestamp
```

---

## 10. Sensor Calibration

Apply calibration factor and identify sensor drift.

---

# 🧹 Data Cleaning Tasks (11–20)

## 11. Cycle Time Validation

Identify unrealistic production cycle times.

---

## 12. Work Order Validation

Validate

```
Work Order → VIN
```

relationships.

---

## 13. Rework Loop Detection

Identify vehicles passing through the same station multiple times.

---

## 14. Shift Derivation

Automatically derive shifts from timestamps.

Example

| Time | Shift |
|------|-------|
|06:00–14:00|Morning|
|14:00–22:00|Evening|
|22:00–06:00|Night|

---

## 15. Scrap Reason Mapping

Map scrap reason codes into descriptions.

---

## 16. Unit Conversion

Standardize

- Torque
- Temperature
- Pressure

into common units.

---

## 17. Outlier Detection

Identify abnormal sensor values using threshold or statistical methods.

---

## 18. Inspection Source Tagging

Tag inspections as

- Manual
- Automated

---

## 19. Tool ID Mapping

Link Tool_ID with Tool Master.

---

## 20. BOM Version Validation

Validate BOM version using effectivity dates.

---

# 📊 Data Transformation

## 1. Overall Equipment Effectiveness (OEE)

```
OEE =
Availability
×
Performance
×
Quality
```

---

## 2. First Pass Yield (FPY)

Calculate FPY for every station and production line.

---

## 3. Defects Per Unit (DPU)

Calculate

```
DPU =
Total Defects
/
Total Units
```

Generate Pareto charts by defect type.

---

## 4. MTBF & MTTR

Calculate

- Mean Time Between Failures
- Mean Time To Repair

---

## 5. Cycle Time Analysis

Analyze production bottlenecks using cycle time distribution.

---

## 6. SPC Control Charts

Generate

- X-Bar Chart
- R Chart

for

- Torque
- Temperature

---

## 7. Traceability Chain

Build complete traceability

```
Supplier
↓

Part

↓

VIN

↓

Warranty Claim
```

---

## 8. Andon Response Metrics

Measure production alert response time.

---

## 9. Cost of Poor Quality (COPQ)

Estimate production losses due to defects.

---

## 10. Throughput Analysis

Analyze throughput using Little's Law.

---

## 11. PFMEA Risk Score

Calculate

```
Severity
×
Occurrence
×
Detection
```

---

## 12. Energy Consumption

Calculate energy consumed per vehicle.

---

## 13. Rework Analytics

Measure

- Rework %
- Reinspection %

---

## 14. Supplier Performance

Calculate

- Supplier PPM
- On-Time Delivery %

---

## 15. Tool Calibration KPI

Measure calibration compliance.

---

## 16. Shift Performance

Compare production performance across shifts.

---

## 17. Warranty Analytics

Identify early failure patterns using warranty claims.

---

## 18. Predictive Quality Features

Generate features for Machine Learning models.

---

## 19. Line Balancing

Compare

- Takt Time
- Cycle Time

---

## 20. Production Plan vs Actual

Build production variance dashboard.

---

# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

---

# 📈 Project Outcome

After completing this project, the dataset becomes:

- Clean
- Consistent
- Analytics Ready
- Traceable
- Suitable for Dashboarding
- Suitable for Machine Learning
- Suitable for Manufacturing KPI Reporting

---

# 👨‍💻 Author

**Chandrachuda Sahoo**

Car Manufacturing Data Cleaning & Transformation Project

```
Industry-Level Manufacturing Analytics using Python & Pandas
```