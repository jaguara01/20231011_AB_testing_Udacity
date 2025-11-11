# UDACITY project on AB Testing

## Project Overview

This project analyzes the results of an A/B test conducted by Udacity on their course overview page. The experiment tested a "Free Trial Screener" to see if it could improve student experience and retention by setting clearer time-commitment expectations upfront.

At the time, the page had two options: "start free trial" and "access course materials."

* **Control Group:** Clicking "start free trial" led directly to the checkout process to enroll in a 14-day free trial, which would auto-convert to a paid subscription.
* **Experiment Group:** Clicking "start free trial" would first ask the user how much time they had to devote to the course.
    * If the user indicated 5 or more hours per week, they proceeded to checkout as usual.
    * If the user indicated fewer than 5 hours per week, a message appeared explaining that Udacity courses typically require more time and suggested accessing the free course materials instead. The user still had the option to continue to the free trial checkout.

## Hypothesis

The hypothesis was that this screener would set clearer expectations, reducing the number of frustrated students who enrolled and then left the free trial due to lack of time. The goal was to achieve this without significantly reducing the number of students who eventually completed the course (i.e., converted to paid users).

## Metrics

Metrics were chosen to validate the experiment's setup (Invariant) and to measure its impact (Evaluation).

### Invariant Metrics (Sanity Checks)
These metrics were not expected to change between the control and experiment groups.
* **Number of cookies:** Unique cookies viewing the course overview page.
* **Number of clicks:** Unique cookies clicking the "Start free trial" button.
* **Click-through-probability:** The ratio of clicks to cookies.

### Evaluation Metrics
These metrics were used to measure the impact of the change.
* **Gross Conversion:** (Number of users who enroll in the free trial) / (Number of unique cookies who click "Start free trial").
* **Net Conversion:** (Number of users who remain enrolled past 14 days and make a payment) / (Number of unique cookies who click "Start free trial").
* **Retention:** (Number of users who remain enrolled past 14 days) / (Number of users who enroll in the free trial).
    * *Note: Retention was ultimately not used as the primary evaluation metric because the required sample size would have needed the experiment to run for an impractical length of time (118+ days).*

## Analysis & Results

The analysis was conducted using the data from `Control.csv` and `Experiment.csv`.

### Sanity Checks
All invariant metrics (Number of cookies, Number of clicks, Click-through-probability) passed the sanity checks. The observed differences between the control and experiment groups were not statistically significant, indicating that the experiment's diversion was successful and unbiased.

### Significance Testing
The evaluation metrics were analyzed to determine if the changes were statistically and practically significant.

* **Gross Conversion:**
    * **Result:** Showed a statistically and practically significant *decrease*.
    * **Interpretation:** This was expected. The screener successfully discouraged some users from enrolling in the free trial, leading to a lower enrollment rate among those who clicked the "start" button.

* **Net Conversion:**
    * **Result:** The change was *not* statistically significant. The calculated confidence interval included 0, meaning it's plausible the change had no effect (or even a negative effect) on net conversion.
    * **Interpretation:** The experiment failed to prove that the screener improves the rate of users converting to paid subscribers.

A Sign Test was also performed, which confirmed these findings: it showed a significant effect for Gross Conversion but failed to show a significant effect for Net Conversion.

## Conclusion

The primary objective of the experiment was to improve the student experience, with the key business metric being an increase in students who not only enroll but also complete the trial and become paying users (Net Conversion).

The analysis showed that while the screener did reduce the number of initial enrollments (Gross Conversion), it **did not lead to a statistically significant improvement in Net Conversion.**

Therefore, based on this analysis, the recommendation is **not to launch** this change. The experiment failed to demonstrate the intended positive impact on student retention and payment.

## Files in this Repository
* `Udacity_AB_Testing.ipynb`: The Jupyter Notebook containing the full analysis.
* `Control.csv`: The daily data for the control group.
* `Experiment.csv`: The daily data for the experiment group.
