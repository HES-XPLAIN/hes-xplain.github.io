# svmTrn

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

## Arguments list
The `svmTrn` algorithm works with both required and optional arguments. Each argument has specific properties:

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

### Train prediction ouput file 
*Path to the file where the train predictions will be stored.*

|  **Property**           | **Value**                    |
|:------------------------|:-----------------------------|
| Is required             | No                           |
| Type                    | `String`                     |
| CLI argument syntax     | `--train_pred_outfile`       | 
| JSON identifier         | `train_pred_outfile`         |
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
* Path to the file where the output trained weights of the model will be stored.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--weights_outfile` | 
| JSON identifier         | `weights_outfile`   |
| Default value           | `weights.wts`       |

---

### ROC output file
*Path to the file where the output ROC curve will be saved.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--output_roc`      |
| JSON identifier         | `output_roc`        |
| Default value           | `roc_curve.png`     |

---

### Return ROC
*Whether to return ROC statistics.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Boolean`           |
| CLI argument syntax     | `--return_roc`      |
| JSON identifier         | `return_roc`        |
| Default value           | `False`             |

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

---

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

### C parameter
*Regularization parameter.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--C`                  |
| JSON identifier         | `C`                    |
| Default value           | `1.0`                  |

---

### Kernel
<!-- TODO: add better description -->
*Kernel type. Options are `linear`, `poly`, `rbf`, and `sigmoid`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--kernel`             |
| JSON identifier         | `kernel`               |
| Default value           | `rbf`                  |

---

### Polynomial degree
<!-- TODO: add better description -->
*Polynomial degree.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Integer`              |
| CLI argument syntax     | `--degree`             |
| JSON identifier         | `degree`               |
| Default value           | `3`                    |

---

### Gamma 
*Gamma value. Can be `float` or `String` with the following options: `scale`, or `auto`.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float` or `String`    |
| CLI argument syntax     | `--gamma`              |
| JSON identifier         | `gamma`                |
| Default value           | `scale`                |

---

### Coef0 
*Term in the kernel function.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Float`                |
| CLI argument syntax     | `--coef0`              |
| JSON identifier         | `coef0`                |
| Default value           | `0.0`                  |

---

### Use shrinking heuristic
*Whether to use the shrinking heuristic.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Boolean`              |
| CLI argument syntax     | `--shrinking`          |
| JSON identifier         | `shrinking`            |
| Default value           | `True`                 |

---

### Tolerance
*Tolerance for the stopping criterion.*

|  **Property**           | **Value**   |
|:------------------------|:------------|
| Is required             | No          |
| Type                    | `Float`     |
| CLI argument syntax     | `--tol`     |
| JSON identifier         | `tol`       |
| Default value           | `0.0001`    |

---

### Cache size
*Kernel cache size(MB).*

|  **Property**           | **Value**          |
|:------------------------|:-------------------|
| Is required             | No                 |
| Type                    | `Float`            |
| CLI argument syntax     | `--cache_size`     |
| JSON identifier         | `cache_size`       |
| Default value           | `200.0`            |

---
                 
### Class weight
*Class balance, for exemple with a dictionnary and 2 classes : `{0:1.2, 1:3.5}`. Can also be `balanced`.*

|  **Property**           | **Value**                 |
|:------------------------|:--------------------------|
| Is required             | No                        |
| Type                    | `String` or `Dictionnary` |
| CLI argument syntax     | `--class_weight`          |
| JSON identifier         | `class_weight`            |
| Default value           | `None`                    |

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

###  Maximum number of iterations
* Maximum number of training iterations. `-1` means no limit.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Integer`             |
| CLI argument syntax     | `--max_iterations`    |
| JSON identifier         | `max_iterations`      |
| Default value           | `-1`                  |

---

###  Decision function shape
*  Decision function shape. Options are `ovo`(one-vs-one), and `ovr` (one-vs-rest).*

|  **Property**           | **Value**                      |
|:------------------------|:-------------------------------|
| Is required             | No                             |
| Type                    | `String`                       |
| CLI argument syntax     | `--decision_function_shape`    |
| JSON identifier         | `decision_function_shape`      |
| Default value           | `ovr`                          |

---

### Break ties
*Whether to break tie decision for `ovr` with more than 2 classes.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             |  No                    |
| Type                    |  `Boolean`             |
| CLI argument syntax     |  `--break_ties`        |
| JSON identifier         |  `break_ties`          |
| Default value           | `False`                |

---

## Usage example

=== "Python"
    ```py
    from trainings import svmTrn

    svmTrn(
    """--train_data_file datanormTrain.txt 
       --train_class_file dataclass2Train.txt 
       --test_data_file datanormTest.txt 
       --test_class_file dataclass2Test.txt 
       --weights_outfile svm/weights.wts 
       --stats_file svm/stats.txt 
       --train_pred_outfile svm/predTrain.out 
       --test_pred_outfile svm/predTest.out 
       --nb_attributes 16 
       --nb_classes 2 
       --root_folder dimlp/datafiles"""
    )
    ```
    
=== "CLI"
    ```
    ./svmTrn --train_data_file datanormTrain.txt --train_class_file dataclass2Train.txt --test_data_file datanormTest.txt --test_class_file dataclass2Test.txt --weights_outfile svm/weights.wts --stats_file svm/stats.txt --train_pred_outfile svm/predTrain.out --test_pred_outfile svm/predTest.out --nb_attributes 16 --nb_classes 2 --root_folder dimlp/datafiles
    ```

## Output interpretation