# CAKE-Bench

Companion repository for the paper:

> **CAKE: Cloud Architecture Knowledge Evaluation of Large Language Models**
>
> Tim Lukas Adam, Phongsakon Mark Konrad, Riccardo Terrenzi, Florian Girardo Lukas, Rahime Yilmaz, Krzysztof Sierszecki, Serkan Ayvaz
>
> Centre for Industrial Software, University of Southern Denmark

## Benchmark Variants

### CAKE-Full (200 questions)

The complete question bank: 200 questions across four cognitive levels and five cloud-native topics. Of these, 188 were used in the paper's evaluation (12 implement-level MCQs were excluded due to a formatting defect in the options array; see Section V of the paper).

### CAKE-Core (128 questions)

A quality-filtered subset of CAKE-Full. A question is included if it meets all of the following criteria based on independent expert annotations (excluding admin):

- Mean correctness >= 4.0 (out of 5)
- Minimum clarity >= 4 (every expert rated clarity at least 4)
- No ambiguity flags from any expert
- No typo flags from any expert

CAKE-Core is the recommended subset for benchmarking, as it controls for question quality variation.

## Dataset Overview

| Cognitive Level | MCQ | Free-response | CAKE-Full | CAKE-Core |
|-----------------|-----|---------------|-----------|-----------|
| Recall          | 50  | 0             | 50        | 41        |
| Analyze         | 56  | 4             | 60        | 40        |
| Design          | 24  | 26            | 50        | 19        |
| Implement       | 12  | 28            | 40        | 28        |
| **Total**       | **142** | **58**    | **200**   | **128**   |

Note: 12 implement-level MCQs were excluded from the paper's evaluation due to a formatting defect, reducing the evaluated MCQ set to 130.

**Topics**: architectural patterns, quality attributes, decomposition strategies, cloud deployment, technical debt.

## Structure

```
questions/
├── full/                               CAKE-Full (200 questions)
│   ├── questions_batch1_recall.json
│   ├── questions_batch2_analyze.json
│   ├── questions_batch3_design.json
│   └── questions_batch4_implement.json
│
└── core/                               CAKE-Core (128 questions)
    ├── questions_batch1_recall.json
    ├── questions_batch2_analyze.json
    ├── questions_batch3_design.json
    └── questions_batch4_implement.json
```

## Question Format

MCQ:

```json
{
  "id": "Q001",
  "question": "What are the three states of a Circuit Breaker pattern?",
  "options": ["Open, Closed, Half-Open", "Active, Inactive, Pending", "..."],
  "correct_answer": "Open, Closed, Half-Open",
  "explanation": "...",
  "topic": "architectural_patterns",
  "skill": "recall",
  "difficulty": "easy"
}
```

Free-response:

```json
{
  "id": "Q131",
  "question": "Design a migration strategy ...",
  "expected_answer": "...",
  "rubric": "Award 5 if ...; 4 if ...; ...",
  "topic": "decomposition",
  "skill": "design",
  "difficulty": "hard"
}
```

## License

This dataset is released for research purposes.
