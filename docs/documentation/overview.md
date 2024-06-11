# :material-book: Documentation

!!! warning
    **This section is under construction and should not be considered as accurate yet.**

Welcome to the **HES-XPLAIN** official documentation. This page holds the entire project documentation for our collection of algorithms designed for various computational tasks in the XAI field.

## Dashboard
Here is a selection of subjects that may fit your needs.
<div class="grid cards" markdown>

-   :material-package-variant:{ .lg .middle } **Installation guide**

    ---

    Install [`dimlpfidex`](#) and get running in minutes.

    [:octicons-arrow-right-24: Installation guide](installation-guide.md)


-   :material-clock-fast:{ .lg .middle } **Getting started**

    ---

    Guided first steps into explainability algorithms. 

    [:octicons-arrow-right-24: Getting started](getting-started.md)


-   :material-application:{ .lg .middle } **Graphical User Interface**

    ---

    Having trouble trying to deal with JSON configuration files? 

    [:octicons-arrow-right-24: Try the GUI](gui.md)


-   :material-code-block-tags:{ .lg .middle } **API reference**

    ---

    Technical documentation for core features.

    [:octicons-arrow-right-24: Reference](/reference)


-   :fontawesome-solid-gears:{ .lg .middle } **Algorithms**

    ---

    All `dimlpfidex` algorithms are described here.

    [:octicons-arrow-right-24: Dive in](algorithms/overview.md)


-   :material-scale-balance:{ .lg .middle } **License**

    ---

    HES-XPLAIN licenses.

    [:octicons-arrow-right-24: License](license.md)

</div>

In case you did not find what you are looking for in this documentation, please refer to the [detailed plan](#documentation-structure) of the documentation. Or feel free to explore it yourself! 


## Application domains
Our tools can be used to bring explainability across a wide range of domains, including but not limited to:

- :material-medical-bag: **Healthcare**: Explainable algorithms can improve diagnostic tools by providing transparent decision-making processes, helping clinicians understand and trust the outputs, which can lead to better patient outcomes.

- :material-finance: **Finances**: Explainable algorithms offer transparency in risk assessment and trading strategies, enabling financial professionals to understand the factors driving model predictions and make more informed decisions.

- :material-chart-arc: **Marketing**: By offering insights into customer segmentation and behavior analysis, our algorithms help marketers understand the underlying reasons behind customer trends, leading to more effective and targeted marketing strategies.

- :material-hammer-wrench: **Engineering**: Explainability in engineering models allows for better system design and optimization by providing clear insights into how various factors influence the model's predictions, facilitating more reliable and robust engineering solutions.

- :material-test-tube: **Research**: Our tools aid in data analysis and hypothesis testing by making the model's decision processes transparent, which helps researchers validate their findings and ensure the reliability of their studies.


## Documentation structure
If you have trouble searching for information you may need, here you can find the detailed structure of the documentation:

```
Documentation
│
├── Introduction
├── Overview of the Repository
├── Application Domains
│
├── Algorithms
│   ├── Description of Different Algorithms ensembles
│   ├── Use Cases for Each Family
│   │
│   ├── Fidex Algorithms
│   │   ├── Overview
│   │   ├── Fidex
│   │   ├── FidexGlo
│   │   ├── FidexGloRules
│   │   └── FidexGloStats
│   │   
│   ├── DIMLP Algorithms
│   │   ├── Overview
│   │   ├── Dimlp
│   │   ├── DimlpBT
│   │   ├── DimlpCls
│   │   ├── DimlpTrn
│   │   └── DimlpPred
│   │   
│   ├── Training methods
│   │   ├── stairObj
│   │   ├── computeRocCurve  
│   │   ├── mlpTrn          
│   │   ├── svmTrn
│   │   ├── convKeras        
│   │   ├── normalization
│   │   ├── crossValid       
│   │   ├── trnFun
│   │   ├── gradBoostTrn     
│   │   └── randForestsTrn
│   │
│   └── File formats
│   
├── Additional Sections
│   ├── Installation Guide
│   ├── Graphic User Interface
│   ├── Getting Started
│   ├── Detailed Examples
│   ├── API Reference
│   ├── Contributing
│   ├── FAQ
│   └── Glossary
│
└── Appendices
    ├── References
    ├── License
    └── Contact Information
```
