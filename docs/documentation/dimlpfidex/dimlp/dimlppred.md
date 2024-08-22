# DimlpPred

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

The `Discretized Interpretable Multi-Layer Perceptron (DIMLP)` is a neural network architecture that combines the predictive power of a traditional Multi-Layer Perceptron (MLP) with the ability to extract interpretable rules. Unlike conventional neural networks, `DIMLP` uses a staircase activation function in the first hidden layer, creating a grid of hyper-rectangles in the feature space. These hyper-rectangles help define discriminant decision boundaries between classes, facilitating the extraction of symbolic rules.

`DimlpPred` generates predictions on a test dataset using the model trained by [dimlpTrn](dimlptrn.md).

For more details on the `Dimlp` algorithm, you can refer to [this paper](../../references.md#a-model-for-single-and-multiple-knowledge-based-networks).

!!!Warning
     You should not execute `DimlpPred` for a model trained by [DimlpBT](dimlpbt.md), it should be trained by [dimlpTrn](dimlptrn.md)!

## Arguments list
The `dimlpPred` algorithm works with both required and optional arguments. Each argument has specific properties:

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

### Test data file
*File containing the test portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_data_file`  | 
| JSON identifier         | `test_data_file`    |
| Default value           | `None`              |

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


### Test predictions output file
*Path to the file where the test predictions will be stored.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `String`               |
| CLI argument syntax     | `--test_pred_outfile`  | 
| JSON identifier         | `test_pred_outfile`    |
| Default value           | `dimlpTest.out`        |

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

## Usage example

!!!example

    === "Python"
        ```py
        from dimlpfidex.dimlp import dimlpPred

        dimlpPred(
        """--test_data_file test_data.txt 
        --weights_file weights.wts 
        --nb_attributes 16 
        --hidden_layers_file hidden_layers.out 
        --nb_classes 2 
        --test_pred_outfile predTest.out 
        --root_folder dimlp/datafiles"""
        )
        ```
        
    === "CLI"
        ```
        ./dimlpPred --test_data_file test_data.txt --weights_file weights.wts --nb_attributes 16 --hidden_layers_file hidden_layers.out --nb_classes 2 --test_pred_outfile predTest.out --root_folder ../dimlp/datafiles
        ```

## Output interpretation

---

### [Test prediction file](#test-predictions-output-file)

This file contains the predicted probabilities for each possible class for each test sample. Each row corresponds to the prediction for a single sample, with `N` values representing the probability that the sample belongs to class `0`, `1`, ... or class `N`. The values in each row sum to 1. The class with the highest probability is considered the predicted class for that sample, unless a decision threshold is applied for a specific class. In that case, if the predicted probability for that class exceeds the threshold, the sample is classified as belonging to that class.

For example:

    0.000718874 0.999281
    0.949143 0.050857

In the first row, the model predicts a probability of approximately 0.0007 that the sample belongs to class 0, and 0.9993 that it belongs to class 1. Therefore, the model predicts class 1 for this sample.
In the second row, the model predicts a probability of 0.949 that the sample belongs to class 0, and 0.051 that it belongs to class 1. Hence, the model predicts class 0 for this sample.

Each row of probabilities allows you to interpret the model's confidence in its predictions, enabling you to understand the likelihood of each sample belonging to a particular class.
