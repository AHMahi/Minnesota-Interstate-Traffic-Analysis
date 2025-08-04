# Minnesota Interstate Traffic Volume – Tableau Dashboard

## Project Overview

- **What**: Tableau Dashboard analyzing interstate traffic volumes across year → month → day → hour, weather, and holiday influences.  
- **Why**: To help Minnesota transportation authorities forecast traffic, plan highway work, and manage congestion.
- **How**: Excel & Tableau used to clean & model data. Dashboard built using calculated fields, Date‑time hierarchies, filters, and Story points. 

---

## Data Sources

| Data Type              | Source                                             | Notes                                                                 |
|------------------------|----------------------------------------------------|-----------------------------------------------------------------------|
| Traffic & Weather Data | Metro_Interstate_Traffic_Volume.csv (UCI / MnDOT) | Combined dataset (2012–2018) with hourly traffic, weather, and holiday tags. |
| Holiday Lookup         | Included in dataset (`holiday` column)            | No external lookup required; common holidays already tagged.         |
| Weather Details        | Included in dataset (e.g., `temp`, `clouds_all`)  | Weather metrics directly available; no merging from external sources. |

RAW `.csv` files are in `/Datasets/`.

No additional lookup tables were used for this project.

---

## Business Problem & Key Questions

1. How do traffic volumes trend across years down to the hour?  
2. Is traffic volume influenced by weather (e.g. smoke, clear, cloudy)?  
3. Which holidays consistently show peak traffic volumes?  

---

## Implementation Process/Steps

1. **Import CSVs** into Tableau Desktop.  
2. Clean and transform data (via Tableau Prep & data pane):
   - Removed nulls/outliers, filtered out incomplete months  
   - Created `Date Hierarchy` using `DATEPART()` functions  
   - Flag holidays via `IF [date] IN (…) THEN “New Year”, etc.`  
3. Create dashboards:
   - Sheet 1: **Traffic volume trend** (Year → Month → Day → Hour hierarchy)  
   - Sheet 2: **Traffic vs Weather** using scatter plots or box-and-whisker  
   - Sheet 3: **Holiday analysis**, color-coded and sized by traffic  
4. Design Dashboard with interactive filters: year selector, weather dropdown, holiday tooltip  
5. Add **Story Point view** to narrate key insights (optional step if preferred)  
6. Use Tableau Public to publish workbook and copy sharable link into your README.

---

## Findings
| Question | Findings |
|----------|----------|
| **Yearly/Hourly Trend** | Volume peaked at ~2 – 3 million vehicles/week pre‑2018, with sharp decline mid‑2018 |
| **Weather vs Traffic** | Clear/cloudy conditions correlated with high volume; smoke and squall days saw significant drops |
| **Holiday Impact** | New Year holidays had the highest traffic peaks; Thanksgiving and Labor Day followed |

---

## Dashboard Screenshots
<img width="1864" height="815" alt="Dashboard 1 (2)" src="https://github.com/user-attachments/assets/ba511397-b33d-4fe0-83d8-33c3acd277b5" />

🔗 **View Live Dashboard on Tableau Public:**  
[Live Tableau Public Dashboard](https://public.tableau.com/views/HighwaytrafficconditionsforinfrastructureDevelopment/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)