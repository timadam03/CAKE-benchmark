# CAKE-Bench

Companion repository for the paper:

> **CAKE: Cloud Architecture Knowledge Evaluation of Large Language Models**
>
> Tim Lukas Adam, Phongsakon Mark Konrad, Riccardo Terrenzi, Florian Girardo Lukas, Rahime Yilmaz, Krzysztof Sierszecki, Serkan Ayvaz
>
> Centre for Industrial Software, University of Southern Denmark

## Benchmark Variants

### CAKE-Full (188 questions)

The complete question bank: 188 questions across four cognitive levels and five cloud-native topics. 12 MCQ-Implement questions were excluded due to formatting issues, see Section V-C of the paper.

### CAKE-Core (116 questions)

A quality-filtered subset of CAKE-Full. A question is included if it meets all of the following criteria based on independent expert annotations (excluding admin):

- Mean correctness >= 4.0 (out of 5)
- Minimum clarity >= 4 (every expert rated clarity at least 4)
- No ambiguity flags from any expert
- No typo flags from any expert

CAKE-Core is the recommended subset for benchmarking, as it controls for question quality variation.

## Dataset Overview

| Cognitive Level | MCQ     | Free-response | CAKE-Full | CAKE-Core |
|-----------------|---------|---------------|-----------|-----------|
| Recall          | 50      | 0             | 50        | 41        |
| Analyze         | 56      | 4             | 60        | 40        |
| Design          | 24      | 26            | 50        | 19        |
| Implement       | 0       | 28            | 28        | 16        |
| **Total**       | **130** | **58**        | **188**   | **116**   |

Note: 12 implement-level MCQs were excluded from the paper's evaluation due to a formatting defect, reducing the evaluated MCQ set to 130.

**Topics**: architectural patterns, quality attributes, decomposition strategies, cloud deployment, technical debt.

## Structure

```
CAKE-questions/
├── CAKE-Core.json                      Core CAKE-benchmark (116 questions)
│
└── CAKE-Full.json                      Full CAKE-benchmark (188 questions)

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
