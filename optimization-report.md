# Workload Optimization Report

## Executive Summary
Total identified monthly savings: **$64.91** across instance scheduling and storage cleanup.

## 1. Instance Scheduling (Priority: HIGH)

| Instance | Type | Current Cost/mo | Scheduled Cost/mo | Savings/mo |
|----------|------|-----------------|-------------------|------------|
| dev-frontend | t3.medium | $30.37 | $10.07 | $20.30 |
| dev-backend | t3.large | $60.74 | $20.13 | $40.61 |
| **Subtotal** |  | **$91.11** | **$30.20** | **$60.91** |

**Implementation:** EventBridge + Lambda scheduler deployed.  
**Finding:** CloudWatch CPU analysis showed both development instances remained near idle after launch activity, supporting business-hours-only scheduling.

## 2. Orphaned EBS Volumes (Priority: MEDIUM)

| Volume ID | Size (GB) | Monthly Cost | Action |
|-----------|-----------|--------------|--------|
| vol-04ecedbdf3ba1b037 | 50 | $4.00 | Delete after backup/dependency verification |
| **Subtotal** |  | **$4.00** |  |

## 3. Old Snapshots (Priority: LOW)

| Count | Total Size (GB) | Monthly Cost | Action |
|-------|------------------|--------------|--------|
| 0 snapshots > 90 days | 0 | $0.00 | No cleanup required at this time |

## Prioritized Recommendations
1. **Enable instance scheduling** — $60.91/month savings with minimal operational risk for development workloads
2. **Delete orphaned EBS volume** — $4.00/month savings after verifying no dependency or recovery need
3. **Review snapshot lifecycle regularly** — no immediate savings identified, but lifecycle policies should be implemented to prevent future waste

## Annual Projected Savings
**$778.92/year**
