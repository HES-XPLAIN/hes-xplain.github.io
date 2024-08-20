# DensCls

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

The `DimlpBT` model is an extension of the standard `Dimlp (Discretized Interpretable Multi-Layer Perceptron)` architecture, which applies the powerful technique of bagging to improve model accuracy and robustness. Bagging, or Bootstrap Aggregating, generates multiple versions of the training set by resampling and trains separate `Dimlp` networks on each dataset. The ensemble of networks is then aggregated to make final predictions, reducing variance and improving predictive performance, particularly on complex datasets. Like the base `Dimlp` model, this version leverages a discretized multi-layer perceptron, which uses a staircase activation function in the first hidden layer, creating a grid of hyper-rectangles in the feature space. These hyper-rectangles help define discriminant decision boundaries between classes, facilitating the extraction of symbolic rules.

Through the use of `Dimlp`'s rule extraction process, this algorithm is capable of producing symbolic rules at both the single network and ensemble levels, offering interpretable insights into the decision-making process. The rule generation process in the `DIMLP` model relies on inducing a decision tree, where virtual hyperplanes are identified between these hyper-rectangles. The rule extraction algorithm extracts unordered rules in polynomial time using heuristic methods. This process ensures 100% fidelity with respect to the training data, meaning that the extracted rules perfectly match the network's decisions.

`DensCls` generates global explanation rules using the `Dimlp` algorithm on the training dataset used to train the model with [dimlpBT](dimlpbt.md), and calculates predictions and accuracy on a train and test dataset.

Additionally, there is another rule extraction algorithm available in the framework called [Fidex](../fidex/overview.md), which has a better algorithmic complexity and allows for both local and global rule extraction.

To get more details on the `Dimlp` algorithm, you can refer to [this paper](../../references.md#a-model-for-single-and-multiple-knowledge-based-networks), and to [this one](../../references.md#is-it-worth-generating-rules-from-neural-network-ensembles) for `dimlpBT`.

## Arguments list
The `densCls` algorithm works with both required and optional arguments. Each argument has specific properties:

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
*Path to the file containing the weights of the model trained with [`dimlpBT`](dimlpbt.md).*

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

### Train predictions output file
*Name of file generated by `densCls` containing the predictions from the training portion of the dataset.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `String`               |
| CLI argument syntax     | `--train_pred_outfile` | 
| JSON identifier         | `train_pred_outfile`   |
| Default value           | `densClsTrain.out`     |

--- 

### Test data file
*Path to the file containing the test portion of the dataset.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `String`               |
| CLI argument syntax     | `--test_data_file`     | 
| JSON identifier         | `test_data_file`       |
| Default value           | `None`                 |

---

### Test true classes file
*Path to the file containing the test true classes of the dataset.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `String`               |
| CLI argument syntax     | `--test_class_file`    | 
| JSON identifier         | `test_class_file`      |
| Default value           | `None`                 |

---

### Test predictions output file
*Name of file generated by `densCls` containing the predictions from the test portion of the dataset.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `String`               |
| CLI argument syntax     | `--test_pred_outfile`  | 
| JSON identifier         | `test_pred_outfile`    |
| Default value           | `densClsTest.out`      |

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

### Use rule extraction 
*Whether to extract rules with [`dimlpBT`](dimlpbt.md) algorithm.*

|  **Property**           | **Value**                   |
|:------------------------|:----------------------------|
| Is required             | No                          |
| Type                    | `Boolean`                   |
| CLI argument syntax     | `--with_rule_extraction`    |
| JSON identifier         | `with_rule_extraction`      |
| Default value           | `False`                     |

---

### Global rules output file 
*Path to the file where the output rule(s) generated by the dimlp algorithm will be stored.*

|  **Property**           | **Value**                   |
|:------------------------|:----------------------------|
| Is required             | No                          |
| Type                    | `String`                    |
| CLI argument syntax     | `--global_rules_outfile`    |
| JSON identifier         | `global_rules_outfile`      |
| Default value           | `None`                      |

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
    from dimlpfidex.dimlp import densCls

    densCls(
    """--train_data_file train_data.txt 
       --train_class_file train_class.txt 
       --test_data_file test_data.txt 
       --test_class_file test_class.txt 
       --nb_attributes 16 
       --hidden_layers_file hidden_layers.out 
       --nb_classes 2 
       --weights_file weights.wts 
       --with_rule_extraction true 
       --global_rules_outfile globalRules.rls 
       --train_pred_outfile predTrain.out 
       --test_pred_outfile testPred.out 
       --stats_file stats.txt 
       --root_folder dimlp/datafiles"""
    )
    ```
    
=== "CLI"
    ```
    ./densCls --train_data_file train_data.txt --train_class_file train_class.txt --test_data_file test_data.txt --test_class_file test_class.txt --nb_attributes 16 --hidden_layers_file hidden_layers.out --nb_classes 2 --weights_file weights.wts --with_rule_extraction true --global_rules_outfile globalRules.rls --train_pred_outfile predTrain.out --test_pred_outfile predTest.out --stats_file stats.txt --root_folder ../dimlp/datafiles
    ```

## Output interpretation

---

### [Train/Test prediction file](#train-predictions-output-file)

This file contains the predicted probabilities for each possible class for each train (or test) sample. Each row corresponds to the prediction for a single sample, with `N` values representing the probability that the sample belongs to class `0`, `1`, ... or class `N`. The values in each row sum to 1. The class with the highest probability is considered the predicted class for that sample, unless a decision threshold is applied for a specific class. In that case, if the predicted probability for that class exceeds the threshold, the sample is classified as belonging to that class.

For example:

    0.000718874 0.999281
    0.949143 0.050857

In the first row, the model predicts a probability of approximately 0.0007 that the sample belongs to class 0, and 0.9993 that it belongs to class 1. Therefore, the model predicts class 1 for this sample.
In the second row, the model predicts a probability of 0.949 that the sample belongs to class 0, and 0.051 that it belongs to class 1. Hence, the model predicts class 0 for this sample.

Each row of probabilities allows you to interpret the model's confidence in its predictions, enabling you to understand the likelihood of each sample belonging to a particular class.

---

### [Statistics file](#statistics-output-file)

This file contains the global accuracy on the training and testing sets (if provided) across all the networks. It offers a clear overview of the model’s performance across different datasets, helping to evaluate how well the model has learned and generalized to unseen data.

`Accuracy`
:   Indicates the proportion of correctly classified samples in each dataset (training, validation, or testing).

---

### [Global rules output file](#global-rules-output-file) 

This file contains all the global rules computed with the `Dimlp` algorithm. The rules are ordered by their covering size and are followed by the performance metrics of each rule on the training and testing sets. Additionally, the file provides performance statistics of the ruleset and its application on testing data.

<p style="font-size:larger;">Explanation of Each Rule:</p>

Each rule consists of conditions on various attributes, followed by the predicted class, and is accompanied by the number of training samples it covers. Let's break down this rule as an example:

    Rule 1: (x1 > 0.653808) (x2 > 0.92407) (x8 < 0.44302) Class = 1 (211)

`x1, x2, x8`
:   These represent the variables from the dataset (x1 is the first attribute).

`>0.653808, >0.92407, <0.44302`
:   The thresholds that the variable values must meet for the rule to be activated.

`Class = 1`
:   The class predicted by the rule when the conditions are met. Here, the rule predicts class 1.

`(211)`
:   The number of training samples covered by the rule. Here, the rule covers 211 samples.

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
:   The average number of training samples covered by each rule.

<hr style="border-top: 1px solid; width: 25%;">

<p style="font-size:larger;">Additional Statistics on testing set:</p>

`Fidelity`
:   Measures how accurately the rules mimic the behavior of the model. This rate reflects the proportion of test samples where the rules' predictions match the model's predictions.

`Accuracy when rules and network agree`
:   The accuracy of the model when the model's predictions match the predictions made by the activated rules.

`Default rule activations rate`
:   The proportion of samples for which no activated rule is found. In such cases, we choose the network's decision.
