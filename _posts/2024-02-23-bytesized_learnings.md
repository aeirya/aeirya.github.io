---
layout: posts
title:  "Byte-sized Learnings"
author_profile: true
tags: ["bytesized"]
---

My Notes On Things I Learn

Here I will write very brief notes on things I read and find interesting.

<!--excerpt-->

## [Quantization and Sharding](https://www.maartengrootendorst.com/blog/quantization/#2-sharding): Use less GPU memory

Sharding: Splitting up the model up and distributing weights accross different devices/GPUs. How to: use _accelerate_ to save model.

Quantization: Map a model's larger bit representation to a smaller bit without losing too much information.

Bfloat 16-bit: Same exponential bits as Float 32-bit (8 bits) but less mantissa bits (7 vs 23).

### 4bit-NormalFloat (NF4)

1. Normalize weights into a certain range. 
2. Quantize weights to 4-bit, with evenly spaced quantization levels w.r.t. normalized weights.
3. Dequantize during computation.


```python
from torch import bfloat16
from transformers import BitsAndBytesConfig

bnb_config = BitsAndBytesConfig(
    load_in_4bit=True,              # 4-bit quantization
    bnb_4bit_quant_type='nf4',      # Normalized float 4
    bnb_4bit_use_double_quant=True, # Second quantization after the first
    bnb_4bit_compute_dtype=bfloat16 # Computation type
)
```

### Pre-Quantization: Store quantized model
There are lots of models in [TheBloke](https://huggingface.co/TheBloke)'s account.

#### GPTQ: Post-Training Quantization for GPT
#### GGUF: GPT-Generated Unified Format
Allows users to use the CPU to run an LLM + offload some of its layers to the GPU. Proper for Apple devices.

```py
# Use `gpu_layers` to specify how many layers will be offloaded to the GPU.
model = AutoModelForCausalLM.from_pretrained(
    "TheBloke/zephyr-7B-beta-GGUF",
    model_file="zephyr-7b-beta.Q4_K_M.gguf",
    model_type="mistral", gpu_layers=50, hf=True
)
```

#### AWQ: Activation-aware Weight Quantization
Like GPTQ, but it assumes not all weights are equally important for performance. Good quantization loss, relatively new. How to: _vllm_

```py
from vllm import LLM, SamplingParams

sampling_params = SamplingParams(temperature=0.0, top_p=1.0, max_tokens=256)
llm = LLM(
    model="TheBloke/zephyr-7B-beta-AWQ", 
    quantization='awq', 
    dtype='half', 
    gpu_memory_utilization=.95, 
    max_model_len=4096
)
output = llm.generate(prompt, sampling_params)

```