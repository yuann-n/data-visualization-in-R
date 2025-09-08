# data-visualization-in-R
# E-Commerce Dashboard

**Author:** Zhiyuan Jiang

## Overview

This repository contains an interactive E‑Commerce dashboard built with **flexdashboard** and **Shiny**. The dashboard visualizes customer distribution, demographics (age and gender), profit and sales analytics, delivery center performance, purchase decision time, and basic regression diagnostics. Preprocessed data files are included as `.rds` resources for faster loading.

---

## Features

* **Worldwide Map:** Interactive choropleth map (Highcharter) showing customers by country. Clicking a country updates demographic charts.
* **Age & Gender Distribution:** Plotly pie charts displaying age group and gender distribution for the selected country and year.
* **Profit Analysis:** Top profit charts by category/brand, support for per-country drill-down via Plotly click events.
* **Delivery Center Performance:** Delivery time distribution across distribution centers and order status breakdown.
* **Purchase Decision Time:** Scatter/line plots of average time to purchase versus number of items, with grouping options.
* **Regression Diagnostics:** Q-Q plot and Cook's distance plots for a sample regression model (for demonstration).

---

## Repository Structure

```
/project-root
  ├─ dashboard.Rmd        # Flexdashboard (Shiny runtime) main file
  ├─ distribution_centers.rds
  ├─ inventory_items_old.rds
  ├─ order_items.rds
  ├─ orders.rds
  ├─ products_old.rds
  ├─ users_old.rds
  ├─ start_to_end_purchase_events.rds
  └─ README.md
```

All `.rds` files listed above are expected to be in the project directory.

---

## Requirements

* R >= 4.1 (recommended)
* CRAN packages (install if missing):

  * `tidyverse`, `dplyr`, `ggplot2`, `plotly`, `highcharter`, `flexdashboard`, `shiny`, `countrycode`, `showtext`, `hms`, `broom`, `ggrepel`, `shinydashboard`, `corrplot`, `here`, `magrittr`

Install example:

```r
install.packages(c(
  "tidyverse", "flexdashboard", "shiny", "highcharter", "plotly",
  "countrycode", "showtext", "hms", "broom", "ggrepel", "shinydashboard", "corrplot"
))
```

**Note:** Some features use `font_add_google()` which requires network access to Google Fonts. If the deployment environment has no outbound internet, consider replacing with system fonts or bundling fonts locally.

---

## How to Run Locally

1. Place the `.rds` resource files in the project root (same folder as `dashboard.Rmd`).
2. In RStudio, open `dashboard.Rmd` and click **Run Document**. This will launch the flexdashboard with Shiny runtime in the Viewer or browser.

Alternatively, run from R console:

```r
rmarkdown::run("dashboard.Rmd")
```

---

## Deployment

You can deploy to shinyapps.io or other Shiny hosting services. Recommendations:

* **Do NOT** commit API tokens, secrets, or `rsconnect::setAccountInfo(...)` calls containing tokens to the repository. Remove or disable these lines before pushing.
* Use `rsconnect::deployApp()` or RStudio Publish for shinyapps.io deployment.

Example (interactive deployment):

```r
# Use interactive authentication in RStudio or set RSCONNECT_PROTOCOL/RSCONNECT_TOKEN securely
rsconnect::deployApp(appDir = ".")
```

---

## Data Notes & Preprocessing

* The dashboard uses preprocessed `.rds` files to speed up loading. If you need to regenerate them from CSVs, follow the original preprocessing scripts (not included).
* Country names must be standardized for `countrycode()` to map to ISO3 (`iso3c`). The Rmd includes small recodes for common misspellings (e.g., "Brasil" → "Brazil").
* Timezone: timestamps are parsed with `tz = 'UTC'`.


---

## Contact

Author: Zhiyuan Jiang

For issues or collaboration, open an issue in this repository or contact the author directly.

---

