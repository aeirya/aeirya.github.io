---
layout: posts
title:  "Extremely brief paper notes"
author_profile: true
tags: ["bytesized", "paper"]
---

Here I share my brief and shallow summarization notes of some of articles I find interesting.

## 2023

### Why Does Zero-Shot Cross-Lingual Generation Fail? An Explanation and a Solution

Hypothesis is, fine-tuning on a single source language increases the XLRS between the source and other languages. As a result, generation is tricker than classification because of unwanted language switch in output. The paper proposed to **use an additional source language** for fine-tuning to explicitly **regularize XLRS**.

### Revisiting Relation Extraction in the era of Large Language Models

ACL 2023

- How to few-shot RE: insert ~10 examples in prompt
- Chain-of-thought (CoT):
    - For in-context GPT-3: 76.5 -> 78.2
    - Generate it with GPT!
    - Used for Flan T5 Large
        - Use in fully-supervised training (80.76, best score)
        - or few-shot setting (76.13)
- Strict evaluation isn't most suited for LLM-extracted relation types. 

### GPT-RE: In-context Learning for Relation Extraction using Large Language Models

EMNLP 2023

- Use best examples for few-shot:

    Encode sentences and retrieve best with kNN
    1. Encode with SimCSE template: The relation between $e_1$ and $e_2$ is: *sentence* 
    2. Encode with BERT-based FT methods: [CLS][SUB_PER]...

- Enrich prompt with GPT-3-generated reasoning:
What are the clues that lead to the relation between [$e_1$] and [$e_2$] to be [relation] in the sentence [context]?
