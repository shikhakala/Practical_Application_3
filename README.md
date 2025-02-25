Readme file

## Notebook path:

[Practical Application 3 notebook](<https://github.com/shikhakala/Practical_Application_3/blob/main/Shikha_Practical_Application_3.ipynb>)

## Key findings document path:

[Analysis document](<https://github.com/shikhakala/Practical_Application_3/blob/main/Practical_Application3_Analysis_and_Findings.docx>)

## Summary of model comparison

### Before Undersampling

| **Model**              | **Test Accuracy** | **Precision** | **Recall** | **F1**   | **ROC-AUC** | **Train Time (s)** |
|------------------------|-------------------|---------------|------------|----------|-------------|--------------------|
| **KNN**                | 0.6765            | 0.2118        | 0.678      | 0.323    | 0.7269      | 0.2292             |
| **LogisticRegression** | 0.7116            | 0.2374        | **0.694**  | 0.354    | 0.7421      | 0.2795             |
| **DecisionTree**       | 0.7984            | 0.3121        | 0.642      | **0.42** | 0.7767      | **0.1468**         |
| **SVM**                | 0.7122            | 0.2377        | 0.694      | 0.354    | 0.7524      | 192.6366           |

**Observations (Before Undersampling)**

1.  **Highest Recall**: Logistic Regression (0.6943) and SVM (0.6935) → Good for catching positives but with modest precision (\~0.24).
2.  **Highest F1**: Decision Tree (0.42), plus best ROC-AUC (0.7767) and high accuracy (0.7984). However, recall is slightly lower (0.6419).
3.  **Training Time**:
    -   **Fastest** is Decision Tree (\~0.15 s).
    -   **Slowest** is SVM (\~192.64 s).

If you **prioritize recall** to avoid missing potential subscribers, **Logistic Regression** or **SVM** stands out. If you want a **more balanced** approach (F1), **Decision Tree** is strong. **KNN** has the lowest accuracy but decent recall (\~0.678).

### After Undersampling

| **Model**              | **Test Accuracy** | **Precision** | **Recall** | **F1**    | **ROC-AUC** | **Train Time (s)** |
|------------------------|-------------------|---------------|------------|-----------|-------------|--------------------|
| **KNN**                | **0.8406**        | 0.372         | 0.582      | 0.454     | 0.7395      | 20.3               |
| **LogisticRegression** | 0.7116            | 0.237         | **0.694**  | 0.354     | 0.7415      | **4.56**           |
| **DecisionTree**       | 0.7949            | 0.311         | 0.661      | **0.423** | 0.7781      | 9.59               |
| **SVM**                | 0.7116            | 0.237         | **0.694**  | 0.354     | 0.7424      | 170.99             |

**Observations (After Undersampling)**

1.  **KNN** jumps to the highest test accuracy (0.8406), but recall is moderate (0.582).
2.  **Logistic Regression & SVM** still **tie on recall** (\~0.694), just like before, with moderate precision.
3.  **Decision Tree** has the best F1 (0.423) and highest ROC-AUC (0.7781).
4.  **Training Time**: Logistic Regression is still fast (4.56 s), while SVM remains slower (170.99 s).

**Undersampling** often boosts recall for some models at the expense of accuracy or precision. KNN notably improves accuracy here, but its recall (0.582) is lower than Logistic Regression/SVM’s \~0.694. Meanwhile, Decision Tree retains a strong balance (F1=0.423, ROC-AUC=0.7781).

### Key Takeaways

1.  **If You Want Highest Recall**:
    -   **Logistic Regression** or **SVM** (both \~0.69 recall), either before or after undersampling, is best for minimizing missed positives.
2.  **If You Want a More Balanced Approach**:
    -   **Decision Tree** often has the best **F1** and strong **ROC-AUC**, though its recall is somewhat lower (\~0.64–0.66).
3.  **KNN’s Contrasting Results**:
    -   **Before** undersampling: Lower accuracy (0.6765) but decent recall (\~0.678).
    -   **After** undersampling: Best accuracy (0.8406) but recall drops (\~0.582).
    -   KNN is sensitive to data distribution changes (like undersampling).
4.  **Undersampling’s Effect**:
    -   Often **improves recall** or changes how models handle the minority class.
    -   May lower precision or accuracy depending on the model.
    -   In this comparison, it boosts KNN’s accuracy significantly but doesn’t necessarily increase recall for all models.

**Summary**

-   **Decision Tree** offers a strong **F1** and **ROC-AUC** if you want a more balanced solution.
-   **Logistic Regression** and **SVM** remain the top choices for **max recall**—ideal if you don’t want to miss potential positive cases (e.g., subscribers).
-   **KNN** is more sensitive to sampling changes, showing high accuracy after undersampling but lower recall, which might not be optimal if your priority is to catch positives.

## Key Business Findings

1.  **Prior Contact Increases Subscription Rates**
    -   **What We Saw:** Clients who were contacted before are far more likely to say “yes” than those contacted for the first time.
    -   **Why It Matters:** Building on existing relationships often yields better results than cold calls.
2.  **Macro-Economic Factors Influence Decisions**
    -   **What We Saw:** Variables like interest rates (Euribor) and employment rates affect whether clients sign up.
    -   **Why It Matters:** Launching campaigns during favorable economic periods can improve success rates.
3.  **Different Models Yield Different Strengths**
    -   **Logistic Regression (Balanced)** consistently catches more potential subscribers (**high recall**).
    -   **Decision Tree** offers a more balanced overall performance (higher F1) but misses more potential subscribers.
    -   **SVM** is similar to Logistic Regression in recall but slower to train.
    -   **KNN** can achieve good accuracy but may miss too many potential subscribers.
4.  **Class Imbalance Distorts Accuracy**
    -   **What We Saw:** If we always predict “no subscription,” we get high accuracy (\~88–90%) but miss all actual positives.
    -   **Why It Matters:** We must focus on **recall** (catching real subscribers) to avoid losing potential sales.

## Next Steps and Recommendations:

1.  **Prioritize Clients with Past Engagement**
    -   **Recommendation:** Make follow-up calls or personalized offers to clients who have interacted with the bank before.
    -   **Benefit:** They are 2–3 times more likely to subscribe than first-time contacts.
2.  **Choose the Right Model**
    -   **Recommendation:** Use **Logistic Regression with Balanced Settings** for highest recall (\~69%), ensuring fewer missed subscribers.
    -   **Benefit:** Minimizes lost opportunities, trains quickly, and is straightforward to interpret.
3.  **Leverage Economic Context**
    -   **Recommendation:** Track economic indicators (e.g., Euribor rates). If rates are favorable, invest more in campaigns; if not, adjust your approach.
    -   **Benefit:** Aligning marketing efforts with good economic conditions can boost subscription rates.
4.  **Adjust the Calling Threshold**
    -   **Recommendation:** Consider lowering the model’s decision cutoff to flag more potential “yes” clients.
    -   **Benefit:** Increases the number of possible subscribers contacted, especially important if phone call costs are low.
5.  **Monitor and Refine Regularly**
    -   **Recommendation:** Retrain or tune the model every few months, as client behavior and economic conditions change.
    -   **Benefit:** Ensures predictions stay accurate over time, maintaining high conversion rates.
