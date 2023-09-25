# Code Scanner

It is designed to detect and analyze code snippets present in the responses generated by a language model. By
identifying the programming languages used in the model's output, platforms can ensure better control over the nature
and type of code shared with users.

## Attack

In some contexts, having a language model inadvertently produce code in its output might be deemed undesirable or risky.
For instance, a user might exploit the model to generate malicious scripts or probe it for potential vulnerabilities.
Controlling and inspecting the code in the model's output can be paramount in ensuring user safety and system integrity.

## How it works

Leveraging the capabilities of
the [huggingface/CodeBERTa-language-id](https://huggingface.co/huggingface/CodeBERTa-language-id) model, the scanner
proficiently identifies code snippets from various programming languages within the model's responses. The scanner can
be configured to either whitelist or blacklist specific languages, granting developers granular control over the type of
code that gets shown in the output.

!!! note
    The scanner is currently limited to extracting and detecting code snippets from Markdown in the following languages:

    - Go
    - Java
    - JavaScript
    - PHP
    - Python
    - Ruby

## Usage

```python
from llm_guard.output_scanners import Code

scanner = Code(allowed=["python"])
sanitized_output, is_valid, risk_score = scanner.scan(prompt, model_output)
```