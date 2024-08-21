# DimlpRul

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

The `Discretized Interpretable Multi-Layer Perceptron (DIMLP)` is a neural network architecture that combines the predictive power of a traditional Multi-Layer Perceptron (MLP) with the ability to extract interpretable rules. Unlike conventional neural networks, `DIMLP` uses a staircase activation function in the first hidden layer, creating a grid of hyper-rectangles in the feature space. These hyper-rectangles help define discriminant decision boundaries between classes, facilitating the extraction of symbolic rules.

The rule generation process in the `DIMLP` model relies on inducing a decision tree, where virtual hyperplanes are identified between these hyper-rectangles. The rule extraction algorithm extracts unordered rules in polynomial time using heuristic methods. This process ensures 100% fidelity with respect to the training data, meaning that the extracted rules perfectly match the network's decisions.

`DimlpRul` generates global explanation rules using the `Dimlp` algorithm on the training dataset used to train the model with [dimlpTrn](dimlptrn.md), and calculates accuracy on a train, test and validation dataset.

Additionally, there is another rule extraction algorithm available in the framework called [Fidex](../fidex/overview.md), which has a better algorithmic complexity and allows for both local and global rule extraction.

For more details on the `Dimlp` algorithm, you can refer to [this paper](../../references.md#a-model-for-single-and-multiple-knowledge-based-networks).

!!!Warning
     You should not execute `DimlpRul` for a model trained by [DimlpBT](dimlpbt.md), it should be trained by [dimlpTrn](dimlptrn.md)!

## Arguments list
The `dimlpRul` algorithm works with both required and optional arguments. Each argument has specific properties:

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
*File containing the training portion of the dataset. It can also contain training "true classes" (see [Train true classes file](#train-true-classes-file)).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--train_data_file` | 
| JSON identifier         | `train_data_file`   |
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

### Weights file
*Path to the file containing the weights of the model trained with [`dimlpTrn`](dimlptrn.md).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--weights_file`    | 
| JSON identifier         | `weights_file`      |
| Default value           | `None`              |

--- 

### Hidden layers file    
*Path to the file containing hidden layers sizes.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | Yes                      |
| Type                    | `String`                 |
| CLI argument syntax     | `--hidden_layers_file`   | 
| JSON identifier         | `hidden_layers_file`     |
| Default value           | `None`                   |

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

### Test data file
*Path to the file containing the test portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--test_data_file`  |
| JSON identifier         | `test_data_file`    |
| Default value           | `None`              |

---

### Test true classes file
*Path to the file containing the test true classes of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--test_class_file` |
| JSON identifier         | `test_class_file`   |
| Default value           | `None`              |

---

### Validation data file
*Path to the file containing the validation portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--valid_data_file` |
| JSON identifier         | `valid_data_file`   |
| Default value           | `None`              |

---

### Validation true classes file
*Path to the file containing the validation true classes of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--valid_class_file`|
| JSON identifier         | `valid_class_file`  |
| Default value           | `None`              |

---

### Global rules output file
*Path to the file where the output rule(s) generated by the dimlp algorithm will be stored.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `String`                |
| CLI argument syntax     | `--global_rules_outfile`|
| JSON identifier         | `global_rules_outfile`  |
| Default value           | `dimlp.rls`             |

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
| Default value           | `None`  |

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

## Usage example

=== "Python"
    ```py
    from dimlpfidex.dimlp import dimlpRul

    dimlpRul(
    """--train_data_file train_data.txt 
    --train_class_file train_class.txt 
    --weights_file weights.wts 
    --test_data_file test_data.txt 
    --test_class_file test_class.txt 
    --nb_attributes 16 
    --hidden_layers_file hidden_layers.out 
    --nb_classes 2 
    --global_rules_outfile globalRules.rls 
    --stats_file stats.txt 
    --root_folder dimlp/datafiles"""
    )
    ```
    
=== "CLI"
    ```
    ./dimlpRul --train_data_file train_data.txt --train_class_file train_class.txt --weights_file weights.wts --test_data_file test_data.txt --test_class_file test_class.txt --nb_attributes 16 --hidden_layers_file hidden_layers.out --nb_classes 2 --global_rules_outfile globalRules.rls --stats_file stats.txt --root_folder ../dimlp/datafiles
    ```

## Output interpretation

---

### [Statistics file](#statistics-output-file)

This file contains accuracy and error measurements on the training, validation, and testing sets (if provided). It offers a clear overview of the model’s performance across different datasets, helping to evaluate how well the model has learned and generalized to unseen data.

`Accuracy`
:   Indicates the proportion of correctly classified samples in each dataset (training, validation, or testing).

`Sum squared error`
:   Represents the sum of the squared differences between the predicted and actual values for the samples in each dataset. It is a measure of the model’s overall error for a given set.

---

### [Global rules output file](#global-rules-output-file) 

This file contains all the global rules computed with the `Dimlp` algorithm. The rules are ordered by their covering size and are followed by the performance metrics of each rule on the training, validation and testing sets. Additionally, the file provides performance statistics of the ruleset and its application on testing data.

<p style="font-size:larger;">Explanation of Each Rule:</p>

Each rule consists of conditions on various attributes, followed by the predicted class, and is accompanied by the number of training and validation samples it covers. Let's break down this rule as an example:

    Rule 1: (x1 > 0.653808) (x2 > 0.92407) (x8 < 0.44302) Class = 1 (211)

`x1, x2, x8`
:   These represent the variables from the dataset (x1 is the first attribute).

`>0.653808, >0.92407, <0.44302`
:   The thresholds that the variable values must meet for the rule to be activated.

`Class = 1`
:   The class predicted by the rule when the conditions are met. Here, the rule predicts class 1.

`(211)`
:   The number of training and validation samples covered by the rule. Here, the rule covers 211 samples.

<hr style="border-top: 1px solid; width: 25%;">

<p style="font-size:larger;">Performance Metrics Associated with the Rule:</p>

For each rule and each dataset, there is some performances associated with the rule. It appears like this :

    Rule    1:   143   134     9     0.937063       Class = 1

`143`
:   The number of samples covered by this rule. 

`134`
:   The number of samples correctly classified by this rule.

`9`
:   The number of samples incorrectly classified by this rule.

`0.937063`
:   The accuracy of this rule in correctly classifying the samples it covers.

`Class = 1`
:   The class predicted by the rule when the conditions are met. Here, the rule predicts class 1.

It is followed by the global accuracy of the rules on the whole set. That means the accuracy of the ruleset in predicting the correct class for the samples, regardless of the model's predictions. It is accurate when there is a correct fidel activated rule, when no rule is activated and the model is correct, or when the activated rules are incorrect but all agree on the correct class.

<hr style="border-top: 1px solid; width: 25%;">

<p style="font-size:larger;">Global Statistics:</p>

`Number of rules`
:   Indicates the total number of rules in the ruleset.

`Number of antecedents`
:   Represents the total number of conditions (antecedents) in the ruleset.

`Number of antecedents per rule`
:   Represents the average number of conditions (antecedents) in each rule.

`Number of examples per rule`
:   The average number of training and validation samples covered by each rule.

<hr style="border-top: 1px solid; width: 25%;">

<p style="font-size:larger;">Additional Statistics on testing set:</p>

`Fidelity`
:   Measures how accurately the rules mimic the behavior of the model. This rate reflects the proportion of test samples where the rules' predictions match the model's predictions.

`Accuracy when rules and network agree`
:   The accuracy of the model when the model's predictions match the predictions made by the activated rules.

`Default rule activations rate`
:   The proportion of samples for which no activated rule is found. In such cases, we choose the network's decision.