# cnnTrn

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description



## Arguments list
The `cnnTrn` algorithm has required and optional arguments to be specified. Each of them has properties:

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

*Original dimensions of the input.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | Yes                      |
| Type                    | pair of `Integers`       |
| CLI argument syntax     | `--original_input_size`  | 
| JSON identifier         | `original_input_size`    |
| Default value           | `None`                   |

---

### Nuber of channels

*Number of channels in the input (should be 3 for RGB image and 1 for a grayscaled image).*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | Yes             |
| Type                    | `Integer`       |
| CLI argument syntax     | `--nb_channels` | 
| JSON identifier         | `nb_channels`   |
| Default value           | `None`          |

---

### Model
*Used model to train. Options are `small`, `large`, `vgg` and `resnet`.*

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
*Number of classes in the dataset (should be equal to the number of outputs of the model).*

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

### Show help
*Display parameters and other helpful information concerning the program usage and terminate it when done.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `None`              |
| CLI argument syntax     | `-h` or `--help`    |
| JSON identifier         | `N/A`               |
| Default value           | `None`              |

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
*Percentage of train data taken for validation.*

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

<!-- TODO: this admonition is not clear -->
!!! warning
    if there is validation files, and you want to use Fidex algorithms later, you will have to use both train and validation datas given here in the train datas and classes of Fidex

---

### Weights output file
* Path to the file where the output trained weights of the model will be stored.*

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

*Number of model training epochs.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--nb_epochs`          |
| JSON identifier         | `nb_epochs`            |
| Default value           | `80`                   |

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

### K parameter
*Parameter to improve dynamics by normalizing input data.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--K`                  |
| JSON identifier         | `K`                    |
| Default value           | `1.0`                  |

---

### Model input size

*Input size in the model. A small size is recommended to speed up the process. The size is modified if necessary.*

|  **Property**           | **Value**                |
|:------------------------|:-------------------------|
| Is required             | Yes                      |
| Type                    | pair of `Integers`       |
| CLI argument syntax     | `--model_input_size`     | 
| JSON identifier         | `model_input_size`       |
| Default value           | `None`                   |

---

### Seed
*Seed for random number generation, `0=random`. Anything else than `0` is an arbitrary seed that can be reused to obtain the same randomly generated sequence and therefore getting same results.*

|  **Property**           | **Value**       |
|:------------------------|:----------------|
| Is required             | No              |
| Type                    | `Integer`       |
| CLI argument syntax     | `--seed`        |
| JSON identifier         | `seed`          |
| Default value           | `0`             |

---

## Usage example

=== "Python"
    ```py
    from trainings import cnnTrn

    cnnTrn(
    """--model small 
       --train_data_file trainData.txt 
       --train_class_file trainClass.txt 
       --test_data_file testData.txt 
       --test_class_file testClass.txt 
       --valid_data_file validData.txt 
       --valid_class_file validClass.txt 
       --original_input_size (28,28) 
       --nb_channels 1 
       --data_format classic 
       --nb_classes 10 
       --root_folder dimlp/datafiles/Mnist"""
    )
    ```
    
=== "CLI"
    ```
    ./cnnTrn --model small --train_data_file trainData.txt --train_class_file trainClass.txt --test_data_file testData.txt --test_class_file testClass.txt --valid_data_file validData.txt --valid_class_file validClass.txt --original_input_size (28,28) --nb_channels 1 --data_format classic --nb_classes 10 --root_folder dimlp/datafiles/Mnist
    ```

## Output interpretation