# Installation guide

!!! warning
    **This section is under construction and should not be considered as accurate yet.**

Here you can find the steps to follow to install the `Dimlpfidex` project on your machine. It can be archived on `Windows`, `Linux`, and `MacOS`. 

## Simple installation (recommended)
Ensure to have `python v3.8.1` or newer (**`3.11`** is recommended)` installed on your machine. Please refer to the [Python official website](https://www.python.org/downloads/) for further information concerning the installation process. 

=== "Windows"
    ```sh
    python --version
    ```

=== "Linux"
    ```sh
    python3 --version
    ```

=== "MacOS"
    ```sh
    python3 --version
    ```

The output of the command above should tell you what version is installed on your machine. Then, check if you also have `pip` installed.

=== "Windows"
    ```sh
    py -m pip --version
    ```

=== "Linux"
    ```sh
    pip --version
    ```

=== "MacOS"
    ```sh
    pip --version
    ```

It should answer with an output like the one below:
```
pip 22.0.2 from /usr/lib/python3/dist-packages/pip (python 3.10)
```

!!!Warning
    The output of the above command must refer to, at least, a `python v3.x.x` version. 

Finally, run the following command to install `Dimlpfidex`:

=== "Windows"
    ```sh
    py -m pip install dimlpfidex
    ```

=== "Linux"
    ```sh
    pip install dimlpfidex
    ```

=== "MacOS"
    ```sh
    pip install dimlpfidex
    ```

To validate all the above steps, try to call one of the algorithms from the `Dimlpfidex` package. To do so, import `Fidex` from `Dimlpfidex` and call the `FidexGloRules` function inside your python interpreter:

```
>>> from dimlpfidex import fidex
>>> fidex.fidexGloRules()
```

Ensure you have the same output like below:
```
---------------------------------------------------------------------

Warning! The files are localised with respect to root folder dimlpfidex.
The arguments can be specified in the command or in a json configuration file with --json_config_file your_config_file.json.

----------------------------

Required parameters:

--train_data_file <str>       Train data file
--train_pred_file <str>       Train prediction file
--train_class_file <str>      Train true class file, not mandatory if classes are specified in train data file
--weights_file <str>          Weights file (not mandatory if a rules file is given with --rules_file)
--rules_file <str>            Rules file to be converted to hyperlocus (not mandatory if a weights file is given with --weights_file)
--global_rules_outfile <str>  Rules output file. If a .json filename is given, rules are saved in a special json format>
--heuristic <int [1,3]>       Heuristic 1: optimal fidexGlo, 2: fast fidexGlo 3: very fast fidexGlo
--nb_attributes <int [1,inf[> Number of attributes in dataset
--nb_classes <int [2,inf[>    Number of classes in dataset

----------------------------

Optional parameters:

--json_config_file <str>      JSON file to configure all parameters. If used, this must be the sole argument and must specify the file's relative path
--root_folder <str>           Folder based on main folder dimlpfidex(default folder) containg all used files and where generated files will be saved. If a file name is specified with another option, his path will be configured with respect to this root folder
--attributes_file <str>       File of attributes
--console_file <str>          File with console logs redirection
--max_iterations <int [1,inf[>
                              Max iteration number, also the max possible number of attributs in a rule, should be 25 if working with images (default: 10)
--min_covering <int [1,inf[>  Minimum covering number (default: 2)
--covering_strategy <bool>    Whether to use this strategy : if no rule is found with min_covering, find best rule with best covering using dichotomic search. Decreases min_fidelity if needed (default: True)
--max_failed_attempts <int [0,inf[>
                              Maximum number of failed attempts to find Fidex rule when covering is 1 and covering strategy is used (default: 30)
--min_fidelity <float [0,1]>  Minimal rule fidelity accepted when generating a rule (default: 1.0)
--lowest_min_fidelity <float [0,1]>
                              Minimal min_fidelity to which we agree to go down during covering_strategy (default: 0.75)
--dropout_dim <float [0,1]>   Dimension dropout parameter (default: 0.0)
--dropout_hyp <float [0,1]>   Hyperplan dropout parameter (default: 0.0)
--nb_quant_levels <int [3,inf[>
                              Number of stairs in staircase activation function (default: 50)
--decision_threshold <float [0,1]>
                              Decision threshold for predictions, you need to specify the index of positive class if you want to use it
--positive_class_index <int [0,nb_classes-1]>
                              Index of positive class for the usage of decision threshold, index starts at 0
--normalization_file <str>    File containing the mean and std of some attributes. Used to denormalize the rules if specified
--mus <list<float ]inf,inf[>> Mean or median of each attribute index to denormalize in the rules
--sigmas <list<float ]inf,inf[>>
                              Standard deviation of each attribute index to denormalize in the rules
--normalization_indices <list<int [0,nb_attributes-1]>>
                              Attribute indices to denormalize in the rules, only used when no normalization_file is given, index starts at 0 (default: [0,...,nb_attributes-1])
--nb_threads <int [1,nb_cores]>
                              Number of threads used for computing the algorithm, 1=sequential execution (default: 1)
--seed <int [0,inf[>          Seed, 0=random (default: 0)

----------------------------

Execution example :

fidex.fidexGloRules("--train_data_file datanormTrain.txt --train_pred_file predTrain.out --train_class_file dataclass2Train.txt --weights_file weights.wts --nb_attributes 16 --nb_classes 2 --heuristic 1 --global_rules_outfile globalRules.rls --root_folder dimlp/datafiles")

---------------------------------------------------------------------
```

You are now set to use all `Dimlpfidex` tools! You can continue by following the [getting-started tutorial](../getting-started) to learn more about how to use the different tools available.

## Installation by compiling sources (alternative)
To install `Dimlpfidex` by compiling sources yourself, please follow the instructions inside the [repository's README](https://github.com/HES-XPLAIN/dimlpfidex/blob/main/README.md#contribution), under the `contribution` section.