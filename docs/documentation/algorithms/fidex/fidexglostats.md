# FidexGloStats

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description
The `fidexGloStats` program extracts statistics from a global ruleset, usually obtained from previous use of the [`fidexGloRules`](fidexglorules.md) along with a test dataset.

The statistics computed for the ruleset are:

- The global rule fidelity rate.
- The global rule accuracy.
- The explainability rate (when we can find one or more rules, either correct ones or activated ones which all agree on the same class).
- The default rule rate (when we can't find any rule activated for a sample).
- The mean number of correct (fidel) activated rules per sample.
- The mean number of wrong (not fidel) activated rules per sample.
- The model tests accuracy.
- The model tests accuracy when rules and models agree.
- The model tests accuracy when activated rules and model agree.

If the [positive class index](#positive-class-index) parameter is used, additional statistics are computed with both the model decision and the rules decision:

- The number of true positive test samples.
- The number of false positive test samples.
- The number of true negative test samples.
- The number of false negative test samples.
- The false positive rate.
- The false negative rate.
- The precision.
- The recall.

All these metrics are generated, as text and/or inside a file.

The statistics computed for the ruleset are:

- The global rule fidelity rate.
- The global rule accuracy.
- The explainability rate (when we can find one or more rules, either correct ones or activated ones which all agree on the same class).
- The default rule rate (when we can't find any rule activated for a sample).
- The mean number of correct (fidel) activated rules per sample.
- The mean number of wrong (not fidel) activated rules per sample.
- The model tests accuracy.
- The model tests accuracy when rules and models agree.
- The model tests accuracy when activated rules and model agree.

If the [positive class index](#positive-class-index) parameter is used, additional statistics are computed with both the model decision and the rules decision:

- The number of true positive test samples.
- The number of false positive test samples.
- The number of true negative test samples.
- The number of false negative test samples.
- The false positive rate.
- The false negative rate.
- The precision.
- The recall.

All these metrics are generated, as text and/or inside a file.

## Arguments list

The `FidexGloStats` algorithm works with both required and optional arguments. Each argument has specific properties:

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
*Default path from where all the other arguments related to file paths are going to be based. Using this allows you to work with paths relative to this location and avoid writing absolute paths or lengthy relative paths.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--root_folder`     | 
| JSON identifier         | `root_folder`       |
| Default value           | `.`                 |

---

### Global Rules file
*Path to the file containing the global rules obtained with `fidexGloRules` algorithm.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | Yes                      |
| Type                    | `String`                 |
| CLI argument syntax     | `--global_rules_file`    | 
| JSON identifier         | `global_rules_file`      |
| Default value           | `None`                   |

---

### Global Rules output file
*Path to the file where the output global rules will be stored with stats on test set, if you want to compute those statistics.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `String`                 |
| CLI argument syntax     | `--global_rules_outfile` | 
| JSON identifier         | `global_rules_outfile`   |
| Default value           | `None`                   |

!!!info
    The filename's extension can be specified as `.json`. Allowing the program to generate a JSON-structured rule output file.

---

### Number of attributes 
*Number of attributes in the dataset (should be equal to the number of inputs of the model). Takes values in the range [1,∞[.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_attributes`   | 
| JSON identifier         | `nb_attributes`     |
| Default value           | `None`              |

---

### Number of classes
*Number of classes in the dataset (should be equal to the number of outputs of the model). Takes values in the range [2,∞[.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_classes`      |
| JSON identifier         | `nb_classes`        |
| Default value           | `None`              |

---

### Test data file       
*File containing the testing portion of the dataset used to train the model. It can also contain training "true classes" (see [Test true classes file](#test-true-classes-file)).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_data_file`  | 
| JSON identifier         | `test_data_file`    |
| Default value           | `None`              |

--- 

### Test predictions file
*File containing the predictions from the testing portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_pred_file`  |
| JSON identifier         | `test_pred_file`    |
| Default value           | `None`              |

<!-- 
TODO: check if the statement below is correct

!!!Warning
    This argument is not required if, **and only if**, the predictions are already specified inside the [test data file](#test-data-file).  
-->
---

### Test true classes file
*File containing "true classes" (expected predictions), from the testing portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `String`            |
| CLI argument syntax     | `--test_class_file` |
| JSON identifier         | `test_class_file`   |
| Default value           | `None`              |

!!!Warning 
    This argument is not required if, **and only if**, the *true classes* are already specified inside the [test data file](#test-data-file).

---

### Attributes file
*File containing attributes (inputs) and classes (outputs) names.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--attributes_file` |
| JSON identifier         | `attributes_file`   |
| Default value           | `None`              |

---

### Logs output file
*Name of file containing every feedback made by the algorithm during its execution. If not specified, the feedback is displayed in the terminal.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--console_file`    |
| JSON identifier         | `console_file`      |
| Default value           | `None`              |

---

### Positive class index
*Index of positive class to compute true/false positive/negative rates, index starts at 0. If it is specified in the rules file, **it has to be the same value**. Takes values in the range `[0,nb_classes-1]`.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `Integer`               |
| CLI argument syntax     | `--positive_class_index`|
| JSON identifier         | `positive_class_index`  |
| Default value           | `None`                  |

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

## Usage example

=== "Python"
    ```py
    from dimlpfidex.fidex import fidexGloStats

    fidexGloStats(
    """ --test_data_file datanormTest.txt 
        --test_pred_file predTest.out 
        --test_class_file dataclassTest.txt 
        --nb_attributes 16 
        --nb_classes 2 
        --stats_file stats.txt 
        --root_folder dimlp/datafiles
        """
    )
    ```
    
=== "CLI"
    ```
    ./fidexGloStats --test_data_file datanormTest.txt --test_pred_file predTest.out --test_class_file dataclassTest.txt --nb_attributes 16 --nb_classes 2 --stats_file stats.txt --root_folder dimlp/datafiles
    ```

## Output interpretation

<<<<<<< HEAD
<<<<<<< HEAD
<!-- TODO: Complete this section -->
=======
<!-- TODO: Complete this section -->
>>>>>>> 11259a2 (Added content)
=======
<!-- TODO: Complete this section -->
>>>>>>> be3d9df (Added arguments list)
