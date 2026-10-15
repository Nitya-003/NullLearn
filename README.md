# NullLearn
### A Blockchain-Based Machine Unlearning Verification System

NullLearn is a project that explores machine unlearning through machine learning evaluation and blockchain-based auditing. It aims to reduce the influence of selected training data on an already-trained model and maintain a tamper-evident record of deletion requests, unlearning operations, and verification results.


## Problem Statement

Machine learning models learn patterns from the data on which they are trained. When a particular data record needs to be deleted, removing it from the original dataset does not automatically remove its influence from an already-trained model. Retraining the model from scratch without the targeted data can be computationally expensive. Additionally, tracking deletion requests and verifying the results of unlearning can be challenging without a reliable audit trail. NullLearn addresses these challenges by exploring a workflow that combines machine unlearning, model evaluation, and blockchain-based audit records.

## Proposed Solution

NullLearn provides a framework for submitting data deletion requests, applying machine unlearning techniques, evaluating the resulting model, and recording relevant evidence.

The proposed system aims to:

- Register machine learning models and dataset versions.
- Track data deletion requests throughout their lifecycle.
- Apply machine unlearning methods to reduce the influence of selected training data.
- Compare the original model, unlearned model, and a reference model retrained without the targeted data.
- Evaluate unlearning behavior using multiple performance and privacy-related metrics.
- Generate structured audit reports containing evaluation results and methodology.
- Use blockchain to maintain tamper-evident records of important events and cryptographic commitments.

Blockchain provides evidence that recorded commitments have not been altered; it does not independently prove that a model has successfully forgotten particular training data.

## System Architecture

```mermaid
flowchart TD
    A["User / ML Engineer"] --> B["NullLearn Dashboard"]
    B --> C["Model & Dataset Registry"]
    B --> D["Data Deletion Request"]

    D --> E["Request Validation"]
    E --> F["Machine Unlearning Engine"]

    C --> F
    F --> G["Unlearned Model"]

    C --> H["Reference Retraining"]
    H --> I["Reference Model"]

    G --> J["Verification & Evaluation"]
    I --> J
    C --> J

    J --> K["Audit Report"]
    K --> L["Generate Cryptographic Commitment"]

    C --> M["Blockchain Audit Layer"]
    D --> M
    L --> M

    M --> N["Tamper-Evident Audit Trail"]
    N --> O["Report & Verification Dashboard"]

    style A fill:#111111,color:#ffffff,stroke:#777777
    style B fill:#111111,color:#ffffff,stroke:#777777
    style F fill:#222222,color:#ffffff,stroke:#aaaaaa
    style J fill:#222222,color:#ffffff,stroke:#aaaaaa
    style M fill:#111111,color:#ffffff,stroke:#aaaaaa
    style N fill:#111111,color:#ffffff,stroke:#aaaaaa
```

## Key Features

### 1. Model and Dataset Registry
Maintain metadata about machine learning models, dataset versions, training configurations, and model artifact commitments.

### 2. Data Deletion Requests
Create and track requests to remove the influence of selected training records from a trained model.

### 3. Machine Unlearning Engine
Apply a selected unlearning method and produce an updated model for further evaluation.

### 4. Verification Lab
Compare the original model, unlearned model, and retrained reference model using performance and privacy-related metrics.

### 5. Blockchain Audit Trail
Record selected events, timestamps, and cryptographic commitments to support the integrity and traceability of audit evidence.

### 6. Audit Reports
Generate structured reports containing request details, model versions, unlearning methodology, evaluation results, and blockchain references.

## Machine Learning Evaluation

NullLearn can assess unlearning behavior through complementary measurements:

- **Test-set accuracy:** Evaluates general predictive performance.
- **Retained-set performance:** Measures performance on data that should remain influential.
- **Forget-set behavior:** Examines model behavior on targeted examples.
- **Membership-inference evaluation:** Assesses whether an attack can still identify targeted records as training members.
- **Retrained-reference comparison:** Compares the unlearned model with a model trained without the targeted records.
- **Execution time:** Compares the computational cost of unlearning with full retraining.

No single metric proves complete forgetting. Evaluation results must be interpreted together and in the context of the selected dataset and unlearning algorithm.


## Privacy and Security

NullLearn follows an off-chain data storage approach to reduce unnecessary exposure of sensitive information.

- Raw datasets and individual training records remain off-chain.
- Model weights and detailed execution logs remain off-chain.
- Only appropriate commitments and minimal audit metadata are recorded on-chain.
- Sensitive identifiers should not be exposed through public transactions.
- Hashing alone does not guarantee privacy, especially when the underlying data is predictable.
- Access controls should protect stored artifacts, requests, and reports.

## Expected Outcome

NullLearn aims to demonstrate a reproducible workflow for machine unlearning and the auditing of its results. The project will investigate how an unlearned model behaves compared with the original model and a retrained reference, while exploring how blockchain commitments can improve the traceability and integrity of audit records.

## Future Enhancements

- Support for additional unlearning algorithms and model architectures.
- Stronger privacy and membership-inference evaluations.
- Independent verification of audit reports.
- Integration with additional blockchain networks.
- Reproducible experiments and downloadable reports.
- Multi-user support and model-owner access controls.
- Advanced verification methods for larger models.

## Academic Disclaimer

NullLearn is an educational and experimental project. Blockchain records can make submitted audit evidence tamper-evident, but they do not independently establish that a machine learning model has completely forgotten a particular training record.

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.
