# Execution Files

!!! warning
    **This section is under construction and should not be considered as accurate yet.**

Execution files refer to all the files that can or must be input to our dimlpfidex algorithms. It is essential that each file follows the correct format to ensure the algorithms run properly. Let's detail the format of each input file.

## Files format

---

### Data files

These files contain the data for training, testing, or validation datasets, and may also include class labels. Each file should have one sample per line, with values separated by spaces, tabs, semicolons, or commas. The following formats are supported:

1. `Only attributes`: Each line contains only the attribute values as floats for one sample.
2. `Attributes followed by an integer class ID`: Each line contains attribute values as floats for one sample, followed by an integer representing the class label.
3. `Attributes followed by a one-hot encoded class`: Each line contains attribute values as floats for one sample, followed by a series of binary values (`0`s and `1`s) representing the class in a one-hot encoded format where the correct class is represented by `1` and the other classes by `0`.

Here is an example for a dataset of 3 samples with 3 attributes and 2 classes, using one-hot encoding :

!!!example

    ```text
    0.5 0.3 0.8 0 1
    0.2 0.7 0.4 1 0
    1.1 0.5 0.2 1 0
    ```

<p style="font-size:larger;">Special Format for Test Data Files (Fidex and FidexGlo):</p>

In the case of [Fidex](../dimlpfidex/fidex/fidex.md) and [FidexGlo](../dimlpfidex/fidex/fidexglo.md), the test data files can also include prediction values. The format for each sample in these files will be as follows:

- First Line: Contains data attributes as floats. It may be followed by class information (either as an integer class ID or in one-hot encoded format).
- Second Line: Contains the prediction values for each class.
- Third Line (optional): Contains class information, only if it was not included in the first line and if present.
- Empty Line: Needs to have an empty line between each sample.

Example of 2 test samples with 3 attributes and 2 classes:

!!!example

    ```text
    0.5 0.3 0.8
    0.3 0.7
    0 1

    0.72 0.12 0.14
    0.6 0.4
    1 0
    ```

---

### Class Files

These files should contain the class label of one sample per line, with values separated by spaces, tabs, semicolons, or commas. The following formats are supported:

1. `Integer class ID`: Each line contains a single integer representing the class label for the corresponding sample.
2. `One-hot encoded class`: Each line contains a series of binary values (`0`s and `1`s) representing the class in a one-hot encoded format, where the correct class is `1` and the others are `0`.

Here is an example for a dataset of 3 samples with 2 classes, using class labels:
These files should contain one line per data sample, each consisting of a series of numerical values ranged between `0` and `1` representing the model's prediction scores for each class.
!!!example

    ```text
    0
    0
    1
    ```

And here is the same example with one-hot encoding:

!!!example

    ```text
    1 0
    1 0
    0 1
    ```

---

### Prediction files

These files should contain one line per data sample, each consisting of a series of numerical values ranged between `0` and `1` representing the model's prediction scores for each class. The sum of the scores in each line should equal 1. The values can be separated by spaces, tabs, semicolons, or commas.

Here is an example for a dataset with 3 samples and 2 classes:

!!!example

    ```text
    0.25 0.75
    0.80 0.20
    0.60 0.40
    ```

---

### Weights file

This file must contain the weights and biases between successive layers of neurons of one neural network trained beforehand. If the model is [DimlpBT](../dimlpfidex/dimlp/dimlpbt.md), the file can contain more than one network. In this case, each network is separated by a `Network <id>` marker. For each network :

- **Odd rows** in the file represent the **bias values** of neurons related to the next layer l~i+1~. There is one bias value for each neuron in that layer.
- **Even rows** represent the values of the **weight matrix** between the current layer l~i~ and the next layer l~i+1~.

If layer l~i~ has *m* neurons and layer l~i+1~ has *n* neurons, the weights are represented as a single row in the file in the following format:

    w_11 w_21 w_31 ... w_m1  w_12 w_22 w_32 ... w_m2  ...  w_1n w_2n w_3n ... w_mn

Where w~ij~ is the weight connecting the i^th^ neuron in layer l~i~ to the j^th^ neuron in layer l~i+1~. The values need to be separated by spaces.

For [Fidex](../dimlpfidex/fidex/overview.md) algorithms, the file can contain only the weights and bias of the first layer as the rest is ignored.

Here is an example with 2 networks:

!!!example

    ```text
    Network 1
    0.1 0.2 0.3
    0.4 0.5 0.6 0.7 0.8 0.9
    0.15 0.25
    0.35 0.45 0.55 0.65
    Network 2
    0.11 0.22 0.33
    0.44 0.55 0.66 0.77 0.88 0.99
    0.155 0.255
    0.355 0.455 0.555 0.655
    ```
---

### Hidden layers file

This file must contain the configuration of the neural network, specifying the number of neurons in each layer. Each row corresponds to a layer in the network.

- The first number indicates the layer number.
- The second number indicates the number of neurons in that layer.
- The two numbers need to be separated by a space.

Example:

    1 16
    2 5

In this example the first layer has 16 neurons and the second has 5.

---

### Attributes file

Thsi file must contain the names of all the attributes from the dataset, followed optionally by the names of the classes. The format is simple and must be followed precisely:

- `One attribute per line`: Each line corresponds to the name of a single attribute.
- `Optional class names`: If you choose to include class names, they should follow after all attributes, with one class name per line.
- `No spaces in names`: Attribute and class names can't contain spaces.

It is important to ensure that all attributes are specified. If class names are included, all classes must also be listed. The order is important as the first attribute/class name will represent the first attribute/class in the dataset. Here is an example for a dataset containing 3 attributes and 2 classes :

!!!example

    ```py
    Attribute1
    Attribute2
    Attribute3
    Class1
    Class2
    ```

---

### Normalization file

This file must contain the mean(or median) and standard deviation (std) values for specific attributes, which are used for normalization or denormalization purposes. Each line corresponds to an attribute, with the format:

    [attribute index/attribute name] : original [mean/median]: [mean value], original std: [std value]

These mean(or median) and std values are applied during normalization to transform raw data into normalized values, and during denormalization to revert normalized values back to their original scale.

Attribute indices can be replaced with attribute names. In this case, an attribute file is required.

Here is an example with some attribute names and using median :

!!!example

    ```text
    Attribute1 : original median: 12.5, original std: 0.53
    Attribute3 : original median: 46.9, original std: 1.53
    Attribute7 : original median: 30.2, original std: 10.3
    ```

---

### Rules file

<p style="font-size:larger;">When launching a Fidex algorithm</p>

This file must contain the decision rules generated by the [Random Forest](../dimlpfidex/training-methods/randforeststrn.md) model or the [Gradient Boosting](../dimlpfidex/training-methods/gradboosttrn.md) model. Each rule corresponds to a specific decision path within a tree, leading to a prediction for a particular class. These rules are used to identify the discriminant hyperplanes in the feature space during the [Fidex](../dimlpfidex/fidex/overview.md) algorithm. Here is an example of a file generated by a `Gradient Boosting` and containing 2 trees :

!!!example

    ```text
    -------------------
    Tree 1
    -------------------
    Rule 1: X15<=0.31187500059604645 X1<=0.5 X13<=0.5 -> value [2.59270259]
    Rule 2: X15<=0.31187500059604645 X1<=0.5 X13>0.5 -> value [0.86412944]
    -------------------
    Tree 2
    -------------------
    Rule 1: X4<=0.5 X9<=0.030500000342726707 X3<=0.573076993227005 -> value [0.16391411]
    Rule 2: X4<=0.5 X9<=0.030500000342726707 X3>0.573076993227005 -> value [-1.52554885]
    ```

Each tree is separated like this and contain some rules. The format of `Gradient Boosting` rules is :

    Rule [id_rule]: [list of antecedants[Xi]{<= OR >}value] -> value [pred_value]

And the format of `Random Forest` rules is :

    Rule [id_rule]: [list of antecedants[Xi]{<= OR >}value] -> class [class_id] Covering: {[1, 0] OR [0,1]}

    - **Rule files**: Contain rules in Dimlp or Fidex format. Formats:\n
      Dimlp: 'Rule 1: (x2 > 0.785787) (x5 > 0.591247) (x8 < 0.443135) Class = 1 (187)'\n
      Fidex: 'X1>=0.414584 X10<0.507982 X5>=0.314835 X6>=0.356158 -> class 0'\n

<p style="font-size:larger;">When denormalizing rules</p>

This file must contain [Fidex](../dimlpfidex/fidex/overview.md) rules or [Dimlp](../dimlpfidex/dimlp/overview.md) rules. These rules are meant to be denormalized in order to get more interpretable results. The rules in the file need to be in one of these formats :

!!!example

    ```text
    Fidex :
        Rule [id_rule]: [list of antecedants[{Xi OR attribute_name}{>= OR <}value]] -> {class [id_class] OR class_name}
        Ex : Rule 1: X1>=0.508498 X0>=0.603383 X7<0.463138 -> class 0
    Dimlp :
        Rule [id_rule]: [list of antecedants[{xi OR attribute_name} {> OR <} value]] Class = [id_class] OR class_name ([covering])
        Ex : Rule 1: (x1 > 0.653808) (x2 > 0.92407) (x8 < 0.44302) Class = 1 (211)
    ```

Note : JSON rule files are not supported for denormalization.

---

### Global rules file

The global rules file is generated by [fidexGloRules](../dimlpfidex/fidex/fidexglorules.md) and can by in a text or a JSON format. Here are the 2 formats explained :

=== "Text file"

    This file must contain all the computed global rules. It begins with global statistics about the ruleset, followed by individual rules, ordered by their covering size, and their associated performance metrics. Here is the beginning of such a file :

        Number of rules : 57, mean sample covering number per rule : 46.140351, mean number of antecedents per rule : 2.754386
        No decision threshold is used.

        Rule 1: X1>=0.508498 X0>=0.603383 X7<0.463138 -> class 0
        Train Covering size : 187
        Train Fidelity : 1
        Train Accuracy : 0.935829
        Train Confidence : 0.954832

        Rule 2: X14>=0.196762 X1>=0.975078 -> class 0
        Train Covering size : 180
        Train Fidelity : 1
        Train Accuracy : 0.9
        Train Confidence : 0.934414

    The file must follow this format. Let's specify explicitely the format of each line :

    First line :

        Number of rules : [nb_rules], mean sample covering number per rule : [mean_covering], mean number of antecedents per rule : [mean_antecedant]

    Second line :

        {No decision threshold is used. OR Using a decision threshold of [threshold] for class [positive_class_index]}

    Then, each rule is separated by an empty line and ranked by covering size with increasing rule id starting with 1. A rule is in this format :

        Rule [id_rule]: [list of antecedants[{Xi OR attribute_name}{>= OR <}value]] -> {class [id_class] OR class_name}
        Train Covering size : [covering_size]
        Train Fidelity : [fidelity]
        Train Accuracy : [accuracy]
        Train Confidence : [confidence]

    Attributes and classes can be specified either by their name (in this case an attributes file must be given) or by their id.

=== "JSON file"

    This file must contain all the computed global rules. It begins with an indication whether a decision threshold was used for prediction and specifies the threshold if applicable. It then follows with each individual rule and its associated performance metrics, ordered by their covering size. The file must be in this format (here we have 2 rules in the file) :
    
!!!example

    ```text
    {
        "positive index class": -1,
        "rules": [
            {
                "accuracy": 1.0,
                "antecedents": [
                    {
                        "attribute": 8,
                        "inequality": false,
                        "value": 0.07228972839342673
                    },
                    {
                        "attribute": 3,
                        "inequality": true,
                        "value": 0.6969069765088105
                    }
                ],
                "confidence": 0.991161,
                "coveredSamples": [
                    67,
                    213,
                    567
                ],
                "coveringSize": 3,
                "fidelity": 1.0,
                "outputClass": 1
            },
            {
                "accuracy": 1.0,
                "antecedents": [
                    {
                        "attribute": 8,
                        "inequality": false,
                        "value": 0.07228972839342673
                    },
                    {
                        "attribute": 3,
                        "inequality": true,
                        "value": 0.6969069765088105
                    }
                ],
                "confidence": 0.991161,
                "coveredSamples": [
                    67,
                    213,
                    567
                ],
                "coveringSize": 3,
                "fidelity": 1.0,
                "outputClass": 1
            }
        ],
        "threshold": -1.0
    }
    ```

    Note : A `true` inequality represents `>=`, while a `false` inequality represents `<`. If threshold and positive_class_index have value -1, there was no threshold used for the generation of the rules.