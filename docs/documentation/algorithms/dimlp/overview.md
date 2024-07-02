# Dimlp algorithms

!!! warning "Warning"
    **This section is under construction and should not be considered as accurate yet.**

The *Discretized Interpretable Multi-Layer Perceptron* is a particular feed-forward neural network architecture, based on the `MLP` architecture, whose main feature is rule generation.

## Architecture
The architecture is built as shown below:

<div align="center">
```mermaid
graph TD;
    d(dimlp algorithms) --> DensCls;
    d --> DimlpBT;
    d --> DimlpCls;
    d --> DimlpTrn;
    d --> DimlpRul;
    d --> DimlpPred;
```
</div>


Each algorithm has its purpose:

- **[DimlpBT](dimlpbt.md)**: 
- **[DimlpRul](dimlprul.md)**:
- **[DimlpCls](dimlpcls.md)**:
- **[DensCls](denscls.md)**: 
- **[DimlpTrn](dimlptrn.md)**: Trains the `Dimlp` model with a given dataset.
- **[DimlpPred](dimlppred.md)**: Compute predictions with the `Dimlp` from a given test dataset.
