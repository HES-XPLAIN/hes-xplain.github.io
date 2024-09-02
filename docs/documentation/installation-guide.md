# Installation guide

## Prerequisites

Before starting the installation process, ensure to have `python 3.9` or newer (**`3.11`** is recommended) installed on your machine. Please refer to the [Python official website](https://www.python.org/downloads/) for further information concerning the installation process.

This can be achieved on `Windows`, `Linux`, and `macOS`.

```sh
python --version
```

The output of the command above should tell you what version is installed on your machine.

Then, check if you also have `pip` installed.
Note you might need to install `python3-pip` on some Linux distributions.

```sh
python -m pip --version
```

It should respond with an output similar to the example below:
```
pip 22.0.2 from /usr/lib/python3/dist-packages/pip (python 3.10)
```

You are now ready to continue with the desired installation guide below.


## Virtual environment

Create a virtual environment for your project and activate it.
Note you might need to install `python3-venv` on some Linux distributions.

=== "Windows"
    ```sh
    python3 -m venv .venv
    .venv/Scripts/activate
    ```

=== "Linux"
    ```sh
    python3 -m venv .venv
    source .venv/bin/activate
    ```

=== "macOS"
    ```sh
    python3 -m venv .venv
    source .venv/bin/activate
    ```


## MLxplain installation
Here you can find the only step to follow to install the `mlxplain` package on your machine.

Install the `mlxplain` package using `pip`:

```sh
python -m pip install mlxplain
```

Now, you should be ready to use the `mlxplain` library. You can continue to follow the [mlxplain examples](mlxplain/examples.md) to learn more about how to use this tool.

## Rules extraction installation
Here you can find the only step to follow to install the `rules-extraction` project on your machine.

Install the `rule-extraction` package using `pip`:

```sh
python -m pip install rules-extraction
```

Now, you should be ready to use the `rules-extraction` library. You can continue to follow the [rules extraction examples](rulesextraction/examples.md) to learn more about how to use this tool.

## Dimlpfidex installation

Here you can find the only step to follow to install the `dimlpfidex` project on your machine.


Install the `dimlpfidex` package using `pip`:

```sh
python -m pip install dimlpfidex
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
(...)
```

You are now set to use all `dimlpfidex` tools! You can continue to follow the [getting-started tutorial](dimlpfidex/getting-started.md) to learn more about how to use the different tools available.
