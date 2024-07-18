# Platform Overview

Our platform brings together a comprehensive suite of tools and resources to help users understand, apply, and compare different XAI techniques. Whether you are a data scientist, decision maker, engineer, or educator, HES-XPLAIN provides the necessary tools to make AI more transparent and trustworthy.

## Components of HES-XPLAIN

### Source Code Repository

Our source code repository hosts all the necessary assets, including:

- **Source Code**: The core algorithms and functionalities developed for XAI.
- **Notebooks**: Interactive Jupyter notebooks that demonstrate how to use our XAI algorithms.
- **Docs**: Comprehensive documentation that guides users on how to utilize the platform effectively.


![Platform Overview](../assets/images/platform_architecture_new.png)


### Algorithms

HES-XPLAIN assembles our own developed algorithms as well as incorporating all algorithms proposed by [OmniXAI](https://github.com/salesforce/omnixai). Our platform provides a comprehensive suite of tools for XAI, enabling users to compare and choose the best techniques for their needs. Explore our algorithms in the [HES-XPLAIN - Algorithms](../algos/) section.

Our algorithms are individually packaged and accessible through the Python Package Index (PyPi), making it easy for users to install and use them in their own projects.


### Deployment Options

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


### Ressource and Tutorials 

We offer multiple resources to enhance XAI knowledge, all accessible from our website including:

- **XAI Resource**: Literature and resources that describe what/why/how Explainable Artificial Intelligence.
- **Tutorial Notebooks**: Step-by-step guides to help users understand and apply XAI methods.
- **Use Case Notebooks**: Showcase how XAI and our platform can be used to solve real-world problems.
- **Datasets and Models**: Embedded datasets and pre-trained models to facilitate experimentation.

More details can be found in the [HES-XPLAIN - Resources](../ressource.md) section.

## Audience

HES-XPLAIN is designed to cater to a diverse audience, including:


!!! info "You are ..."

    === "a decision maker"

        ![Decision maker](../assets/images/tie.svg){ width="200px", align=left }
        # You are interested in business **benefits, risks and costs**.

        - Get an [introduction](../introduction.md) to explainability
        - Access web demos and use case scenarios

    === "an engineer"

        ![Engineer](../assets/images/hammer-wrench.svg){ width="200px", align=left }
        # You want to **try XAI algorithms**.

        - Discover use cases as [Jupyter notebooks](notebooks.md)
        - Get data set, algorithms and Python code

    === "a data scientist"

        ![Data scientist](../assets/images/test-tube.svg){ width="200px", align=left }
        # You want to **use XAI** algorithms in **your pipelines**.

        - Obtain conda and PyPi packages
        - Get extensive API documentation

    === "a professor"

        ![Professor](../assets/images/school.svg){ width="200px", align=left }
        # You want a tool for **teaching** explainable AI.

        - Deploy the platform on school IT infrastructure or public cloud
        - Adapt provided use cases to teaching needs

***