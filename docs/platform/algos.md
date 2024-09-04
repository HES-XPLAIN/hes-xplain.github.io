# Algorithms

HES-XPLAIN includes a variety of algorithms developed by our team, while also supporting integration with a wide range of modern XAI algorithms via the [OmniXAI](https://github.com/salesforce/OmniXAI) library.

This section provides a concise overview of our algorithms, detailing how they can be used individually and how they can be used in conjonction with those provided by OmniXAI through our comprehensive package.

* :material-view-grid-plus: **Individual usage**: Each algorithm is available as a separate package, allowing users to select and use them individually based on their specific needs.

* :material-view-grid: **Unified integration**: The platform is able to function as a cohesive ensemble where these individual packages can be accessed and used together through an overarching package.

To access our Python packages, see the page [Usage](usage.md).

## Individual algorithms

Overview of our own developed algorithms.

### Rules Extraction

**[Rules Extraction](../documentation/rulesextraction/overview.md)** focuses on developing high-level explanation algorithms.

This module includes three distinct approaches:

1. **Rule Extraction**: Deriving rules that represent the decision logic of the AI model.
2. **Local Identification of Relevant Patterns**: Identifying patterns that are significant in localized regions of the data.
3. **Generation of Global Meaningful Patterns**: Creating patterns that provide a global understanding of the model's behavior.

Additionally, a novel algorithm is developed to combine these approaches, resulting in comprehensive and coherent explanations.

### DIMLPFidex

**[DIMLPFidex](../documentation/dimlpfidex/overview.md)** is a module gathering an ensemble of algorithms designed to provide low-level explanations. It focuses on extracting propositional rules from deep models. This module contains many training algorithms modified to permit the usage of our explanation algorithms.

We present three explanation algorithms:

* **[Fidex](../documentation/dimlpfidex/fidex/fidex.md)**: Provides localized explanations by generating rules that describe the model’s behavior for specific data samples.
* **[FidexGlo](../documentation/dimlpfidex/fidex/fidexglorules.md)**: Offers a global understanding of the model's behavior by aggregating local rules into a comprehensive ruleset.
* **[Dimlp](../documentation/dimlpfidex/dimlp/overview.md)**: Extracts global propositional rules from deep models, specifically trained using the `Dimlp` architecture, to explain the model's overall decision-making process.

### Fuzzy-CoCo

**Fuzzy-CoCo** is an algorithm developed to construct fuzzy systems using genetic algorithms based on the following paper done by [Prof. Carlos Andrés Peña-Reyes](../team.md#prof-carlos-andres-pena-reyes) : [A fuzzy-genetic approach to breast cancer diagnosis](https://www.sciencedirect.com/science/article/pii/S0933365799000196)

These systems predict human decision-making outcomes and provide understandable explanations. FUGE combines the predictive power of fuzzy logic with the clarity of human-like reasoning.

The newest implementation of Fuzzy-Coco is currently in development and will be distributed in our HES-XPLAIN platform. 
The modern development of Fuzzy-CoCO is done [here](https://github.com/HES-XPLAIN/fuge) under the name FUGE. 

---

## Integration with OmniXAI

Overview of the overarching package for use via an unified interface.

### MLXplain

**[MLXplain](../documentation/mlxplain/overview.md)** serves as the code framework that unifies our various algorithms, creating a cohesive platform for eXplainable AI (XAI).

Built on the robust capabilities of [OmniXAI](https://github.com/salesforce/OmniXAI), a comprehensive Python library dedicated to explainable AI, MLXplain enhances this foundation by incorporating our additional algorithms, resulting in a powerful and versatile environment for practitioners.

By reusing all modern standard algorithms available through the OmniXAI library, MLXplain ensures users have access to a broad spectrum of XAI techniques and functionalities. This integration allows users to make full use of the explainable AI potential, facilitating the comparison between different methods and simplifying experimentation and implementation.
