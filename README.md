# LeetCoTE (LeetCode Training and Evaluation dataset)

<p align="center">
    <a href="https://huggingface.co/datasets/newfacade/LeetCoTE">💻 Data </a> •
</p>

## Introduction

LeetCoTE (LeetCode Training and Evaluation dataset) is a dataset consists of 1700+ Python leetcode problems that can be used for LLM training and evaluation.

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

We use [python-leetcode](https://github.com/fspv/python-leetcode) to collect problems and corresponding metadata, then we split problem description into two parts: description without examples and examples, concatenate description without examples and `lang_code` to get query, parse examples to get test case. Finally, we extract completion from [doocs/leetcode](https://github.com/doocs/leetcode), test cases and completion are cross verified using [human-eval](https://github.com/openai/human-eval).
 
## Training

To use LeetCoTE for training:

1. Split LeetCoTE into train and eval dataset, order LeetCoTE by `question_id` and use problems with bigger `question_id` for evaluation if a good choice.
2. `meta.en_src` as query, `meta.en_tgt` as response, SFT train the LLM using the train set.
  
## Evaluation

We evaluate based on [human-eval](https://github.com/openai/human-eval), suppose you split LeetCoTE and get a evaluation file `leetcote_eval_problem.jsonl`, now you just need to generate completion for each query, suppose you save the completion file as `leetcote_eval_completions.jsonl`, then that command will evaluate completions for you:

```shell
$ evaluate_functional_correctness leetcote_eval_completions.jsonl --problem_file=leetcote_eval_problem.jsonl
```
