# Document-Grounded Quantitative Reasoning Shared Task

This directory contains the participant release for the DocInsights 2026 shared task.

Each task provides a PDF document and a paraphrased user query. Systems must locate the relevant passage, calculate the requested result from that document, and return the supporting visible PDF block ID(s).

All participant task IDs and PDF filenames are opaque. Solve only from the provided PDF; do not infer answers from filenames, metadata, or external source-question lookup.

## Splits

| Split | Tasks | Public labels | Purpose |
| --- | ---: | --- | --- |
| `train` | 908 | Yes | Develop and test a system locally. |
| `val` | 217 | No | Submit predictions to the official leaderboard. |

Each split contains `tasks.jsonl` and a `documents/` directory. The train split also contains `labels.jsonl` with the final answer and exact evidence block IDs.

Every task row has only:

```json
{
  "instance_id": "task_000001",
  "user_query": "Use the relevant quantitative passage in this document to determine the requested result.",
  "document_pdf": "documents/task_000001.pdf"
}
```

Read [PARTICIPANT_INSTRUCTIONS.md](PARTICIPANT_INSTRUCTIONS.md) before building or submitting a system.

Submit a complete validation JSONL file through the [submission portal](https://amitbcp-docsem-docinsights.hf.space/). The workshop page and public data mirror are available at [DocInsights 2026](https://docinsights-workshop.github.io/docinsights-2026/shared-task/) and [Hugging Face](https://huggingface.co/datasets/amitbcp/docinsights-2026-shared-task-data).

## License

Copyright (c) 2026 Oracle and/or its affiliates. Released under the [Universal Permissive License v1.0](../LICENSE.txt).

## Citation

If you use this shared-task release, please cite the originating paper:

```bibtex
@article{singh2026gsmsem,
  title={GSM-SEM: Benchmark and Framework for Generating Semantically Variant Augmentations},
  author={Jyotika Singh and Fang Tu and Aziza Mirsaidova and Amit Agarwal and Hitesh Laxmichand Patel and Sandip Ghoshal and Miguel Ballesteros and Karan Dua and Yassine Benajiba and Weiyi Sun and Tao Sheng and Graham Horwood and Sujith Ravi and Dan Roth},
  year={2026},
  eprint={2605.07053},
  archivePrefix={arXiv},
  primaryClass={cs.CL},
  url={https://arxiv.org/abs/2605.07053}
}
```
