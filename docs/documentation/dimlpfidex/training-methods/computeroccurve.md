# computeRocCurve

## Description

The `computeRocCurve` algorithm calculates and plots the `ROC` (Receiver Operating Characteristic) curve based on a set of test predictions and true classes. The `ROC` curve is a graphical representation that illustrates the diagnostic ability of a binary classifier as its decision threshold is varied. It plots the true positive rate (sensitivity) against the false positive rate (1 - specificity), allowing for the evaluation of the model's performance across different thresholds. This implementation uses `scikit-learn`'s built-in functions to efficiently compute and plot the ROC curve, providing insights into the trade-off between sensitivity and specificity for the given predictions. Note that this algorithm is not applicable to [SVM](svmtrn.md) models.

## Arguments list
The `computeRocCurve` algorithm works with both required and optional arguments. Each argument has specific properties:

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

### Test true classes file
*File containing "true classes" (expected predictions), from the test portion of the dataset used to train the model.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_class_file` | 
| JSON identifier         | `test_class_file`   |
| Default value           | `None`              |

---

### Test prediction file

*File containing predictions on the test portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_pred_file`  | 
| JSON identifier         | `test_pred_file`    |
| Default value           | `None`              |

---

### Positive class index
*Index of positive class, index starts at `0`. Takes values in the range `[0,nb_classes-1]`.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | Yes                     |
| Type                    | `Integer`               |
| CLI argument syntax     | `--positive_class_index`|
| JSON identifier         | `positive_class_index`  |
| Default value           | `None`                  |

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

### Statistics output file
*Name of the output file that will contain the AUC score, it can be the training statistics file.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--stats_file`      |
| JSON identifier         | `stats_file`        |
| Default value           | `None`              |

---

### Display parameter inputs
*Whether to show currently used parameters by the program while running.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Boolean`           |
| CLI argument syntax     | `--show_params`     |
| JSON identifier         | `show_params`       |
| Default value           | `True`              |

---

### ROC output file
*Path to the file where the output ROC curve will be saved.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--output_roc`      |
| JSON identifier         | `output_roc`        |
| Default value           | `roc_curve.png`     |

---

### Estimator
*Name of the used estimator.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--estimator`      |
| JSON identifier         | `estimator`        |
| Default value           | `None`     |

---

## Usage example

!!!example

    === "Python"
        ```py
        from trainings import computeRocCurve

        computeRocCurve(
        """--test_class_file test_class.txt 
        --test_pred_file predTest.out 
        --positive_class_index 1 
        --output_roc roc_curve.png 
        --stats_file stats.txt 
        --root_folder dimlp/datafiles 
        --nb_classes 2"""
        )
        ```
        
    === "CLI"
        ```
        ./computeRocCurve --test_class_file test_class.txt --test_pred_file predTest.out --positive_class_index 1 --output_roc roc_curve.png --stats_file stats.txt --root_folder ../dimlp/datafiles --nb_classes 2
        ```

## Output interpretation

---

### [Roc curve](#roc-output-file)

This file contains a ROC (Receiver Operating Characteristic) curve, which is used to evaluate the performance of the model during training. The ROC curve is a plot with the following components:

`X-Axis (False Positive Rate)`
:   This represents the proportion of negative samples that are incorrectly classified as positive. It measures the rate of false positives at various classification thresholds.

`Y-Axis (True Positive Rate)`
:   This represents the proportion of positive samples that are correctly classified as positive.

`Curve`
:   The curve itself shows the trade-off between the true positive rate and the false positive rate across different decision thresholds for the classifier. The curve starts at (0, 0) and moves towards (1, 1).

`AUC (Area Under the Curve)`
:   This value quantifies the overall performance of the model. It ranges from 0 to 1, with a value of 1 indicating perfect classification and a value of 0.5 indicating a model with no discriminative power. The higher the AUC, the better the model’s ability to distinguish between the positive and negative classes.

This ROC curve visually illustrates how well the model is performing by showing the balance between the true positive rate and the false positive rate, with the AUC providing a summary measure of the model's classification performance.

---

### [Statistics file](#statistics-output-file)

This file contains some statistics of the model aleady computed before. The AUC score computed on the test set is written at the end of the file.

`AUC (Area Under the Curve)`
:   This value quantifies the overall performance of the model. It ranges from 0 to 1, with a value of 1 indicating perfect classification and a value of 0.5 indicating a model with no discriminative power. The higher the AUC, the better the model’s ability to distinguish between the positive and negative classes.