# Dataiku Data Contract Generator

Generate standardized JSON data contracts directly from Dataiku datasets.

This plugin automatically extracts dataset schema, metadata, and governance information to create machine-readable JSON data contracts that can be shared across teams and integrated into governance workflows.

---

## Why?

One of the biggest challenges in modern data platforms is that datasets rarely come with clear ownership, expectations, or documentation.

Data contracts help solve this by creating a shared agreement between data producers and consumers.

This plugin automates much of that process by generating standardized contracts directly from your Dataiku projects.

---

## Features

- Automatically extracts dataset schema
- Captures table and column descriptions
- Generates standardized JSON data contracts
- Supports sensitive data metadata designations
- Supports classifications and governance categories
- Infers numeric precision (`multipleOf`) where possible
- Creates managed folders automatically

---

## Example Contract

```json
{
  "name": "customer_transactions",
  "description": "Customer transaction history used for fraud detection.",

  "properties": {
    "transaction_id": {
      "order": 1,
      "type": "string",
      "title": "transaction_id",
      "description": "Unique transaction identifier"
    },
    "customer_id": {
      "order": 2,
      "type": "string",
      "title": "customer_id",
      "description": "Unique customer identifier",
      "sensitive": "id",
      "classification": Input a classification type,
      "category": Input a category
    },
    "amount": {
      "order": 3,
      "type": "number",
      "title": "amount",
      "description": "Transaction amount",
      "multipleOf": 0.01
    }
  }
}
```

---

## How it Works

1. Select a dataset.
2. Launch the **Generate Data Contract** macro.
3. Review and add governance metadata.
4. The plugin generates a JSON data contract.
5. The contract is written to the project's `data_contracts` managed folder.

---

## Output

Contracts are written as

```
<dataset_name>_data_contract.json
```

inside a Dataiku managed folder

```
data_contracts/
```

---

## Compatibility

- Dataiku DSS 12.7+

---

## Roadmap

- YAML contract support

---

## Blog Series

This project accompanies my blog series on data contracts.

- Part 1 – [The Case for Data Contracts]([https://yourblog.com/data-contracts](https://medium.com/@julhofmeister/the-case-for-data-contracts-e2c2af6ee2e1)) 
- Part 2 – Operationalizing Data Contracts with Dataiku *(coming soon)*

---

## License

Apache 2.0

---

## Disclaimer

This is an independent open-source project built using the Dataiku plugin framework and is not an officially supported Dataiku product.
