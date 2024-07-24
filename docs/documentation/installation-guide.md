# Installation guide

!!! warning
    **This section is under construction and should not be considered as accurate yet.**

Here you can find the steps to follow to install the `dimlpfidex` project on your machine. It can be achieved on `Windows`, `Linux`, and `macOS`. 

Before starting the installation process, ensure to have `python v3.9` or newer (**`3.11`** is recommended) installed on your machine. Please refer to the [Python official website](https://www.python.org/downloads/) for further information concerning the installation process. 

=== "Windows"
    ```sh
    python --version
    ```

=== "Linux"
    ```sh
    python3 --version
    ```

=== "macOS"
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

=== "macOS"
    ```sh
    pip --version
    ```

It should respond with an output similar to the example below:
```
pip 22.0.2 from /usr/lib/python3/dist-packages/pip (python 3.10)
```

!!!Warning
    The output of the above command must refer to, at least, a `python v3.x.x` version. 

Finally, run the following command to install `dimlpfidex`:

=== "Windows"
    ```sh
    python -m pip install dimlpfidex
    ```

=== "Linux"
    ```sh
    pip install dimlpfidex
    ```

=== "macOS"
    ```sh
    pip install dimlpfidex
    ```

To validate all the above steps, try to call one of the algorithms from the `dimlpfidex` package. To do so, import `Fidex` from `dimlpfidex` and call the `FidexGloRules` function inside your python interpreter:

```
>>> from dimlpfidex import fidex
>>> fidex.fidexGloRules()
```

Ensure you have the same output as below:
```
---------------------------------------------------------------------

Warning! The files are located with respect to the root folder dimlpfidex.
The arguments can be specified in the command or in a json configuration file with --json_config_file your_config_file.json.

----------------------------

Required parameters:

--train_data_file <str>       Path to the file containing the train portion of the dataset
--train_class_file <str>      Path to the file containing the train true classes of the dataset, not mandatory if classes are specified in train data file
--train_pred_file <str>       Path to the file containing predictions on the train portion of the dataset
--weights_file <str>          Path to the file containing the trained weights of the model (not mandatory if a rules file is given with --rules_file)
--rules_file <str>            Path to the file containing the trained rules to be converted to hyperlocus (not mandatory if a weights file is given with --weights_file)
--global_rules_outfile <str>  Path to the file where the output rule(s) will be stored. If a .json extension is given, rules are saved in JSON format
--heuristic <int [1,3]>       Heuristic 1: optimal fidexGlo, 2: fast fidexGlo 3: very fast fidexGlo. (Faster algorithms are less efficient)
--nb_attributes <int [1,inf[> Number of attributes in the dataset
--nb_classes <int [2,inf[>    Number of classes in the dataset

----------------------------

Optional parameters:

--json_config_file <str>      Path to the JSON file that configures all parameters. If used, this must be the sole argument and must specify the file's relative path
--root_folder <str>           Path to the folder, based on main default folder dimlpfidex, containing all used files and where generated files will be saved. If a file name is specified with another option, its path will be relative to this root folder
--attributes_file <str>       Path to the file containing the labels of attributes and classes
--console_file <str>          Path to the file where the terminal output will be redirected. If not specified, all output will be shown on your terminal
--max_iterations <int [1,inf[>
                              Maximum number of iterations, also the maximum possible number of antecedents in a rule, it should be 25 when working with images (default: 10)
--min_covering <int [1,inf[>  Minimum number of samples covered by the generated rules (default: 2)
--covering_strategy <bool>    Whether to use the covering strategy : if no rule is found with min_covering, find best rule with best covering using dichotomic search. Decreases min_fidelity if needed (default: True)
--max_failed_attempts <int [0,inf[>
                              Maximum number of failed attempts to find a Fidex rule when the covering is 1 and the covering strategy is used (default: 30)
--min_fidelity <float [0,1]>  Minimal rule fidelity accepted when generating a rule (default: 1.0)
--lowest_min_fidelity <float [0,1]>
                              Minimal min_fidelity to which we agree to go down during the covering_strategy (default: 0.75)
--dropout_dim <float [0,1]>   Probability of dropping a dimension during rule extraction (default: 0.0)
--dropout_hyp <float [0,1]>   Probability of dropping a hyperplane during rule extraction (default: 0.0)
--decision_threshold <float [0,1]>
                              The decision threshold used for predictions, you need to specify the index of the positive class if you want to use it
--positive_class_index <int [0,nb_classes-1]>
                              Index of the positive class for the usage of a decision threshold, index starts at 0
--nb_quant_levels <int [3,inf[>
                              Number of stairs in the staircase activation function (default: 50)
--normalization_file <str>    Path to the file containing the mean and standard deviation of some attributes. Used to denormalize the rules if specified
--mus <list<float ]-inf,inf[>>
                              Mean or median of each attribute index to be denormalized in the rules
--sigmas <list<float ]-inf,inf[>>
                              Standard deviation of each attribute index to be denormalized in the rules
--normalization_indices <list<int [0,nb_attributes-1]>>
                              Attribute indices to be denormalized in the rules, only used when no normalization_file is given, index starts at 0 (default: [0,...,nb_attributes-1])
--nb_threads <int [1,nb_cores]>
                              Number of threads used for computing the algorithm, 1=sequential execution (default: 1)
--seed <int [0,inf[>          Seed for random number generation, 0=random. Anything else than 0 is an arbitrary seed that can be reused to obtain the same randomly generated sequence and therefore getting same results (default: 0)

----------------------------

Execution example :

fidex.fidexGloRules("--train_data_file datanormTrain.txt --train_pred_file predTrain.out --train_class_file dataclass2Train.txt --weights_file weights.wts --nb_attributes 16 --nb_classes 2 --heuristic 1 --global_rules_outfile globalRules.rls --root_folder dimlp/datafiles")

---------------------------------------------------------------------
```

You are now set to use all `dimlpfidex` tools! You can continue to follow the [getting-started tutorial](getting-started.md) to learn more about how to use the different tools available.
