# :material-notebook: Use cases notebooks

Welcome to the interactive notebooks section, dedicated to showcase Explainable Artificial Intelligence (XAI) techniques in various use cases.

These notebooks aim to make XAI more approachable by providing practical examples and explanations.
We have curated a diverse range of notebooks for audiences with varying levels of expertise.

Explore our collection of notebooks to understand how AI models make decisions, interpret their outputs, and gain insights into their predictions.

## Interactive sessions

Whether you prefer the convenience of launching an online interactive session or the flexibility of a local session,
we provide you with the necessary tools. Simply choose between launching an **online session** in **Google Colab**
or setting up a **local session** with our provided **Docker Compose files**.

**Note:** A **Google account** is required to access Google Colab free of charge.

??? tip ":simple-googlecolab: Online session: How to launch Google Colab"

    * Click on the provided link to open the notebook in your browser.
    * In the upper right corner of the editor, click on the downward arrow right of the **Connect** and then **Change runtime type**.
    * Select **T4 GPU** to make use of GPU accelleration, then **Save**.
    * Click on **Connect**.

When you are done, the environment will be shutdown after 30 minutes of inactivity. You can also shut it down
manually by clicking on **Runtime** menu then by selecting **Disconnect and delete runtime**.

??? tip ":octicons-desktop-download-24: Local session: How to install Docker Desktop"

    The provided Docker Compose files allow you to easily launch Jupyter notebooks and embedded data locally, giving you
    convenient access to the notebook content and data.

    You only need to install [Docker Desktop](https://www.docker.com/) and then download the Docker Compose file.

    * Go to the [Docker website](https://www.docker.com/)
    * Download the appropriate Docker Desktop version for your operating system (:simple-windows11: :simple-apple: :simple-linux:).
    * Open a terminal or command prompt and run `docker version` to verify the installation.
    * Ensure Docker Desktop is running.
    * Download the Docker Compose files on this page and launch them with `docker compose up -f path/to/docker-compose.yml`.


## Use Case : Sport Image Classification 

Through this use case, we aim to to show how to use XAI techniques and methods to create an explainable model to classify images from the Sports Image Classification dataset. We also builds post-hoc explanations to explain the model and its prediction. 

!!! example "Sport Image Classification"

    ![Sports Image](assets/images/examples/sports_classification.jpg){ width="200px", align=left }

    **Sports Image Classification**

    * :simple-googlecolab: **Online**: <a href="https://colab.research.google.com/github/HES-XPLAIN/notebooks/blob/main/use_case_sport_classification/use_case_sport_image_classification.ipynb" target="_blank">XAI for Sport Image Classification</a>
    * :octicons-desktop-download-24: **Local**: <a href="https://raw.githubusercontent.com/HES-XPLAIN/notebooks/main/docker-compose.yml" target="_blank">Docker Compose file</a> **(Right click, "Save link as")**

https://github.com/HES-XPLAIN/notebooks/blob/main/use_case_sport_classification/use_case_sport_image_classification.ipynb

    **Important**: To run the notebook on Google Colab, ensure to change the variable `use_colab` in the first cell to **True**.

## Use Case : Complex Images

WIP

## Use Case : Tabular Dataset

WIP

