# Starbucks Rewards: Decoding Customer Engagement with Data

## Project Overview

Starbucks rewards its customers through various promotional offers, such as Buy-One-Get-One (BOGO), discounts, and informational campaigns. Each offer type aims to boost customer engagement and spending. But which demographic groups respond best to each offer type? What is the optimal way to present these offers to maximize their effectiveness?

This project analyzes customer behavior using a simulated dataset that mirrors Starbucks rewards app data. By combining demographic, transactional, and promotional data, we aim to identify which groups are most responsive to different offer types and how these offers can be optimized for delivery and duration. This analysis provides actionable insights to help Starbucks craft data-driven marketing strategies.

---

## Problem Statement

The central challenge is to determine:

1. **Which demographic groups respond best to each offer type (BOGO, discount, informational)?**
2. **What are the optimal channels and durations for sending these offers?**

The expected outcome is a data-driven strategy for tailoring offers based on customer behavior, demographics, and channel preferences. This involves analyzing engagement patterns, offer completion rates, and channel effectiveness.

---

## Metrics

To evaluate the effectiveness of the analysis and models, we use the following metrics:

- **Precision:** To measure how accurately the model predicts offer completions, especially for the minority class (completed offers).
- **Recall:** To capture the proportion of actual offer completions correctly identified.
- **F1-Score:** To balance precision and recall for a more comprehensive evaluation.
- **Feature Importance:** To identify which factors (e.g., age, income, channel) most influence offer responsiveness.

These metrics are particularly relevant due to the imbalanced nature of the dataset, where "no completion" events dominate.

---

## Data Exploration

### Datasets

1. **Portfolio Dataset:** Contains meta-information about offers, including type, duration, reward, and channels.
2. **Profile Dataset:** Provides demographic details such as age, gender, income, and membership date.
3. **Transcript Dataset:** Logs user interactions, including transactions, offers received, viewed, and completed.

### Key Observations

- **Portfolio:**
  - Offers are distributed across three types: BOGO, discount, and informational.
  - Channels include email, mobile, social, and web.

- **Profile:**
  - Gender distribution is skewed toward males.
  - A significant portion of users have an age of 118, indicating missing or erroneous data.

- **Transcript:**
  - Events include transactions, offer received, offer viewed, and offer completed.
  - "Offer completed" events are significantly less frequent than other events.

### Visualizations

- **Gender Distribution:** [Placeholder for bar chart]
- **Income Range Distribution:** [Placeholder for histogram]
- **Age Distribution (after cleaning):** [Placeholder for histogram]

These visualizations revealed key patterns, such as the dominance of middle-income users and the importance of cleaning erroneous age data.

---

## Methodology

### Data Preprocessing

1. **Portfolio Dataset:** Expanded categorical channels into dummy variables for analysis.
2. **Profile Dataset:**
   - Replaced missing age values (118) with NaN.
   - Converted membership dates into datetime format and calculated membership duration.
3. **Transcript Dataset:** Extracted relevant fields such as offer IDs, transaction amounts, and rewards. Merged this data with profile and portfolio datasets.

### Feature Engineering

- **Offer Response Features:** Created features to track whether an offer was viewed before being completed.
- **Time-Based Features:** Added membership duration and offer timing metrics.
- **Demographic Features:** Integrated age, income, and gender data for segmentation.

### Implementation

Two classification models were implemented:

1. **Random Forest Classifier:**
   - A robust ensemble method to capture nonlinear relationships.
   - Included hyperparameter tuning to optimize performance.

2. **Logistic Regression:**
   - A baseline model for comparison.

---

## Results

### Model Performance

#### Random Forest Classifier

| Metric        | Precision | Recall | F1-Score |  
|---------------|-----------|--------|----------|
| No Completion | 89%       | 100%   | 94%      |
| Completion    | 19%       | 1%     | 1%       |
| **Accuracy**  | **89%**   |        |          |

#### Logistic Regression

| Metric        | Precision | Recall | F1-Score |  
|---------------|-----------|--------|----------|
| No Completion | 89%       | 100%   | 94%      |
| Completion    | 0%        | 0%     | 0%       |
| **Accuracy**  | **89%**   |        |          |

### Insights

- **Random Forest** outperformed Logistic Regression in predicting offer completions but struggled due to data imbalance.
- Feature importance analysis highlighted the significant influence of income, age, and channel on offer completion rates.

[Placeholder for Feature Importance Bar Chart]

---

## Recommendations

1. **Target Demographics:**
   - Younger users (20–40): Focus on BOGO offers via mobile and social channels.
   - High-income users: Emphasize discounts delivered through email.
   - Female users: Use informational campaigns to raise awareness.

2. **Channel Optimization:**
   - Mobile and email channels are most effective across offer types.

3. **Offer Duration:**
   - Set offer durations to 7–10 days for optimal engagement.

4. **Address Data Imbalance:**
   - Apply oversampling techniques like SMOTE to improve model performance for offer completions.

5. **Future Enhancements:**
   - Incorporate clustering to segment customers further.
   - Explore time-series analysis to refine offer timing.

---

## Reflection

This project provided valuable insights into customer behavior on the Starbucks rewards app. One challenge was handling the imbalanced dataset, which affected model performance for offer completions. Despite this, the analysis revealed actionable strategies for personalizing offers.

### Potential Improvements

1. **Rich Feature Engineering:** Add features like transaction frequency and time-of-day patterns.
2. **Advanced Modeling:** Use Gradient Boosting or Neural Networks for improved predictions.
3. **Dynamic Offers:** Implement time-sensitive offers based on customer activity patterns.

---

## Conclusion

By analyzing customer behavior, this project answered the central question: **"Which demographic groups respond best to each offer type, and how should Starbucks deliver these offers?"** With improved targeting and personalization, Starbucks can enhance customer engagement and loyalty, maximizing the impact of its rewards program.

---

## Resources

- [Pandas Documentation](https://pandas.pydata.org/)
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [Matplotlib Documentation](https://matplotlib.org/)

---

