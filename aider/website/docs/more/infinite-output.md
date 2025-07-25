---
parent: More info
nav_order: 480
description: Aider can handle "infinite output" from models that support prefill.
---

# Infinite output

LLM providers limit how much output a model can generate from a single request.
This is usually called the output token limit.

Aider is able to work around this limit with models that support
"prefilling" the assistant response.
When you use aider with a model that supports prefill, you will see
"infinite output" noted in the announcement lines displayed at launch:

```
Aider v0.58.0
Main model: claude-3-5-sonnet-20240620 with diff edit format, prompt cache, infinite output
```

Models that support prefill can be primed to think they started their response
with a specific piece of text.
You can put words in their mouth, and they will continue generating
text from that point forward.

When aider is collecting code edits from a model and
it hits the output token limit,
aider simply initiates another LLM request with the partial
response prefilled.
This prompts the model to continue where it left off,
generating more of the desired response.
This prefilling of the partially completed response can be repeated,
allowing for very long outputs.
Joining the text across these output limit boundaries 
requires some heuristics, but is typically fairly reliable.

Aider supports "infinite output" for models that support "prefill",
such as:

<!--[[[cog
import requests
import json

# Fetch the JSON data
url = "https://raw.githubusercontent.com/BerriAI/litellm/refs/heads/main/model_prices_and_context_window.json"
response = requests.get(url)
data = json.loads(response.text)

# Process the JSON to find models with supports_assistant_prefill=true
prefill_models = [model for model, info in data.items() if info.get('supports_assistant_prefill') == True]

# Generate the list of models
model_list = "\n".join(f"- {model}" for model in sorted(prefill_models))

cog.out(model_list)
]]]-->
- anthropic.claude-3-5-haiku-20241022-v1:0
- anthropic.claude-3-5-sonnet-20241022-v2:0
- anthropic.claude-3-7-sonnet-20250219-v1:0
- anthropic.claude-opus-4-20250514-v1:0
- anthropic.claude-sonnet-4-20250514-v1:0
- apac.anthropic.claude-3-5-sonnet-20241022-v2:0
- apac.anthropic.claude-sonnet-4-20250514-v1:0
- azure_ai/mistral-medium-2505
- claude-3-5-haiku-20241022
- claude-3-5-haiku-latest
- claude-3-5-sonnet-20240620
- claude-3-5-sonnet-20241022
- claude-3-5-sonnet-latest
- claude-3-7-sonnet-20250219
- claude-3-7-sonnet-latest
- claude-3-haiku-20240307
- claude-3-opus-20240229
- claude-3-opus-latest
- claude-3-sonnet-20240229
- claude-4-opus-20250514
- claude-4-sonnet-20250514
- claude-opus-4-20250514
- claude-sonnet-4-20250514
- codestral/codestral-2405
- codestral/codestral-latest
- databricks/databricks-claude-3-7-sonnet
- deepseek/deepseek-chat
- deepseek/deepseek-coder
- deepseek/deepseek-r1
- deepseek/deepseek-reasoner
- deepseek/deepseek-v3
- eu.anthropic.claude-3-5-haiku-20241022-v1:0
- eu.anthropic.claude-3-5-sonnet-20241022-v2:0
- eu.anthropic.claude-3-7-sonnet-20250219-v1:0
- eu.anthropic.claude-opus-4-20250514-v1:0
- eu.anthropic.claude-sonnet-4-20250514-v1:0
- mistral/codestral-2405
- mistral/codestral-latest
- mistral/codestral-mamba-latest
- mistral/devstral-small-2505
- mistral/magistral-medium-2506
- mistral/magistral-medium-latest
- mistral/magistral-small-2506
- mistral/magistral-small-latest
- mistral/mistral-large-2402
- mistral/mistral-large-2407
- mistral/mistral-large-2411
- mistral/mistral-large-latest
- mistral/mistral-medium
- mistral/mistral-medium-2312
- mistral/mistral-medium-2505
- mistral/mistral-medium-latest
- mistral/mistral-small
- mistral/mistral-small-latest
- mistral/mistral-tiny
- mistral/open-codestral-mamba
- mistral/open-mistral-7b
- mistral/open-mistral-nemo
- mistral/open-mistral-nemo-2407
- mistral/open-mixtral-8x22b
- mistral/open-mixtral-8x7b
- mistral/pixtral-12b-2409
- mistral/pixtral-large-2411
- mistral/pixtral-large-latest
- openrouter/anthropic/claude-3.5-sonnet
- openrouter/anthropic/claude-3.7-sonnet
- openrouter/anthropic/claude-sonnet-4
- openrouter/deepseek/deepseek-r1
- openrouter/deepseek/deepseek-r1-0528
- us.anthropic.claude-3-5-haiku-20241022-v1:0
- us.anthropic.claude-3-5-sonnet-20241022-v2:0
- us.anthropic.claude-3-7-sonnet-20250219-v1:0
- us.anthropic.claude-opus-4-20250514-v1:0
- us.anthropic.claude-sonnet-4-20250514-v1:0
- vertex_ai/claude-3-5-haiku
- vertex_ai/claude-3-5-haiku@20241022
- vertex_ai/claude-3-5-sonnet
- vertex_ai/claude-3-5-sonnet-v2
- vertex_ai/claude-3-5-sonnet-v2@20241022
- vertex_ai/claude-3-5-sonnet@20240620
- vertex_ai/claude-3-7-sonnet@20250219
- vertex_ai/claude-3-haiku
- vertex_ai/claude-3-haiku@20240307
- vertex_ai/claude-3-opus
- vertex_ai/claude-3-opus@20240229
- vertex_ai/claude-3-sonnet
- vertex_ai/claude-3-sonnet@20240229
- vertex_ai/claude-opus-4
- vertex_ai/claude-opus-4@20250514
- vertex_ai/claude-sonnet-4
- vertex_ai/claude-sonnet-4@20250514
<!--[[[end]]]-->


