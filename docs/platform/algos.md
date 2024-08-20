# Algorithms

HES-XPLAIN includes a variety of algorithms developed by our team, as well as integrating modern standard algorithms through the OmniXAI library. This section provides a brief 
description of each of our own developed algorithms, as well as how they can be used individually or through our MLXplain package for comparison with OmniXAI algorithms.

## Our Developed Algorithms

### MLXplain

**MLXplain** is a comprehensive framework that brings together various algorithms to provide a unified platform for eXplainable AI (XAI). This framework serves as the backbone for 
integrating our own developed algorithms with the modern standards provided by OmniXAI.

### Rules Extraction

**Rules Extraction** focuses on developing high-level explanation algorithms. This module includes three distinct approaches:

1. **Rule Extraction**: Deriving rules that represent the decision logic of the AI model.
2. **Local Identification of Relevant Patterns**: Identifying patterns that are significant in localized regions of the data.
3. **Generation of Global Meaningful Patterns**: Creating patterns that provide a global understanding of the model's behavior.

Additionally, a novel algorithm is developed to combine these approaches, resulting in comprehensive and coherent explanations.

### DIMLPFidex

**DIMLPFidex** is a module gathering an ensemble of algorithms designed to provide low-level explanations. It focuses on extracting propositional rules from deep models. This module contains many training algorithms modified to permit the usage of our explanation algorithms. We present three explanation algorithms:

1. **[Fidex](../../documentation/algorithms/fidex/fidex/)**: Provides localized explanations by generating rules that describe the model’s behavior for specific data samples.
2. **[FidexGlo](../../documentation/algorithms/fidex/fidexglorules/)**: Offers a global understanding of the model's behavior by aggregating local rules into a comprehensive ruleset.
3. **[Dimlp](../../documentation/algorithms/dimlp/overview/)**: Extracts global propositional rules from deep models, specifically trained using the `Dimlp` architecture, to explain the model's overall decision-making process.

### FUGE

**FUGE** is an algorithm developed to construct fuzzy systems. These systems predict human decision-making outcomes and provide understandable explanations. FUGE combines the 
predictive power of fuzzy logic with the clarity of human-like reasoning.

## Integration with OmniXAI

HES-XPLAIN not only includes our proprietary algorithms but also incorporates all modern standard algorithms through the [OmniXAI](https://github.com/omnixai/omnixai) library. This 
integration ensures that users have access to a wide range of XAI techniques and functionalities.

### MLXplain Package

Our **MLXplain** package serves as the "glue" that seamlessly integrates our developed algorithms with the OmniXAI API. This integration allows users to benefit from the following:

- Access to modern XAI algorithms provided by OmniXAI.
- Enhanced functionality through OmniXAI's robust features.
- The ability to use our specialized algorithms alongside industry-standard methods, providing a comprehensive toolkit for XAI.

## Individual and Integrated Usage

All of the algorithms developed by HES-XPLAIN can be used individually because we have packaged them separately. This allows users to use each algorithm as a standalone tool 
according to their specific needs.

Additionally, our platform functions as a comprehensive repository where these individual packages can be accessed and used together. The **MLXplain** package enables users to 
compare and utilize our algorithms in conjunction with OmniXAI algorithms, offering a unified and versatile platform for XAI.

By combining the strengths of our algorithms with the extensive capabilities of OmniXAI, HES-XPLAIN offers a powerful and versatile platform for developing and applying eXplainable 
AI techniques.

---

    
