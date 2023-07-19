# :material-notebook: Use cases notebooks

Welcome to the interactive notebooks section, dedicated to showcase Explainable Artificial Intelligence (XAI) techniques in various use cases.

These notebooks aim to make XAI more approachable by providing practical examples and explanations.
We have curated a diverse range of notebooks for audiences with varying levels of expertise.

Explore our collection of notebooks to understand how AI models make decisions, interpret their outputs, and gain insights into their predictions.

## Interactive sessions

Whether you prefer the convenience of launching an online interactive session or the flexibility of a local session,
we provide you with the necessary tools. Simply choose between launching an **online session** in **GitHub Codespaces**
or setting up a **local session** with our provided **Docker Compose files**.

??? tip ":octicons-codespaces-24: Online session: How to launch GitHub Codespace"

    !!! note "A **GitHub account** is required to access GitHub Codespace"

        Codespace is free up to 120h/CPU per month with a free account.

    * Click on the provided link to open an embedded :simple-visualstudiocode: **VSCode** editor in your browser.
    * In the upper right corner of the editor, click on **Select Kernel** and then **Connect to Codespace**.
    * Choose a machine configuration (2 or 4 cores) on the Codespace dropdown menu.
    * Wait for the session to load.
    * You are ready to start working with the interactive Jupyter notebook.

??? tip ":octicons-desktop-download-24: Local session: How to install Docker Desktop"

    The provided Docker Compose files allow you to easily launch Jupyter notebooks and embedded data locally, giving you
    convenient access to the notebook content and data.

    You only need to install [Docker Desktop](https://www.docker.com/) and then download the Docker Compose file.

    * Go to the [Docker website](https://www.docker.com/)
    * Download the appropriate Docker Desktop version for your operating system (:simple-windows11: :simple-apple: :simple-linux:).
    * Open a terminal or command prompt and run `docker version` to verify the installation.
    * Download the Docker Compose files on this page and launch them with `docker compose up`.


## Sport Image Classification

Through this use case, we aim to empower users to grasp the potential of CAM as a tool for transparent and interpretable sport image classification.

!!! example "Sport Image Classification with Class Activation Maps (CAM)"

    ![CAM](assets/images/examples/CAM.png){ width="200px", align=left }

    **Class Activation Maps (CAM)**

    * :octicons-codespaces-24: **Online**: [Exploring Class Activation Maps for Sport Image Classification](https://github.dev/HES-XPLAIN/notebooks/blob/main/use_case_sport_classification/sport_image_classification.ipynb)
    * :octicons-desktop-download-24: **Local**: [Docker Compose file](https://raw.githubusercontent.com/HES-XPLAIN/notebooks/main/docker-compose.yml)

    In this use case, we dive into sport image classification and showcase the power of **Class Activation Maps** (CAM) as an
    interpretability tool.

    CAM allows us to visualize the regions of an image that contribute most to the model's classification decision.
    By overlaying **heatmaps** onto the original images, we gain insights into the model's attention and its understanding of different sports.

While focusing on a specific image classification task using a pre-trained model,  our goal is to demonstrate how XAI empowers users to explore and interpret image classifiers effectively.

By the end of this use case, you will have a solid understanding of CAM and how to integrate it into your own sport image classification projects.