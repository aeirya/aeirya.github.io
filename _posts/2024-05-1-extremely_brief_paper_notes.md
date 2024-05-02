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

