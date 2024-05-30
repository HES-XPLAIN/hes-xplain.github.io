# :material-book: Documentation

!!! warning "Warning"
    **This section is under construction and cannot be considered usable and accurate yet.**

## Introduction
Welcome to the **HES-XPLAIN** official documentation ! This page holds the entire project documentation for our diverse collection of algorithms designed for various computational tasks in the XAI field. The goal of this section is to help on how to use each algorithm, with practical examples and guidance on interpreting results. There is also other subsections offering additional conteent to enlighten your light.



## Dashboard
Here is a selection of subjects that may fit your needs.
<div class="grid cards" markdown>

-   :material-package-variant:{ .lg .middle } **Installation guide**

    ---

    Install [`dimlpfidex`](#) and get running in minutes.

    [:octicons-arrow-right-24: Installation guide](#)


-   :material-clock-fast:{ .lg .middle } **Getting started**

    ---

    Guided first steps into explainability algorithms. 

    [:octicons-arrow-right-24: Getting started](#)


-   :material-application:{ .lg .middle } **Graphical User Interface**

    ---

    Having trouble trying to deal with JSON configuration files ? 

    [:octicons-arrow-right-24: Check this out](#)


-   :material-code-block-tags:{ .lg .middle } **API reference**

    ---

    Technical documentation for core features.

    [:octicons-arrow-right-24: Reference](#)


-   :fontawesome-solid-gears:{ .lg .middle } **Fidex algorithms**

    ---

    All you need to know about Fidex algorithms.

    [:octicons-arrow-right-24: Dive in](#)

-   :fontawesome-solid-gears:{ .lg .middle } **DIMLP algorithms**

    ---

    All you need to know about DIMLP algorithms.

    [:octicons-arrow-right-24: Dive in](#)


-   :material-scale-balance:{ .lg .middle } **License**

    ---

    HES-XPLAIN is licensed under BSD-3

    [:octicons-arrow-right-24: License](#)

</div>

In case you did not find what you are looking for in this documentation, please refer to the [detailed plan](#overview-of-the-repository) of the documentation. Or feel free to explore it yourself ! 


## Application Domains
Our tools can be used to bring explainability across a wide range of domains, including but not limited to:

- :material-medical-bag: **Healthcare**: Explainable algorithms can improve diagnostic tools by providing transparent decision-making processes, helping clinicians understand and trust the outputs, which can lead to better patient outcomes.

- :material-finance: **Finances**: Explainable algorithms offer transparency in risk assessment and trading strategies, enabling financial professionals to understand the factors driving model predictions and make more informed decisions.

- :material-chart-arc: **Marketing**: By offering insights into customer segmentation and behavior analysis, our algorithms help marketers understand the underlying reasons behind customer trends, leading to more effective and targeted marketing strategies.

- :material-hammer-wrench: **Engineering**: Explainability in engineering models allows for better system design and optimization by providing clear insights into how various factors influence the model's predictions, facilitating more reliable and robust engineering solutions.

- :material-test-tube: **Research**: Our tools aid in data analysis and hypothesis testing by making the model's decision processes transparent, which helps researchers validate their findings and ensure the reliability of their studies.


## Overview of the documentation structure
If you have trouble searching for information you may need, here you can find the detailed structure of the documentation:

```
Documentation
│
├── Introduction
├── Overview of the Repository
├── Application Domains
│
├── Algorithms
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
│   └── Training methods
│       ├── stairObj
│       ├── computeRocCurve  
│       ├── mlpTrn          
│       ├── svmTrn
│       ├── convKeras        
│       ├── normalization
│       ├── crossValid       
│       ├── trnFun
│       ├── gradBoostTrn     
│       └── randForestsTrn
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

!!! note "note"
    The documentation skeleton is going to be removed in future updates.

## Documentation skeleton
    1 Documentation Overview
        1.1 Introduction
        1.2 Overview of the Repository
        1.3 Application Domains

    2 Algorithms
        2.1 Description of Different Algorithms ensembles
        2.3 Use Cases for Each Family

        2.1 Fidex algorithms
            2.1.1 Overview
                2.1.1.1 Introduction to Fidex Algorithms
                2.1.1.2 General Use Cases
                2.1.1.3 Graphical Representation (if applicable)
            2.1.2 Fidex
                2.1.2.1 Description
                2.1.2.2 Usage Instructions
                2.1.2.3 Example Code
                2.1.2.4 Output Interpretation
            2.1.3 FidexGlo
                2.1.3.1 Description
                2.1.3.2 Usage Instructions
                2.1.3.3 Example Code
                2.1.3.4 Output Interpretation
            2.1.4 FidexGloRules
                2.1.4.1 Description
                2.1.4.2 Usage Instructions
                2.1.4.3 Example Code
                2.1.4.4 Output Interpretation
            2.1.5 FidexGloStats
                2.1.5.1 Description
                2.1.5.2 Usage Instructions
                2.1.5.3 Example Code
                2.1.5.4 Output Interpretation

        2.2 DIMLP algorithms 
            2.2.1 Overview
                2.2.1.1 Introduction to DIMLP Algorithms
                2.2.1.2 General Use Cases
                2.2.1.3 Graphical Representation
            2.2.2 Dimlp
                2.2.2.1 Description
                2.2.2.2 Usage Instructions
                2.2.2.3 Example Code
                2.2.2.4 Output Interpretation
            2.2.3 DimlpBT
                2.2.3.1 Description
                2.2.3.1 Usage Instructions
                2.2.3.1 Example Code
                2.2.3.1 Output Interpretation
            2.2.4 DimlpCls
                2.2.4.1 Description
                2.2.4.2 Usage Instructions
                2.2.4.3 Example Code
                2.2.4.4 Output Interpretation
            2.2.5 DimlpTrn
                2.2.5.1 Description
                2.2.5.2 Usage Instructions
                2.2.5.3 Example Code
                2.2.5.4 Output Interpretation
            2.2.6 DimlpPred
                2.2.6.1 Description
                2.2.6.2 Usage Instructions
                2.2.6.3 Example Code
                2.2.6.4 Output Interpretation

        2.3 Training methods
            2.3.1 Overview
                2.3.1.1 Introduction to Fidex Algorithms
                2.3.1.2 General Use Cases
                2.3.1.3 Graphical Representation (if applicable)
            2.3.2 gradBoostTrn
                2.3.2.1 Description
                2.3.2.2 Usage Instructions
                2.3.2.3 Example Code
                2.3.2.4 Output Interpretation
            2.3.3 computeRocCurve      
                2.3.3.1 Description
                2.3.3.2 Usage Instructions
                2.3.3.3 Example Code
                2.3.3.4 Output Interpretation
            2.3.4 randForestsTrn
                2.3.4.1 Description
                2.3.4.2 Usage Instructions
                2.3.4.3 Example Code
                2.3.4.4 Output Interpretation
            2.3.5 trnFun
                2.3.5.1 Description
                2.3.5.2 Usage Instructions
                2.3.5.3 Example Code
                2.3.5.4 Output Interpretation
            2.3.6 convKeras    
                2.3.6.1 Description
                2.3.6.2 Usage Instructions
                2.3.6.3 Example Code
                2.3.6.4 Output Interpretation
            2.3.7 mlpTrn   
                2.3.7.1 Description
                2.3.7.2 Usage Instructions
                2.3.7.3 Example Code
                2.3.7.4 Output Interpretation
            2.3.8 stairObj
                2.3.8.1 Description
                2.3.8.2 Usage Instructions
                2.3.8.3 Example Code
                2.3.8.4 Output Interpretation
            2.3.9 crossValid    
                2.3.9.1 Description
                2.3.9.2 Usage Instructions
                2.3.9.3 Example Code
                2.3.9.4 Output Interpretation
            2.3.10 normalization
                2.3.10.1 Description
                2.3.10.2 Usage Instructions
                2.3.10.3 Example Code
                2.3.10.4 Output Interpretation
            2.3.11 svmTrn
                2.3.11.1 Description
                2.3.11.2 Usage Instructions
                2.3.11.3 Example Code
                2.3.11.4 Output Interpretation
        
    3 Additional Sections
        3.1 Installation Guide
            3.1.1 Prerequisites
            3.1.2 Installation Steps
            3.1.3 Troubleshooting
        3.2 Graphic User Interface
            3.2.1 Purpose
            3.2.2 Installation steps
        3.3 Getting Started
            3.3.1 Quick Start Guide
            3.3.2 Basic Examples
            3.3.3 Common Pitfalls and Solutions
        3.4 Detailed Examples
            3.4.1 Use Case 1
            3.4.2 Use Case 2
            3.4.3 Use Case 3
        3.5 API Reference
            3.5.1 Detailed Documentation of Functions and Classes
            3.5.2 Input Parameters
            3.5.3 Output Specifications
            3.5.4 Code Examples
        3.6 Contributing
            3.6.1 Contribution Guidelines
            3.6.2 How to Submit a Bug Report
            3.6.3 How to Submit a Feature Request
            3.6.4 Coding Standards
        3.7 FAQ
            3.7.1 Frequently Asked Questions
            3.7.2 Troubleshooting Tips
            3.7.3 Common Issues and Solutions
        3.8 Glossary
            3.8.1 Definitions of Key Terms
            3.8.2 Acronyms and Abbreviations

    4 Appendices
        4.1 References
            4.1.1 Academic Papers
            4.1.2 Books
            4.1.3 Online Resources
        4.2 License
            4.2.1 Licensing Information
        4.3 Contact Information
            4.3.1 How to Get Support
            4.3.2 Contact Details for Maintainers



