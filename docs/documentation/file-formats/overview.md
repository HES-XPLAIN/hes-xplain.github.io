# File formats

!!!Warning
    **This section is under construction and should not be considered as accurate yet.**

## Important Guidelines for File Usage

Before using our algorithms, consider the following essential guidelines for managing and preprocessing files and data:

### File Naming Conventions:

There are no strict checks on the filenames provided by the user, so it is highly recommended to follow logical and consistent naming conventions to ensure clarity and ease of use. Here are some recommended extensions:
    
    Rule Files: .rls
    Prediction Files: .out
    Weight Files: .wts
    Images: .png
    Other Files: .txt

### Categorization of Attributes:
    
It is crucial to properly categorize attributes that have a set of discrete possible values. Each attribute should be expressed as either an integer or a float. For example, binary attributes such as "SMOKER" can take values 0 or 1. For multi-class attributes like color, it is recommended to use separate binary attributes, such as IS_RED, IS_GREEN, etc. This avoids introducing artificial proximity between unrelated categories (e.g., assigning 0 to red, 1 to blue, 2 to green).

### Data Normalization:
    
Normalizing your data before training can improve the performance of certain models. Keep the following in mind:

- Normalization is recommended before training with [DimlpTrn](../dimlpfidex/dimlp/dimlptrn.md) and [DimlpBT](../dimlpfidex/dimlp/dimlpbt.md).
- Normalization is not necessary for [CNN](../dimlpfidex/training-methods/cnntrn.md), [MLP](../dimlpfidex/training-methods/mlptrn.md), and [SVM](../dimlpfidex/training-methods/svmtrn.md) as normalization is handled internally during the training process.
- Decision trees (e.g., [Gradient Boosting](../dimlpfidex/training-methods/gradboosttrn.md), [Random Forests](../dimlpfidex/training-methods/randforeststrn.md)) do not require normalization as they are robust to unnormalized data.

Do not forget to denormalize the generated rules with the [normalization](../dimlpfidex/training-methods/normalization.md) tool afterwards if you have normalized your data.

---

Here you can find all the documentation related to specific file formats used by our algorithms.

<div class="grid cards" markdown>

-   **JSON configuration files**

    ---

    All about our configuration files.

    [:octicons-arrow-right-24: More](json-configuration-files.md)

-   **Execution files**

    ---

    All about the input files used during the execution of our algorithms.

    [:octicons-arrow-right-24: More](execution-files.md)
</div>