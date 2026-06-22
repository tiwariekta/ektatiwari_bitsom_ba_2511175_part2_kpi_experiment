# Hypothesis Test Notes

## Business Objective

The purpose of this experiment is to determine whether the new onboarding campaign increases the percentage of users who convert to a paid subscription.

The primary business decision is whether the treatment experience should be rolled out to all users.

---

# Metric Being Tested

## Paid Conversion Rate

Formula:

Paid Conversion Rate = Converted Users / Total Users

This metric was selected because it is the North Star Metric for the experiment and directly measures business success.

---

# Test Type

## One-Tailed Two-Proportion Z-Test

A Two-Proportion Z-Test is appropriate because:

* We are comparing conversion rates between two independent groups.
* The outcome variable (converted_to_paid) is binary (0 or 1).
* Sample sizes are sufficiently large.
* The business question specifically asks whether the Treatment performs better than the Control.

---

# Hypotheses

## Null Hypothesis (H0)

The Treatment group conversion rate is less than or equal to the Control group conversion rate.

H0: Treatment Conversion Rate ≤ Control Conversion Rate

---

## Alternative Hypothesis (H1)

The Treatment group conversion rate is greater than the Control group conversion rate.

H1: Treatment Conversion Rate > Control Conversion Rate

---

# Significance Level

Alpha (α) = 0.05

A 95% confidence level will be used.

---

# Decision Rule

If:

P-value < 0.05

Reject the Null Hypothesis.

Conclude that the Treatment significantly improves Paid Conversion Rate.

Otherwise:

Fail to Reject the Null Hypothesis.

Conclude that there is insufficient evidence to support a rollout decision.

---

# Test Inputs

| Metric          | Control | Treatment |
| --------------- | ------: | --------: |
| Total Users     |     690 |       710 |
| Converted Users |      22 |        50 |
| Conversion Rate |   3.19% |     7.04% |

---

# Interpretation Logic

If the Treatment group demonstrates a statistically significant improvement in Paid Conversion Rate without creating unacceptable risks in guardrail metrics, the treatment may be recommended for launch.

Guardrail metrics evaluated separately include:

* Refund Rate
* Support Ticket Rate
* Days To Convert
* Engagement Score

These metrics ensure that conversion improvements are sustainable and do not negatively impact user experience.
