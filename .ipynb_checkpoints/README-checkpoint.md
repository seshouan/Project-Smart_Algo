# Project-Smart_Algo

Combines algorithmic trading with financial Python programming and machine learning to create an algorithmic trading bot that learns and adapts to new data and evolving markets

## Baseline

Our ML performance baseline was created with an SVM model, and our predictive strategy outperformed actual returns, ending up with a cumulative return of ~1.6x vs. the cumulative actual returns of ~1.4x [net 20% gain]:

<img src="Resources/Baseline.png" alt="Baseline" width="600"/>

## Tuning - Dataset Size

Tuning the dataset with slices of 6 months sets the cumulative returns of the strategy to ~1.77x and that of the actuals to ~1.58x [net 19% gain]:

<img src="Resources/Tuned-6_month_offset.png" alt="Tune_6_months" width="600"/>

Tuning the dataset with slices of 1 month sets the cumulative returns of the strategy to ~1.32x and that of the actuals to ~1.3x [net 2% gain]:

<img src="Resources/Tuned-1_month_offset.png" alt="Tune_1_month" width="600"/>

Tuning the dataset with slices of 9 months sets the cumulative returns of the strategy to ~1.6x and that of the actuals to ~1.65x, while experiencing big swings between the cumulative returns of the strategy and actuals in the prior periods [net 5% loss]:

<img src="Resources/Tuned-9_month_offset.png" alt="Tune_9_months" width="600"/>

Tuning the dataset with slices of 7 months sets the cumulative returns of the strategy to ~1.86x and that of the actuals to ~1.6x [net 26% gain]:

<img src="Resources/Tuned-7_month_offset.png" alt="Tune_7_months" width="600"/>

**Question:** What impact resulted from increasing or decreasing the training window?

**Answer:** Increasing the dataset helps improve the cumulative returns of the strategy, but up to a point, then it degrades it.

## Tuning - SMA Params

Only increasing the short window from 4 to 25 sets the cumulative returns of the strategy to ~1.46x and that of the actuals to ~1.4x [net 6% gain]:

<img src="Resources/Tuned_Window-Short_Only.png" alt="Tuned_Window-Short_Only" width="600"/>

Only increasing the long window from 100 to 125 sets the cumulative returns of the strategy to ~1.58x and that of the actuals to ~1.49x [net 9% gain]:

<img src="Resources/Tuned_Window-Long_Only.png" alt="Tuned_Window-Long_Only" width="600"/>

Adjusting both the short window to 25 and the long window to 125 sets the cumulative returns of the strategy to ~1.42x and that of the actuals to ~1.5x [net 8% loss]:

<img src="Resources/Tuned_Window-Both.png" alt="Tuned_Window-Both" width="600"/>

**Question:** What impact resulted from increasing or decreasing either or both of the SMA windows?

**Answer:** Adjusting just one of the windows up by 25 days provides a little gain, but adjusting both upwards by 25 days at the same time results in a net loss of the strategy compared to actuals

## Tuning - Best Combination

The best combo tested is:
- dataset with slices of 7 months
- short window of 4
- long window of 80

This sets the cumulative returns of the strategy to ~1.85x and that of the actuals to ~1.52x [net 33% gain] 

<img src="Resources/Best.png" alt="Best" width="600"/>

## New ML Classifier

We reset the data to the baseline and used LogisticRegression as an alternative ML classifier, and obtained a result that sets the cumulative returns of the strategy to ~1.38x and that of the actuals to ~1.4x [net 4% loss]:

<img src="Resources/Alt_Classifier.png" alt="Alt_ML" width="600"/>

## Evaluation Report
(For this report, express your final conclusions and analysis. Support your findings by using the PNG images that you created)
We repeatedly tuned an ML model that is combined with an algorithmic logic to optimize the resulting predictive trading strategy.

We started with a baseline that achieved a cumulative 20% gain over actual returns:

<img src="Resources/Baseline.png" alt="Baseline" width="600"/>

We improved the performance of our baseline to achieve a cumulative 33% gain over actual returns by making the following adjustments:
- dataset with slices of 7 months
- short window of 4
- long window of 80

<img src="Resources/Best.png" alt="Best" width="600"/>

We tried to improve our baseline model by switching to a logistical regression classifier, instead of the SVC, and this resulted in a cumulative loss of the strategy of 2%:

<img src="Resources/Alt_Classifier.png" alt="Alt_ML" width="600"/>

In conclusion, while we may have found a combination of parameters that provide a cumulative returns gain of 33% over the actual returns, there is always opportunity to further improve on it with additional tuning.
