# Fitness Tracker App | Power BI Design
A personal fitness dashboard built in Power BI, designed to monitor individual health metrics over time. The report delivers a clean, app-like experience with dynamic personalization, interactive time filtering, and visually rich KPIs.

Dashboard Preview

https://github.com/user-attachments/assets/ccda60af-b9cb-40e8-9b1d-28cec8fa26cb

<br>

## Overall Design

The report uses a **neumorphic design** aesthetic - soft, app-like UI with subtle shadows and rounded card surfaces that mimic a physical fitness app rather than a traditional BI report. Custom PNG icons replace default chart icons for steps, calories, heart rate, and sessions, and a custom SVG background reinforces the single-page app feel.

<br>

## Data Model

- **Lean model** with 1 fact-style table (`factFitnessStats`) and 2 dimension tables: `dimUser` and `dimDate`
- All measures centralised in a dedicated `Metrics` table

<br>

## DAX Measures

All measures are centralised in the `Metrics` table and organised into **6 folders**:

| Folder | Key Measures | Purpose |
|---|---|---|
| 01. Heart Rate | `Avg Heart Rate over Selected Period`, `Avg Heart Rate - Target Min`, `Avg Heart Rate - Axis Fill`, `Avg Heart Range` | Heart rate average represented in the stacked progress bar without a custom visual |
| 02. Steps | `Avg Daily Steps over Selected Period`, `Avg Daily Steps - Target Min`, `Avg Daily Steps - Axis Fill`, `Avg Daily Steps Range` | Same method as Heart Rate
| 03. Calories | `Avg Daily Calories over Selected Period`, `Avg Daily Calories - Target Min`, `Avg Calories - Axis Fill`, `Avg Calories Target Range` | Calorie intake/burn tracking with target-band logic |
| 04. Exercise Sessions | `Total Exercise Sessions over Selected Period`, `Total Exercise Sessions - Target Min`, `Total Exercise Sessions - Axis Fill`, `Total Exercise Sessions Range` | Session count |
| Health Score | `Health Score`, `Health Score - Fill to 100` | `Health Score` aggregates all activity into a single wellness index; `Fill to 100` ensures the donut chart always renders as a complete circle |
| Other | `Welcome Text` | Dynamically displays the user's name, pulling from `dimUser` to personalise the dashboard header |

<br>

## Visuals

| Visual | Purpose |
|---|---|
| 4x KPI Cards | Steps, heart rate, calories, sessions, headline numbers |
| 4x Stacked Bar Charts | Progress-to-target for each KPI, rendered using x-axis constant line |
| 5x Line Charts | Daily trends over the selected period |
| 1x Donut Chart | Health Score visualised as a percentage ring |
| 4x Image visuals | Custom icons (steps, calories, heart rate, sessions) |
| Bookmark Navigator | Switches between views or user states |
| Text boxes | Labels, headers, and the dynamic welcome message |

<br>

## Interactivity

- **5 slicers** filter by year, quarter, month, weekday, and user name
- **Bookmark navigator** for toggling between dashboard states
- **Date hierarchy** on `dimDate` enables drill-down from year to individual day
- All KPI and chart measures recalculates automatically on slicer change
