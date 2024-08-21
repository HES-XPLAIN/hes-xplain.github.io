# gradBoostTrn

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

The `Gradient Boosting` decision tree model is an ensemble learning technique that builds a series of decision trees, where each tree corrects the errors of the previous ones. This method is widely used for both classification and regression tasks due to its strong predictive performance. In this implementation, we use the version provided by `scikit-learn`, which allows for flexible and efficient training. The generated decision tree rules allow [Fidex](../fidex/overview.md) to identify hyperplanes in the feature space that discriminate between different classes, thus enabling the extraction of decision rules, making the model's decisions more transparent and easier to explain. For more details on the `Gradient Boosting` algorithm with `Dimlp`, you can refer to [this paper](../../references.md#a-rule-extraction-technique-applied-to-ensembles-of-neural-networks-random-forests-and-gradient-boosted-trees).

## Arguments list
The `gradBoostTrn` algorithm works with both required and optional arguments. Each argument has specific properties:

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
*Default path from where all the other arguments related to file paths are going to be based. Using this allows you to work with paths relative from this location and avoid writing absolute paths or lengthy relative paths.*

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

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `String`              |
| CLI argument syntax     | `--train_pred_outfile`| 
| JSON identifier         | `train_pred_outfile`  |
| Default value           | `predTrain.out`       |

---

### Test prediction output file

*Path to the file where the test predictions will be stored.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `String`             |
| CLI argument syntax     | `--test_pred_outfile`| 
| JSON identifier         | `test_pred_outfile`  |
| Default value           | `predTest.out`       |

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
*Path to the file where the gradient boosting output rules will be stored.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--rules_outfile`   |
| JSON identifier         | `rules_outfile`     |
| Default value           | `GB_rules.rls`      |

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

### Loss function
*Loss function to be used and optimized. Options are `log_loss` and `exponential`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--loss`            |
| JSON identifier         | `loss`              |
| Default value           | `log_loss`          |

---

### Learning rate
*Shrinks the contribution of each tree. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Float`             |
| CLI argument syntax     | `--learning_rate`   |
| JSON identifier         | `learning_rate`     |
| Default value           | `0.1`               |

---

### Subsample
*Fraction of samples to be used for fitting the individual base learners. Takes values in the range `]0,1]`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Float`             |
| CLI argument syntax     | `--subsample`       |
| JSON identifier         | `subsample`         |
| Default value           | `1.0`               |

---

### Criterion
*Function to measure split quality. Options are `friedman_mse` and `squared_error`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--criterion`       |
| JSON identifier         | `criterion`         |
| Default value           | `friedman_mse`      |

---

### Maximum depth
*Maximum depth of the individual regression estimators. Can be an `Integer` in the range `[2,∞[` or `no_max_depth`.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Integer` or `String`|
| CLI argument syntax     | `--max_depth`        |
| JSON identifier         | `max_depth`          |
| Default value           | `3`                  |

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
| Type                    | `Integer`, `Float` or `String` |
| CLI argument syntax     | `--max_features`               |
| JSON identifier         | `max_features`                 |
| Default value           | `sqrt`                         |

---

### Maximum number of leaf nodes
*Grow trees with a limited amount of leaf nodes in a best-first fashion. Takes values in the range `[2,∞[`.*

|  **Property**           | **Value**          |
|:------------------------|:-------------------|
| Is required             | No                 |
| Type                    | `Integer`           |
| CLI argument syntax     | `--max_leaf_nodes` |
| JSON identifier         | `max_leaf_nodes`   |
| Default value           | `None`             |
                                                            
---

### Minimum impurity decrease
*A node will be split if this split induces a decrease of the impurity greater than or equal to this value. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `Float`                   |
| CLI argument syntax     | `--min_impurity_decrease` |
| JSON identifier         | `min_impurity_decrease`   |
| Default value           | `0.0`                     |
                                                            
---

### Initial estimator
*Estimator object used to compute the initial predictions. Option is `zero`.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | No              |
| Type                    | `String`        |
| CLI argument syntax     | `--init`        |
| JSON identifier         | `init`          |
| Default value           | `None`          |

---

### Seed
*Seed for random number generation. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | No              |
| Type                    | `Integer`       |
| CLI argument syntax     | `--seed`        |
| JSON identifier         | `seed`          |
| Default value           | `None`          |

---

### Verbosity level
*Controls the verbosity when fitting and predicting. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | No              |
| Type                    | `Integer`       |
| CLI argument syntax     | `--verbose`     |
| JSON identifier         | `verbose`       |
| Default value           | `0`             |

---

### Warm start
*Whether to reuse the solution of the previous call to fit and add more estimators to the ensemble.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | No              |
| Type                    | `Boolean`       |
| CLI argument syntax     | `--warm_start`  |
| JSON identifier         | `warm_start`    |
| Default value           | `False`         |

---

### Validation Fraction
*Proportion of training data to set aside as validation set for early stopping. Takes values in the range `]0,1[`.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Float`                  |
| CLI argument syntax     | `--validation_fraction`  |
| JSON identifier         | `validation_fraction`    |
| Default value           | `0.1`                    |

---

### Number of non-significant iterations before stopping
*Decide if early stopping will be used to terminate training when the validation score is not improving, stopping if the validation doesn't improve during this number of iterations. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Integer`                |
| CLI argument syntax     | `--n_iter_no_change`     |
| JSON identifier         | `n_iter_no_change`       |
| Default value           | `None`                   |

---

### Tolerance
*Tolerance for the early stopping. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**   |
|:------------------------|:------------|
| Is required             | No          |
| Type                    | `Float`     |
| CLI argument syntax     | `--tol`     |
| JSON identifier         | `tol`       |
| Default value           | `0.0001`    |

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

## Usage example

=== "Python"
    ```py
    from trainings import gradBoostTrn

    gradBoostTrn(
    """--train_data_file train_data.txt 
       --train_class_file train_class.txt 
       --test_data_file test_data.txt 
       --test_class_file test_class.txt 
       --stats_file gb/stats.txt 
       --train_pred_outfile gb/predTrain.out 
       --test_pred_outfile gb/predTest.out 
       --rules_outfile gb/GB_rules.rls 
       --nb_attributes 16 
       --nb_classes 2 
       --root_folder dimlp/datafiles"""
    )
    ```
    
=== "CLI"
    ```
    ./gradBoostTrn --train_data_file train_data.txt --train_class_file train_class.txt --test_data_file test_data.txt --test_class_file test_class.txt --stats_file gb/stats.txt --train_pred_outfile gb/predTrain.out --test_pred_outfile gb/predTest.out --rules_outfile gb/GB_rules.rls --nb_attributes 16 --nb_classes 2 --root_folder ../dimlp/datafiles
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

This file contains the decision rules generated by the Gradient Boosting Decision Tree model. Each set of rules corresponds to a specific tree in the model, and these rules are used to identify the discriminant hyperplanes in the feature space during the [Fidex](../fidex/overview.md) algorithm.

<p style="font-size:larger;">File structure:</p>

The file is organized into trees, with each tree containing a series of rules. Each tree contributes to the overall decision-making process in the Gradient Boosting model.

<p style="font-size:larger;">Rule structure:</p>

Each rule consists of conditions on various attributes, followed by a score value. Let's break down this rule as an example:

    Rule 1: X2<=0.8075000047683716 X0<=0.7166664898395538 X4<=0.5 -> value [1.69695588]

`X2, X0, X4`
:   These represent the variables from the dataset.

`Rule 1`
:   This indicates the rule number within the tree.

`Conditions`
:   The conditions are logical comparisons between a feature (X) and a threshold value (e.g., X1<=0.5). Multiple conditions are combined in a rule, and all conditions must be satisfied for the rule to apply.

`Value`
:   This represents the output value (or prediction) of the tree if the conditions of the rule are satisfied. The value is typically a contribution to the final prediction in the Gradient Boosting model.

---

### [Statistics file](#statistics-output-file)

This file contains accuracy on the training and testing sets. It offers a clear overview of the model’s performance across different datasets, helping to evaluate how well the model has learned and generalized to unseen data.

`Accuracy`
:   Indicates the proportion of correctly classified samples in each dataset (training or testing).