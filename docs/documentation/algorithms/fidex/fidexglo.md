# FidexGlo

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description
<!-- TODO: Complete this section -->

<!-- TODO: Complete this section -->

## Arguments list
The `FidexGlo` algorithm has required and optional arguments to be specified. Each of them has properties:

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

### Test data file

*Path to the file containing test sample(s) data, it can contain [predictions](#test-prediction-file), and [true classes](#test-true-classes-file) if [fidex is used](#if-fidex-is-used) too.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_data_file`  | 
| JSON identifier         | `test_data_file`    |
| Default value           | `None`              |

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

### Test prediction file

*Path to the file containing predictions on the test portion of the dataset. If it is used, the [test data file](#test-data-file) must only contain the test data.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--test_pred_file`  | 
| JSON identifier         | `test_pred_file`    |
| Default value           | `None`              |

!!!note
    The [test data file](#test-data-file) can hold the predictions too. This means it is possible to merge the content of the test prediction file into the [test data file](#test-data-file) instead of using this parameter. 

---

### Explanation file

<!-- TODO: complete this description -->
*Path to the file where explanation(s) will be stored.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--explanation_file`| 
| JSON identifier         | `explanation_file`  |
| Default value           | `None`              |

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

### Using the minimal version
*Whether to use the minimal version, which only gets correct activated rules. [If fidex is used](#if-fidex-is-used), it launches `Fidex` when no such rule is found.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Boolean`                |
| CLI argument syntax     | `--with_minimal_version` |
| JSON identifier         | `with_minimal_version`   |
| Default value           | `False`                  |

---

### Use FidexGlo with Fidex
*Whether to call `Fidex` while executing the `FidexGlo` algorithm or not.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Boolean`           |
| CLI argument syntax     | `--with_fidex`      | 
| JSON identifier         | `with_fidex`        |
| Default value           | `False`             |

!!!note
    If this parameter is used, there is [another set of parameters](#if-fidex-is-used) to be specified too.

---

### If Fidex is used
!!!note
    This section is only usable if the parameter named "[use FidexGlo with fidex](#use-fidexglo-with-fidex)" is specified. 

### Train data file

<!-- TODO if train predictions file Note admonition is true, use this description instead
*File containing the training portion of the dataset used to train the model, from which the ruleset/weights belong. It can also contain training "true classes" and training predictions (see [Train true classes file](#train-true-classes-file) and [Train predictions files](#train-predictions-file)).* 
-->
*File containing the training portion of the dataset used to train the model, from which the ruleset/weights belong. It can also contain training predictions (see [Train predictions files](#train-predictions-file)).*

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
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--train_pred_file` | 
| JSON identifier         | `train_pred_file`   |
| Default value           | `None`              |

<!--TODO check if the statement below is true 
!!!note
    This argument is not required if, **and only if**, the predictions are already specified inside the [train data file](#train-data-file).  
-->
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

!!! note
    This argument is not required if, **and only if**, the *true classes* are already specified inside the [train data file](#train-data-file). 

--- 
    
### Weights file
*File containing the model weights.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `String`            |
| CLI argument syntax     | `--weights_file`    | 
| JSON identifier         | `weights_file`      |
| Default value           | `None`              |

!!! note
    This argument is not required if, **and only if**, the [rules file](#rules-file) is specified instead. 

--- 

### Rules file
*File containing a collection of rules.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `String`            |
| CLI argument syntax     | `--rules_file`      | 
| JSON identifier         | `rules_file`        |
| Default value           | `None`              |

!!! note
    This argument is not required if, **and only if**, the [weights file](#weights-file) is specified instead. 

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

!!!note
    Classes can be specified in the [test data file](#test-data-file) too. This means it is possible to merge classes into the [test data file](#test-data-file) instead of using this parameter.

---

### Maximum number of iterations
<!-- TODO: complete this description -->
*Number of iterations allowed.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Integer`           |
| CLI argument syntax     | `--max_iterations`  |
| JSON identifier         | `max_iterations`    |
| Default value           | `10`                |

!!!Tip
    If you're working with images, we recommend you specify this argument with `25`.

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

### Number of rules
*Number of `Fidex` rules to compute per sample when launching the `Fidex` algorithm*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--nb_fidex_rules`     |   
| JSON identifier         | `nb_fidex_rules`       |
| Default value           | `1`                    |


---

### Dimension dropout
<!-- TODO: complete this description -->
*Dimension dropout parameter. Goes from `0.0` to `1.0`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--dropout_dim`        |
| JSON identifier         | `dropout_dim`          |
| Default value           | `0.0`                  |

---

### Hyper-plane dropout
<!-- TODO: complete this description -->
*Hyper-plane dropout parameter. Goes from `0.0` to `1.0`.*

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
*Attribute indices to denormalize in the rules, it is only used when no [normalization file](#normalization-file) is given. Indexes starts at 0.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Float list`             |
| CLI argument syntax     | `--normalization_indices`|
| JSON identifier         | `normalization_indices`  |
| Default value           | `[0,...,nb_attributes-1]`|

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


## Usage example

=== "Python"
    ```py

    from dimlpfidex.fidex import fidexGlo

    fidexGlo("""
    --root_folder dimlp/datafiles 
    --test_data_file datanormTest.txt 
    --test_pred_file predTest.out 
    --global_rules_file globalRules.rls 
    --nb_attributes 16 
    --nb_classes 2 
    --explanation_file explanation.txt 
    --with_fidex true 
    --train_data_file datanormTrain.txt 
    --train_pred_file predTrain.out 
    --train_class_file dataclass2Train.txt 
    --test_class_file dataclass2Test.txt 
    --weights_file weights.wts"""
    )
    ```
    
=== "CLI"
    ```
    ./fidexGlo --test_data_file datanormTest.txt --test_pred_file predTest.out --global_rules_file globalRules.rls --nb_attributes 16 --nb_classes 2 --explanation_file explanation.txt --root_folder dimlp/datafiles --with_fidex true --train_data_file datanormTrain.txt --train_pred_file predTrain.out --train_class_file dataclass2Train.txt --test_class_file dataclass2Test.txt --weights_file weights.wts" 
    ```

## Output interpretation

<!-- TODO: Complete this section -->