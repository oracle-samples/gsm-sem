## GSM-SEM

This repository contains semantic variant dataset samples - SEM, SymbolicSEM, and PlusSEM.

## Getting Started

The shared dataset consists of the medium-or-higher samples in:

- `datasets/SEM.jsonl`
- `datasets/SymbolicSEM.jsonl`
- `datasets/PlusSEM.jsonl`

Each of these files contains records where `strictness.med` is `true`. The
`datasets/all_strictness_settings/` directory contains the corresponding
unfiltered files with every strictness setting, for reference.

Prompts used for curation and evaluation steps can be found in `prompts/`

## Dataset Details

Datasets contains semantically variant arithmetic questions for evaluating how models handle answer-preserving changes to a problem. The GSM-SEM datasets shared contain samples of semantically variant arithmetic samples, presenting a new dimension of arithmetic variants useful for evaluation of models on arithmetic tasks.
All files are JSONL: one JSON object per line. 

### Fields shared by all datasets

| Field | Description |
| --- | --- |
| `original_id` | Identifier of the underlying GSM8K problem. |
| `SEM_id` | Identifier of the semantic variant. |
| `question` | The question to answer for this record. |
| `final_answer` | Correct final answer to `question`. |
| `gsm8k_question` | The original GSM8K question. |
| `gsm8k_answer` | Worked solution for the original GSM8K question, ending in `#### <answer>`. |
| `gsm8k_final_answer` | Terminal answer extracted from `gsm8k_answer`. |
| `strictness` | Boolean annotations for `none`, `min`, `min-med`, `med`, `med-max`, and `max` strictness levels. |

For medium-or-higher filtering, select records where `strictness.med` is `true`.

The examples below use `...` to abbreviate worked-solution fields; full records
contain the complete solutions.

### SEM

`SEM.jsonl` contains semantic variants of the original GSM8K problem. Its fields are exactly the shared fields above.

```json
{
  "original_id": 955,
  "SEM_id": 199,
  "question": "A university dormitory has 1000 rooms, with 1/5 currently filled. During the start of the semester, 50 new students move in each day. How many vacant rooms will remain after 2 weeks?",
  "final_answer": "100",
  "gsm8k_question": "A hospital has a capacity of 1000 beds with 1/5 occupied. Due to the coronavirus outbreak, 50 patients are admitted into the hospital each day. Calculate the total number of unoccupied beds in the hospital after 2 weeks.",
  "gsm8k_answer": "... #### 100",
  "gsm8k_final_answer": "100",
  "strictness": {"none": true, "min": true, "min-med": true, "med": true, "med-max": false, "max": false}
}
```

### SymbolicSEM

`SymbolicSEM.jsonl` combines a semantic variant with a symbolic/numerical instantiation. In addition to the shared fields, it contains:

| Field | Description |
| --- | --- |
| `symbolic_id` | Identifier of the symbolic source/template. |
| `symbolic_instance` | Identifier of the numerical instantiation within that symbolic source. |
| `symbolic_question` | Symbolically instantiated question before its SEM wording variant. |
| `symbolic_answer` | Worked solution for `symbolic_question`, ending in `#### <answer>`. |

`final_answer` is extracted from the terminal `####` value in `symbolic_answer`. `gsm8k_final_answer` remains the answer to the original GSM8K problem.

```json
{
  "original_id": 930,
  "SEM_id": 255,
  "question": "Liam has a collection of puzzles, with 74 pieces in the jigsaw puzzle box, 42 cards in the memory game deck, and 32 tiles in the dominoes set. After receiving a bag of pick-up sticks, his total number of game pieces is now 189. How many pick-up sticks are in the bag?",
  "final_answer": "41",
  "symbolic_id": 9,
  "symbolic_instance": 1,
  "symbolic_question": "When Ava watches her cousin, she gets out a variety of toys for him. The bag of building blocks has 74 blocks in it. The bin of stuffed animals has 42 stuffed animals inside. The tower of stacking rings has 32 multicolored rings on it. Ava recently bought a tube of bouncy balls, bringing her total number of toys for her cousin up to 189. How many bouncy balls came in the tube?",
  "symbolic_answer": "... #### 41",
  "gsm8k_question": "When Sophie watches her nephew, she gets out a variety of toys for him. The bag of building blocks has 31 blocks in it. The bin of stuffed animals has 8 stuffed animals inside. The tower of stacking rings has 9 multicolored rings on it. Sophie recently bought a tube of bouncy balls, bringing her total number of toys for her nephew up to 62. How many bouncy balls came in the tube?",
  "gsm8k_answer": "... #### 14",
  "gsm8k_final_answer": "14",
  "strictness": {"none": true, "min": true, "min-med": true, "med": true, "med-max": true, "max": false}
}
```

### PlusSEM

`PlusSEM.jsonl` contains GSM-Plus perturbations together with their SEM wording variants. In addition to the shared fields, it contains:

| Field | Description |
| --- | --- |
| `gsmplus_question` | Numerically or structurally perturbed GSM-Plus question. |
| `gsmplus_answer` | Worked solution for `gsmplus_question`, ending in `#### <answer>`. |
| `gsmplus_perturbation_type` | Type of GSM-Plus perturbation, such as `numerical substitution`. |

`final_answer` is the terminal `####` answer in `gsmplus_answer` for the current SEM question; `gsm8k_final_answer` is the terminal answer in `gsm8k_answer` for the original GSM8K question.

```json
{
  "original_id": 434,
  "SEM_id": 415,
  "question": "How much does each candy bar cost if George buys 5 of them after purchasing chips for $1.2, receiving $0.05 in change from a $5 bill?",
  "final_answer": "0.75",
  "gsmplus_question": "The vending machines sell chips for 40 cents. George spent $5 and bought 3 bags of chips and had 1% of his money left. If he bought 5 candy bars, how much does a candy bar cost?",
  "gsmplus_answer": "... #### 0.75",
  "gsmplus_perturbation_type": "reversing operation",
  "gsm8k_question": "The vending machines sell chips for 40 cents and candy bars for 75 cents. George spent $5 and got 3 bags of chips and had 1% of his money left. How many candy bars did he buy?",
  "gsm8k_answer": "... #### 5",
  "gsm8k_final_answer": "5",
  "strictness": {"none": true, "min": true, "min-med": true, "med": true, "med-max": true, "max": false}
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

## Citation

If you use GSM-SEM or any of its variants in your research, please cite:

```bibtex
@article{singh2026gsmsem,
      title={GSM-SEM: Benchmark and Framework for Generating Semantically Variant Augmentations},
      author={Jyotika Singh and Fang Tu and Aziza Mirsaidova and Amit Agarwal and Hitesh Laxmichand Patel and Sandip Ghoshal and Miguel Ballesteros and Karan Dua and Yassine Benajiba and Weiyi Sun and Tao Sheng and Graham Horwood and Sujith Ravi and Dan Roth},
      year={2026},
      eprint={2605.07053},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2605.07053},
}
```