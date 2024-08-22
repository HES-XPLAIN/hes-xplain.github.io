# Execution Files

!!! warning
    **This section is under construction and should not be considered as accurate yet.**

Execution files are all the files that can or must be inputed to our `dimlpfidex` algorithms. It is important that each file is written with the correct format for the algorithms to run properly.

!!!example

    === "CLI"
        Executing [`Fidex`](../dimlpfidex/fidex/fidex.md) `CLI` command without configuration file:
        ```
        ./fidex --root_folder my/folder/ --train_data_file train_data.txt --train_pred_file train_predictions.out --train_class_file train_classes.txt --test_data_file test_data.txt --nb_attributes 16 --nb_classes 2 --weights_file weights.wts --rules_outfile output_rules.rls --stats_file output_stats.txt
        ```

        Executing [`Fidex`](../dimlpfidex/fidex/fidex.md) with [this configuration](#example) file
        ```
        ./fidex --json_config_file my_conf.json
        ```
    
    === "Python"

        Executing [`Fidex`](../dimlpfidex/fidex/fidex.md) `Python` command without configuration file:

        ```py

        from dimlpfidex.fidex import fidex

        fidex(
        """--root_folder my/folder/ 
            --train_data_file train_data.txt 
            --train_pred_file train_predictions.out 
            --train_class_file train_classes.txt 
            --test_data_file test_data.txt 
            --nb_attributes 16 
            --nb_classes 2 
            --weights_file weights.wts 
            --rules_outfile output_rules.rls 
            --stats_file output_stats.txt"""
        )
        ```

        Executing [`Fidex`](../dimlpfidex/fidex/fidex.md) with [this configuration](#example) file
        ```py
        from dimlpfidex.fidex import fidex
        fidex("""--json_config_file my_conf.json""")
        ```


If you are not used to JSON, you can:

-  learn more about JSON [here](https://json.org) and try it by yourself.
-   use our [graphical user interface](../dimlpfidex/gui.md) and generate your configuration file easily.

## Example

Here is a simple example of the content of a configuration file named `my_conf.json`, this one respects the comparison above.

```json
{
    "root_folder": "my/folder/",
    "train_data_file": "train_data.txt",
    "train_pred_file": "train_predictions.out", 
    "train_class_file": "train_classes.txt ",
    "test_data_file": "test_data.txt ",
    "nb_attributes": 16,
    "nb_classes": 2,
    "weights_file": "weights.wts ",
    "rules_outfile": "output_rules.rls",
    "stats_file": "output_stats.txt"
}
```

!!!Tip
    You can find configuration file templates for every `dimlpfidex` algorithm [here](https://github.com/HES-XPLAIN/dimlpfidex/tree/main/templates).
