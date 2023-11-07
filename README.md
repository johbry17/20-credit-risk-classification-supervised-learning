# Module 20 Challenge, 7 November 2023, Credit Risk Analysis Using Supervised Learning

## Overview of the Analysis

This project builds two supervised machine learning logistic regression models using data from a hypothetical peer-to-peer lending services company ("crowdlending"). It compares the results of both models and recommends using the later model, which corrects for sample size data skewing, to minimize the risk of loans to lenders and borrowers. Also, note the use of stratify=y to ensure proportionate data sampling in the splitting of training and testing data.

The training and testing data contains a range of standard financial loan information (loan size, debt to income ratio, interest rate, etc), and labels the data with whether or not the loan was repaid. The supervised learning models are tested by how effectively they predict the credit-worthy versus the defaulters.

Most of the data points (~97%) are credit-worthy (75,036 versus 2,500 defaulters). To minimize the data skewing that comes with such a disproportionate sample, the second model uses the RandomOverSampler module from the imbalanced-learn library, ensuring the credit-worthy and default-prone are equally represented in the training data, and delivering sufficiently statistically better results as detailed below.

## Results

* Machine Learning Model 1 (Logistic Regression predictions):
  * Accuracy: 99.2%
  * Balanced Accuracy: 94.4%
  * Precision and recall (credit-worthy): 100%, 100%
  * Precision and recall (defaulters): 87%, 89%

* Machine Learning Model 2 (Resampled Logistic Regression - i.e., ):
  * Accuracy: 99.5%
  * Balanced Accuracy: 99.6%
  * Precision and recall (credit-worthy): 100%, 100%
  * Precision and recall (defaulters): 87%, 100%

Some comparative stats, with the latter, resampled model's numbers always listed first: Lower false negatives (2 vs. 67). Slightly higher rate of false positives (91 vs. 80). Higher true negatives (623 vs. 558). Lower true positives (18679 vs. 18668). Precision and recall are the same in both models for the credit-worthy. Precision remains the same for defaulters (87%), but recall increased to 100% for the defaulters (from 89%). 

## Summary

The second model will give a few more loans out to the default-prone, but that's compensated for by screening out far more defaulters. 11 more defaulters will get loans, but 65 more defaulters will be correctly identified. The second model will, in general, lead to numerically more loan repayments. Assuming the monetary value of the loans is proportionate, the second model will give lenders a greater return on investment (a few more losses to gain substantially more income).

With the second model, a few more people who should not be lent money will get loans (false positives), but many more people who should be denied will be identified (true negatives). Risk is lower for lenders and presumably increases profitability.

## References

Dataset provided by edX Boot Camps, LLC

## Acknowledgments

Thanks to Geronimo Perez for feedback and assistance

## Author

Bryan Johns, November 2023
