# :material-chat-question: Introduction to XAI

What is Explainable AI, why is it needed, and where can it be used?

## Traditional AI models

!!! failure inline end "Traditional AI model"

    * Why did the model do that?
    * Why not something else?
    * When does the model succeed?
    * When does it fail?
    * When can we trust it?
    * How do we correct an error?

Artificial intelligence (AI) is **rapidly permeating numerous aspects of our lives** and is evolving into a
**game-changer** in many areas, including healthcare, energy, marketing, finance, security,
transportation, robotics, and image/speech recognition. AI growth is fuelled by the rapid increase of
available computational power, the abundance of data for training and testing sophisticated AI
models, and the resurgence of Machine learning (ML) in the last decade.


```mermaid
graph LR
E(Input data) --> C;
A(Training Data) --> B[Learning Process Algorithm];
B --> C(Learned Function);
C --> D[Output Prediction];
D --->|Why?| F((Lack of Transparency));
```

A **major drawback** with artificial neural networks is that it is **very difficult to explain their responses**
because their knowledge is embedded within the values of the parameters and neuron activations,
which are at first glance incomprehensible. The **transparency of AI models** is an important research
topic, as transparency is essential with respect to the European General Data Protection Regulation
(GDPR). In general, under the GDPR, every individual has the right to receive an explanation when
a decision has been made about them.

> Artificial intelligence (AI) is rapidly growing in various fields due to the availability
of computational power and data for training models. However, the lack of transparency in
AI models, particularly deep neural networks, is a major concern as it raises ethical and legal questions
limiting their societal acceptance.

**Explainable AI (XAI)** aims to address this issue by **explaining how a model produces its
results**.

***

## Explainable AI models

!!! success inline end "Explainable AI model"

    * We can understand why
    * We can understand why not
    * We know when it will succeed
    * We know when it will fail
    * We know when to trust it
    * We know when it erred

The impressive effectiveness of AI applications based on DL is often shadowed by their inability to explain
their behaviours to human users. Understanding how these algorithms operate, would allow **demystifying AI**,
making such black-boxes intelligible and explainable, and **improving everyone's confidence** in these tools.
Explainable AI encompasses AI methods aimed at explaining to a given audience, why or how a model produces
its results.

```mermaid
graph LR
E(Input data) --> C;
A(Training Data) --> B[New Learning Process];
B --> C(Explainable Model);
C --> D[Explanation Interface];
D --> F((User Understanding));
```

XAI seeks to address this issue by developing AI models that can provide explanations that are clear, concise, and relevant to the user's context. By providing interpretable explanations for its decisions, XAI can help users better understand the reasoning behind AI models and build trust in their reliability and accuracy.

The **benefits of XAI** are many. For example, it can help to improve the accuracy and performance of
AI models by enabling users to identify and correct errors or biases in the data or the model itself.
XAI can also enhance the accountability and transparency of AI systems, which is essential for ensuring
ethical and fair use of AI in society.

> Explainability is a cornerstone for attaining some of the fundamental principles of **responsible AI**:
*fairness*, *transparency*, *privacy*, *accountability*, *safety*, *security*, and *reliability*.

---

## Application domains

Explainable AI (XAI) is relevant across a diverse array of domains, including but not limited to:

- :material-medical-bag: **Healthcare**: Explainable algorithms can significantly enhance diagnostic tools by providing transparent decision-making processes. This transparency helps clinicians understand and trust the outputs of AI systems, which can lead to improved patient outcomes. For instance, when an AI system suggests a diagnosis, the ability to trace back the reasoning behind that suggestion allows healthcare professionals to make more informed decisions, ultimately benefiting patient care.

- :material-finance: **Finances**: In the financial sector, explainable algorithms offer crucial transparency in risk assessment and trading strategies. Financial professionals can gain insights into the factors driving model predictions, enabling them to make more informed decisions. This is particularly important in an industry where trust and accountability are paramount, as understanding the rationale behind automated decisions can help mitigate risks and enhance compliance with regulatory standards.

- :material-chart-arc: **Marketing**: Explainable AI provides valuable insights into customer segmentation and behavior analysis. By elucidating the underlying reasons behind customer trends, marketers can develop more effective and targeted marketing strategies. For example, understanding why certain demographics respond positively to specific campaigns allows for the optimization of marketing efforts, leading to increased engagement and conversion rates.

- :material-hammer-wrench: **Engineering**: In the field of engineering, explainability in models allows for better system design and optimization. By providing clear insights into how various factors influence the model's predictions, engineers can create more reliable and robust solutions. This is particularly beneficial in complex systems where understanding the interplay of different variables is essential for effective design and implementation.

- :material-test-tube: **Research**: Explainability tools play a vital role in data analysis and hypothesis testing within research. By making the model's decision processes transparent, researchers can validate their findings and ensure the reliability of their studies. This transparency fosters a deeper understanding of the data and the models used, which is crucial for advancing knowledge in various scientific fields.

> Explainability is a transformative approach that increases transparency and trust across multiple domains.

---

## HES-SO flagship project

The HES-XPLAIN project is associated to the [Swiss AI Center](https://swiss-ai-center.ch/), the flagship project of the [HES-SO](team.md#the-hes-so) (University of Applied Sciences and Arts of Western Switzerland).

The Swiss AI Center’s mission is to accelerate the adoption of artificial intelligence in the digital transition of Swiss SMEs. The associated socio-economic challenge is to increase their competitiveness, to limit relocation and to create new competences at the interface of laboratories and the practical use of artificial intelligence.

As such, a demonstration module on AI explainability has been integrated within the Swiss AI Center online platform [Core Engine](https://app.swiss-ai-center.ch/). The implementation of a GradCAM module using a pre-trained model based on our use cases has been carried out. The choice of this specific algorithm was driven by its explicitly visual presentation, which facilitates understanding of explainability for non-experts.
