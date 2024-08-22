Here is how you can use our super cool platform



## Easy-to-use platform

Artificial intelligence (AI) is increasingly integrated into essential sectors like healthcare, finance, and legal systems. However, users ooften rely on AI-generated decisions without fully understanding the underlying mechanisms and reasoning, which can lead to trust issues. This concern is particularly acute when decisions carry significant consequences.

eXplainable Artificial Intelligence (XAI) seeks to enhance the clarity and trustworthiness of AI decisions by elucidating the logic behind predictions. Despite advancements in this field, many existing XAI tools remain complex and challenging to use.

Our platform aims to address this challenge by making XAI more accessible to all users. We provide an intuitive, open-source environment that consolidates various XAI techniques helping users to better understand and apply AI insights effectively.


## Using notebooks

**How to use interactive sessions with notebooks**

You can launch notebooks conveniently in an online interactive session, or if you prefer the flexibility of a local session we provid you with the necessary tools.

Simply choose between launching an **online session** in **Google Colab**
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


## Deployment Options

HES-XPLAIN provides flexible deployment options to suit different user needs:

- **Google Colab**: Online deployment through Google Colab for easy access and experimentation with our algorithms, tutorials, and use cases.
- **Container**: Local deployment using Docker files to easily try our solutions locally.
- **Private Deployment Platform**: Private deployement to ensure privacy within the HES-XPAIN platform


The container registry contains assets that facilitate deployment, including:

- **Notebook Server Package**: A pre-configured environment to run Jupyter notebooks.
- **Docker Image**: Containerized versions of our platform components for easy deployment on local machines or cloud environments.


For advanced users and enterprises, we offer a private deployment platform that supports:

- **Private Datasets**: Securely manage and use private datasets within the HES-XPLAIN platform.
- **Deployment Flexibility**: Deploy our solutions within private infrastructures using Kubernetes or other orchestration tools.