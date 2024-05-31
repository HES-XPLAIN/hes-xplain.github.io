# Graphical User Interface

!!! warning
    **This section is under construction and should not be considered as accurate yet.**

The Dimlpfidex Graphical User Interface was made to help with **`JSON configuration files`**. All the `Fidex` and `Training methods` algorithms can be fed with these files to supply all the data needed to execute them. The problem is, you may not be experienced with `JSON` and `configuration files`. This is the reason why we offer you two outcomes: 

1. Learn by yourself with our [JSON configuration file documentation](file-formats/json-configuration-files.md).
2. Follow the next section to learn how to use the GUI, a tool made to ease your experience with **`JSON configuration files`**.

## Description
[JSON](https://www.json.org/json-en.html) or `JavaScript Object Notation` is a lightweight data interchange format that is easy for humans to read, and easy for machines to parse and generate. It is used to structure data in a way that is both human-readable and machine-friendly, making it an ideal choice for configuration files.

## Installation guide

To install the Dimlpfidex GUI, follow these steps:

!!! tip "Installation guide for..."

    === "Windows"
        1. **Download** the archive by opening your any browser and [downloading the latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
        2. **Decompress** the achive with any file archiver, place the folder where you can find it afterwards (Desktop, Documents, etc...).
        3. **Execute** the program by double-clicking on the `dimlpfidex_gui.exe` file.
        4. Done !

    === "Linux"
        1. **Download** the archive by opening your any browser and [downloading the latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
        2. **Decompress** the achive with any file archiver and place the folder where you can find it afterwards (Desktop, Documents, etc...).
        3. **Execute** the program with the `a.` or `b.` instruction: 
            1. By double-clicking on the `dimlpfidex_gui` file.
            2. By executing the following commands:
            ```sh
            # lets say you placed the folder inside /home/$USER/Documents/
            cd  /home/$USER/Documents/dimlpfidex_gui/
            ./dimlpfidex_gui
            ```
        4. Done !

    === "Web (OS agnostic)"
        1. **Download** the archive by opening your any browser and [downloading the latest release](https://github.com/HES-XPLAIN/dimlpfidex/releases/)
        2. **Decompress** the achive with any file archiver and place the folder where you can find it afterwards (Desktop, Documents, etc...).
        3. **Execute** the web app by...
            1. installing [node.js](https://www.nodejs.org) if needed.
            2. Running the following command:
            ```sh
            # lets say you placed the folder inside the Documents/ folder 
            cd /home/$USER/Documents/dimlpfidex_gui # (Linux based)
            dir %HOMEPATH%/dimlpfidex_gui # (Linux based)
            node app.js
        ```


2. **Clone the Repository**: Open your terminal and run the following command to clone the repository:
    ```bash
    git clone https://github.com/your-repo/dimlpfidex-gui.git
    ```

3. **Navigate to the Directory**: Change to the directory where the repository was cloned:
    ```bash
    cd dimlpfidex-gui
    ```

4. **Install Dependencies**: Install the required Python packages using pip:
    ```bash
    pip install -r requirements.txt
    ```

5. **Run the GUI**: Start the GUI by running the following command:
    ```bash
    python run_gui.py
    ```

6. **Access the GUI**: Open your web browser and navigate to `http://localhost:5000` to access the GUI.

## Usage guide
### Launching the GUI


### Features of the GUI

- **User-Friendly Forms**: The GUI provides forms with dropdowns, checkboxes, and text inputs to simplify the creation and editing of JSON files.
- **Validation**: The GUI includes validation checks to ensure that the JSON configuration files are correctly formatted.





