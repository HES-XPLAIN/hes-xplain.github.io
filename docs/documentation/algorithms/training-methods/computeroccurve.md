# computeRocCurve

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

## Arguments list
The `computeRocCurve` algorithm works with both required and optional arguments. Each argument has specific properties:

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
*Default path from where all the other arguments related to file paths are going to be based. Using this allows you to work with paths relative from this location and avoid writing absolute paths or lengthy relative paths.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--root_folder`     | 
| JSON identifier         | `root_folder`       |
| Default value           | `.`                 |

---

### Test true classes file
*File containing "true classes" (expected predictions), from the test portion of the dataset used to train the model.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_class_file` | 
| JSON identifier         | `test_class_file`   |
| Default value           | `None`              |

---

### Test prediction file

*File containing predictions on the test portion of the dataset.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | Yes                 |
| Type                    | `String`            |
| CLI argument syntax     | `--test_pred_file`  | 
| JSON identifier         | `test_pred_file`    |
| Default value           | `None`              |

---

### Positive class index
*Index of positive class for the usage of decision threshold, index starts at `0`. Takes values in the range `[0,nb_classes-1]`.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | Yes                     |
| Type                    | `Integer`               |
| CLI argument syntax     | `--positive_class_index`|
| JSON identifier         | `positive_class_index`  |
| Default value           | `None`                  |

---

### Number of classes
*Number of classes in the dataset (should be equal to the number of outputs of the model). Takes values in the range [2,∞[.*

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

### Statistics output file
*Name of the output file that will contain all computed statistics.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--stats_file`      |
| JSON identifier         | `stats_file`        |
| Default value           | `None`              |

---

### Display parameter inputs
*Whether to show currently used parameters by the program while running.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `Boolean`           |
| CLI argument syntax     | `--show_params`     |
| JSON identifier         | `show_params`       |
| Default value           | `True`              |

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

### Estimator
*Name of the used estimator.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--output_roc`      |
| JSON identifier         | `output_roc`        |
| Default value           | `roc_curve.png`     |

---

## Usage example

=== "Python"
    ```py
    from trainings import computeRocCurve

    computeRocCurve(
    """--test_class_file dataclass2Test.txt 
       --test_pred_file predTest.out 
       --positive_class_index 1 
       --output_roc roc_curve.png 
       --stats_file stats.txt 
       --root_folder dimlp/datafiles 
       --nb_classes 2"""
    )
    ```
    
=== "CLI"
    ```
    ./computeRocCurve --test_class_file dataclass2Test.txt --test_pred_file predTest.out --positive_class_index 1 --output_roc roc_curve.png --stats_file stats.txt --root_folder dimlp/datafiles --nb_classes 2
    ```

## Output interpretation