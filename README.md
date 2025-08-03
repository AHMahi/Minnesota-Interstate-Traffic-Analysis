# Minnesota Interstate Traffic Volume – Tableau Dashboard

**Interactive analysis of hourly traffic volumes in the MN DOT dataset, exploring patterns over time, weather, and holidays.**

---

## 🧭 Project Overview

- **What**: Tableau Dashboard analyzing interstate traffic volumes across year → month → day → hour, weather, and holiday influences.  
- **Why**: To support transportation planning in Minnesota—help authorities forecast traffic, improve infrastructure decisions, and manage congestion periods.  
- **How**: Tableau Prep (optional) or Tableau Desktop used to clean & model data. Dashboard built using calculated fields, Date‑time hierarchies, filters, and Story points. 

---

## 📁 Data Sources

| Data Type | Source | Notes |
|-----------|--------|-------|
| Traffic counts | Metro_Interstate_Traffic_Volume.csv (MnDOT) | Hourly traffic data 2012–2018 with `holiday_flag` |
| Weather | NOAA historical weather / open source weather API | Merged manually or in Prep with traffic |
| (Optional) Holiday lookup | U.S. calendar APIs or manual CSV | For date tags like “New Year”, “Thanksgiving” |

RAW `.csv` files are in `/data/`. Any lookup tables go in `/bin/`.

---

## 🧠 Business Problem & Key Questions

1. How do traffic volumes trend across years down to the hour?  
2. Is traffic volume influenced by weather (e.g. smoke, clear, cloudy)?  
3. Which holidays consistently show peak traffic volumes?  

| Question | Findings |
|----------|----------|
| **Yearly/Hourly Trend** | Volume peaked at ~2 – 3 million vehicles/week pre‑2018, with sharp decline mid‑2018 |
| **Weather vs Traffic** | Clear/cloudy conditions correlated with high volume; smoke and squall days saw significant drops |
| **Holiday Impact** | New Year holidays had the highest traffic peaks; Thanksgiving and Labor Day followed |

---

## 🛠️ Implementation Pipeline

1. **Import CSVs** into Tableau Desktop.  
2. Clean and transform (via Tableau Prep or data pane):
   - Remove nulls/outliers, filter out incomplete months  
   - Create `Date Hierarchy` using `DATEPART()` functions  
   - Flag holidays via `IF [date] IN (…) THEN “New Year”, etc.`  
3. Create dashboards:
   - Sheet 1: **Traffic volume trend** (Year → Month → Day → Hour hierarchy)  
   - Sheet 2: **Traffic vs Weather** using scatter plots or box-and-whisker  
   - Sheet 3: **Holiday analysis**, color-coded and sized by traffic  
4. Design Dashboard with interactive filters: year selector, weather dropdown, holiday tooltip  
5. Add **Story Point view** to narrate key insights (optional step if preferred)  
6. Use Tableau Public to publish workbook and copy sharable link into your README.

---

## 🖼️ Dashboard Sketches

Place your screenshots here. Example:

