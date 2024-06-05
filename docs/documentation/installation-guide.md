# Installation guide

!!! warning
    **This section is under construction and should not be considered as accurate yet.**

Here you can find the steps to follow to install the `Dimlpfidex` project on your machine. It can be archived on `Windows`, `Linux`, and `MacOS`. 

## Prerequisites
You should have the following resources to use `Dimlpfidex`:



### Simple installation (recommended)
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




### Installation by compiling sources (alternative)
To install `Dimlpfidex` by compiling sources yourself, please follow the instructions inside the [repository's README](https://github.com/HES-XPLAIN/dimlpfidex/blob/main/README.md#contribution), under the `contribution` section.