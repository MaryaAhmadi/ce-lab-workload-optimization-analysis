# Lab M7.04 - Workload Optimization Analysis

**Repository:** https://github.com/MaryaAhmadi/ce-lab-workload-optimization-analysis.git

**Activity Type:** Individual  
**Estimated Time:** 45-60 minutes

## 📌 Overview

This lab focuses on identifying and reducing unnecessary cloud costs in a development environment.  
You will analyze workload usage patterns, implement automated instance scheduling, and audit storage resources to uncover hidden costs.

The goal is to apply FinOps and cloud optimization best practices to achieve measurable cost savings.

---

## 🎯 Learning Objectives

By completing this lab, you will be able to:

- Analyze workload usage patterns (business hours vs. off-hours)
- Implement automated EC2 instance scheduling using EventBridge and Lambda
- Calculate cost savings from start/stop automation
- Identify orphaned EBS volumes and outdated snapshots
- Produce a prioritized workload optimization report with projected savings

---

## ⚙️ Prerequisites

- AWS account with permissions for:
  - EC2
  - Lambda
  - EventBridge
  - EBS
  - IAM
- AWS CLI v2 installed and configured
- Completion of Module 7 (Day 1–2)
- Basic understanding of:
  - JSON policies
  - Lambda functions

---

## 🧪 Lab Activities

### 1. Environment Setup
- Launched development EC2 instances:
  - `dev-frontend (t3.medium)`
  - `dev-backend (t3.large)`
- Tagged resources for automation:
  - `Environment=development`
  - `Schedule=business-hours`
  - `Lab=m7-04`
- Created an unattached EBS volume to simulate orphaned storage

---

### 2. Usage Analysis
- Collected CPU utilization metrics from CloudWatch
- Observed:
  - Very low CPU usage after initial startup
  - Near-idle utilization (<1%) across most time periods
- Conclusion:
  - Instances are suitable for business-hours-only operation

📄 See: `usage-analysis.md`

---

### 3. Cost Optimization (Scheduling)
- Calculated savings by running instances only during:
  - Monday–Friday, 8 AM – 7 PM
- Results:
  - **Monthly savings:** $60.91
  - **Reduction:** ~67%

---

### 4. Automation Implementation
- Created IAM role for Lambda execution
- Built Lambda function (`scheduler.py`) to:
  - Start instances during business hours
  - Stop instances during off-hours
- Configured EventBridge rules:
  - Start: weekday mornings
  - Stop: weekday evenings

---

### 5. Storage Audit
- Identified unattached EBS volume:
  - Size: 50 GB
  - Monthly cost: $4.00
- No snapshots older than 90 days found

---

## 💰 Optimization Summary

| Category | Monthly Savings |
|----------|----------------|
| Instance Scheduling | $60.91 |
| EBS Cleanup | $4.00 |
| **Total** | **$64.91** |

**Annual Savings:** **$778.92**

---

## 📊 Key Findings

- Development workloads were significantly underutilized
- ~76% of runtime occurred during idle periods
- Automated scheduling provides the highest impact with minimal risk
- Orphaned storage contributes to hidden recurring costs

---

## 🚀 Recommendations (Priority Order)

1. **Enable instance scheduling (HIGH)**
   - Immediate and significant cost reduction
   - No impact on development workflows

2. **Remove orphaned EBS volumes (MEDIUM)**
   - Verify before deletion

3. **Implement snapshot lifecycle policies (LOW)**
   - Prevent future storage waste

---

## 📁 Repository Contents

- `scheduler.py` → Lambda function for automation
- `usage-analysis.md` → CPU usage analysis
- `optimization-report.md` → Detailed cost optimization report

---

## ✅ Verification Checklist

- [x] EC2 instances created and tagged
- [x] CloudWatch metrics analyzed
- [x] Lambda scheduler implemented
- [x] EventBridge rules configured
- [x] Cost savings calculated
- [x] EBS audit completed
- [x] Optimization report created

---

## 🧹 Cleanup

All lab resources were terminated after completion to avoid unnecessary charges.

---

## 📚 Additional Resources

- AWS EC2 Documentation  
- AWS Lambda Documentation  
- AWS EventBridge Documentation  
- FinOps Foundation Best Practices  

---

## 🎉 Conclusion

This lab demonstrates how simple automation and resource auditing can reduce cloud costs by over **60%** in non-production environments.  
Applying these practices at scale can lead to substantial organizational savings.

---
## Additional Resources

Refer to Module 7 Day 2 lessons and AWS documentation.

**Good luck! 🚀**
