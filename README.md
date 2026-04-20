# EThio-Nightlights
### Spatiotemporal Dynamics of Economic Activity in Ethiopia
#### A Big Data Analytics Approach Using Satellite Night-time Luminosity, 2014–2022

---

## Overview

This project demonstrates the application of **big data analytics and remote sensing** to development economics, producing sub-national evidence on spatial inequality and economic trajectory that is directly relevant to **country-level reporting frameworks** — including the UN Sustainable Development Goals (SDG 7, SDG 10, SDG 11), World Bank country diagnostics, and UNDP Human Development country reports.

Traditional country reports on development access rely on household surveys (DHS, MICS) which are expensive, infrequent, and spatially coarse. Satellite-derived night-time luminosity (NTL) offers a scalable, high-frequency, high-resolution alternative that can monitor development dynamics between survey cycles — at a granularity no conventional data collection method can match.

Ethiopia is an analytically significant case: the country undertook substantial infrastructure expansion between 2014 and 2022, while also experiencing conflict (Tigray, 2020–2022), climate stress (Horn of Africa drought), and administrative restructuring. This combination makes it an ideal setting for evaluating NTL as a responsive and spatially explicit development indicator.

## please scroll down for visualisations.
---

## Big Data Dimensions

The scale of computation in this analysis places it firmly within the **big data domain**:

| Dimension | Detail |
|---|---|
| Spatial coverage | 1.1 million km² (Ethiopia) |
| Temporal coverage | 2014–2022, biennial composites |
| Input raster resolution | 100 m (WorldPop), ~500 m (VIIRS) |
| Pixel count per layer | ~110 million pixels (WorldPop at 100 m) |
| Total observations processed | >500 million pixel-year observations across 5 time points |
| Administrative units analysed | 12 regional states × ~70 zones |
| Cloud compute platform | Google Earth Engine (serverless, distributed) |

Processing this volume of satellite and population data on a local machine is computationally infeasible. Google Earth Engine's distributed cloud infrastructure handles petabyte-scale geospatial datasets through parallelised server-side computation — a standard big data architecture applied to a development analytics use case.

---

## Analytical Framework

Night-time light (NTL) radiance captured by the VIIRS satellite sensor is an established proxy for economic activity, infrastructure density, and urbanisation intensity, following Henderson, Storeygard & Weil (2012). NTL integrates signals from electricity infrastructure, commercial activity, road lighting, and industrial operations — making it a composite indicator of spatial development intensity rather than a narrow measure of any single infrastructure dimension.

**Three analytical outputs are produced:**

**1. Current state (2022)** — Spatial development gap at zonal and regional level, measuring the proportion of the inhabited population residing in zones with NTL radiance below the detection threshold. This maps development inequality across ~70 zones and 12 regions.

**2. Temporal trajectory (2014–2022)** — Linear trend slope estimated per pixel via ordinary least squares regression across five annual composites. Slope (nW/cm²/sr per year) represents the sustained direction and magnitude of economic activity change — distinguishing growth corridors from stagnant or declining zones.

**3. Population-weighted access** — NTL development gap weighted by WorldPop gridded population at 100 m resolution, ensuring that sparsely populated dark zones do not distort national or regional aggregates. This is the metric most directly comparable to country report indicators.

---

## Relevance to Country Reports

| Country Report Framework | Indicator this analysis informs |
|---|---|
| SDG 7 (Affordable and Clean Energy) | Proxy for energy access distribution at sub-national level |
| SDG 10 (Reduced Inequalities) | Spatial distribution of development intensity across zones |
| SDG 11 (Sustainable Cities) | Urban growth hotspot identification and peri-urban expansion |
| World Bank Country Economic Memorandum | Sub-national economic activity proxy, regional convergence |
| UNDP Human Development Report | Spatial dimension of human development distribution |
| Ethiopia 10-Year Development Plan (2021–2030) | Baseline and progress monitoring for regional infrastructure targets |

NTL-based analytics are particularly valuable for **countries where administrative data is incomplete, delayed, or spatially uneven** — which characterises much of sub-Saharan Africa. The 2022 snapshot aligns with the Ethiopia 10-Year Development Plan baseline period, while the 2014–2022 trend captures the full arc of the Growth and Transformation Plan II implementation period — providing a data-driven complement to official country reporting.

---

## Key Findings

- National mean NTL radiance increased from **0.081 nW/cm²/sr (2014)** to **0.289 nW/cm²/sr (2022)** — a **253.5% increase** consistent with documented electrification expansion, industrial park development, and urban growth during this period.
- The **spatial development gap** at 0.3 nW/cm²/sr threshold stands at **66%** of the inhabited population in 2022, reflecting persistent rural-urban and inter-regional inequality.
- **Northeast zones** (Afar, Tigray, north Amhara) show the highest development deficit, while the **Addis Ababa metropolitan corridor** shows the lowest — a spatial gradient consistent with infrastructure investment patterns reported in national development planning documents.
- **Growth hotspot zones** (linear trend slope > 0.040 nW/cm²/sr per year) are spatially concentrated, indicating that infrastructure investment has not yet produced broad convergence across zones.
- The **population-weighted overlay** reveals a mismatch between zones with the lowest absolute luminosity and zones with the largest underserved populations — a finding with direct implications for infrastructure targeting in country-level planning.

---

## Data Sources

| Dataset | Description | Resolution | Source |
|---|---|---|---|
| VIIRS VCMCFG | Cloud-free monthly NTL composites | ~500 m | NOAA via GEE |
| WorldPop GP 100 m | Unconstrained population estimates | 100 m | WorldPop via GEE |
| FAO GAUL 2015 | Administrative boundaries (regional and zonal) | — | FAO via GEE |

**Note on dataset selection:** The stray-light corrected product (VCMSLCFG) introduces an artificial noise floor of ~0.3–0.5 nW/cm²/sr over equatorial regions, distorting low-radiance rural values. VCMCFG is the methodologically appropriate choice for development gap analysis in sub-Saharan Africa.

---

## Visualisations

### s_1 — Spatial Development Gap at Zonal Level (2022)
![Spatial development gap — zonal level](Images/s_1.png)

### s_2 — NTL Trend Slope 2014–2022
![NTL trend slope 2014–2022](Images/s_2.png)

### s_3 — NTL Absolute Change 2014–2022
![NTL absolute change 2014–2022](Images/s_3.png)

### s_4 — Population Distribution (WorldPop 2020)
![Population distribution](Images/s_4.png)

### s_5 — Ethiopia Night-time Lights 2022
![Ethiopia night-time lights 2022](Images/s_5.png)

### s_6 — Spatial Development with Population Overlay
![Spatial development with population overlay](Images/s_6.png)

### s_7 — Urban and Public Infrastructure Growth Hotspots
![Growth hotspots](Images/s_7.png)

### s_8 — Spatial Development Gap at Regional Level (2022)
![Spatial development gap — regional level](Images/s_8.png)

---

## Repository Structure

```
EThio-Nightlights/
│
├── Images/
│   ├── s_1.png    Spatial development gap — zonal level
│   ├── s_2.png    NTL trend slope 2014–2022
│   ├── s_3.png    NTL absolute change 2014–2022
│   ├── s_4.png    Population distribution
│   ├── s_5.png    Ethiopia night-time lights 2022
│   ├── s_6.png    Spatial development with population overlay
│   ├── s_7.png    Growth hotspots
│   └── s_8.png    Spatial development gap — regional level
│
├── ethiopia_ntl_temporal_v9.js             Temporal analysis (2014–2022)
├── ethiopia_electricity_access_gee_v6.js   Development gap analysis (2022)
└── README.md
```

---

## Tools and Environment

| Tool | Role |
|---|---|
| Google Earth Engine | Distributed cloud computation over petabyte-scale rasters |
| VIIRS VCMCFG | Annual NTL composite generation and trend estimation |
| ee.Reducer.linearFit | Pixel-level OLS trend regression across time series |
| ee.Reducer.percentile | Adaptive visualisation stretch (99th percentile) |
| ee.Reducer.sum / reduceRegions | Zonal and national population aggregation |
| WorldPop | Population-weighted development gap denominator |

All computation is server-side on GEE infrastructure. No local processing required beyond the script editor.

---

## Limitations

- NTL radiance is a composite signal and cannot independently disaggregate electricity access from road lighting, commercial activity, or industrial output. Findings represent development intensity rather than any single infrastructure dimension.
- The VCMCFG instrument has a detection floor of approximately 0.20–0.30 nW/cm²/sr in this region. Threshold selection is sensitive at this boundary and should be validated against sub-national survey data where available.
- Administrative boundaries (FAO GAUL 2015) predate recent restructuring in southern Ethiopia and may not reflect all current zonal boundaries.
- WorldPop 2020 is used as the population denominator throughout; temporal mismatch with the 2014 NTL baseline is a limitation for early-period population weighting.

---

## References

- Henderson, J. V., Storeygard, A., & Weil, D. N. (2012). Measuring economic growth from outer space. *American Economic Review*, 102(2), 994–1028.
- Donaldson, D., & Storeygard, A. (2016). The view from above: Applications of satellite data in economics. *Journal of Economic Perspectives*, 30(4), 171–198.
- Falchetta, G., Pachauri, S., Parkinson, S., & Byers, E. (2019). A high-resolution gridded dataset to assess electrification in sub-Saharan Africa. *Scientific Data*, 6, 110.
- Elvidge, C. D., et al. (2017). VIIRS night-time lights. *International Journal of Remote Sensing*, 38(21), 5860–5879.
- Federal Democratic Republic of Ethiopia. (2021). *Ten-Year Development Plan 2021–2030*. National Planning Commission, Addis Ababa.

---

*Data accessed via Google Earth Engine public data catalogue. Administrative boundaries: FAO GAUL 2015. Population: WorldPop Global Project, University of Southampton. Night-time lights: NOAA National Centers for Environmental Information.*
