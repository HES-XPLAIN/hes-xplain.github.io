Here is how you can use our super cool platform


## Audience

HES-XPLAIN provides the essential tools and resources for data scientists, decision makers, engineers, or educators to effectively understand and apply XAI, and thus promoting greater transparency and trust in AI technologies.

The platform is specifically designed to meet the needs of different key users:


!!! info "You are ..."

    === "a decision maker"

        ![Decision maker](../assets/images/tie.svg){ width="200px", align=left }
        You want to **understand** the **relevance of XAI** for your business.

        - Get an overview of explainability opportunities
        - Get insights and visualizations that facilitate informed decision-making
        - Access resources and use case scenarios to guide XAI choices

    === "an engineer"

        ![Engineer](../assets/images/hammer-wrench.svg){ width="200px", align=left }
        You want to **try XAI algorithms**.

        Get access to exploratory use cases notebooks and datasets

        - Discover use cases as [Jupyter notebooks](../notebooks.md)
        - Get datasets, algorithms and Python code

    === "a data scientist"

        ![Data scientist](../assets/images/test-tube.svg){ width="200px", align=left }
        You want to **use XAI** algorithms along **your models**.

        Get access to algorithmes and API documentation.

        - Obtain Python PyPi packages
        - Get extensive API documentation

    === "a professor"

        ![Professor](../assets/images/school.svg){ width="200px", align=left }
        You want a tool to **facilitate teaching** of explainable AI.

        - Get access to tutorials and comprehensive guides.
        - Provide students with practical knowledge and hands-on experience in XAI methodologies

        - Deploy the platform on school IT infrastructure or public cloud
        - Adapt provided use cases to teaching needs


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
