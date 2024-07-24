# Fraud Transaction Detection 

## Problem Statement

In recent years we have seen a huge increase in Fraud attempts, making fraud detection important as well as challenging. Despite countless efforts and human supervision, hundreds of millions are lost due to fraud. Fraud can happen using various methods ie, stolen credit cards, misleading accounting, phishing emails, etc. Due to small cases in large population detection of fraud is important as well as challenging.

Data mining and machine learning help to foresee and rapidly distinguish fraud and make quick move to limit costs. Using data mining tools, a huge number of transactions can be looked to spot pattern and distinguish fraud transactions.

### Dataset

* step - maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation).

* type - CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER.

* amount - amount of the transaction in local currency.

* nameOrig - customer who started the transaction

* oldbalanceOrg - initial balance before the transaction

* newbalanceOrig - new balance after the transaction

* nameDest - customer who is the recipient of the transaction

* oldbalanceDest - initial balance recipient before the transaction. Note that there is not information for customers that start with M (Merchants).

* newbalanceDest - new balance recipient after the transaction. Note that there is not information for customers that start with M (Merchants).

* isFraud - This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system.

* isFlaggedFraud - The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.

###Summary and Conclusion :

### Summary

1. **Exploratory Data Analysis (EDA):**
   - The most frequent number of steps taken falls between 150 and 400.
   - A significant number of transactions have fewer than 100 steps.
   - The distribution of steps is right-skewed, suggesting most transactions are completed in fewer steps.

2. **Transaction Types:**
   - Most common transaction type: CASH_OUT (35.2%).
   - Other transaction types: PAYMENT (33.8%), TRANSFER (22.0%), DEBIT (8.4%), and CASH_IN (0.7%).
   - High percentage of cash out transactions could indicate potential fraud.
   - Low percentage of cash-in transactions could be unusual and warrant further investigation.

3. **Top 20 Organization Names:**
   - Identified destinations with the highest number of transactions.
   - Look for unusual destinations with significantly higher transaction counts.

4. **Legitimate vs. Fraudulent Transactions:**
   - 98.87% of transactions are legitimate.
   - 0.13% of transactions are fraudulent.
   - Fraudulent transactions, though rare, have significant implications.
   - Advanced fraud detection systems are crucial for effective fraud prevention.

5. **Flagged Transactions:**
   - 99.87% of transactions are not flagged as fraudulent.
   - Only 0.13% of transactions are flagged for further review.
   - Significant class imbalance with flagged fraudulent transactions being extremely rare.

6. **Transaction Amounts:**
   - 98.95% of the total transaction amount corresponds to legitimate transactions.
   - 1.05% of the total transaction amount corresponds to fraudulent transactions.
   - Fraudulent transactions, though few, involve larger amounts, posing significant financial risks.
   - Continuous improvement of fraud detection systems is necessary.

7. **Feature Encoding:**
   - Encoded categorical features such as transaction type, origin account, and destination account.

8. **Data Splitting:**
   - Split the dataset into features (X) and target (y).
   - Applied SMOTE for handling class imbalance.

9. **Feature Scaling:**
   - Applied MinMaxScaler for scaling features.

10. **Model Creation:**
    - Created a Logistic Regression model.

11. **Model Evaluation:**
    - Predicted on train and test data.
    - Overall accuracy: 92%.
    - Most important features: oldbalanceOrg, newbalanceOrg, amount.

12. **Cross-Validation:**
    - After cross-validation, accuracy: 91%.
    - Consistent performance across different data subsets indicates model reliability.

### Conclusion

The analysis and modeling process revealed key insights and demonstrated the effectiveness of the Logistic Regression model in predicting fraudulent transactions. The EDA highlighted the transaction patterns and potential indicators of fraud. Despite the class imbalance, the application of SMOTE and feature scaling ensured a balanced and effective model.

The model achieved a high accuracy of 92%, with consistent performance validated through cross-validation (91%). The most important features contributing to fraud detection were oldbalanceOrg, newbalanceOrg, and amount, indicating these factors play a crucial role in identifying fraudulent transactions.

Overall, the model provides a reliable tool for detecting fraud, but continuous monitoring and improvement are essential to adapt to evolving fraud tactics. The advanced fraud detection system is crucial for maintaining the integrity and reliability of the transaction system, protecting it from significant financial risks associated with fraudulent activities.

### Overall Summary

The initial Logistic Regression model, which included correlation analysis and outlier detection, achieved an accuracy of 83%. In contrast, the refined model, developed without outlier detection and correlation-based feature removal, improved significantly, achieving a 92% accuracy. This comparison demonstrates that handling outliers and correlated features might not always be beneficial, highlighting the importance of iterative model tuning and evaluation.

Insights on handling thresholds from a business perspective based on  model's performance:

1. **Understanding Threshold Impact**:
   - **ROC AUC Interpretation**: With a high ROC AUC of 92%, your model effectively distinguishes between fraudulent and legitimate transactions.
   - **Threshold Adjustment**: Adjusting the threshold allows you to balance between detecting more fraudulent transactions (sensitivity) and minimizing false alarms (specificity).

2. **Business Goals**:
   - **Minimizing Fraudulent Losses**: If the primary goal is to reduce financial losses from fraudulent transactions, consider lowering the threshold. This increases sensitivity, catching more fraud cases, but might lead to more false positives.
   - **Efficiency in Operations**: To streamline operations and reduce unnecessary investigations, you might opt for a higher threshold to increase specificity. This lowers false positives but could increase false negatives.

3. **Impact of Threshold Changes(0.5)**:
   - **Increasing Threshold**: Raises the bar for classifying a transaction as fraudulent, reducing false positives but potentially missing some fraud cases (increased false negatives).
   - **Decreasing Threshold**: Lowers the criteria for fraud detection, capturing more fraud cases (reduced false negatives) but possibly increasing false positives.

4. **Optimization Strategy**:
   - Use the ROC curve to visualize trade-offs: Identify the optimal threshold that balances your business's tolerance for false positives and false negatives.
   - Conduct cost-benefit analysis: Consider the financial impact of misclassifications (e.g., transaction investigation costs vs. potential fraud losses) to guide threshold decisions.

5. **Continuous Monitoring and Adjustment**:
   - Monitor model performance over time: As transaction patterns evolve, periodically reassess and adjust the threshold to maintain optimal performance.
   - Utilize feedback loops: Incorporate feedback from fraud analysts and operational teams to refine thresholds based on real-world insights and changing fraud tactics.

By aligning threshold adjustments with specific business objectives and continuously evaluating performance, you can optimize your fraud detection system effectively while minimizing operational costs and maximizing fraud detection accuracy.
