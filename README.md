# 🏃 Fitness Tracker App — Power BI Design
A personal fitness dashboard built in Power BI, designed to monitor individual health metrics over time. The report delivers a clean, app-like experience with dynamic personalization, interactive time filtering, and visually rich KPIs.

Dashboard Preview

https://github.com/user-attachments/assets/ccda60af-b9cb-40e8-9b1d-28cec8fa26cb

<br>


## 📐 Data Model

The report is built on a simple but effective star schema with three tables:

| Table | Role |
|---|---|
| `Metrics` | Fact table: stores all fitness measurements (steps, calories, heart rate, sessions) |
| `dimDate` | Date dimension: supports time intelligence with a Calendar hierarchy (Year → Quarter → Month → Weekday) |
| `dimUser` | User dimension: enables per-user filtering and personalization |

<br>


## 📊 Visuals Used

| Visual | Purpose |
|---|---|
| **Card** | KPI snapshots - Avg Heart Rate, Avg Daily Steps, Avg Daily Calories, Total Exercise Sessions, Health Score |
| **Donut Chart** | Health Score progress ring - splits score vs. remainder to 100 |
| **Bar Chart** | Metric performance vs. target ranges |
| **Line Chart** | Health Score trend over time with drill-down hierarchy |
| **Multi-Row Card** | Dynamic welcome text display |
| **Slicer** | Dropdown user selector (single-select, filters entire page) |
| **Bookmark Navigator** | Time period switcher (Year / Quarter / Month / Day) |
| **Image** | Custom icons for each metric (heart rate, steps, calories, sessions) |
| **Text Box** | Layout labels and section headers |

<br>


## ⚙️ DAX Measures

A set of DAX measures power the interactivity and visual formatting of the dashboard:

**Core KPIs**
- `Avg Heart Rate over Selected Period`
- `Avg Daily Steps over Selected Period`
- `Avg Daily Calories over Selected Period`
- `Total Exercise Sessions over Selected Period`
- `Health Score`

**Donut Chart Logic**
- `Health Score - Fill to 100` calculates the complement of Health Score to complete the ring visual

**Target Range & Axis Fill Measures** *(used to build reference lines inside bar charts)*
- `Avg Heart Rate - Target Min` / `Avg Heart Range` / `Avg Heart Rate - Axis Fill`
- `Avg Daily Steps - Target Min` / `Avg Daily Steps Range` / `Avg Daily Steps - Axis Fill`
- `Avg Daily Calories - Target Min` / `Avg Calories Target Range` / `Avg Calories - Axis Fill`
- `Total Exercise Sessions - Target Min` / `Total Exercise Sessions Range` / `Total Exercise Sessions - Axis Fill`

**Dynamic Text**
- `Welcome Text` — generates a personalized greeting based on the selected user

<br>


## 🔖 Bookmarks & Navigation

Four bookmarks drive the **time period selector**, each updating the line chart's drill hierarchy level:

| Bookmark | Chart Level Shown |
|---|---|
| Year | Year only |
| Quarter | Year → Quarter |
| Month | Year → Quarter → Month |
| Day | Year → Quarter → Month → Weekday |

The **Bookmark Navigator** visual renders these as styled buttons, giving the report an app-like feel without any custom code.

<br>


## 🎨 Design & Theming

- **Custom theme** applied at the report level for consistent branding across all visuals
- **Custom PNG icons** registered as static resources for each metric card (heart rate, steps, calories, sessions)
- **SVG background** designed in Powerpoint for more aesthetic features
- **Simple Image** custom visual used to display metric icons cleanly within the layout

<br>


## 🔍 Interactivity & Filtering

- **User Slicer** - dropdown, single-select, filters all visuals to a specific athlete
- **Bookmark Navigator** - switches the line chart's time granularity (Year / Quarter / Month / Day) without navigating away from the page
- **Cross-filtering** - all visuals participate in cross-filtering
- **Advanced filters** applied per visual via bookmark state, ensuring each time-period view shows only the relevant metrics

<br>


## 🛠️ Skills Demonstrated

- Star schema data modelling
- Time intelligence with DAX and date hierarchies
- Advanced DAX for target ranges and axis fill patterns (stacked bar trick)
- Calculated measure for dynamic welcome/greeting text
- Bookmark-driven navigation for UX-style time filtering
- Custom theme design and branding
- Static resource management (PNG icons, SVG, custom JSON theme)
- Custom visual integration (Simple Image)
- Single-page app layout design in Power BI

