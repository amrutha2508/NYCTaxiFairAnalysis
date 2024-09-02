# NYCTaxiFairAnalysis

Following points highlight the critical aspects of data preparation, cleaning, and modeling, along with insights into the taxi fare data and its predictive modeling.

**1. Data Quality Issues:**
   
-> No null values, but several variables have negative values that don't make sense (e.g., fare_amount, extra, mta_tax, improvement_surcharge, total_amount).

-> Outliers are present in fare_amount, trip_distance, tip_amount, and total_amount.

-> RateCodeID has an unusual value of 99 which should be addressed.

-> There are trips with passenger_count = 0 and trip_distance = 0, potentially indicating canceled trips or data errors.

**2. Data Cleaning:**
   
-> Remove the Unnamed: 0 column as it's not useful.

-> Variables like improvement_surcharge, mta_tax, and extra are considered to have minimal impact on price and should be removed based on domain knowledge.

-> Impute or handle outliers in trip_distance, fare_amount, tip_amount, and total_amount.

-> Address negative values in monetary columns.

**3. Feature Considerations:**
   
-> RateCodeID should be examined for unusual values and its impact on fare amount.

-> VendorID does not provide significant predictive value for total_amount.

-> passenger_count shows minimal variation in effect on tip amounts.

-> payment_type shows significant differences, particularly between credit card and cash payments, which may be leveraged for encouraging specific payment methods.

**4. Observations:**

-> Trips to specific locations (e.g., Newark, JFK) and with certain rate codes (e.g., RateCodeID 2) have higher total_amounts.

-> High tip amounts are observed for trips to/from Newark/JFK and those paid by credit card.

-> trip_distance shows high variability and outliers but may not need alteration due to reasonable physical distance constraints.

-> Monthly and daily ride patterns show seasonal and weekly variations, with notable dips in summer months and February, and higher revenues on Thursdays.

**5. Modeling Insights:**

->There was evidence of data leakage when using mean_distance and mean_duration columns. To avoid this, compute means using only the training data and apply them to the test set.

->Separate handling of data with RateCodeID 2 (JFK trips) may improve model accuracy.

**6. Model Performance:**

->The model performed well with an R² of 0.871 on the test set, indicating it explains a substantial portion of the variance in fare_amount.

->The performance suggests that the model is robust and not overfitting, with better performance on the test set compared to the training set.
