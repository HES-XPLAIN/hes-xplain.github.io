# DimlpTrn

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description
<!-- TODO: add description -->

## Arguments list
The `dimlpTrn` algorithm works with both required and optional arguments. Each argument has specific properties:

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

### Train predictions output file
*Path to the file where the train predictions will be stored.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `String`                 |
| CLI argument syntax     | `--train_pred_outfile`   |
| JSON identifier         | `train_pred_outfile`     |
| Default value           | `dimlpTrain.out`       |

---

### Test data file
*Path to the file containing the test portion of the dataset.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `String`             |
| CLI argument syntax     | `--test_data_file`   |
| JSON identifier         | `test_data_file`     |
| Default value           | `None`               |

---

### Test true classes file
*Path to the file containing the test true classes of the dataset.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `String`             |
| CLI argument syntax     | `--test_class_file`  |
| JSON identifier         | `test_class_file`    |
| Default value           | `None`               |

---

### Test prediction output file
*Path to the file where the test predictions will be stored.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `String`             |
| CLI argument syntax     | `--test_pred_outfile`|
| JSON identifier         | `test_pred_outfile`  |
| Default value           | `dimlpTest.out`      |

---

### Weights file
*File containing the model pretrained weights.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--weights_file`    | 
| JSON identifier         | `weights_file`      |
| Default value           | `None`              |

--- 

### Weights output file
*Path to the file where the output trained weights of the model will be stored.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `String`             |
| CLI argument syntax     | `--weights_outfile`  |
| JSON identifier         | `weights_outfile`    |
| Default value           | `dimlp.wts`          |

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

### Validation prediction output file
*Path to the file where the validation predictions will be stored.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `String`              |
| CLI argument syntax     | `--valid_pred_outfile`|
| JSON identifier         | `valid_pred_outfile`  |
| Default value           | `dimlpValidation.out` |

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
| Default value           | `statsDimlpBT.txt`  |

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

### First hidden layer
*Number of neurons in the first hidden layer.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--first_hidden_layer` |
| JSON identifier         | `first_hidden_layer`   |
| Default value           | `nb_attributes`        |

---

### Hidden layers
*Number of neurons in each hidden layer, from the second layer to the last.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `List of integers`     |
| CLI argument syntax     | `--hidden_layers`      |
| JSON identifier         | `hidden_layers`        |
| Default value           | `None`                 |

---

### Hidden layers output file
*Path to the file where output hidden layers sizes will be stored.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `String`                  |
| CLI argument syntax     | `--hidden_layers_outfile` |
| JSON identifier         | `hidden_layers_outfile`   |
| Default value           | `hidden_layers.out`       |

---

### Use rule extraction
*Whether to extract rules with dimlpBT algorithm.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `Boolean`                 |
| CLI argument syntax     | `--with_rule_extraction`  |
| JSON identifier         | `with_rule_extraction`    |
| Default value           | `False`                   |

---

### Global rules output file
*Path to the file where the output rule(s) will be stored.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `String`                  |
| CLI argument syntax     | `--global_rules_outfile`  |
| JSON identifier         | `global_rules_outfile`    |
| Default value           | `None`                    |

---

### Learning rate
*Back-propagation learning parameter.*

|  **Property**           | **Value**          |
|:------------------------|:-------------------|
| Is required             | No                 |
| Type                    | `Float`            |
| CLI argument syntax     | `--learning_rate`  |
| JSON identifier         | `learning_rate`    |
| Default value           | `0.1`              |

---

### Momentum
*Back-propagation momentum parameter.*

|  **Property**           | **Value**     |
|:------------------------|:--------------|
| Is required             | No            |
| Type                    | `Float`       |
| CLI argument syntax     | `--momentum`  |
| JSON identifier         | `momentum`    |
| Default value           | `0.6`         |

---

### Flat spot
*Back-propagation flat spot elimination parameter.*

|  **Property**           | **Value**     |
|:------------------------|:--------------|
| Is required             | No            |
| Type                    | `Float`       |
| CLI argument syntax     | `--flat`      |
| JSON identifier         | `flat`        |
| Default value           | `0.01`        |

---

### Error threshold
*Error threshold to stop training.*

|  **Property**           | **Value**         |
|:------------------------|:------------------|
| Is required             | No                |
| Type                    | `Float`           |
| CLI argument syntax     | `--error_thresh`  |
| JSON identifier         | `error_thresh`    |
| Default value           | `None`            |

---

### Accuracy threshold
*Accuracy threshold to stop training, goes from 0 to 1.*

|  **Property**           | **Value**         |
|:------------------------|:------------------|
| Is required             | No                |
| Type                    | `Float`           |
| CLI argument syntax     | `--acc_thresh`    |
| JSON identifier         | `acc_thresh`      |
| Default value           | `None`            |

---

### Absolute error threshold
*Absolute difference error threshold, 0 if not using this stopping criteria.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Float`             |
| CLI argument syntax     | `--abs_error_thresh`|
| JSON identifier         | `abs_error_thresh`  |
| Default value           | `0`                 |

---

### Number of epochs
*Number of model training epochs.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_epochs`       |
| JSON identifier         | `nb_epochs`         |
| Default value           | `1500`              |

---

### Number of epochs before showing error metric
*Number of training epochs before showing error.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_epochs_error` |
| JSON identifier         | `nb_epochs_error`   |
| Default value           | `10`                |

---

### Number of examples per net
*Number of examples for one single network, 0 for all examples, it is not recommended to change this value.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_ex_per_net`   |
| JSON identifier         | `nb_ex_per_net`     |
| Default value           | `0`                 |

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
    from dimlpfidex.dimlp import dimlpTrn

    dimlpTrn(
    """--train_data_file datanormTrain.txt 
    --train_class_file dataclass2Train.txt 
    --test_data_file datanormTest.txt 
    --test_class_file dataclass2Test.txt 
    --nb_attributes 16 
    --hidden_layers 5 
    --nb_classes 2 
    --weights_outfile dimlpDatanormBT.wts 
    --with_rule_extraction true 
    --global_rules_outfile globalRules.rls 
    --train_pred_outfile predTrain.out 
    --test_pred_outfile predTest.out 
    --root_folder dimlp/datafiles"""
    )
    ```
    
=== "CLI"
    ```
    ./dimlpTrn --train_data_file datanormTrain.txt --train_class_file dataclass2Train.txt --test_data_file datanormTest.txt --test_class_file dataclass2Test.txt --nb_attributes 16 --hidden_layers 5 --nb_classes 2 --weights_outfile dimlpDatanormBT.wts --with_rule_extraction true --global_rules_outfile globalRules.rls --train_pred_outfile predTrain.out --test_pred_outfile predTest.out --root_folder dimlp/datafiles
    ```

## Output interpretation
<!-- TODO: add output interpretation -->