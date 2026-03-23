# Workload Usage Pattern Analysis

## Observations
- The newly launched development instances show very low CPU utilization overall.
- `dev-frontend` had a brief initial utilization spike (~8.68%), then dropped to near-idle levels.
- `dev-backend` remained near idle across the observed period, with CPU utilization below 0.2%.
- The observed pattern supports treating these instances as non-production workloads suitable for business-hours scheduling.

## Active Window
- **Business hours:** Monday-Friday 8:00 AM - 7:00 PM (local time)
- **Idle hours:** Weeknights and weekends
- **Optimization opportunity:** Stop development instances during off-hours to reduce compute waste
