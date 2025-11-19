# Gemini 3.0 Pro API

> One unified entry to Google’s latest Gemini 3.0 Pro, with stronger reasoning, richer multimodal understanding, and production‑grade reliability – powered by EvoLink.

[![Status](https://img.shields.io/badge/Gemini%203.0%20Pro-Preview-blue)](#)  
[![API](https://img.shields.io/badge/API-EvoLink%20Unified%20Gateway-success)](#)  
[![Formats](https://img.shields.io/badge/Format-OpenAI%20SDK%20%7C%20Google%20Native-informational)](#)

**Project website:** https://gemini3api.com  
> `gemini3api.com` is a focused Gemini 3 landing page built on top of EvoLink, guiding you to the right docs, models, and EvoLink signup.

---

## Table of Contents

1. [Overview: What Is Gemini 3.0 Pro?](#overview-what-is-gemini-30-pro)
2. [Key Capabilities](#key-capabilities)
3. [Model Comparison: GPT‑5 / Claude 4.5 / Gemini 2.5 / Qwen 3](#model-comparison-gpt5--claude-45--gemini-25--qwen-3)
4. [Why Use Gemini 3 via EvoLink & gemini3api.com?](#why-use-gemini-3-via-evolink--gemini3apicom)
5. [Quickstart: OpenAI SDK Format](#quickstart-openai-sdk-format)
6. [Quickstart: Google Native API Format](#quickstart-google-native-api-format)
7. [Async Jobs & Production Workloads](#async-jobs--production-workloads)
8. [Advanced Usage Examples](#advanced-usage-examples)
9. [Best Practices: Choosing Between Models](#best-practices-choosing-between-models)
10. [FAQ](#faq)

---

## Overview: What Is Gemini 3.0 Pro?

Gemini 3.0 Pro is Google’s latest flagship general‑purpose model. Compared with the Gemini 2.x family, its positioning is clear:

- **Much stronger complex reasoning**: Leading performance on ARC‑AGI‑2, GPQA Diamond, Humanity’s Last Exam and other hard benchmarks (based on sources like Vellum and THE DECODER).
- **Natively multimodal**: A single model that jointly handles text, images, audio, and video, and reasons across modalities.
- **Very long context and large outputs**: Public benchmarks show context windows up to around 1M tokens and output windows in the tens of thousands of tokens (exact limits depend on provider/platform).
- **Agent‑ready**: Designed for tool use, long‑horizon planning, and multi‑step workflows, with clear improvements over Gemini 2.5.

From a user’s point of view:  
If you want a model that not only “answers questions” but can **decompose complex tasks, plan multi‑step workflows, understand rich multimodal context, and produce stable, reliable plans**, Gemini 3.0 Pro is built for that.

Through **EvoLink** – and the dedicated entrypoint **https://gemini3api.com** – you can call Gemini 3 via a single unified API gateway, either in OpenAI‑compatible format or Google Native API format, without wiring up multiple cloud providers yourself.

---

## Key Capabilities

Combining Google’s official materials with third‑party evaluations (Vellum, THE DECODER, Kilo Code, etc.), Gemini 3.0 Pro stands out in several areas:

- **Substantially improved reasoning**
  - Strong scores on GPQA Diamond (PhD‑level QA), Humanity’s Last Exam, ARC‑AGI‑2, and more, clearly ahead of Gemini 2.5 and often ahead of GPT‑5.1 / Claude 4.5 on reasoning‑heavy tasks.
  - More stable on abstract puzzles, math, and cross‑disciplinary questions – ideal for architecture design, scientific analysis, strategy/finance reasoning, and similar workloads.

- **Native multimodal understanding**
  - Third‑party reports highlight a key strength: multimodality.
  - Leading results on MMMU‑Pro and Video‑MMMU; on ScreenSpot‑Pro (UI screen understanding) Gemini 3 Pro significantly outperforms GPT‑5.1 and Claude 4.5.
  - Practically, this makes it great for **explaining videos, understanding product dashboard screenshots, analyzing complex UIs, and reasoning over code+UI contexts**.

- **Long context & high throughput**
  - Context windows in the ~1M‑token range and output windows up to ~60K tokens (varies by provider).
  - Well‑suited for long‑document QA, repository‑scale code refactors, and multi‑hour meeting/video summarization.

- **Agentic behavior & automation**
  - Strong performance on long‑horizon/agent benchmarks (e.g., Vending‑Bench‑type evaluations), with consistent tool use and planning.
  - Crucial for AI agents that need to call tools repeatedly, navigate file systems, and orchestrate multi‑step flows with minimal supervision.

---

## Model Comparison: GPT‑5 / Claude 4.5 / Gemini 2.5 / Qwen 3

> The table below is a directional comparison drawn from public sources (Vellum, Vals, THE DECODER, etc.). Exact numbers and limits should be confirmed with each provider.

### Capability Comparison (High‑Level)

| Model                | Provider | Approx Release Time | Main Positioning                         | Reasoning / Exams (qualitative)                           | Multimodal (qualitative)                      | Context Size (directional)         | Best‑Fit Scenarios                                      |
|----------------------|----------|---------------------|-------------------------------------------|-----------------------------------------------------------|-----------------------------------------------|------------------------------------|--------------------------------------------------------|
| **Gemini 3.0 Pro**   | Google   | 2025 Q4 (Preview)   | Flagship + Reasoning + Multimodal + Agent | Leading on ARC‑AGI‑2 / GPQA / Humanity’s Last Exam, etc. | Leading on MMMU‑Pro, Video‑MMMU, ScreenSpot   | ~1M context, 10K+ output tokens    | Complex reasoning, multimodal, agents, long docs/repos |
| **GPT‑5 / 5.1**      | OpenAI   | 2025 (iterating)    | Flagship + Ecosystem                      | Very strong; slightly lower than Gemini 3 on some tests   | Strong multimodal, slightly weaker in some UI/video tests | 100K–1M (by tier)                 | General apps, plugin/extension ecosystem, UX           |
| **Claude 4.5 family**| Anthropic| 2025                | Safety, dialogue, writing & summarization | Excellent reasoning, especially long‑text analysis        | Multimodal support; slightly behind Gemini 3 on some UI tests | Hundreds of thousands tokens      | Writing, knowledge bases, safety‑sensitive workloads   |
| **Gemini 2.5 Pro**   | Google   | 2025 H1             | Previous flagship, reasoning & multimodal | Noticeably weaker than 3.0 Pro                           | Strong multimodal, but behind 3.0 in hard tasks | Hundreds of thousands–1M (tier‑specific) | Cost‑sensitive workloads with moderate performance needs |
| **Qwen 3 Max / VL**  | Alibaba  | 2025 H2             | Multilingual, code, Chinese‑first         | Very solid on math and coding                             | VL variants offer strong multimodality        | ~200K context (varies)             | Chinese workloads, code, localized vertical domains    |

You can read this table as:

- If you care most about **“top‑end reasoning + multimodal + agents”**, Gemini 3.0 Pro is a very strong first choice or benchmark model.
- If you prioritize **ecosystem/plugins/deployment breadth**, GPT‑5 remains essential.
- Claude 4.5 shines in **writing, summarization, and dialogue quality**, especially on long texts.
- Qwen 3 is highly competitive for **Chinese, code, and localized scenarios**.
- With **EvoLink + gemini3api.com** you can A/B test and switch between these models behind a single unified gateway.

---

## Why Use Gemini 3 via EvoLink & gemini3api.com?

EvoLink is not a single model; it’s a **unified AI gateway** that exposes many frontier models through one API. Gemini 3 is one of the flagships under the “Text Series”.

**gemini3api.com** sits on top of this gateway as a **focused Gemini 3 landing page**:

- A clean entrypoint to understand Gemini 3’s strengths.
- A direct bridge into EvoLink’s console, docs, and keys.
- A marketing/developer funnel dedicated to Gemini 3 use cases.

Compared to wiring up multiple cloud providers yourself, EvoLink + gemini3api.com offers:

- **One key for many models**
  - Single API base: `https://api.evolink.ai`.
  - No need to juggle separate Google/OpenAI/Alibaba credentials and billing.

- **Two request formats, one backend**
  - **OpenAI SDK format**  
    Use `/v1/chat/completions` with `model: "gemini-3-pro-preview"`. You can mostly reuse existing OpenAI SDK code.
  - **Google Native API format**  
    Use `/v1beta/models/gemini-3-pro-preview:{method}` (`generateContent` / `streamGenerateContent`), with the familiar `contents`/`parts` structure.

- **Unified async jobs & monitoring**
  - For heavy jobs, set `X-Async-Mode: true` to return a task ID immediately.
  - Use `GET /v1/tasks/{task_id}` to poll status and fetch results (shared pattern across image, video, and text jobs).
  - Shared statuses (`pending` / `running` / `completed` / `failed`) and unified cost estimates.

- **Multi‑series models under one roof**
  - Image Series: `gpt-4o-image`, Seedream, Qwen, Wan, etc.
  - Video Series: `veo3`, `sora2`, etc.
  - Text Series: Gemini 3 / Gemini 2.5 / Claude / Kimi K2 / others.
  - You can string together text, image, video, and multimodal workflows in a single project.

If you just want the “shortest path” to trying Gemini 3, start here: **https://gemini3api.com**.

---

## Quickstart: OpenAI SDK Format

The OpenAI‑style API is ideal if you already have OpenAI code. Migration is almost zero‑effort.

### 1. Get an API Key

1. Visit **https://gemini3api.com** and follow the link to EvoLink signup (or go directly to https://evolink.ai/).
2. Open **Dashboard → API Keys**:  
   https://evolink.ai/dashboard/keys  
3. Create a new key and store it securely, e.g. `sk-evo-xxxxxxxxxx`.

Add the following headers to your requests:

```http
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```

### 2. Minimal cURL Example

Use `chat.completions` with `model: "gemini-3-pro-preview"`:

```bash
curl --request POST \
  --url https://api.evolink.ai/v1/chat/completions \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "model": "gemini-3-pro-preview",
    "messages": [
      {
        "role": "user",
        "content": "Introduce yourself in three sentences and give one ideal use case for you."
      }
    ]
  }'
```

Typical response (adapted from EvoLink docs):

```json
{
  "id": "chatcmpl-20251010015944503180122WJNB8Eid",
  "model": "gemini-3-pro-preview",
  "object": "chat.completion",
  "created": 1760032810,
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "Hello! I'm a Large Language Model, trained and developed by Google..."
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 13,
    "completion_tokens": 1891,
    "total_tokens": 1904,
    "completion_tokens_details": {
      "reasoning_tokens": 1480
    }
  }
}
```

Note the `reasoning_tokens` field inside `usage`, which helps you understand how much of the budget went into deep reasoning.

### 3. Python Example (OpenAI SDK Compatible)

If you’re using the official `openai` SDK, simply point `base_url` to EvoLink:

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://api.evolink.ai/v1"
)

resp = client.chat.completions.create(
    model="gemini-3-pro-preview",
    messages=[
        {
            "role": "system",
            "content": "You are a senior architect, strong in reasoning and multimodal understanding."
        },
        {
            "role": "user",
            "content": "Design a code review workflow powered by Gemini 3, with a focus on security and maintainability."
        }
    ]
)

print(resp.choices[0].message.content)
```

### 4. Streaming Responses

EvoLink’s OpenAI‑style interface supports the familiar `stream` flag:

```python
stream = client.chat.completions.create(
    model="gemini-3-pro-preview",
    messages=[{"role": "user", "content": "Explain quicksort step by step."}],
    stream=True,
)

for chunk in stream:
    delta = chunk.choices[0].delta.content or ""
    print(delta, end="", flush=True)
```

---

## Quickstart: Google Native API Format

If you’re used to Google’s Gemini Native API (`generateContent` / `streamGenerateContent`), EvoLink exposes a compatible surface.

### 1. Basic Request Structure

As per EvoLink’s docs:  
`POST https://api.evolink.ai/v1beta/models/gemini-3-pro-preview:{method}`

- `method` is a path parameter:
  - `generateContent`: return the full response at once.
  - `streamGenerateContent`: return a streaming response.

Example (simple text conversation):

```bash
curl --request POST \
  --url "https://api.evolink.ai/v1beta/models/gemini-3-pro-preview:generateContent" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "contents": [
      {
        "role": "user",
        "parts": [
          { "text": "Please introduce yourself" }
        ]
      }
    ]
  }'
```

Typical response (adapted from EvoLink docs):

```json
{
  "candidates": [
    {
      "content": {
        "role": "model",
        "parts": [
          {
            "text": "Hello! I'm a large language model, trained and developed by Google..."
          }
        ]
      },
      "finishReason": "STOP",
      "index": 0,
      "safetyRatings": [{}]
    }
  ],
  "usageMetadata": {
    "promptTokenCount": 4,
    "candidatesTokenCount": 611,
    "totalTokenCount": 2422,
    "thoughtsTokenCount": 1807
  }
}
```

### 2. Async Mode

Enable async processing via the header:

```http
X-Async-Mode: true
```

When `X-Async-Mode=true`, both `generateContent` and `streamGenerateContent` return an **async task response** with a `task_id`, instead of waiting for the full output.

Example:

```bash
curl --request POST \
  --url "https://api.evolink.ai/v1beta/models/gemini-3-pro-preview:generateContent" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --header "X-Async-Mode: true" \
  --data '{
    "contents": [
      {
        "role": "user",
        "parts": [
          { "text": "Analyze this 50-page technical document and propose an architecture refactor plan." }
        ]
      }
    ]
  }'
```

The response will contain a `task_id`. Later, fetch the result with:

```bash
curl "https://api.evolink.ai/v1/tasks/{task_id}" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

This pattern is shared across other heavy workloads (image generation, video generation, etc.) in EvoLink.

---

## Async Jobs & Production Workloads

In production, Gemini 3 is rarely used only for “simple chat” – typical workloads include:

- Batch analysis of long documents or repositories.
- Multimodal analysis (images + text + logs).
- Multi‑stage pipelines: e.g., ingest PDFs → summarize → emit structured JSON → trigger downstream jobs.

Recommended pattern:

- **Submit heavy jobs with `X-Async-Mode=true`**
  - Avoid frontend/backend timeouts.
  - Especially important when output is long or latency is unpredictable.

- **Use the unified Task API for polling or notifications**
  - `GET /v1/tasks/{task_id}` exposes:
    - `status`: `pending` / `running` / `completed` / `failed`
    - `progress`: 0–100
    - `results`: model outputs
    - `usage`: reserved credits / estimated cost, etc.
  - You can send callbacks/notifications when tasks finish, or implement progress bars on the frontend.

- **Centralize monitoring and cost control**
  - Fields like `promptTokenCount`, `candidatesTokenCount`, `thoughtsTokenCount` help you:
    - Understand average reasoning depth per job.
    - Spot cost concentration in a few very hard tasks.
  - Combine EvoLink’s dashboard with your own telemetry for full visibility.

---

## Advanced Usage Examples

### 1. Multi‑Turn Conversation (OpenAI SDK Format)

```python
from openai import OpenAI

client = OpenAI(api_key="YOUR_API_KEY", base_url="https://api.evolink.ai/v1")

messages = [
    {
        "role": "system",
        "content": "You are a senior technical consultant, expert in system architecture and AI product design."
    },
    {
        "role": "user",
        "content": "I’m building a fast‑growing SaaS product. How can I use Gemini 3 to build an intelligent support copilot?"
    }
]

resp = client.chat.completions.create(
    model="gemini-3-pro-preview",
    messages=messages,
    temperature=0.3
)

print(resp.choices[0].message.content)
```

### 2. Multimodal Input (Google Native: Text + Image)

Below is a schematic request (for actual file handling, refer to EvoLink’s `image_understanding` / `multi_file` examples):

```json
POST https://api.evolink.ai/v1beta/models/gemini-3-pro-preview:generateContent
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json

{
  "contents": [
    {
      "role": "user",
      "parts": [
        { "text": "Look at this product metrics dashboard and explain anomalies for this month in a non-technical way." },
        {
          "file_data": {
            "file_uri": "https://your-cdn.com/dashboard.png",
            "mime_type": "image/png"
          }
        }
      ]
    }
  ]
}
```

Gemini 3 will jointly reason over the text instructions and the image, which is extremely useful for operations, analytics, and product reviews.

### 3. Structured Output & Tooling

Gemini 3 is very good at producing structured outputs for downstream tools. You can enforce JSON‑only responses via prompt:

```python
system_prompt = """
You are a strict JSON generator. Always output valid JSON only.

Response schema:
{
  "risks": [
    {"type": "string", "severity": "low|medium|high", "description": "string"}
  ],
  "opportunities": [
    {"area": "string", "impact": "string"}
  ]
}
"""

user_prompt = "Read this business plan (omitted) and analyze key risks and opportunities."

# Then call Gemini 3 with these prompts, same as above.
```

On top of EvoLink, you can feed this structured output directly into risk systems, BI, or any automation pipeline.

---

## Best Practices: Choosing Between Models

When you have GPT‑5 / Claude 4.5 / Gemini 2.5 / Qwen 3 / Gemini 3 all available, use the following mental model:

### 1. Choose by Task Type

- **Complex reasoning, multimodal synthesis, agents/multi‑step automation**
  - Prefer: **Gemini 3.0 Pro**
- **Ecosystem, plugins, tight integration with existing OpenAI stack**
  - Prefer: **GPT‑5 / 5.1**
- **Long‑form summarization, writing, enterprise knowledge bases**
  - Prefer: **Claude 4.5 family**
- **Chinese‑first workloads, localization, cost‑sensitive coding tasks**
  - Prefer: **Qwen 3 Max / VL**
- **Cost‑optimized workloads with moderate performance needs**
  - Consider: **Gemini 2.5 Pro / Flash**

### 2. Choose by Cost Shape

- Gemini 3 is priced for reasoning‑heavy use cases: per‑token cost can be higher, but it often saves retries and manual iterations.
- In EvoLink, you can:
  - Use **Gemini 3** for “hard / critical path” steps.
  - Use **Gemini 2.5 / Qwen 3 / lighter models** for bulk/simple tasks.
  - Control traffic per model via the `model` field.

### 3. Ship Decisions via A/B Testing

With EvoLink and gemini3api.com:

- Same endpoint, different `model` values:
  - `gemini-3-pro-preview`
  - `gpt-5` (example)
  - `qwen-3-max`
- Application‑level strategy:
  - Route 10% of traffic to Gemini 3 and measure lift.
  - Keep 90% on cheaper models.
  - Adjust based on success rate, user satisfaction, and per‑request cost.

---

## FAQ

**Q1: Is `gemini-3-pro-preview` a final model?**  
Not yet. The `-preview` suffix indicates Google’s preview phase. It is already very capable but may still evolve in capabilities and pricing. For production, use monitoring and gradual rollouts.

**Q2: I already use the OpenAI SDK. How much code do I need to change?**  
Very little. In most cases:

1. Set `base_url` to `https://api.evolink.ai/v1`.
2. Replace your API key with an EvoLink key.
3. Change `model` to `"gemini-3-pro-preview"`.

Most of your existing OpenAI SDK code remains unchanged.

**Q3: I prefer Google’s `generateContent`. Can I use that directly?**  
Yes. EvoLink exposes `/v1beta/models/gemini-3-pro-preview:{method}` compatible with Google’s Native API semantics (`contents`, `generationConfig`, `streamGenerateContent`, etc.). Just change the base URL to EvoLink.

**Q4: Do I have to use Native API for multimodal?**  
For complex multimodal scenarios, Native API format is recommended because it mirrors Google’s official semantics and examples (e.g., `image_understanding`, `audio_analysis`). Actual capabilities and file handling should follow EvoLink’s docs.

**Q5: How do I discover the latest models and JSON examples?**  
Check EvoLink’s Quickstart and model family docs – those typically show example JSON payloads with `model` names like `gpt-4o-image`, `veo3-fast`, `gemini-3-pro-preview`, etc. If EvoLink provides a “model list” API, you can also use that for discovery.

**Q6: Can I mix Gemini 3 with other models in a single workflow?**  
Yes. EvoLink is designed as a multi‑model hub. You can, for example:

- Step 1: Use `qwen-3-max` for a cheap Chinese summary.
- Step 2: Use `gemini-3-pro-preview` for deep reasoning and decision‑making.
- Step 3: Use `gpt-5` for final English polishing.

**Q7: Where should I start if I just want to try this quickly?**  
Visit **https://gemini3api.com**. It will guide you to EvoLink, the right docs, and give you a clean entrypoint to run your first Gemini 3 request.

---

