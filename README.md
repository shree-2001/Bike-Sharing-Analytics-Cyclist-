# BIBA – Hustle_ADJ (Cyclist) Analytics & CRM

A complete Business Intelligence & Business Analytics (BIBA) project for **Cyclist** — a fictional European bike manufacturer and bike-sharing provider — combining **data engineering**, **CRM (Zoho)**, and **Power BI dashboards** to deliver actionable insights across marketing, operations, and customer support.

---

## 🧭 Overview

This repo showcases an end‑to‑end analytics workflow:

- **Data acquisition & preparation** (Kaggle dataset of bike trips; Python cleaning/merging; PostgreSQL tables).
- **Process analytics** aligned to **Six Sigma (DMAIC)** and a practical **Marketing Funnel**.
- **Zoho CRM implementation** for campaigns, services, and case profiling (lead → customer, feedback → resolution).
- **Power BI** dashboards (Hustle_ADJ.pbix) for usage insights by bike type, geography, time, station, and customer segment.

> The goal is to make data‑driven decisions that improve customer satisfaction, streamline support, and optimize marketing and operations.

---

## 📦 Repo Structure

```
.
├── powerbi/
│   └── Hustle_ADJ.pbix          # Main Power BI report (open with Power BI Desktop)
├── data/
│   ├── raw/                     # Raw CSVs from Kaggle (place here)
│   └── processed/               # Cleaned & merged outputs
├── sql/
│   └── cyclist_schema.sql       # Example DDL to create tables in PostgreSQL
├── notebooks/
│   └── 01_prepare_data.ipynb    # Optional: Python data prep notebook
├── assets/
│   ├── dashboards/              # Exported PNGs of report pages for README gallery
│   └── logos/
└── README.md
```

> Tip: If you only need the dashboards, open `powerbi/Hustle_ADJ.pbix` in **Power BI Desktop**.

---

## 🧰 Tech Stack

- **Power BI Desktop** – interactive dashboards & DAX
- **Python (optional)** – data cleaning & joining (pandas)
- **PostgreSQL (optional)** – curated tables for CRM & BI
- **Zoho CRM** – marketing campaigns, services, feedback
- **Zoho Analytics (optional)** – supplemental reporting

---

## 🗂️ Data

- **Domain**: Bike‑sharing trips and customer interactions for *Cyclist* (fictional company).
- **Source**: Kaggle (CSV). Download via Kaggle API or website and place files under `data/raw/`.
- **Key fields**: `ride_id`, `rideable_type`, `member_casual`, `start_station_name`, `start_station_id`, `end_station_name`, `end_station_id`, `start_time`, `end_time`, `start_lat`, `start_lng`, `end_lat`, `end_lng`.

### Preparation (summary)
1. Load raw CSVs.
2. **Merge** datasets (consistent schema).
3. **Clean**: drop duplicates, handle nulls, fix datatypes.
4. **Split** by `rideable_type` if needed (e.g., classic vs. electric).
5. **Persist** to PostgreSQL (optional) and/or export cleaned CSVs to `data/processed/`.

---

## 🗄️ PostgreSQL Schema (example)

Create a simple table for curated trips:

```sql
CREATE SCHEMA IF NOT EXISTS cyclist;

CREATE TABLE IF NOT EXISTS cyclist.trips (
  ride_id            TEXT PRIMARY KEY,
  rideable_type      TEXT,
  member_casual      TEXT,
  start_station_id   TEXT,
  start_station_name TEXT,
  end_station_id     TEXT,
  end_station_name   TEXT,
  start_time         TIMESTAMP,
  end_time           TIMESTAMP,
  start_lat          DOUBLE PRECISION,
  start_lng          DOUBLE PRECISION,
  end_lat            DOUBLE PRECISION,
  end_lng            DOUBLE PRECISION
);
```

> Load your cleaned CSV into `cyclist.trips` (COPY, \\copy, or a GUI client).

---

## 🧩 Zoho CRM Implementation (high‑level)

1. Sign in to **Zoho CRM** → **Settings** → **Data Administration** → **Import**.
2. Choose **Leads/Deals/Products/Cases** as needed.
3. Upload the **CSV** export (from `data/processed/`), map fields, import.
4. Use **Campaigns** for outbound marketing, **Cases** for customer issues, and **Products/Services** for catalog & order tracking.
5. Enable **dashboards/reports** or sync to **Zoho Analytics** for cross‑module insights.

---

## 📊 Power BI Dashboards

Open `powerbi/Hustle_ADJ.pbix` to explore interactive pages such as:

- **Usage by Bike Type & Geography**  
  Compare **classic vs. electric** usage with aggregated `start_lat/end_lat` and `start_lng/end_lng`; map top countries/cities/stations.

- **Member vs. Casual Trends (Monthly)**  
  Time series of trips by `member_casual` to see seasonality and growth.

- **Station Performance**  
  Top **start/end** stations; concentrations by latitude/longitude; patterns that inform station placement and inventory.

- **Population & Demand Signals**  
  Average `start_lat` paired with **population** (if present) to infer demand hotspots.

- **Customer Support & Resolution** (optional)  
  Funnel/KPIs from feedback intake → assignment → QA → final resolution and satisfaction.

### Exporting Visuals for the README
In Power BI Desktop: **File → Export → Export to PDF** or **Export → PNG** for each page. Save images under `assets/dashboards/` and link them below.

---

## 🖼️ Dashboard Gallery (placeholders)

> Replace the image paths after exporting PNGs from Power BI.

![Usage by Bike Type](assets/dashboards/01_bike_type_usage.png)
![Member vs Casual Monthly](assets/dashboards/02_member_casual_monthly.png)
![Station Performance](assets/dashboards/03_station_performance.png)
![Geo Coverage](assets/dashboards/04_geo_coverage.png)

---

## 🚀 Getting Started

### Prerequisites
- **Power BI Desktop** (Windows) – to open `.pbix`
- **Python 3.9+** with `pandas` (optional for data prep)
- **PostgreSQL 13+** (optional if you want a database layer)

### Quickstart
1. Clone the repo and open `powerbi/Hustle_ADJ.pbix` in Power BI Desktop.
2. If using local CSVs, update **Data Source Settings** to point to your `data/processed/` path.
3. Refresh the model to rebuild visuals.

### Reproduce Data Prep (optional)
- Use the sample notebook `notebooks/01_prepare_data.ipynb` or your own script to:
  - Read CSVs from `data/raw/`
  - Clean & merge
  - Save curated outputs to `data/processed/`
  - (Optional) Load into PostgreSQL using `psycopg2` or a GUI tool

---

## 🔧 Development Notes

- Keep PBI measures (DAX) self‑documented with clear names & descriptions.
- Prefer **star schema** (fact trips + dimension stations/bikes/customers) for scalable models.
- For CRM alignment, use consistent IDs and datatypes across exports/imports.
- Track **versioned** exports of CSVs to ensure reproducibility of visuals.

---

## ✅ KPIs & Questions This Project Answers

- What’s the trend of **trips** by **bike type** and **customer segment**?
- Which **stations** and **regions** drive the most activity?
- How do **member vs casual** behaviors differ month‑over‑month?
- Where are opportunities for **marketing campaigns** and **station expansion**?
- How effective is the **feedback → resolution** support loop?

---

## 👥 Contributors

- **Ajith Gundan** – Data prep, dashboards
- **Dineshkumar Lingapandiyan** – CRM setup, dashboards
- **Jayashree Rajkumar** – Documentation, dashboards

> Equal contributions across CRM, Power BI, and documentation.

---

## 📄 License

Choose a license that fits your needs (e.g., MIT).

---

## 🙌 Acknowledgements

- Kaggle dataset providers and community
- Zoho CRM & Zoho Analytics
- Microsoft Power BI

---

## ✉️ Contact

For questions, please open an **Issue** or reach out via email.
