# normalization

!!!warning
    **This section is under construction and should not be considered as accurate yet.**

## Description

The normalization is a method that adjusts the scale of data attributes, typically by converting values to a standard range (e.g., zero mean and unit variance), facilitating more efficient and accurate model training. This algorithm offers flexibility by allowing normalization based on pre-defined parameters, calculated statistics from provided data files, or manual input of mean and standard deviation. Additionally, it supports denormalizing rule files for more interpretable results. The process generates normalized data files and denormalized rule files, and is especially useful when preparing data for [Dimlp](../dimlp/overview.md) models.

Keep the following in mind:

- Normalization is recommended before training with [DimlpTrn](../dimlp/dimlptrn.md) and [DimlpBT](../dimlp/dimlpbt.md).
- Normalization is not necessary for [CNN](cnntrn.md), [MLP](mlptrn.md), and [SVM](svmtrn.md) as normalization is handled internally during the training process.
- Decision trees (e.g., [Gradient Boosting](gradboosttrn.md), [Random Forests](randforeststrn.md)) do not require normalization as they are robust to unnormalized data.

Do not forget to denormalize the generated rules afterwards if you have normalized your data.

## Arguments list
The `normalization` algorithm works with both required and optional arguments. Each argument has specific properties:

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
| Is required             | No                  |
| Type                    | `Integer`           |
| CLI argument syntax     | `--nb_classes`      |
| JSON identifier         | `nb_classes`        |
| Default value           | `None`              |

---

### Attributes file
*File containing attributes and classes names.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No                  |
| Type                    | `String`            |
| CLI argument syntax     | `--attributes_file` |
| JSON identifier         | `attributes_file`   |
| Default value           | `None`              |

---

### Data files
*List of data files to normalize, they are normalized with respect to the first one if [normalization file](#normalization-file) is not specified.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `List of strings`   |
| CLI argument syntax     | `--data_files`      |
| JSON identifier         | `data_files`        |
| Default value           | `None`              |

!!!Warning
    This argument is not required if, **and only if**, the [rule files](#rule-files) is specified. 

---

### Rule files
*List of rule files to denormalize, denormalization is possible only if a [normalization file](#normalization-file) or [mus](#mus), [sigmas](#sigmas) and [normalization indices](#normalization-indices) are given.*

|  **Property**           | **Value**           |
|:------------------------|:--------------------|
| Is required             | No**                |
| Type                    | `List of strings`   |
| CLI argument syntax     | `--rule_files`      |
| JSON identifier         | `rule_files`        |
| Default value           | `None`              |

!!!Warning
    This argument is not required if, **and only if**, the [data files](#data-files) is specified. 

---
### Missing values
*String representing a missing value in your data.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No**                    |
| Type                    | `String`                |
| CLI argument syntax     | `--normalization_file`  |
| JSON identifier         | `normalization_file`    |
| Default value           | `None`                  |

!!!Warning
    This argument **is required** for normalization. Put `NaN` or any string not present in your data if there is no missing data.

---

### Normalization file
*File containing the mean and standard deviation for specified attributes to normalize data or denormalize rules.*

|  **Property**           | **Value**               |
|:------------------------|:------------------------|
| Is required             | No                      |
| Type                    | `String`                |
| CLI argument syntax     | `--normalization_file`  |
| JSON identifier         | `normalization_file`    |
| Default value           | `None`                  |

---

### Mus
*Mean or median of each attribute index specified in [normalization indices](#normalization-indices) to normalize data or denormalize rules. This argument is used alongside [sigmas](#sigmas) and [normalization indices](#normalization-indices). Takes values in the range `]-∞,∞[`.*

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
*Standard deviation of each attribute index specified in [normalization indices](#normalization-indices) to normalize data or denormalize rules. This argument is used alongside [mus](#mus) and [normalization indices](#normalization-indices). Takes values in the range `]-∞,∞[`.*

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
*Indices of attributes to normalize or denormalize. Index starts at 0. Each index takes values in the range `[0,nb_attributes-1]`.*

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

### Normalization output file
*Path to the file where the mean and standard deviation of the normalized attributes will be stored.*

|  **Property**           | **Value**                     |
|:------------------------|:------------------------------|
| Is required             | No                            |
| Type                    | `String`                      |
| CLI argument syntax     | `--output_normalization_file` | 
| JSON identifier         | `output_normalization_file`   |
| Default value           | `normalization_stats.txt`     |

---

### Data output files
*List containing the paths where the normalized data files will be saved.*

|  **Property**           | **Value**                                         |
|:------------------------|:--------------------------------------------------|
| Is required             | No                                                |
| Type                    | `List of strings`                                 |
| CLI argument syntax     | `--output_data_files`                             |
| JSON identifier         | `output_data_files`                               |
| Default value           | `<original_name>_denormalized<original_extension>`|

!!!Warning
    If one name is specified, all names are required.

---

### Rule output files
*List containing the paths where the denormalized rule files will be saved.*

|  **Property**           | **Value**                                         |
|:------------------------|:--------------------------------------------------|
| Is required             | No                                                |
| Type                    | `List of strings`                                 |
| CLI argument syntax     | `--output_rule_files`                             |
| JSON identifier         | `output_rule_files`                               |
| Default value           | `<original_name>_denormalized<original_extension>`|

!!!Warning
    If one name is specified, all names are required.

---

### Use median
*Whether to use median instead of mean to normalize.*

|  **Property**           | **Value**             |
|:------------------------|:----------------------|
| Is required             | No                    |
| Type                    | `Boolean`             |
| CLI argument syntax     | `--with_median`       |
| JSON identifier         | `with_median`         |
| Default value           | `False`               |

---

### Fill missing values
*Whether to fill missing values with mean (or median) during normalization.*

|  **Property**           | **Value**              |
|:------------------------|:-----------------------|
| Is required             | No                     |
| Type                    | `Boolean`              |
| CLI argument syntax     | `--fill_missing_values`|
| JSON identifier         | `fill_missing_values`  |
| Default value           | `True`                 |

---


## Usage example

For datafile normalization :

!!!example

    === "Python"
        ```py
        from trainings import normalization

        normalization(
        """--data_files [train_data.txt,test_data.txt]
        --normalization_indices [0,2,4]
        --nb_attributes 16
        --missing_values NaN
        --root_folder dimlp/datafiles"""
        )
        ```
        
    === "CLI"
        ```
        ./normalization --data_files [train_data.txt,test_data.txt] --normalization_indices [0,2,4] --nb_attributes 16 --missing_values NaN --root_folder ../dimlp/datafiles
        ```

For rulefile denormalization :

!!!example

    === "Python"
        ```py
        from trainings import normalization

        normalization(
        """--normalization_file normalization_stats.txt
        --rule_files globalRules.rls
        --nb_attributes 16
        --root_folder dimlp/datafiles"""
        )
        ```
        
    === "CLI"
        ```
        ./normalization --normalization_file normalization_stats.txt --rule_files globalRules.rls --nb_attributes 16 --root_folder ../dimlp/datafiles
        ```

## Output interpretation

---

### [Normalized output data files](#data-output-files)

This file contains the normalized values of a dataset (taken from an original data file), where certain attributes have been adjusted based on a predefined mean (or median) and standard deviation (std). For attributes with defined mean and std values, normalization is applied using the formula: \( \text{normalized_value} = \frac{\text{(value - mean)}}{std} \)​. If no mean and std are defined for an attribute, its values remain unchanged during the normalization process. This normalization helps standardize data for more effective use in machine learning models.

---

### [Denormalized output rule files](#rule-output-files)

This file contains denormalized values for a set of rules (taken from an original rules file) based on predefined mean (or median) and standard deviation (std) values for certain attributes. For attributes with defined mean and std values, denormalization is applied using the formula: \( \text{denormalized_value} =(\text{normalized_value}×std)+\text{mean} \). Attributes without defined mean and std values will remain unchanged during the denormalization process. This procedure helps convert normalized rule thresholds back to their original scale, making the rules easier to interpret.

---

### [Normalization output file](#normalization-output-file)

This file stores the mean(or median) and standard deviation (std) values for specific attributes, which are used for normalization or denormalization purposes. Each line corresponds to an attribute, with the format:

    [attribute index] : original mean: [mean value], original std: [std value]

These mean(or median) and std values are applied during normalization to transform raw data into normalized values, and during denormalization to revert normalized values back to their original scale.

Attribute indices can be replaced with attribute names. In this case, an attribute file is required.