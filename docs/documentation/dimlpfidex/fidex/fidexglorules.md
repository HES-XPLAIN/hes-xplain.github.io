# FidexGloRules

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

The [Fidex](fidex.md) algorithm is an approach to rule extraction that can be applied to supervised neural networks and their ensembles, convolutional neural networks, decision tree ensembles, and support vector machines. The name of the algorithm is a contraction of *fidelity* and *explainability*. *Fidelity* refers to how well an extracted rule mimics the behavior of a given model.

`FidexGloRules` uses `Fidex` to generate one rule for each sample in the dataset. These local rules are then aggregated to form a global ruleset that explains the overall behavior of the model. The key idea remains identifying discriminant hyperplanes in the feature space that separate different classes. This is achieved through the staircase activation function in models containing a [DIMLP](../dimlp/overview.md) layer, or by leveraging decision tree rules generated from [Random Forest](../training-methods/randforeststrn.md) and [Gradiend Boosting](../training-methods/gradboosttrn.md) models. The global ruleset is refined using a heuristic to remove redundant rules while ensuring full coverage of the training dataset.

`FidexGloRules` retains the efficiency of `Fidex` in terms of computational complexity, but due to the need to generate one rule per sample and aggregate them into a global ruleset, the complexity becomes quadratic with respect to the number of samples. Specifically, it scales quadratically with the product of the problem's dimensionality, the number of training samples, and the maximal number of rule antecedents.

This approach is particularly effective for providing a comprehensive explanation of a model's decision-making process across an entire dataset, rather than just for individual samples. By optimizing fidelity and reducing the rule set through heuristic techniques, `FidexGloRules` produces a concise and interpretable global explanation.

For more details on the `Fidex` and `FidexGloRules` (called `FidexGlo`) algorithms, you can refer to [this paper](../../references.md#fidex-an-algorithm-for-the-explainability-of-ensembles-and-svms).


## Arguments list
The `FidexGloRules` algorithm works with both required and optional arguments. Each argument has specific properties:

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

### Global Rules output file
*Name of the file containing global rules generated by the algorithm.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | Yes                      |
| Type                    | `String`                 |
| CLI argument syntax     | `--global_rules_outfile` | 
| JSON identifier         | `global_rules_outfile`   |
| Default value           | `None`                   |

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

### Heuristic
*Defines which heuristic to use when executing the algorithm. Values can be:*

- *`1`: optimal rule generation. Gets the best of the algorithm capabilities but can be time-consuming depending on the size of your dataset.*
- *`2`: Faster rules generation. Computes rules faster while keeping a good (but not as good as heuristic `1`) rule quality.* 
- *`3`: Fastest rules generation. Gets a set of decent (but not as good as heuristic `2`) global rules in the fastest way possible.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | Yes                     |
| Type                    | `Integer`               |
| CLI argument syntax     | `--heuristic`           |
| JSON identifier         | `heuristic`             |
| Default value           | `None`                  |

!!!tip
    If you use heuristic `1` or `2`, you can also specify a [number of threads](#number-of-threads) to accelerate the process.

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
*Maximum number of `Fidex` iterations allowed. Also the maximum possible number of antecedents in a rule. Takes values in the range `[1,∞[`.

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

### Number of threads
*Threads used to compute the algorithm. This parameter **has no effect** if the heuristic used is not `1` or `2`. Takes values in the range `[1,nb_cores]`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--nb_threads`         |
| JSON identifier         | `nb_threads`           |
| Default value           | `1`                    |

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

!!!example

    === "Python"
        ```py
        from dimlpfidex.fidex import fidexGloRules

        fidexGloRules(
        """--root_folder dimlp/datafiles 
        --train_data_file train_data.txt 
        --train_pred_file predTrain.out 
        --train_class_file train_class.txt 
        --nb_attributes 16 
        --nb_classes 2 
        --weights_file weights.wts 
        --global_rules_outfile globalRules.rls 
        --heuristic 1
        --nb_threads 4"""
        )
        ```
        
    === "CLI"
        ```
        ./fidexGloRules --root_folder ../dimlp/datafiles --train_data_file train_data.txt --train_pred_file predTrain.out --train_class_file train_class.txt  --nb_attributes 16 --nb_classes 2 --weights_file weights.wts --global_rules_outfile globalRules.rls --heuristic 1 --nb_threads 4
        ```

## Output interpretation

---

### [Global rules output file](#global-rules-output-file) 

=== "Text file"

    This file contains all the computed global rules. It begins with global statistics about the ruleset, followed by individual rules, ordered by their covering size, and their associated performance metrics.

    <p style="font-size:larger;">Global Statistics:</p>

    `Number of rules`
    :   Indicates the total number of rules in the ruleset.

    `Mean sample covering number per rule`
    :   The average number of training samples covered by each rule.

    `Mean number of antecedents per rule`
    :   Represents the average number of conditions (antecedents) in each rule.

    `Decision threshold`
    :   Indicates whether a decision threshold was used for prediction and specifies the threshold if applicable.

    <hr style="border-top: 1px solid; width: 25%;">

    <p style="font-size:larger;">Explanation of Each Rule:</p>

    Each rule consists of conditions on various attributes, followed by the predicted class, and is accompanied by several performance metrics. Let's break down this rule as an example:

        Rule 1: X0>=0.65839 X1>=0.423139 X8>=0.105399 -> class 0
            Train Covering size : 121
            Train Fidelity : 1
            Train Accuracy : 0.950413
            Train Confidence : 0.97161
    `X0, X1, X8`
    :   These represent the variables from the dataset.

    `>=0.65839, >=0.423139, >=0.105399`
    :   The thresholds that the variable values must meet for the rule to be activated.

    `-> class 0`
    :   The class predicted by the rule when the conditions are met. Here, the rule predicts class 0.

    <hr style="border-top: 1px solid; width: 25%;">

    <p style="font-size:larger;">Performance Metrics Associated with the Rule:</p>

    `Train Covering size`
    : Indicates the number of training samples that are covered by the rule. For Rule 1, it covers 121 samples.

    `Train Fidelity`
    : Measures how well the rule aligns with the model’s predictions. A fidelity of 1 means that the rule exactly matches the model’s predictions for all the samples it covers.

    `Train Accuracy`
    : The accuracy of the rule in correctly classifying the samples it covers. In the case of Rule 1, 95.04% of the covered samples are correctly classified.

    `Train Confidence`
    : This is the average confidence score of the model’s predictions for the samples covered by the rules. It is computed based on the prediction scores of the covered samples, indicating the model’s confidence in its classifications. For Rule 1, the confidence is 97.16%.

    Each subsequent rule follows the same structure.

=== "JSON file"

    This file contains all the computed global rules. It begins with an indication whether a decision threshold was used for prediction and specifies the threshold if applicable. It then follows with each individual rule and its associated performance metrics, ordered by their covering size. Let's break down this rule as an example:

        {
            "accuracy": 1.0,
            "antecedents": [
                {
                    "attribute": 8,
                    "inequality": false,
                    "value": 0.07228972839342673
                },
                {
                    "attribute": 3,
                    "inequality": true,
                    "value": 0.6969069765088105
                }
            ],
            "confidence": 0.991161,
            "coveredSamples": [
                67,
                213,
                567
            ],
            "coveringSize": 3,
            "fidelity": 1.0,
            "outputClass": 1
        }

    `accuracy`
    : The accuracy of the rule on the samples it covers. For this rule, 100% of the covered samples are correctly classified.

    `antecedents`
    : Each antecedant of the rule which is composed of an attribute (a variable from the dataset), an inequality, and a value. A `true` inequality represents `>=`, while a `false` inequality represents `<`. The value is the threshold that the attribute's value must meet for the rule to be activated. In this rule, the first antecedant specifies that `X8 < 0.07228972839342673`.

    `confidence`
    : Represents the average confidence score of the model’s predictions for the samples covered by the rule. For this rule, the confidence is 99.12%.

    `coveredSamples`
    : Indicates the samples covered by the rule. This rule coveres the samples 67, 213 and 567.

    `coveringSize`
    : Indicates the number of samples that are covered by the rule. This rule covers 3 samples.

    `fidelity`
    : Measures how well the rule aligns with the model’s predictions. A fidelity of 1 means that the rule exactly matches the model’s predictions for all the samples it covers.

    `outputClass`
    : Indicates the class prediction of the rule, the predicted class is 1.

    Each subsequent rule follows the same structure.