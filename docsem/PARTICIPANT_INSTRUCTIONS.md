# Document-Grounded Quantitative Reasoning - Participant Instructions

## Task

Each instance provides a PDF document and a separate `user_query`. Locate the relevant passage in the PDF, reason only from that passage, and return the final numerical answer together with the supporting PDF block ID(s). Documents contain background prose, tables, dates, numerical facts, and unrelated questions; do not combine facts from different passages unless the target scenario explicitly requires it.

The `user_query` paraphrases the relevant information need. It does not copy the target question, its numerical inputs, or a request identifier from the PDF.

## Input format

Each JSONL line is one instance:

```json
{
  "instance_id": "task_000001",
  "user_query": "Use the relevant quantitative passage in this document to determine the outcome concerning fog and city.",
  "document_pdf": "documents/task_000001.pdf"
}
```

`document_pdf` is relative to the split directory. Read the PDF as an ordinary document: headings, paragraphs, lists, and tables are visual presentation elements, not a structured input schema. Every content block begins with a visible identifier in the form `b01: <block content>`; use these identifiers when reporting evidence.

The train split includes a separate `labels.jsonl` for local development. The validation manifest contains only `instance_id`, `user_query`, and `document_pdf`; its labels are organizer-only.

## Required prediction format

Submit one JSON object per validation instance, in any order:

```json
{
  "instance_id": "task_000001",
  "answer": "140",
  "evidence": ["b14"]
}
```

Requirements:

- `instance_id` must exactly match the input instance.
- `answer` must contain only the final answer, with no explanation or units unless the answer itself requires a unit.
- `evidence` must be a non-empty list of visible PDF block IDs.
- Include every block directly needed to state the target question and its inputs.

## Evaluation

The primary score is normalized exact-match accuracy on `answer`. Answers are normalized by trimming whitespace, ignoring case, removing a leading final-answer marker, and treating numerically equivalent decimal forms as equal where applicable. Evidence is evaluated separately by exact block-set match, with evidence F1 reported as a diagnostic measure.

## Data access

The public package contains labelled train data and unlabelled validation inputs.
Validation labels remain private and are used only by the official submission portal.

Each task uses an opaque identifier. Do not infer answers from filenames,
document metadata, or external source-question lookup; solve from the supplied PDF.

## Use of external data and systems

Participants should document the model(s), external training data, retrieval
resources, tools, and prompting strategy used by their system. Organizers will
publish citation and provenance information with the workshop materials.
