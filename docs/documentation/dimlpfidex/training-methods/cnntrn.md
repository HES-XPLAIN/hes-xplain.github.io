# cnnTrn

## Description

The `CNN` (Convolutional Neural Network) is a deep learning architecture commonly used for tasks involving image data, such as classification and object detection. In this implementation, we use the `Keras` library, which allows for easy integration of popular CNN architectures like `ResNet` and `VGG`. The algorithm can be applied to a wide range of datasets, including well-known image datasets like `MNIST`, `CIFAR-10`, and `CIFAR-100`. Additionally, the inclusion of the [Dimlp](../dimlp/overview.md) layer adds interpretability by enabling the extraction of decision rules via the [Fidex](../fidex/overview.md) algorithm, making the model's decisions more transparent and easier to explain.

## Practical informations

It is important to reduce the size of the images beforehand, as processing high-resolution images can be very time-consuming, especially when using [Fidex](../fidex/fidex.md) or [FidexGloRules](../fidex/fidexglorules.md).

If you want to add a new model to `cnnTrn`, go to the [cnnTrn](https://github.com/HES-XPLAIN/dimlpfidex/blob/main/trainings/cnnTrn.py) file and add the new model name in the `--model` argument :

    parser.add_argument("--model", choices=["small", "large", "vgg", "resnet", "newModel"], metavar="<{small, large, vgg, resnet, newModel}>", help="Training model", required=True)

Next, define this model inside the code after the other models, just before the following line:

    else:
        raise ValueError(f"Internal error : No model has been executed, given model : {args.model}.")

If your model is not 2D, you will need to change the `pair_type` of the `original_input_size` and `model_input_size` arguments to `list_type` in order to accept more or fewer than 2 values.

## Arguments list
The `cnnTrn` algorithm works with both required and optional arguments. Each argument has specific properties:

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

### Original input size

*Original dimensions of the input. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | Yes                      |
| Type                    | `Pair of Integers`       |
| CLI argument syntax     | `--original_input_size`  | 
| JSON identifier         | `original_input_size`    |
| Default value           | `None`                   |

---

### Number of channels

*Number of channels in the input (should be 3 for RGB image and 1 for a grayscaled image). Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | Yes             |
| Type                    | `Integer`       |
| CLI argument syntax     | `--nb_channels` | 
| JSON identifier         | `nb_channels`   |
| Default value           | `None`          |

---

### Model
*Model used to train. Options are `small`, `large`, `vgg` and `resnet`.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | Yes             |
| Type                    | `String`        |
| CLI argument syntax     | `--model`       | 
| JSON identifier         | `model`         |
| Default value           | `None`          |

---

### Data format
*Format of the values, `normalized_01` if the values are normalized between `0` and `1`, `classic` if they are between `0` and `255`. Options are `normalized_01`, `classic` and `other`.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | Yes             |
| Type                    | `String`        |
| CLI argument syntax     | `--data_format` | 
| JSON identifier         | `data_format`   |
| Default value           | `None`          |

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

### Train and validation predictions output file
*Path to the file where the output train and validation (in this order) prediction will be stored.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `String`                     |
| CLI argument syntax     | `--train_valid_pred_outfile` | 
| JSON identifier         | `train_valid_pred_outfile`   |
| Default value           | `predTrain.out`              |

---

### Test prediction ouput file 
*Path to the file where the test predictions will be stored.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `String`                     |
| CLI argument syntax     | `--test_pred_outfile`        | 
| JSON identifier         | `test_pred_outfile`          |
| Default value           | `predTest.out`               |

---

### Validation ratio
*Percentage of train data taken for validation. Not used if validation files are given. Takes values in the range `]0,1[`.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Float`             |
| CLI argument syntax     | `--valid_ratio`     | 
| JSON identifier         | `valid_ratio`       |
| Default value           | `0.1`               |

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
*Path to the file containing the validation true classes of the dataset, mandatory if classes are not specified in the [validation data file](#validation-data-file).*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--valid_class_file`|
| JSON identifier         | `valid_class_file`  |
| Default value           | `None`              |

!!! warning
    If validation files are given, when using Fidex algorithms, you will need to merge the [train data file](#train-data-file) and [validation data file](#validation-data-file) (in this order) as well as the [train class file](#train-true-classes-file) and the [validation class file](#validation-true-classes-file) (in this order) and feed them to Fidex as respectively the [train data file](../fidex/fidex.md/#train-data-file) and the [train class file](../fidex/fidex.md/#train-true-classes-file).

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

### Number of epochs

*Number of model training epochs. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--nb_epochs`          |
| JSON identifier         | `nb_epochs`            |
| Default value           | `80`                   |

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

### Model input size

*Input size in the model. A small size is recommended to speed up the process. The size is modified if necessary. Takes values in the range `[1,∞[`.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | Yes                      |
| Type                    | `Pair of Integers`       |
| CLI argument syntax     | `--model_input_size`     | 
| JSON identifier         | `model_input_size`       |
| Default value           | `None`                   |

---

### Seed
*Seed for random number generation, `0=random`. Anything else than `0` is an arbitrary seed that can be reused to obtain the same randomly generated sequence and therefore getting same results. Takes values in the range `[0,∞[`.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | No              |
| Type                    | `Integer`       |
| CLI argument syntax     | `--seed`        |
| JSON identifier         | `seed`          |
| Default value           | `0`             |

---

## Usage example

!!!example

    === "Python"
        ```py
        from trainings import cnnTrn

        cnnTrn(
        """--model small 
        --train_data_file train_data.txt 
        --train_class_file train_class.txt 
        --test_data_file test_data.txt 
        --test_class_file test_class.txt 
        --original_input_size (28,28) 
        --nb_channels 1 
        --data_format classic 
        --nb_classes 10 
        --root_folder dimlp/datafiles/Mnist"""
        )
        ```
        
    === "CLI"
        ```
        ./cnnTrn --model small --train_data_file train_data.txt --train_class_file train_class.txt --test_data_file test_data.txt --test_class_file test_class.txt --original_input_size (28,28) --nb_channels 1 --data_format classic --nb_classes 10 --root_folder ../dimlp/datafiles/Mnist
        ```

## Output interpretation

---

### [Train and validation/Test prediction file](#test-prediction-ouput-file)

This file contains the predicted probabilities for each possible class for each train and validation (or test) sample. In the train prediction file, there are train predictions followed by validation predictions. Each row corresponds to the prediction for a single sample, with `N` values representing the probability that the sample belongs to class `0`, `1`, ... or class `N`. The values in each row sum to 1. The class with the highest probability is considered the predicted class for that sample, unless a decision threshold is applied for a specific class. In that case, if the predicted probability for that class exceeds the threshold, the sample is classified as belonging to that class.

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

### HDF5 trained weights output file

This file stores the weights of a trained model in HDF5 format (.h5). The file is used to save the parameters (weights and biases) of the model after it has been trained, allowing you to reload the model later for inference or further training without needing to retrain it from scratch.

---

### [Statistics file](#statistics-output-file)

This file contains accuracy on the training and testing sets. It offers a clear overview of the model’s performance across different datasets, helping to evaluate how well the model has learned and generalized to unseen data.

`Accuracy`
:   Indicates the proportion of correctly classified samples in each dataset (training or testing).