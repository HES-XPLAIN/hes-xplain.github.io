# gradBoostTrn

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

## Arguments list
The `gradBoostTrn` algorithm works with both required and optional arguments. Each argument has specific properties:

- **Is required** means whether an argument **must** be specified when calling the program or not.
- **Type** specifies the argument datatype.
- **CLI argument syntax** is the exact name to use if you are writing the argument along with the program call.
- **JSON identifier** is the exact name to use if you are writing the argument inside a [JSON configuration file](../../file-formats/json-configuration-files.md).
- **Default value** is the value that will be used by the program if the argument is not specified. If `none`, it could mean that the argument is not used at all during the algorithm execution or could also mean that you have to specify it yourself.

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
*Number of attributes in the dataset (should be equal to the number of inputs of the model).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_attributes`   | 
| JSON identifier         | `nb_attributes`     |
| Default value           | `None`              |

---

### Number of classes
*Number of classes in the dataset (should be equal to the number of outputs of the model).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_classes`      |
| JSON identifier         | `nb_classes`        |
| Default value           | `None`              |

---

### Show help
*Display parameters and other helpful information concerning the program usage and terminate it when done.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `None`              |
| CLI argument syntax     | `-h` or `--help`    |
| JSON identifier         | `N/A`               |
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
| Default value           | `None`              |

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
*Number of generated trees in the forest.*

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
*Shrinks the contribution of each tree.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Float`             |
| CLI argument syntax     | `--learning_rate`   |
| JSON identifier         | `learning_rate`     |
| Default value           | `0.1`               |

---

### Subsample
*Fraction of samples to be used for fitting the individual base learners.*

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
*Maximum depth of the individual regression estimators. Can be an `Integer` from `2` to infinity or `no_max_depth`.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Integer` or `String`|
| CLI argument syntax     | `--max_depth`        |
| JSON identifier         | `max_depth`          |
| Default value           | `3`                  |

---

### Minimum of samples to split
*Minimum number of samples required to split an internal node, if float, it is a fraction of the number of samples.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Integer` or `Float` |
| CLI argument syntax     | `--min_samples_split`|
| JSON identifier         | `min_samples_split`  |
| Default value           | `2`                  |

---

### Minimum of samples to be leaf
*Minimum number of samples required to be at a leaf node, if float, it is a fraction of the number of samples.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Integer` or `Float` |
| CLI argument syntax     | `--min_samples_leaf` |
| JSON identifier         | `min_samples_leaf`   |
| Default value           | `1`                  |

---

### Minimum weighted fraction to be leaf
<!-- TODO: this description is weird, should be replaced -->
*Minimum weighted fraction of the total sum of input samples weights required to be at a leaf node. Goes from `0.0` to `0.5`.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `Float`                      |
| CLI argument syntax     | `--min_weight_fraction_leaf` |
| JSON identifier         | `min_weight_fraction_leaf`   |
| Default value           | `0.0`                        |

---

### Maximum number of features
*Number of features to consider when looking for the best split. If float, it is a fraction of the number of features. `1` stand for `1 feature`, for all features put `all`, not `1.0`. Values can be a `String`, options are: `sqrt`, `log2` or `all`. It can be a `float` from `0.0` to `1.0` or an `integer` from `1` to infinity.*

|  **Property**           | **Value**                      |
|:------------------------|:-------------------------------|
| Is required             | No                             |
| Type                    | `Integer` or `Float` or `String`|
| CLI argument syntax     | `--max_features`               |
| JSON identifier         | `max_features`                 |
| Default value           | `sqrt`                         |

---

### Maximum number of leaf nodes
*Grow trees with a limited amount of leaf nodes in a best-first fashion.*

|  **Property**           | **Value**          |
|:------------------------|:-------------------|
| Is required             | No                 |
| Type                    | `Integer`           |
| CLI argument syntax     | `--max_leaf_nodes` |
| JSON identifier         | `max_leaf_nodes`   |
| Default value           | `None`             |
                                                            
---

### Minimum impurity decrease
*A node will be split if this split induces a decrease of the impurity greater than or equal to this value.*

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
*Seed for random number generation. From `0` to infinity.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | No              |
| Type                    | `Integer`       |
| CLI argument syntax     | `--seed`        |
| JSON identifier         | `seed`          |
| Default value           | `None`          |

---

### Verbosity level
*Controls the verbosity when fitting and predicting.*

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
*Proportion of training data to set aside as validation set for early stopping. Goes from `0.0` to `1.0`*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Float`                  |
| CLI argument syntax     | `--validation_fraction`  |
| JSON identifier         | `validation_fraction`    |
| Default value           | `0.1`                    |

---

### Number of non-significant iterations before stopping
*Decide if early stopping will be used to terminate training when the validation score is not improving, stopping if the validation doesn't improve during this number of iterations.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Integer`                |
| CLI argument syntax     | `--n_iter_no_change`     |
| JSON identifier         | `n_iter_no_change`       |
| Default value           | `None`                   |

---

### Tolerance
*Tolerance for the early stopping.*

|  **Property**           | **Value**   |
|:------------------------|:------------|
| Is required             | No          |
| Type                    | `Float`     |
| CLI argument syntax     | `--tol`     |
| JSON identifier         | `tol`       |
| Default value           | `0.0001`    |

---

### CCP alpha
*Complexity parameter used for Minimal Cost-Complexity Pruning.*

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
    """--train_data_file datanormTrain.txt 
       --train_class_file dataclass2Train.txt 
       --test_data_file datanormTest.txt 
       --test_class_file dataclass2Test.txt 
       --stats_file gb/stats.txt 
       --train_pred_outfile gb/predTrain.out 
       --test_pred_outfile gb/predTest.out 
       --rules_outfile gb/RF_rules.rls 
       --nb_attributes 16 
       --nb_classes 2 
       --root_folder dimlp/datafiles"""
    )
    ```
    
=== "CLI"
    ```
    ./gradBoostTrn --train_data_file datanormTrain.txt --train_class_file dataclass2Train.txt --test_data_file datanormTest.txt --test_class_file dataclass2Test.txt --stats_file gb/stats.txt --train_pred_outfile gb/predTrain.out --test_pred_outfile gb/predTest.out --rules_outfile gb/RF_rules.rls --nb_attributes 16 --nb_classes 2 --root_folder dimlp/datafiles
    ```

## Output interpretation