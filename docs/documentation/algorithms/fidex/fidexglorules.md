# FidexGloRules

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description
`FidexGloRules` computes a rule for each training sample by calling [`Fidex`](fidex.md). `Fidex` is based on the training samples, a hyperlocus, and is directed by the given parameters, including the dropout and the maximum number of iterations allowed.

It works by identifying hyperplanes in the feature space that discriminate between different classes of samples and constructing a rule for the training sample based on these hyperplanes covering this sample and as many other training samples as possible. Then, a heuristic is used to remove the duplicated and unnecessary rules.

The `Fidex` algorithm is computed until a rule is created or until the [maximum number of failed attempts limit](#maximum-number-of-failed-attempts) is reached.

- The first attempt to generate a rule with a covering greater or equal to the [minimum covering](#minimum-covering) and a fidelity greater or equal to the [minimum fidelity](#minimum-fidelity).
- If the attempt fails and the [use of dichotomic search](#use-dichotomic-search) is enabled, `Fidex` is computed to find a rule with the maximum possible minimal covering that can be lower than the [minimum covering](#minimum-covering) initially set.
- If all attempts fail, the targeted fidelity is gradually lowered until it succeeds or the [lowest fidelity allowed](#minimum-generated-fidelity) is reached.
- Each failed attempt at the [lowest minimal fidelity](#minimum-generated-fidelity) is counted.
- If the [maximum of failed attempts](#maximum-number-of-failed-attempts) limit is reached, then no rule will not be computed for this sample.

## Arguments list
The `FidexGloRules` algorithm works with both required and optional arguments. Each argument has specific properties:

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

### Train data file
*File containing the training portion of the dataset used to train the model, from which the ruleset/weights belong. It can also contain training "true classes" and training predictions (see [Train true classes file](#train-true-classes-file) and [Train predictions files](#train-predictions-file)).*

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
| Is required             | No**                |
| Type                    | `String`            |
| CLI argument syntax     | `--train_pred_file` | 
| JSON identifier         | `train_pred_file`   |
| Default value           | `None`              |

!!!Warning
    This argument is not required if, **and only if**, the predictions are already specified inside the [train data file](#train-data-file).  

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
    If you use heuristic `1`, you can also specify a [number of threads](#number-of-threads) to accelerate the process.

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
*Maximum number of `Fidex` iterations allowed. Also the maximum possible number of antecedents in a rule.

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
*Minimal number of samples covered by every generated rule.*

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
*Number of attempts allowed to compute a rule that could not be found by the algorithm.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--max_failed_attempts`|
| JSON identifier         | `max_failed_attempts`  |
| Default value           | `30`                   |

---

### Number of threads
*Threads used to compute the algorithm. This parameter **has no effect** if the heuristic used is not `1`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `integer`              |
| CLI argument syntax     | `--nb_threads`         |
| JSON identifier         | `nb_threads`           |
| Default value           | `0`                    |

---

### Minimum fidelity
*Lowest fidelity score allowed for a rule to be selected. Goes from `0.0` to `1.0`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--min_fidelity`       |
| JSON identifier         | `min_fidelity`         |
| Default value           | `1.0`                  |

---

### Minimum generated fidelity
*Lowest fidelity score to which we agree to go down when a rule must be generated.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--lowest_min_fidelity`|
| JSON identifier         | `lowest_min_fidelity`  |
| Default value           | `0.75`                 |

---

### Dimension dropout
*Percentage of dimensions that are ignored during an iteration. Goes from `0.0` to `1.0`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--dropout_dim`        |
| JSON identifier         | `dropout_dim`          |
| Default value           | `0.0`                  |

---

### Hyperplane dropout
*Percentage of hyperplanes that are ignored during an iteration. Goes from `0.0` to `1.0`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--dropout_hyp`        |
| JSON identifier         | `dropout_hyp`          |
| Default value           | `0.0`                  |

---
### Number of stairs
<!-- TODO: complete this description -->
*Number of "stairs" in the staircase function.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--nb_quant_levels`    |
| JSON identifier         | `nb_quant_levels`      |
| Default value           | `50`                   |

---

### Decision threshold
*Threshold for predictions to be considered as correct. Goes from `0.0` to `1.0`.*


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
*Index of positive class for the usage of decision threshold, index starts at `0`.*

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
<!-- TODO: This description must be improved -->
*File containing the mean and standard deviation for specified attributes that have been normalized. These values are saved inside a file to denormalize the corresponding attributes. If specified, it is used to denormalize the rules.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `String`                |
| CLI argument syntax     | `--normalization_file`  |
| JSON identifier         | `normalization_file`    |
| Default value           | `None`                  |

---

### Mus
<!-- TODO: This description must be improved -->
*Mean or median of each attribute index to denormalize in the rules.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `Float list`            |
| CLI argument syntax     | `--mus`                 |
| JSON identifier         | `mus`                   |
| Default value           | `None`                  |

---

### Sigmas
<!-- TODO: This description must be improved -->
*Standard deviation of each attribute index to denormalize in the rules.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `Float list`            |
| CLI argument syntax     | `--sigmas`              |
| JSON identifier         | `sigmas`                |
| Default value           | `None`                  |

---
### Normalization indices
*Attribute indices to denormalize in the rules, only used when no normalization_file is given, index starts at 0 (default: [0,...,nb_attributes-1])*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Float list`             |
| CLI argument syntax     | `--normalization_indices`|
| JSON identifier         | `normalization_indices`  |
| Default value           | `None`                   |

---
### Seed
*Number to feed the random generator. If `0`, the randomness cannot be reproduced. If any other number `x` is used, you can reproduce the same output if `x` is re-used.*

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
    from dimlpfidex.fidex import fidexGloRules

    fidexGloRules(
    """--root_folder my/folder/
       --train_data_file train_data.txt 
       --train_pred_file train_predictions.out 
       --train_class_file train_classes.txt 
       --nb_attributes 16 
       --nb_classes 2 
       --weights_file weights.wts 
       --rules_outfile output_rules.rls 
       --heuristic 1
       --nb_threads 4"""
    )
    ```
    
=== "CLI"
    ```
    ./fidexGloRules --root_folder my/folder/ --train_data_file train_data.txt --train_pred_file train_predictions.out --train_class_file train_classes.txt  --nb_attributes 16 --nb_classes 2 --weights_file weights.wts --rules_outfile output_rules.rls --nb_threads 4
    ```

## Output interpretation

<!-- TODO: Complete this section -->
