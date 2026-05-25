---
name: p2i-workflow-cn
description: Turn rough image ideas into structured final prompts with a strict two-window workflow. Use when the user wants prompt refinement, rough idea to final prompt, or a reusable image prompting skill in Chinese or English.
---

# P2I Workflow Skill

## What this skill is

This is a reusable `prompt engineering skill`, not an image generation skill.

Its job is to turn a rough image idea into a structured, copy-ready final prompt before the user sends it to an image model.

Core workflow:

```txt
Prompt 1 -> Prompt 2 -> Image generation
```

Two-window model:

```txt
A Window: generate Prompt 2, text only
B Window: use Prompt 2 for actual image generation
```

## What this skill must do

- Stay in `A Window` by default
- Output text only
- Never generate the image directly
- Never say “I will generate the image now”
- Never treat the final prompt as the current execution task
- Return a structured `Prompt 2` that can be copied into `B Window`

## Direct prompt entrypoints

If the user wants a prompt template they can copy directly, use:

- Chinese Prompt 1: [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)
- English Prompt 1: [prompts/prompt1-final-en.md](./prompts/prompt1-final-en.md)

## When to use Chinese vs English

Use the Chinese Prompt 1 when:

- the user writes in Chinese
- the main target is `GPT Image / GPT Image 2 / 即梦 / 可灵`
- the user wants Chinese-first prompting
- the prompt is intended for Chinese workflow readability

Use the English Prompt 1 when:

- the main target is `Midjourney`, `Ideogram`, `Stable Diffusion`, or other English-first ecosystems
- the user wants stronger cross-platform compatibility
- the prompt needs English style words, camera words, material words, or text-in-image reliability
- the user explicitly asks for an English prompt workflow

Default rule:

- If unclear, prefer Chinese for Chinese users
- If the user says “I want broader compatibility” or names English-first tools, switch to English Prompt 1

## Output contract

The output must contain:

1. `【图片类型判断】 / [Image Type]`
2. `【参考方向】 / [Reference Direction]`
3. `【结构提炼】 / [Structure]`
4. `【最终可复制提示词】 / [Final Copy-Ready Prompt]`
5. `【可替换变量】 / [Replaceable Variables]`
6. `【可选版本方向】 / [Optional Directions]`
7. `【质量检查】 / [Quality Check]`

Hard rules:

- Only one code block is allowed in the entire output
- That code block can only appear in the final prompt section
- The code block must contain:
  - the final main prompt
  - the `Negative Prompt`
- Do not output multiple conflicting main directions

## Decision rules

- If the user gives multiple possible directions, collapse them into one main route
- If the user input is incomplete, choose the safest default instead of getting stuck
- If the user asks for “something I can copy directly,” still keep the structured workflow
- If the user only says “help me write a prompt,” default to this skill instead of direct image generation

## Recommended workflow

1. Identify the image category
2. Choose one main route
3. Extract subject, material, scene, composition, lens, lighting, color, style, and usage
4. Build a stable final prompt
5. Add a category-specific `Negative Prompt`
6. Add a small set of replaceable variables
7. End with a quality check

## Source of truth

Primary files:

- [README.md](./README.md)
- [README.zh-CN.md](./README.zh-CN.md)
- [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)
- [prompts/prompt1-final-en.md](./prompts/prompt1-final-en.md)
- [docs/workflow.md](./docs/workflow.md)

Examples:

- [examples/plush-toy-fight-example.md](./examples/plush-toy-fight-example.md)
- [examples/skincare-bottle-product-example.md](./examples/skincare-bottle-product-example.md)
- [examples/cyberpunk-poster-example.md](./examples/cyberpunk-poster-example.md)
