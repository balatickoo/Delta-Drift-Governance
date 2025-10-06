# Delta-Drift-Governance
Databricks-native Responsible AI framework for data &amp; model drift observability and governance
# 🧩 Delta Drift Governance Architecture  
**Responsible AI | Databricks | Delta Lake | Observability**

---

## 🌐 Overview

As enterprises move from isolated models to production pipelines, **data and model drift** become the silent disruptors of reliability.  
This project demonstrates a **governance-first architecture** for **detecting, summarizing, and visualizing drifts** within Databricks’ serverless environment, using Delta tables, Matplotlib, and schema-safe writes.

I architected this framework based on my experience leading **data engineering and ML pipelines at Mashreq**, integrating reliability and drift observability into production-scale environments.

---

## ⚙️ Core Objectives

| Objective | Description |
|------------|-------------|
| 🧠 **Monitor Model Drift** | Track PSI (Population Stability Index) and data distribution shifts in near-real time |
| 🧾 **Schema-Safe Writes** | Handle append/overwrite logic robustly in Delta Lake |
| 🔍 **Governance JSON Telemetry** | Export structured summaries for dashboards and audit systems |
| 📊 **Visualization Layer** | Generate PSI trendlines and heatmaps for interpretability |
| 🔔 **Alert Readiness** | Enable export to Splunk or Databricks SQL Alerts (optional) |

---

## 🧱 Architecture Blueprint

The following diagram represents the **A1–A6 modular architecture**:  
✅ Drift ingestion → PSI calculation → summary → visualization → governance JSON export → optional Splunk integration

![Architecture](visuals/DriftGovernance_WorkflowDesign.png)

---

## 🔢 Key Functional Modules

| Cell | Function | Description |
|------|-----------|-------------|
| **A1** | Load and prepare sample predictions | Simulate baseline/current model outputs |
| **A2** | Schema-safe Delta write | Add overwrite-safe logic to Delta tables |
| **A3** | Drift computation | Compute PSI, null-rate change, and statistical deltas |
| **A4** | Visualization | Generate time series, heatmaps, and drift level mapping |
| **A5** | JSON export | Create governance telemetry and dashboard metadata |
| **A6** | Dashboard packaging | Compose consolidated JSON for audit dashboards or Splunk |

---

## 🧮 Proof of Execution

### PSI Summary Table
![PSI Summary](visuals/psi_summary_table.png)

### Time Series Trends
![Time Series](visuals/psi_timeseries.png)

### Heatmap
![PSI Heatmap](visuals/psi_heatmap.png)

### Drift Governance Summary
![Governance Summary](visuals/delta_drift_visual_gallery.png)

---

## 🧰 Challenge → Resolution Log

| Challenge | Resolution |
|------------|-------------|
| Delta table append/overwrite issues | Added schema-safe write logic with `.option("overwriteSchema","true")` |
| Serverless RDD restriction | Replaced `.rdd.isEmpty()` with `.count()` validation |
| Visualization gaps | Used Matplotlib for PSI heatmaps and trend series |
| DBFS access denial | Rerouted JSON export to `/Workspace/Shared` or Data URI link |
| Interpretation clarity | Introduced drift-level bins and structured governance telemetry |

---

## 📁 Repository Structure


