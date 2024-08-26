## Overview

The data has been split into two groups:

* **Training set (`train.csv`)**
* **Test set (`test.csv`)**

The training set should be used to build your machine learning models, with the outcome provided for each passenger. Your model will use features like passengers’ gender and class, with potential feature engineering.

The test set should be used to evaluate your model on unseen data. The ground truth is not provided, and your goal is to predict survival for each passenger in the test set.

Additionally, a `gender_submission.csv` file is included as an example of a submission format, assuming all female passengers survive.

## Data Dictionary

| Variable | Definition                   | Key                                                    |
| -------- | ---------------------------- | ------------------------------------------------------ |
| surviva  | Survival                     | 0 = No<br />1 = Yes                                    |
| pclass   | Ticket class                 | 1 = 1st<br />2 = 2nd<br />3 = 3rd                      |
| sex      | Sex                          |                                                        |
| age      | Age in years                 |                                                        |
| sibsp    | # of siblings/spouses aboard |                                                        |
| parch    | # of parents/children aboard |                                                        |
| ticket   | Ticket number                |                                                        |
| fare     | Passenger fare               |                                                        |
| cabin    | Cabin number                 |                                                        |
| embarked | Port of Embarkation          | C = Cherbourg<br />Q = Queenstown<br />S = Southampton |

## Variable Notes

* **pclass** : Proxy for socio-economic status (SES)
  * 1st = Upper, 2nd = Middle, 3rd = Lower
* **age** : Fractional if less than 1; estimates are in the form of `xx.5`
* **sibsp** : Family relations as:
  * Sibling = brother, sister, stepbrother, stepsister
  * Spouse = husband, wife (mistresses and fiancés ignored)
* **parch** : Family relations as:
  * Parent = mother, father
  * Child = daughter, son, stepdaughter, stepson
  * Some children traveled only with a nanny, hence `parch=0` for them.
