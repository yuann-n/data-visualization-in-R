# data-visualization-in-R
# E-Commerce Dashboard

**Author:** Zhiyuan Jiang

## Overview

This eCommerce dashboard provides an interactive and insightful view into customer demographics, profitability, delivery performance, and purchase behavior. I used flexdashboard to build the entire dashboard structure, incorporating shiny to enable interactivity and adjust the layout within each page. Highcharter was used to create an interactive map, and plotly was employed to generate interactive data visualizations.

---

## Features

* **Worldwide Map:** Displays a global map showing customer distribution across different countries. Alongside the map, pie charts present the age and gender proportions of customers in each country. Users can click on any country on the map to view detailed demographic information specific to that region.
* **Profit Analysis:** Highlights the categories and brands generating the highest profits. Provides detailed breakdowns of profits by category and brand within each country. Users can click on the country bar chart on the left to update the right panel, reflecting the selected country's specific profit data.
* **Delivery Center Performance:** Shows the distribution of delivery times across different distribution centers. Visualizes the percentage of different delivery statuses (e.g., on-time, delayed) for each center. Enables users to understand the efficiency of each center and identify potential areas for operational improvement.
* **Purchase Decision Time:** Illustrates the relationship between purchase quantity and average decision-making time. Provides insights into customer behavior, showing how decision time increases as purchase quantity rises. Supports strategic planning by highlighting potential changes in customer decision-making with larger purchases.
* **Regression Diagnostics:** Offers a deeper analysis of data through a linear model that explores relationships within the dataset. Includes diagnostic plots such as the Q-Q plot and Cook's Distance plot to assess model fit and detect influential data points. Supports users in understanding the model's robustness and the data's suitability for linear analysis.

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

