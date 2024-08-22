
Our platform is divided in several sections, which interacts with each other to deliver XAI solutions to the end user.

```mermaid
graph LR
    subgraph Repo["Open source repository"]
        direction LR
        souceCode["Source code"]
        notebooksSrc["Notebook sources"]
    end

    subgraph External["External projects"]
        direction LR
        omnixai["OmniXAI"]
    end


    subgraph Pypi["PyPI packages"]
        direction TB
        dimlpfidex["dimlpfidex package"]
        rulesextract["rules-extraction package"]
        mlxplain["MLxplain package"]
    end

    subgraph Website["Website"]
        direction LR
        overview["Project overview"]
        notebookLinks["Notebooks index"]
        docs["Docs. & API ref."]
    end

    subgraph Datasets["Datasets"]
        direction LR
        kaggle["Kaggle"]
        huggingface["Hugging face"]
    end

    subgraph Notebooks["Notebooks"]
        direction LR
        colab["Google colab"]
        docker["Docker images"]
    end

    subgraph Endusers["End users"]
        direction LR
        decisionMakers["Decision makers"]
        engineers["Engineers"]
        dataScientists["Data scientists"]
        enthousiasts["Students & ML enthousiasts"]
    end

    souceCode-- "is compiled into" -->Pypi
    souceCode-- "is documented in" -->docs 
    notebooksSrc-- "are hosted by" -->Notebooks
    Notebooks-- "help" -->Endusers
    Datasets-- "can be used with" -->Notebooks
    notebookLinks-- "links to" -->Notebooks
    Website-- "enlight" -->Endusers
    Pypi-- "can be used by" -->Endusers
    Pypi-- "are used in" -->Notebooks
    omnixai-- "empowers" -->mlxplain

```

## Open source repository
Where core algorithms and features are developed.

HES-XPLAIN assembles our own developed algorithms as well as incorporating all algorithms proposed by [OmniXAI](https://github.com/salesforce/omnixai). Our platform provides a comprehensive suite of tools for XAI, enabling users to compare and choose the best techniques for their needs. Explore our algorithms in the [HES-XPLAIN - Algorithms](algos.md) section.

## PyPI package
Python wrappers meant to ease the installation and use of our tools:

## Notebooks & Datasets
Practical ressources & content aiming to help understanding how to use the different features provided, all accessible from our website including:

- **XAI Resource**: Literature and resources that describe what/why/how Explainable Artificial Intelligence.
- **Tutorial Notebooks**: Step-by-step guides to help users understand and apply XAI methods.
- **Use Case Notebooks**: Showcase how XAI and our platform can be used to solve real-world problems.
- **Datasets and Models**: Embedded datasets and pre-trained models to facilitate experimentation.

These are provided with solutions that facilitate deployment, including:

- **Notebook Server Package**: A pre-configured environment to run Jupyter notebooks.
- **Docker Image**: Containerized versions of our platform components for easy deployment on local machines or cloud environments.

More details can be found in the [notebooks](../notebooks.md) section.