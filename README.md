# LeetCoTE (LeetCode Training and Evaluation dataset)

<p align="center">
    <a href="https://huggingface.co/datasets/newfacade/LeetCoTE">💻 Data </a> •
</p>

## Introduction

LeetCoTE (LeetCode Training and Evaluation dataset) is a dataset consists of 1700+ Python leetcode problems that can be used for training and evaluation.

## Data Fields

Consistent with [human-eval](https://github.com/openai/human-eval) problem file format.

- `task_id`: corresponding leetcode problem question title slug, relates to problem url
- `prompt`: prefix of completion, e.g basic import
- `entry_point`: function name for evaluation
- `test`: check function using test cases
- `completion`: completion only without the prompt
- `examples`: test cases
- `meta`:
    - `question_id`: leetcode problem question id
    - `difficulty`: Easy, Medium or Hard
    - `lang_code`: completion format
    - `en_question_title`: problem description
    - `en_src`: query
    - `en_tgt`: correct response

## Data Curation

We use [python-leetcode](https://github.com/fspv/python-leetcode) to collect problems and corresponding metadata, then we split problem description into two parts: description without examples and examples, concatenate description without examples and `lang_code` to get query, parse examples to get test case. Finally, extract completion from [doocs/leetcode](https://github.com/doocs/leetcode), test cases and completion are cross verified.
 
## Training
  
## Evaluation
