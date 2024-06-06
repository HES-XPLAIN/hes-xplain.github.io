# Graphical User Interface

!!! warning
    **This section is under construction and should not be considered as accurate yet.**

The Dimlpfidex Graphical User Interface was made to help with **`JSON configuration files`**. All [Dimlpfidex](https://github.com/HES-XPLAIN/dimlpfidex) algorithms can be fed with these files to supply all the data needed to execute them. The problem is, you may not be experienced with `JSON` and `configuration files`. This is the reason why we offer you two outcomes: 

1. Learn by yourself now to write configuration files with our [JSON configuration file documentation](file-formats/json-configuration-files.md).
2. Follow the next section to learn how to use this GUI.

## Installation guide

To install the Dimlpfidex GUI, follow these steps:

=== "Windows"
    1. **Download** the [latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
    2. **Decompress** the archive.
    3. **Execute** the program named `dimlpfidex_gui.exe`.
    4. Done!

=== "Linux"
    1. **Download** the [latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
    2. **Decompress** the archive.
    3. **Execute** the program named `dimlpfidex_gui`.
    4. Done!

=== "Web (OS agnostic)"
    1. **Download** the [latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
    2. **Decompress** the archive.
    3. **Execute** the web app by installing [node.js](https://www.nodejs.org) if needed and Running the following commands:
        ``` title="Linux"
        cd PATH/TO/dimlpfidex
        node app.js
        ```
        ``` title="Windows"
        dir PATH\TO\dimlpfidex
        node app.js
        ```
    4. Open your browser and search for `localhost:8000`
    5. Done!

## Usage guide

To use the GUI, start by opening the app, select the form corresponding to the algorithm you want to use, fill out the form, and generate it by clicking on the button at the bottom of the form. 

### Features of the GUI

- **User-Friendly Forms**: The GUI provides forms with dropdowns, checkboxes, and text inputs to simplify the creation and editing of JSON files.
- **Validation**: The GUI includes validation checks to ensure that the JSON configuration files are correctly formatted.
- **Large palette**: It can generate a configuration file for every algorithm from `Fidex`, `DIMLP`, and `Training methods` ensembles.
- **Embedded documentation**: Has descriptions for every form's component and has a glossary explaining every single field purpose. 

### Field's anatomy

<center><img src="../../assets/images/gui/gui_fieldanatomy.png" width="75%"/></center>
<center><i>Field anatomy</i></center>

1. **Field name**: Indicates the name or label of the field.
2. **File Explorer button**: Allows users to browse and select a file (available for path-related fields, **excluding the web version**).
3. **Default button**: Clicking on this button, if colored, automatically adds a default value to the field.
4. **Information icon**: When hovered over with the mouse, it describes the field.
5. **Required icon**: If colored, indicates that the field must be filled out and cannot be left empty.

!!!Warning
    The web application cannot use the file browsing feature because of technical limitations.

### Field types
<center><img src="../../assets/images/gui/gui_fieldnumeric.png" width="75%"/></center>
<center><i>Example of numeric field</i></center>

<center><img src="../../assets/images/gui/gui_fieldfilepath.png" width="75%"/></center>
<center><i>Example of file path field</i></center>

List of data types handled:

- `integers`
- `Double precision numbers`
- `Strings`
- `Restricted choice strings`
- `File paths`
- `Booleans`
- `Directory paths`
- `Dictionaries`
- `List of strings`
- `List of integers`
- `List of file paths`
- `List of double precision numbers`