# randForestsTrn

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

The `Random Forest` model is an ensemble learning method that constructs multiple decision trees during training and merges their outputs to improve overall predictive accuracy and reduce overfitting. This method is highly effective for both classification and regression tasks. In this implementation, we use the version provided by `scikit-learn`, which allows for flexible and efficient training. The generated decision tree rules allow [Fidex](../fidex/overview.md) to identify hyperplanes in the feature space that discriminate between different classes, thus enabling the extraction of decision rules, making the model's decisions more transparent and easier to explain. For more details on the `Random Forest` algorithm with `Dimlp`, you can refer to [this paper](../../references.md#a-rule-extraction-technique-applied-to-ensembles-of-neural-networks-random-forests-and-gradient-boosted-trees).

## Arguments list
The `randForestsTrn` algorithm works with both required and optional arguments. Each argument has specific properties:

- **Is required** means whether an argument **must** be specified when calling the program or not.
- **Type** specifies the argument datatype.
- **CLI argument syntax** is the exact name to use if you are writing the argument along with the program call.
- **JSON identifier** is the exact name to use if you are writing the argument inside a [JSON configuration file](../../file-formats/json-configuration-files.md).
- **Default value** is the value that will be used by the program if the argument is not specified. If `None`, it could mean that the argument is not used at all during the algorithm execution or could also mean that you have to specify it yourself.

---

### Show help
*Display parameters and other helpful information concerning the program usage and terminate it when done.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `None`                  |
| CLI argument syntax     | `-h`, `--help` or `None`|
| JSON identifier         | `N/A`                   |
| Default value           | `None`                  |

!!!Warning
    Every other specified argument will be ignored.

---

### JSON configuration file
*File containing the configuration for the algorithm in JSON format (see more about [JSON configuration files](../../file-formats/json-configuration-files.md)).*

|  **Property**           | **Value**                   |
|:------------------------|:----------------------------|
| Is required             | No                          |
| Type                    | `String`                    |
| CLI argument syntax     | `--json-configuration-file` | 
| JSON identifier         | `N/A`                       |
| Default value           | `None`                      |

!!!Warning
    If you use this argument, **it must be the only one specified**. No other argument can be specified with it.

---

### Root folder path
*Default path from where all the other arguments related to file paths are going to be based. Using this allows you to work with paths relative to this location and avoid writing absolute paths or lengthy relative paths.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--root_folder`     | 
| JSON identifier         | `root_folder`       |
| Default value           | `.`                 |

---

### Train data file
*File containing the train portion of the dataset, It can also contain training "true classes" (see [Train true classes file](#train-true-classes-file)).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--train_data_file` |
| JSON identifier         | `train_data_file`   |
| Default value           | `None`              |

--- 

### Test data file

*Path to the file containing test portion of the dataset, It can also contain testing "true classes" (see [Test true classes file](#test-true-classes-file)).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_data_file`  | 
| JSON identifier         | `test_data_file`    |
| Default value           | `None`              |

---

### Number of attributes 
*Number of attributes in the dataset (should be equal to the number of inputs of the model). Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_attributes`   | 
| JSON identifier         | `nb_attributes`     |
| Default value           | `None`              |

---

### Number of classes
*Number of classes in the dataset (should be equal to the number of outputs of the model). Takes values in the range `[2,∞[`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_classes`      |
| JSON identifier         | `nb_classes`        |
| Default value           | `None`              |

---

### Train true classes file
*File containing "true classes" (expected predictions), from the train portion of the dataset used to train the model.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No**                 |
| Type                    | `String`             |
| CLI argument syntax     | `--train_class_file` | 
| JSON identifier         | `train_class_file`   |
| Default value           | `None`               |

!!! warning
    This argument is not required if, **and only if**, the *true classes* are already specified inside the [train data file](#train-data-file).

---

### Test true classes file
*File containing "true classes" (expected predictions), from the test portion of the dataset used to train the model.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `String`            |
| CLI argument syntax     | `--test_class_file` | 
| JSON identifier         | `test_class_file`   |
| Default value           | `None`              |

!!! warning
    This argument is not required if, **and only if**, the *true classes* are already specified inside the [test data file](#test-data-file). 

---

### Train prediction output file 
*Path to the file where the train predictions will be stored.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `String`                     |
| CLI argument syntax     | `--train_pred_outfile`       | 
| JSON identifier         | `train_pred_outfile`         |
| Default value           | `predTrain.out`              |

---

### Test prediction output file 
*Path to the file where the test predictions will be stored.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `String`                     |
| CLI argument syntax     | `--test_pred_outfile`        | 
| JSON identifier         | `test_pred_outfile`          |
| Default value           | `predTest.out`               |

---

### Statistics output file
*Name of the output file that will contain all computed statistics.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--stats_file`      |
| JSON identifier         | `stats_file`        |
| Default value           | `stats.txt`         |

---

### Logs output file
*Name of file containing every feedback made by the algorithm during its execution. If not specified, the feedback is displayed into the terminal.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--console_file`    |
| JSON identifier         | `console_file`      |
| Default value           | `None`              |

---

### Rules output file
*Path to the file where the random forests output rules will be stored.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--rules_outfile`   |
| JSON identifier         | `rules_outfile`     |
| Default value           | `RF_rules.rls`      |

---

### Number of estimators
*Number of generated trees in the forest. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Integer`           |
| CLI argument syntax     | `--n_estimators`    |
| JSON identifier         | `n_estimators`      |
| Default value           | `100`               |

---

### Criterion
*Function to measure split quality. Options are `gini`, `entropy`, and `log_loss`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--criterion`       |
| JSON identifier         | `criterion`         |
| Default value           | `gini`              |

---

### Maximum depth
*Maximum depth of the tree. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Integer`            |
| CLI argument syntax     | `--max_depth`        |
| JSON identifier         | `max_depth`          |
| Default value           | `None`               |

---

### Minimum of samples to split
*Minimum number of samples required to split an internal node, if float, it is a fraction of the number of samples. Takes `integers` in the range `[2,∞[` and `floats` in the range `]0,1]`.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Integer` or `Float` |
| CLI argument syntax     | `--min_samples_split`|
| JSON identifier         | `min_samples_split`  |
| Default value           | `2`                  |

---

### Minimum of samples to be leaf
*Minimum number of samples required to be at a leaf node, if float, it is a fraction of the number of samples. Takes `integers` in the range `[1,∞[` and `floats` in the range `]0,1[`.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Integer` or `Float` |
| CLI argument syntax     | `--min_samples_leaf` |
| JSON identifier         | `min_samples_leaf`   |
| Default value           | `1`                  |

---

### Minimum weighted fraction to be leaf
*Minimum weighted fraction of the sum total of input samples weights required to be at a leaf node. Takes values in the range `[0,0.5]`.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `Float`                      |
| CLI argument syntax     | `--min_weight_fraction_leaf` |
| JSON identifier         | `min_weight_fraction_leaf`   |
| Default value           | `0.0`                        |

---


### Maximum number of features
*Number of features to consider when looking for the best split. If float, it is a fraction of the number of features. `1` stand for `1 feature`, for all features put `all`, not `1.0`. Values can be a `String`, options are: `sqrt`, `log2` or `all`. Takes `floats` in the range `]0,1[` and `integers` in the range `[1,∞[`.*

|  **Property**           | **Value**                      |
|:------------------------|:-------------------------------|
| Is required             | No                             |
| Type                    | `Integer` or `Float` or `String`|
| CLI argument syntax     | `--max_features`               |
| JSON identifier         | `max_features`                 |
| Default value           | `sqrt`                         |

---

### Maximum number of leaf nodes
*Grow trees with a limited amount of leaf nodes in a best-first fashion. Takes values in the range `[2,∞[`.*

|  **Property**           | **Value**          |
|:------------------------|:-------------------|
| Is required             | No                 |
| Type                    | `Integer`          |
| CLI argument syntax     | `--max_leaf_nodes` |
| JSON identifier         | `max_leaf_nodes`   |
| Default value           | `None`             |
                                                            
---

### Minimal impurity decrease
*A node will be split if this split induces a decrease of the impurity greater than or equal to this value. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `Float`                   |
| CLI argument syntax     | `--min_impurity_decrease` |
| JSON identifier         | `min_impurity_decrease`   |
| Default value           | `0.0`                     |

---

### Bootstrap
*Whether bootstrap samples are used when building trees.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `Boolean`                 |
| CLI argument syntax     | `--bootstrap`             |
| JSON identifier         | `bootstrap`               |
| Default value           | `True`                    |

---

### Out-of-bag score
*Whether to use out-of-bag samples to estimate the generalization score.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `Boolean`                 |
| CLI argument syntax     | `--oob_score`             |
| JSON identifier         | `oob_score`               |
| Default value           | `False`                   |

---

### Number of jobs
*Number of jobs to run in parallel, `-1` = using all processors.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `Integer`                 |
| CLI argument syntax     | `--n_jobs`                |
| JSON identifier         | `n_jobs`                  |
| Default value           | `1`                       |

---

### Seed
*Seed for random number generation. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `Integer`                 |
| CLI argument syntax     | `--seed`                  |
| JSON identifier         | `seed`                    |
| Default value           | `None`                    |

---

### Verbose
*Controls the verbosity when fitting and predicting. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Integer`             |
| CLI argument syntax     | `--verbose`           |
| JSON identifier         | `verbose`             |
| Default value           | `0`                   |

---

### Warm start
*Whether to reuse the solution of the previous call to fit and add more estimators to the ensemble.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Boolean`             |
| CLI argument syntax     | `--warm_start`        |
| JSON identifier         | `warm_start`          |
| Default value           | `False`               |

---

### Class weight
*Class balance, for exemple with a dictionnary and 2 classes : `{0:1.2, 1:3.5}`. Can also be `balanced` and `balanced_subsample`.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `String` or `Dictionnary` |
| CLI argument syntax     | `--class_weight`          |
| JSON identifier         | `class_weight`            |
| Default value           | `None`                    |

---

### CCP alpha
*Complexity parameter used for Minimal Cost-Complexity Pruning. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**    |
|:------------------------|:------------ |
| Is required             | No           |
| Type                    | `Float`      |
| CLI argument syntax     | `--ccp_alpha`|
| JSON identifier         | `ccp_alpha`  |
| Default value           | `0.0`        |

---

### Maximum samples to draw
*Number of samples to draw to train each base estimator for bootstrap, if float, it is a fraction of the number of samples. Takes `floats` in the range `]0,1]` and `integers` in the range `[1,∞[`.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Float` or `Integer` |
| CLI argument syntax     | `--max_samples`      |
| JSON identifier         | `max_samples`        |
| Default value           | `None`               |

---

## Usage example

!!!example

    === "Python"
        ```py
        from trainings import randForestsTrn

        randForestsTrn(
        """--train_data_file train_data.txt 
        --train_class_file train_class.txt 
        --test_data_file test_data.txt 
        --test_class_file test_class.txt 
        --stats_file rf/stats.txt 
        --train_pred_outfile rf/predTrain.out 
        --test_pred_outfile rf/predTest.out 
        --rules_outfile rf/RF_rules.rls 
        --nb_attributes 16 
        --nb_classes 2 
        --root_folder dimlp/datafiles"""
        )
        ```
        
    === "CLI"
        ```
        ./randForestsTrn --train_data_file train_data.txt --train_class_file train_class.txt --test_data_file test_data.txt --test_class_file test_class.txt --stats_file rf/stats.txt --train_pred_outfile rf/predTrain.out --test_pred_outfile rf/predTest.out --rules_outfile rf/RF_rules.rls --nb_attributes 16 --nb_classes 2 --root_folder ../dimlp/datafiles
        ```

## Output interpretation

---

### [Train/Test prediction file](#train-prediction-output-file)

This file contains the predicted probabilities for each possible class for each train (or test) sample. Each row corresponds to the prediction for a single sample, with `N` values representing the probability that the sample belongs to class `0`, `1`, ... or class `N`. The values in each row sum to 1. The class with the highest probability is considered the predicted class for that sample, unless a decision threshold is applied for a specific class. In that case, if the predicted probability for that class exceeds the threshold, the sample is classified as belonging to that class.

For example:

    0.000718874 0.999281
    0.949143 0.050857

In the first row, the model predicts a probability of approximately 0.0007 that the sample belongs to class 0, and 0.9993 that it belongs to class 1. Therefore, the model predicts class 1 for this sample.
In the second row, the model predicts a probability of 0.949 that the sample belongs to class 0, and 0.051 that it belongs to class 1. Hence, the model predicts class 0 for this sample.

Each row of probabilities allows you to interpret the model's confidence in its predictions, enabling you to understand the likelihood of each sample belonging to a particular class.

---

### [Rules output file](#rules-output-file)

This file contains the decision rules generated by the Random Forest model. Each rule corresponds to a specific decision path within a tree, leading to a prediction for a particular class. These rules are used to identify the discriminant hyperplanes in the feature space during the [Fidex](../fidex/overview.md) algorithm.

<p style="font-size:larger;">File structure:</p>

The file is organized into trees, with each tree containing a series of rules. Each tree contributes to the overall decision-making process in the Random Forest model.

<p style="font-size:larger;">Rule structure:</p>

Each rule consists of conditions on various attributes, followed by a score value. Let's break down this rule as an example:

    Rule 46: X0>0.6833335161209106 X3<=0.4423079937696457 X12<=0.5 X0<=0.75 -> class 1 Covering: [0, 1]

`X0, X3, X12`
:   These represent the variables from the dataset.

`Rule 46`
:   This indicates the rule number within the tree.

`Conditions`
:   The conditions are logical comparisons between a feature (X) and a threshold value (e.g., X1<=0.5). Multiple conditions are combined in a rule, and all conditions must be satisfied for the rule to apply.

`class 1`
:   The class predicted by the rule when the conditions are met. Here, the rule predicts class 1.

`Covering: [0, 1]`
:   The covering indicates the number of samples in the training dataset that are covered by the rule and belong to each class. For example, a covering of [1, 0] means that one sample belonging to class 0 is covered by this rule, while [0, 1] means that one sample belonging to class 1 is covered.

---

### [Statistics file](#statistics-output-file)

This file contains accuracy on the training and testing sets. It offers a clear overview of the model’s performance across different datasets, helping to evaluate how well the model has learned and generalized to unseen data.

`Accuracy`
:   Indicates the proportion of correctly classified samples in each dataset (training or testing).