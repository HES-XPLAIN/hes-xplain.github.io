# mlpTrn

## Description

The `MLP` (Multi-Layer Perceptron) is a class of feedforward artificial neural networks that consists of multiple layers of nodes, including an input layer, one or more hidden layers, and an output layer. It is commonly used for both classification and regression tasks. In this implementation, we use the version provided by `scikit-learn`, which allows for flexible and efficient training. The inclusion of the [Dimlp](../dimlp/overview.md) layer adds interpretability by enabling the extraction of decision rules via the [Fidex](../fidex/overview.md) algorithm, making the model's decisions more transparent and easier to explain.

## Arguments list
The `mlpTrn` algorithm works with both required and optional arguments. Each argument has specific properties:

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
*File containing the train portion of the dataset, It can also contain training "true classes" (see [Train true classes file](#train-true-classes-file)).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--train_data_file` |
| JSON identifier         | `train_data_file`   |
| Default value           | `None`              |

--- 

### Test data file

*Path to the file containing test portion of the dataset, It can also contain testing "true classes" (see [Test true classes file](#test-true-classes-file)).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_data_file`  |
| JSON identifier         | `test_data_file`    |
| Default value           | `None`              |

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

### Train true classes file
*File containing "true classes" (expected predictions), from the train portion of the dataset used to train the model.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No**                 |
| Type                    | `String`             |
| CLI argument syntax     | `--train_class_file` | 
| JSON identifier         | `train_class_file`   |
| Default value           | `None`               |

!!! warning
    This argument is not required if, **and only if**, the *true classes* are already specified inside the [train data file](#train-data-file).

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

!!! warning
    This argument is not required if, **and only if**, the *true classes* are already specified inside the [test data file](#test-data-file). 

---

### Train prediction output file 
*Path to the file where the train predictions will be stored.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `String`                     |
| CLI argument syntax     | `--train_pred_outfile`       | 
| JSON identifier         | `train_pred_outfile`         |
| Default value           | `predTrain.out`              |

---

### Test prediction output file 
*Path to the file where the test predictions will be stored.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `String`                     |
| CLI argument syntax     | `--test_pred_outfile`        | 
| JSON identifier         | `test_pred_outfile`          |
| Default value           | `predTest.out`               |

---

### Statistics output file
*Name of the output file that will contain all computed statistics.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--stats_file`      |
| JSON identifier         | `stats_file`        |
| Default value           | `stats.txt`         |

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

### Weights output file
*Path to the file where the output trained weights of the model will be stored.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--weights_outfile` | 
| JSON identifier         | `weights_outfile`   |
| Default value           | `weights.wts`       |

---

### Number of stairs
*Number of stairs in the staircase activation function used in the Dimlp layer. Takes values in the range `[3,∞[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--nb_quant_levels`    |
| JSON identifier         | `nb_quant_levels`      |
| Default value           | `50`                   |

---

### K parameter
*Parameter to improve dynamics by normalizing input data. Takes values in the range `]0,∞[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--K`                  |
| JSON identifier         | `K`                    |
| Default value           | `1.0`                  |

---

### Hidden layers size
*Size of each hidden layer. Each size takes values in the range `[1,∞[`.

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `List of integers`     |
| CLI argument syntax     | `--hidden_layer_sizes` |
| JSON identifier         | `hidden_layer_sizes`   |
| Default value           | `100`                  |

---

### Activation function
*Used activation function. Options `identity`, `logistic`, `tanh` and `relu`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `String`               |
| CLI argument syntax     | `--activation`         |
| JSON identifier         | `activation`           |
| Default value           | `relu`                  |

---

### Solver
*Solver for weight optimization. Options `lbfgs`, `sgd` and `adam`.*

|  **Property**           | **Value**          |
|:------------------------|:-------------------|
| Is required             | No                 |
| Type                    | `String`           |
| CLI argument syntax     | `--solver`         |
| JSON identifier         | `solver`           |
| Default value           | `adam`             |

---

### Alpha
*Strength of the `L2 regularization` term. Takes values in the range `]0,∞[`.*

|  **Property**           | **Value**          |
|:------------------------|:-------------------|
| Is required             | No                 |
| Type                    | `Float`            |
| CLI argument syntax     | `--alpha`          |
| JSON identifier         | `alpha`            |
| Default value           | `0.0001`           |

---

### Batch size
*Size of minibatches for stochastic optimizers for `adam` and `stochastic gradient descent`. Can be a number in the range `[1,∞[` or `auto`.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `Integer` or `String`|
| CLI argument syntax     | `--batch_size`       |
| JSON identifier         | `batch_size`         |
| Default value           | `auto`               |

---

### Learning rate
*Learning rate schedule for weight updates for `stochastic gradient descent` solver. Options are `constant`, `invscaling`, and `adaptive`.*

|  **Property**           | **Value**            |
|:------------------------|:---------------------|
| Is required             | No                   |
| Type                    | `String`             |
| CLI argument syntax     | `--learning_rate`    |
| JSON identifier         | `learning_rate`      |
| Default value           | `constant`           |

---

### Initial learning rate
*Initial learning rate for `adam` and `stochastic gradient descent`. Takes values in the range `]0,∞[`.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Float`               |
| CLI argument syntax     | `--learning_rate_init`|
| JSON identifier         | `learning_rate_init`  |
| Default value           | `0.001`               |

---

### Power T
*Exponent for inverse scaling learning rate for `stochastic gradient descent`. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Float`               |
| CLI argument syntax     | `--power_t`           |
| JSON identifier         | `power_t`             |
| Default value           | `0.5`                 |

---

###  Maximum number of iterations
*Maximum number of training iterations. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Integer`             |
| CLI argument syntax     | `--max_iterations`    |
| JSON identifier         | `max_iterations`      |
| Default value           | `200`                 |

---

### Shuffle
*Whether to shuffle samples in each iteration for `stochastic gradient descent` and `adam`.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Boolean`             |
| CLI argument syntax     | `--shuffle`           |
| JSON identifier         | `shuffle`             |
| Default value           | `True`                |

---

### Seed
*Seed for random number generation for `stochastic gradient descent` and `adam`. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | No              |
| Type                    | `Integer`       |
| CLI argument syntax     | `--seed`        |
| JSON identifier         | `seed`          |
| Default value           | `None`          |

---

### Tolerance
*Tolerance for the optimization. Takes values in the range `]0,∞[`.*

|  **Property**           | **Value**   |
|:------------------------|:------------|
| Is required             | No          |
| Type                    | `Float`     |
| CLI argument syntax     | `--tol`     |
| JSON identifier         | `tol`       |
| Default value           | `0.0001`    |

---

### Verbose
*Enable verbose output.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Boolean`             |
| CLI argument syntax     | `--verbose`           |
| JSON identifier         | `verbose`             |
| Default value           | `False`               |

---

### Warm start
*Whether to reuse the previous solution to fit initialization.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Boolean`             |
| CLI argument syntax     | `--warm_start`        |
| JSON identifier         | `warm_start`          |
| Default value           | `False`               |

---

### Momentum
*Momentum for gradient descent update for `stochastic gradient descent`. Takes values in the range `[0,1]`.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Float`               |
| CLI argument syntax     | `--momentum`          |
| JSON identifier         | `momentum`            |
| Default value           | `0.9`                 |

---

### Use Nesterovs momentum
*Whether to use the Nesterov’s momentum for `stochastic gradient descent` and `momentum`.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Boolean`             |
| CLI argument syntax     | `--nesterovs_momentum`|
| JSON identifier         | `nesterovs_momentum`  |
| Default value           | `True`                |

---

### Early stopping
*Whether to use early stopping to terminate training when validation score is not improving for `stochastic gradient descent` and `adam`.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Boolean`             |
| CLI argument syntax     | `--early_stopping`    |
| JSON identifier         | `early_stopping`      |
| Default value           | `False`               |

---

### Validation fraction
*Proportion of training data to set aside as validation set for early stopping. Takes values in the range `[0,1[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--validation_fraction`|
| JSON identifier         | `validation_fraction`  |
| Default value           | `0.1`                  |

---

### Beta 1
*Exponential decay rate for estimates of first moment vector in `adam`. Takes values in the range `[0,1[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--beta_1`             |
| JSON identifier         | `beta_1`               |
| Default value           | `0.9`                  |

---

### Beta 2
*Exponential decay rate for estimates of second moment vector in `adam`. Takes values in the range `[0,1[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--beta_2`             |
| JSON identifier         | `beta_2`               |
| Default value           | `0.999`                |

---

### Epsilon
*Value for numerical stability in `adam`. Takes values in the range `]0,∞[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--epsilon`            |
| JSON identifier         | `epsilon`              |
| Default value           | `1e-08`                |

---

### Number of non-significant iterations before stopping
*Maximum number of epochs to not meet `tol` improvement for `stochastic gradient descent` and `adam`. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Integer`                |
| CLI argument syntax     | `--n_iter_no_change`     |
| JSON identifier         | `n_iter_no_change`       |
| Default value           | `10`                     |

---

### Maximum number of loss function calls
*Maximum number of loss function calls for `lbfgs`. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | No                       |
| Type                    | `Integer`                |
| CLI argument syntax     | `--max_fun`              |
| JSON identifier         | `max_fun`                |
| Default value           | `15000`                  |

## Usage example

!!!example

    === "Python"
        ```py
        from trainings import mlpTrn

        mlpTrn(
        """--train_data_file train_data.txt 
        --train_class_file train_class.txt 
        --test_data_file test_data.txt 
        --test_class_file test_class.txt 
        --weights_outfile mlp/weights.wts 
        --stats_file mlp/stats.txt 
        --train_pred_outfile mlp/predTrain.out 
        --test_pred_outfile mlp/predTest.out 
        --nb_attributes 16 
        --nb_classes 2 
        --root_folder dimlp/datafiles"""
        )
        ```
        
    === "CLI"
        ```
        ./mlpTrn --train_data_file train_data.txt --train_class_file train_class.txt --test_data_file test_data.txt --test_class_file test_class.txt --weights_outfile mlp/weights.wts --stats_file mlp/stats.txt --train_pred_outfile mlp/predTrain.out --test_pred_outfile mlp/predTest.out --nb_attributes 16 --nb_classes 2 --root_folder ../dimlp/datafiles
        ```

## Output interpretation

---

### [Train/Test prediction file](#train-prediction-output-file)

This file contains the predicted probabilities for each possible class for each train (or test) sample. Each row corresponds to the prediction for a single sample, with `N` values representing the probability that the sample belongs to class `0`, `1`, ... or class `N`. The values in each row sum to 1. The class with the highest probability is considered the predicted class for that sample, unless a decision threshold is applied for a specific class. In that case, if the predicted probability for that class exceeds the threshold, the sample is classified as belonging to that class.

For example:

    0.000718874 0.999281
    0.949143 0.050857

In the first row, the model predicts a probability of approximately 0.0007 that the sample belongs to class 0, and 0.9993 that it belongs to class 1. Therefore, the model predicts class 1 for this sample.
In the second row, the model predicts a probability of 0.949 that the sample belongs to class 0, and 0.051 that it belongs to class 1. Hence, the model predicts class 0 for this sample.

Each row of probabilities allows you to interpret the model's confidence in its predictions, enabling you to understand the likelihood of each sample belonging to a particular class.

---

### [Weights output file](#weights-output-file)

This file contains the weights and biases of the first hidden layer of the neural network, which is the [Dimlp](../dimlp/overview.md) layer.

- The **first row** in the file represent the **bias values**. There is one bias value for each neuron.
- The **second row** represent the values of the **weight matrix** between the first layer and the next one.

---

### [Statistics file](#statistics-output-file)

This file contains accuracy on the training and testing sets. It offers a clear overview of the model’s performance across different datasets, helping to evaluate how well the model has learned and generalized to unseen data.

`Accuracy`
:   Indicates the proportion of correctly classified samples in each dataset (training or testing).