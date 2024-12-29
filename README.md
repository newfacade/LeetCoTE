# LeetCoTE (LeetCode Training and Evaluation dataset)

<p align="center">
    <a href="https://huggingface.co/datasets/newfacade/LeetCoTE">💻 Data </a> •
</p>

## Introduction

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
 
## Training
  
## Evaluation
