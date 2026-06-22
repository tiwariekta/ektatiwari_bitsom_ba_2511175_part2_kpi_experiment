## Business Problem Statement

The company recently launched a new onboarding and activation campaign designed to improve early user engagement and increase conversion from free users to paying customers.

Users were randomly assigned to one of two groups:

* Control Group: Existing onboarding experience
* Treatment Group: New onboarding campaign experience

The key business decision is whether the new onboarding campaign should be rolled out to all users.

This decision impacts multiple stakeholders including Product Management, Marketing, Customer Success, Revenue Operations, and Company Leadership.

The primary objective is to improve Paid Conversion Rate, which measures the percentage of users who successfully convert to a paid subscription.

While improving conversion is important, several risks must also be monitored. An increase in conversions could potentially lead to lower-quality conversions, increased refund requests, higher support burden, reduced engagement quality, or slower conversion times.

Before making a rollout recommendation, evidence is required to demonstrate that the Treatment group performs better than the Control group on the primary success metric. Statistical testing must be performed to determine whether any observed improvement is meaningful and not due to random variation. In addition, guardrail metrics must be evaluated to ensure that the treatment does not negatively impact user experience or business outcomes.


# Part 2: KPI Framework, Business Experiment Analysis & Decision Recommendation

## Business Context

A subscription-based digital product company launched a new onboarding and activation campaign to improve early user engagement and increase paid conversions.

Users were randomly assigned into two groups:

* Control Group: Existing onboarding experience
* Treatment Group: New onboarding campaign experience

The objective of this analysis was to determine whether the Treatment experience should be rolled out to all users based on conversion performance, business impact, and risk assessment.

---

# Dataset Description

The dataset contains user-level experiment data including onboarding funnel activity, conversion outcomes, revenue, engagement, and support interactions.

### Dataset Size

| Metric                    | Value |
| ------------------------- | ----: |
| Total Records             | 1,408 |
| Records After Cleaning    | 1,400 |
| Duplicate Records Removed |     8 |

### Key Fields

* user_id
* experiment_group
* region
* device_type
* traffic_source
* plan_type
* visited_landing_page
* started_trial
* completed_onboarding
* converted_to_paid
* revenue_30d
* support_tickets_30d
* refund_requested
* days_to_convert
* engagement_score

---

# North Star Metric

## Paid Conversion Rate

**Formula**

Paid Conversion Rate = Converted Users / Total Users

### Why This Metric Was Selected

The onboarding campaign was designed to increase the number of users who become paying customers.

Paid Conversion Rate directly measures business success and customer acquisition effectiveness.

It is the strongest indicator of whether the onboarding experience creates meaningful business value.

---

# KPI Tree Summary

The KPI Tree was designed around Paid Conversion Rate.

### Primary Drivers

#### 1. Acquisition & Landing Page Effectiveness

* Landing Page Visit Rate
* Traffic Source Quality

#### 2. Onboarding & Activation Effectiveness

* Trial Start Rate
* Onboarding Completion Rate

#### 3. Engagement & Monetization Quality

* Engagement Score
* Revenue Quality

### Guardrail Metrics

* Refund Rate
* Support Ticket Rate
* Days to Convert

---

# Experiment Analysis Approach

The experiment dataset was validated and prepared before analysis.

### Data Quality Checks Performed

#### Missing Values

| Column           | Missing Count |
| ---------------- | ------------: |
| device_type      |            18 |
| traffic_source   |            24 |
| engagement_score |            14 |
| days_to_convert  |          1336 |

The large number of missing values in days_to_convert was expected because only converted users have conversion dates.

---

#### Duplicate Users

Eight duplicate user records were identified as exact duplicates and removed.

---

#### Binary Validation

The following fields were validated and confirmed to contain only valid binary values (0 or 1):

* visited_landing_page
* started_trial
* completed_onboarding
* converted_to_paid
* refund_requested

---

#### Revenue Outlier Review

Revenue outliers were retained because they corresponded to successfully converted paying users and represented valid business outcomes.

---

#### Experiment Balance Validation

The distribution of users across:

* Regions
* Device Types
* Traffic Sources

was reviewed and found to be reasonably balanced between Control and Treatment groups.

---

# Experiment Results Summary

| Metric                     | Control | Treatment |
| -------------------------- | ------: | --------: |
| User Count                 |     690 |       710 |
| Landing Page Visit Rate    |  63.62% |    72.39% |
| Trial Start Rate           |  25.07% |    29.01% |
| Onboarding Completion Rate |  15.65% |    21.13% |
| Paid Conversion Rate       |   3.19% |     7.04% |
| Average Revenue Per User   |   51.97 |     54.25 |
| Refund Rate                |   0.00% |     0.42% |
| Support Ticket Rate        |  14.78% |    24.79% |
| Average Engagement Score   |   57.05 |     62.91 |
| Average Days to Convert    |    8.86 |      6.40 |

The Treatment group outperformed the Control group across all major funnel metrics.

---

# Hypothesis Test Summary

## Test Type

One-Tailed Two-Proportion Z-Test

## Hypotheses

### Null Hypothesis (H0)

Treatment Conversion Rate ≤ Control Conversion Rate

### Alternative Hypothesis (H1)

Treatment Conversion Rate > Control Conversion Rate

---

## Results

| Metric                    |    Value |
| ------------------------- | -------: |
| Control Conversion Rate   |    3.19% |
| Treatment Conversion Rate |    7.04% |
| Z Score                   |    3.264 |
| P Value                   | 0.000549 |
| Significance Level        |     0.05 |

### Decision

Reject the Null Hypothesis.

The Treatment group demonstrated a statistically significant improvement in Paid Conversion Rate.

---

# Guardrail Metrics Considered

## Refund Rate

Increased slightly from 0.00% to 0.42%.

Risk Assessment: Low

---

## Support Ticket Rate

Increased from 14.78% to 24.79%.

Risk Assessment: Moderate

---

## Days to Convert

Improved from 8.86 days to 6.40 days.

Risk Assessment: Positive Outcome

---

## Engagement Score

Improved from 57.05 to 62.91.

Risk Assessment: Positive Outcome

---

# Segment-Level Insights

### Region

Treatment outperformed Control across all major regions.

### Device Type

Treatment outperformed Control across Desktop, Mobile, and Tablet users.

### Traffic Source

Treatment improved conversion rates for:

* Email
* Organic
* Paid Search
* Referral

However, Social traffic users experienced lower conversion rates under Treatment and should be monitored after rollout.

---

# Final Recommendation

## Recommendation: Launch

The Treatment onboarding experience should be launched because:

* Paid Conversion Rate improved significantly.
* Statistical significance was achieved.
* Revenue per user increased.
* Engagement improved.
* Conversion speed improved.
* No major region-level or device-level declines were observed.

Although Support Ticket Rate increased and Social traffic users showed slightly lower conversion performance, these risks do not outweigh the overall business benefit.

The rollout should proceed with continued monitoring of support ticket trends and Social traffic performance.

---

# Assumptions and Limitations

### Assumptions

* Paid Conversion Rate is the primary success metric.
* Missing days_to_convert values represent non-converted users.
* Duplicate user records were unintentional duplicates and removed.

### Limitations

* Long-term retention metrics were not available.
* Customer lifetime value was not included.
* Refund volume was very small.
* Social traffic segment requires additional monitoring after rollout.

---

# Screenshots Included

The repository contains the following screenshots:

* screenshots/summary_metrics.png
* screenshots/hypothesis_test_output.png
* screenshots/kpi_tree_preview.png

These screenshots provide evidence of the KPI framework, experiment summary metrics, and hypothesis testing results.

---

# Repository Deliverables

* data/campaign_experiment_data.xlsx
* analysis/experiment_analysis.xlsx
* analysis/hypothesis_test_notes.md
* analysis/ab_test_calculations.xlsx
* outputs/experiment_summary.xlsx
* outputs/recommendation_memo.md
* outputs/kpi_tree.png
* screenshots/summary_metrics.png
* screenshots/hypothesis_test_output.png
* screenshots/kpi_tree_preview.png
* README.md
