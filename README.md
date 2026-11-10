# Instrumental Variables: Weak Instruments, Compliers and the Exclusion Restriction

## Objective

I used simulation and a replication of Card (1995) to see when instrumental variables recover a causal effect and when they fail.

## Methodology

- I simulated a weak instrument with a true effect of 1.0, built so that OLS is biased upward, and compared the OLS and 2SLS estimates across many draws.
- I tracked the first-stage F statistic in each draw and looked at how often a significant 2SLS estimate landed far from the truth.
- I replicated Card's (1995) college-proximity instrument for schooling, estimating the first stage, OLS and 2SLS returns to schooling.
- I added a small direct effect of the instrument on the outcome, which breaks the exclusion restriction, and measured how far this moves the 2SLS estimate.
- I wrote my own two-stage least squares function from two OLS regressions: the first regresses the endogenous variable on the instrument, and the second regresses the outcome on the fitted values from the first.
- I checked my function against the linearmodels package.

## Key Findings

- With a weak instrument (median first-stage F of 0.5), the median 2SLS estimate was 2.038, against a true effect of 1.0. The median OLS estimate was 1.998. So 2SLS was no closer to the truth than OLS, and a significant 2SLS estimate was usually far from the truth.
- In the Card (1995) replication, the first-stage F was 16.7. The OLS return to schooling was 0.0740 and the 2SLS return was 0.1323, so the instrumented estimate is larger than the OLS estimate.
- A small direct effect of the instrument on the outcome moves the 2SLS estimate, so the exclusion restriction matters even when the instrument is strong. The size of the shift is in my results for this part of the lab.
- The 2SLS estimate from my own function matched linearmodels.
