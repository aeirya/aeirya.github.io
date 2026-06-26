---

layout: single
title: "Opfel"
permalink: /projects/opfel/
excerpt: "A small Ollama-based bridge for Apfeller."
classes: wide
-------------

# Opfel

**Opfel** is a small local-AI utility that lets **Apfeller** talk to **Ollama** instead of relying on Apfel.

It is simple by design: Apfeller plugins send their requests as usual, and Opfel redirects them to a local Ollama model. The goal is to make the same workflow more flexible, local, and hackable.

[View on GitHub](https://github.com/aeirya/opfel)

## Notes

* Built with Python and shell scripting
* Requires Ollama, Apfeller, and Python 3
* Install with `./install.sh [LLM tag]`
