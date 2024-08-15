# Fidex

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

<!-- TODO: complete this description -->
The `Fidex` algorithm is an approach to rule extraction that can be applied to neural network ensembles (including convolutional neural networks), decision tree ensembles, and support vector machines. The name of the algorithm is a contraction of *fidelity* and *explainability*. *Fidelity* refers to how well an extracted rule mimics the behavior of a given model.

## Arguments list
The `Fidex` algorithm works with both required and optional arguments. Each argument has specific properties:

- **Is required** means whether an argument **must** be specified when calling the program or not.
- **Type** specifies the argument datatype.
- **CLI argument syntax** is the exact name to use if you are writing the argument along with the program call.
- **JSON identifier** is the exact name to use if you are writing the argument inside a [JSON configuration file](../../file-formats/json-configuration-files.md).
- **Default value** is the value that will be used by the program if the argument is not specified. If `none`, it could mean that the argument is not used at all during the algorithm execution or could also mean that you have to specify it yourself.

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
    If you use this argument, **it must be the only one specified**. No other argument can be specified with it.

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
*File containing the training portion of the dataset used to train the model, from which the ruleset/weights belong. It can also contain training "true classes" (see [Train true classes file](#train-true-classes-file)).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--train_data_file` | 
| JSON identifier         | `train_data_file`   |
| Default value           | `None`              |

--- 
        
### Train predictions file
*File containing the predictions from the training portion of the dataset used to train the model.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--train_pred_file` | 
| JSON identifier         | `train_pred_file`   |
| Default value           | `None`              |

--- 

### Train true classes file
*File containing "true classes" (expected predictions), from the training portion of the dataset used to train the model.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `String`            |
| CLI argument syntax     | `--train_class_file`| 
| JSON identifier         | `train_class_file`  |
| Default value           | `None`              |

!!! warning
    This argument is not required if, **and only if**, the *true classes* are already specified inside the [train data file](#train-data-file). 

--- 

### Test data file       
*File containing the testing portion of the dataset used to train the model. It can also contain training "true classes" and training predictions (see [Test true classes file](#test-true-classes-file) and [Test predictions files](#test-predictions-file)).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_data_file`  | 
| JSON identifier         | `test_data_file`    |
| Default value           | `None`              |

--- 
    
### Weights file
*File containing the model trained weights.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `String`            |
| CLI argument syntax     | `--weights_file`    | 
| JSON identifier         | `weights_file`      |
| Default value           | `None`              |

!!! warning
    This argument is not required if, **and only if**, the [rules file](#rules-file) is specified instead. 

--- 

### Rules file
*File containing the model trained rules.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `String`            |
| CLI argument syntax     | `--rules_file`      | 
| JSON identifier         | `rules_file`        |
| Default value           | `None`              |

!!! warning
    This argument is not required if, **and only if**, the [weights file](#weights-file) is specified instead. 

--- 

### Rules output file
*Name of the file containing rules generated by `Fidex`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--rules_outfile`   | 
| JSON identifier         | `rules_outfile`     |
| Default value           | `None`              |

!!!info
    The filename's extension can be specified as `.json`. Allowing the program to generate a JSON-structured rule output file.

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

### Test predictions file
*File containing the predictions from the testing portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `String`           |
| CLI argument syntax     | `--test_pred_file`  |
| JSON identifier         | `test_pred_file`    |
| Default value           | `None`              |

!!!Warning
    This argument is not required if, **and only if**, the predictions are already specified inside the [test data file](#test-data-file).  

---

### Test true classes file
*File containing "true classes" (expected predictions), from the testing portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                |
| Type                    | `String`            |
| CLI argument syntax     | `--test_class_file` |
| JSON identifier         | `test_class_file`   |
| Default value           | `None`              |

!!!Warning 
    The true classes can also be specified inside the [test data file](#test-data-file). This means it is possible to merge classes into the [test data file](#test-data-file) instead of using this parameter.

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

### Statistics output file
*Name of the output file that will contain statistics concerning the algorithm execution.*

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

### Maximum number of iterations
*Maximum number of `Fidex` iterations allowed. Also the maximum possible number of antecedents in a rule. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Integer`           |
| CLI argument syntax     | `--max_iterations`  |
| JSON identifier         | `max_iterations`    |
| Default value           | `10`                |

!!!Tip
    If you're working with images, we recommend setting this argument to `25`.

---

### Minimum covering
*Minimal number of samples covered by every generated rule. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Integer`           |
| CLI argument syntax     | `--min_covering`    |
| JSON identifier         | `min_covering`      |
| Default value           | `2`                 |

---

### Use dichotomic search
*Whether or not the algorithm uses a dichotomic strategy to compute a rule. This occurs when the algorithm fails to find a rule with the [minimum covering](#minimum-covering) value used.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Boolean`            |
| CLI argument syntax     | `--covering_strategy`|
| JSON identifier         | `covering_strategy`  |
| Default value           | `True`               |

---

### Maximum number of failed attempts
*Number of attempts allowed to compute a rule that could not be found by the algorithm. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--max_failed_attempts`|
| JSON identifier         | `max_failed_attempts`  |
| Default value           | `30`                   |

---

### Minimum fidelity
*Lowest fidelity score allowed for a rule to be selected. Takes values in the range `[0,1]`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--min_fidelity`       |
| JSON identifier         | `min_fidelity`         |
| Default value           | `1.0`                  |

---

### Minimum generated fidelity
*Lowest fidelity score to which we agree to go down when a rule must be generated. Takes values in the range `[0,1]`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--lowest_min_fidelity`|
| JSON identifier         | `lowest_min_fidelity`  |
| Default value           | `0.75`                 |

---

### Dimension dropout
*Percentage of dimensions that are ignored during an iteration. Takes values in the range `[0,1]`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--dropout_dim`        |
| JSON identifier         | `dropout_dim`          |
| Default value           | `0.0`                  |

---

### Hyperplane dropout
*Percentage of hyperplanes that are ignored during an iteration. Takes values in the range `[0,1]`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--dropout_hyp`        |
| JSON identifier         | `dropout_hyp`          |
| Default value           | `0.0`                  |

---
### Number of stairs
*Number of stairs in the staircase activation function used in the Dimlp layer during training. Takes values in the range `[3,∞[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--nb_quant_levels`    |
| JSON identifier         | `nb_quant_levels`      |
| Default value           | `50`                   |

---

### Decision threshold
*Threshold for predictions to be considered as correct. Takes values in the range `[0,1]`.*


|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--decision_threshold` |
| JSON identifier         | `decision_threshold`   |
| Default value           | `None`                 |

!!!Warning
    The [index of positive class](#positive-class-index) must be specified too if you want to use this argument. 

---

### Positive class index
*Index of positive class for the usage of decision threshold, index starts at `0`. Takes values in the range `[0,nb_classes-1]`.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No**                    |
| Type                    | `Integer`               |
| CLI argument syntax     | `--positive_class_index`|
| JSON identifier         | `positive_class_index`  |
| Default value           | `None`                  |

!!!Warning
    If [decision threshold](#decision-threshold) is used, then this argument **is required**. 

---

### Normalization file
*File containing the mean and standard deviation for specified attributes that have been normalized. If specified, it is used to denormalize the rules.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `String`                |
| CLI argument syntax     | `--normalization_file`  |
| JSON identifier         | `normalization_file`    |
| Default value           | `None`                  |

---

### Mus
*Mean or median of each attribute index specified in [normalization indices](#normalization-indices) that have been normalized. This argument is used alongside [sigmas](#sigmas) and [normalization indices](#normalization-indices). If specified, it is used to denormalize the rules. Takes values in the range `]-∞,∞[`.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No**                    |
| Type                    | `Float list`            |
| CLI argument syntax     | `--mus`                 |
| JSON identifier         | `mus`                   |
| Default value           | `None`                  |

!!!Warning
    If [sigmas](#sigmas) or [normalization indices](#normalization-indices) are used, then this argument **is required**. Not used if a [normalization file](#normalization-file) is given.

---

### Sigmas
*Standard deviation of each attribute index specified in [normalization indices](#normalization-indices) that have been normalized. This argument is used alongside [mus](#mus) and [normalization indices](#normalization-indices). If specified, it is used to denormalize the rules. Takes values in the range `]-∞,∞[`.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No**                    |
| Type                    | `Float list`            |
| CLI argument syntax     | `--sigmas`              |
| JSON identifier         | `sigmas`                |
| Default value           | `None`                  |

!!!Warning
    If [mus](#mus) or [normalization indices](#normalization-indices) are used, then this argument **is required**. Not used if a [normalization file](#normalization-file) is given.

---

### Normalization indices
*Indices of attributes that have been normalized. If specified, it is used to denormalize the rules. Index starts at 0. Each index takes values in the range `[0,nb_attributes-1]`.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No**                     |
| Type                    | `List of integers`       |
| CLI argument syntax     | `--normalization_indices`|
| JSON identifier         | `normalization_indices`  |
| Default value           | `[0,...,nb_attributes-1]`|

!!!Warning
    If [mus](#mus) or [sigmas](#sigmas) are used, then this argument **is required**. Not used if a [normalization file](#normalization-file) is given.

---

### Seed
*Number to feed the random generator. If `0`, the randomness cannot be reproduced. If any other number `x` is used, you can reproduce the same output if `x` is re-used. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `Integer`               |
| CLI argument syntax     | `--seed`                |
| JSON identifier         | `seed`                  |
| Default value           | `0`                     |

---


## Usage example

=== "Python"
    ```py
    from dimlpfidex.fidex import fidex

    fidex(
    """--root_folder dimlp/datafiles 
       --train_data_file train_data.txt 
       --train_pred_file predTrain.out 
       --train_class_file train_class.txt 
       --test_data_file test_data.txt 
       --test_class_file test_class.txt 
       --test_pred_file predTest.out 
       --nb_attributes 16 
       --nb_classes 2 
       --weights_file weights.wts 
       --rules_outfile output_rules.rls 
       --stats_file output_stats.txt"""
    )
    ```
    
=== "CLI"
    ```
    ./fidex --root_folder ../dimlp/datafiles --train_data_file train_data.txt --train_pred_file predTrain.out --train_class_file train_class.txt --test_data_file test_data.txt --test_class_file test_class.txt --test_pred_file predTest.out --nb_attributes 16 --nb_classes 2 --weights_file weights.wts --rules_outfile output_rules.rls --stats_file output_stats.txt
    ```


## Output interpretation

<!-- TODO: complete this section -->
