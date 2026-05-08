## GSM-SEM

This repository contains semantic variant dataset samples - SEM, SymbolicSEM, and PlusSEM.

## Getting Started

The data can be found at `dataset/SEM.jsonl`, `dataset/SymbolicSEM.jsonl`, `dataset/PlusSEM.jsonl`.  

Prompts used for curation and evaluation steps can be found in `prompts/`

## Dataset Details

Dataset contains samples of semantically variant arithmetic samples, presenting a new dimension of arithmetic variants useful for evaluation of models on arithmetic tasks.

Each sample contains the following fields:

original_id: ID for the sample question.
SEM_id: Semantic variant ID.
question: Sample question.
final_answer: Final answer to the question.
strictness: {'none': True/False, 'min': True/False, 'min-med': True/False, 'med': True/False, 'med-max': True/False, 'max': True/False}

Example
```
{
  "original_id": 1141,
  "SEM_id": 1,
  "question": "John is trying to eat a dozen eggs a day. For the first month, he eats 3 eggs a day, and then he increases it to 5 eggs a day for the second month. How many dozen eggs will he have eaten at the end of 2 months?",
  "final_answer": "20",
  "strictness": {'none': False, 'min': False, 'min-med': False, 'med': True, 'med-max': True, 'max': True}
}
```  

## Dataset Creation
The data was created through a combination of synthetic generation and manual curation between September and October 2025. The research work is being published by Oracle, and this data is part of research being released to the community

## Intended Use
These datasets are being shared with the research community to facilitate reproduction of our results and foster further research in this area. It is intended to be used by domain experts who are independently capable of evaluating the quality of outputs before acting on them.

## Contributing

*If your project has specific contribution requirements, update the CONTRIBUTING.md file to ensure those requirements are clearly explained*

This project welcomes contributions from the community. Before submitting a pull request, please [review our contribution guide](./CONTRIBUTING.md)

## Security

Please consult the [security guide](./SECURITY.md) for our responsible security vulnerability disclosure process

## License

Copyright (c) 2026 Oracle and/or its affiliates.

ORACLE AND ITS AFFILIATES DO NOT PROVIDE ANY WARRANTY WHATSOEVER, EXPRESS OR IMPLIED, FOR ANY SOFTWARE, MATERIAL OR CONTENT OF ANY KIND CONTAINED OR PRODUCED WITHIN THIS REPOSITORY, AND IN PARTICULAR SPECIFICALLY DISCLAIM ANY AND ALL IMPLIED WARRANTIES OF TITLE, NON-INFRINGEMENT, MERCHANTABILITY, AND FITNESS FOR A PARTICULAR PURPOSE. FURTHERMORE, ORACLE AND ITS AFFILIATES DO NOT REPRESENT THAT ANY CUSTOMARY SECURITY REVIEW HAS BEEN PERFORMED WITH RESPECT TO ANY SOFTWARE, MATERIAL OR CONTENT CONTAINED OR PRODUCED WITHIN THIS REPOSITORY. IN ADDITION, AND WITHOUT LIMITING THE FOREGOING, THIRD PARTIES MAY HAVE POSTED SOFTWARE, MATERIAL OR CONTENT TO THIS REPOSITORY WITHOUT ANY REVIEW. USE AT YOUR OWN RISK.

Released under the Universal Permissive License v1.0 as shown at
<https://oss.oracle.com/licenses/upl/>.
