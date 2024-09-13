# DimlpFidex Graphical User Interface

The dimlpfidex Graphical User Interface was made to help with **`JSON configuration files`**. All [dimlpfidex](https://github.com/HES-XPLAIN/dimlpfidex) algorithms can be fed with these files to supply all the data needed to execute them. However, you may not be experienced with `JSON` and `configuration files`. This is the reason why we offer you two outcomes: 

1. Learn by yourself how to write configuration files with our [JSON configuration file documentation](../file-formats/json-configuration-files.md).
2. Follow the next section to learn how to generate configuration files with this GUI.


<center><img src="/assets/images/gui/gui_mainpage.png" style="border-radius:15px" width="80%"/></center>
<center><i>Welcome page</i></center>

## Installation guide

To install the dimlpfidex GUI, follow these steps:

=== "Windows"
    1. **Download** the [latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
    2. **Decompress** the archive.
    3. **Execute** the program named `dimlpfidex_gui.exe`.
    4. Done!

=== "Linux & macOS"
    1. **Download** the [latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
    2. **Decompress** the archive.
    3. **Execute** the program named `dimlpfidex_gui`.
    4. Done!

=== "Web (OS agnostic)"
    1. **Download** the [latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
    2. **Decompress** the archive.
    3. **Execute** the web app by installing [node.js](https://www.nodejs.org) if needed and Running the following commands:
        ``` title="Linux"
        cd PATH/TO/GUI-SOURCES/
        npm install express
        node app.js
        ```
        ``` title="Windows"
        dir PATH\TO\GUI-SOURCES\
        npm install express
        node app.js
        ```
    4. Open your browser and search for `localhost:8000`
    5. Done!

## Usage guide

To quickly learn how to use the GUI for generating configuration files, you can explore our [notebook](../../notebooks.md#generate-dimlpfidex-json-configuration-files-with-the-gui) for a step-by-step guide.

To get started with the GUI, open the app, choose the form corresponding to the algorithm you want to use, fill it out, and generate the configuration file by clicking the button at the bottom of the form.

### Features of the GUI

- **User-Friendly Forms**: The GUI provides forms with dropdowns, checkboxes, and text inputs to simplify the creation and editing of JSON files.
- **Validation**: The GUI includes validation checks to ensure that the JSON configuration files and its embedded informations are correctly formatted.
- **Large palette**: It can generate a configuration file for every algorithm from `Fidex`, `DIMLP`, and `Training methods` ensembles.
- **Embedded documentation**: Has descriptions for every form's component and has a glossary explaining every single field purpose. 

<center><img src="/assets/images/gui/gui_formexample.png" style="border-radius:15px" width="80%"/></center>
<center><i>Example of form</i></center>

### Field's anatomy
The GUI forms are composed of multiple fields, some are more complex than others. Here is an example of a field 'anatomy':

<center><img src="/assets/images/gui/gui_fieldanatomy.png" style="border-radius:15px"/></center>
<center><i>Field anatomy</i></center>

!!!info
    Some numeric fields can have the upper bound `inf`, meaning infinity (which is not really infinite but it idicates that there is no fixed upper bound)

1. **Current Field Datatype Selector**: Some fields are dynamic and can accept various types of input. This selector allows you to switch between different types, and it is currently active.  
2. **Unselected Field Datatype Selector**: This selector is inactive but can be clicked to switch to a different field type.
3. **Lower Bound of a Numeric Field**: In this example, a numeric field is displayed with a lower limit, preventing values from being set below this boundary.
4. **Field Name**: Displays the `[datatype]` and the label of the field.
5. **Upper Bound of a Numeric Field**: Similar to item #3, this field has an upper limit, preventing values from exceeding this boundary.
6. **Default Button**: Clicking this button (when highlighted) automatically applies a default value to the field.
7. **Information Icon**: When hovered over, this icon provides a description of the field.
8. **Required Icon**: If highlighted, it indicates that the field is mandatory and cannot be left empty. 

!!!Warning
    The web application cannot use the file browsing feature because of technical limitations.

### Field types

The GUI is currently able to handle several types of data, including:

`integers` (numbers without fractional part)

<center><img src="/assets/images/gui/gui_fieldnumeric.png" style="border-radius:15px" width="90%"/></center>
<center><i>Example of numeric field</i></center>

`double precision numbers` (numbers with fractional part)

`Strings` (sequence of characters)

`Restricted choices` (pre-defined keywords to select)

<center><img src="/assets/images/gui/gui_restrictedchoicefield.png" style="border-radius:15px" width="90%"/></center>
<center><i>Example of restricted choices</i></center>

`File paths` (paths present in your system leading to a chosen file)

<center><img src="/assets/images/gui/gui_fieldfilepath.png" style="border-radius:15px" width="90%"/></center>
<center><i>Example of file path field</i></center>

`Booleans` (yes or no answers)

`Directory paths` (paths present in your system leading to a chosen directory)

`Dictionaries` (key-pair collection)

`List of strings`

`List of integers`

`List of file paths`

`List of double precision numbers`
