Click [here](https://anabodevan.quarto.pub/data-journeys/blog/diff-diff/) for the full project

## TL;DR 

- Initial Drop: Properties near the incinerator were ~$30% cheaper in 1981, but this ignored pre-existing differences.
- Pre-Trends: Even in 1978 (pre-construction), nearby homes were ~$18,800 cheaper, suggesting omitted variables.
- DiD Estimate: After accounting for baseline differences and market trends, the incinerator caused a statistically insignificant price drop of ~$11,864.
- Controls Matter: Adding property characteristics (age, size, bathrooms, etc.) reduced bias and revealed the true causal effect: a significant 13.2% devaluation due to the incinerator.
- Visual Evidence: Parallel trends held roughly pre-construction, supporting DiD validity.

Conclusion: The incinerator reduced nearby home values, but earlier estimates overstated the effect due to unobserved property differences.



## Introduction

The differences-in-differences (DiD) is a statistical method that compares the changes in outcomes between a treatment group and a control group before and after an intervention. By examining how the gap between the two groups evolve over time, DiD helps isolate the impact of the intervention from other external factors that might affect the outcome variable.

Woolridge: the impact of building an trash incinerator on real state appreciation

Woolridge (2023) simplified an econometric analysis by Kiel and MacClain (1995) that evaluated the influence the construction of a trash incinerator in North Andover on real estate appreciation. In 1978, there were rumors a new trash incinerator would be build, but construction only began in 1981, and operations started in 1985.

The general hypothesis is that properties close to the incinerator (4.8 km radius) would be less valuable than more distant properties. Using the woolridge package, we will run a five-step analysis to verify the hypothesis suggested in the exercise.

## Five-step analysis

- Simple Regression (1981)

  - A basic regression is run using only the "near the incinerator" variable (yes/no).

  - This alone cannot establish causality, as it ignores other factors affecting prices.

- Baseline Check (1978)

  - The same regression is repeated for 1978 (pre-incinerator) to see if price differences existed before construction.

- Difference in Averages (DiD Estimate)

  - The causal effect is estimated by comparing the average price change (1981 vs. 1978) for homes near vs. far from the incinerator.

- Interaction Regression

  - A regression with an interaction term (near incinerator × year) tests whether the price drop is statistically significant.

- Adding Controls

  - To improve accuracy, control variables (house age, bathrooms, square footage, etc.) are included in the regression.
