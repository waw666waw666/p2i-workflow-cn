# P2I Workflow

[English](./README.md) | [简体中文](./README.zh-CN.md)

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Language: Chinese-first](https://img.shields.io/badge/language-Chinese--first-blue.svg)](./README.zh-CN.md)
[![Type: Skill](https://img.shields.io/badge/type-skill-orange.svg)](./SKILL.md)

> Prompt to Image Workflow
> A reusable skill and prompt workflow for turning rough Chinese image ideas into structured, copy-ready final prompts.

P2I stands for `Prompt to Image`.

This repository is not an image generation app. It is a prompt engineering workflow that helps users move from a rough idea to a stable final prompt before sending it to an image model.

## Why this skill

Most image prompting failures happen before image generation:

- The model starts generating images instead of returning a prompt
- The output is hard to copy and reuse
- Chinese prompts are unstable in structure
- `Negative Prompt` is missing or generic
- Multiple conflicting styles get mixed together
- There is no fixed workflow from rough idea to final prompt

P2I solves that with a strict two-window workflow.

```txt
Prompt 1 -> Prompt 2 -> Image generation
```

## Try it now

- Direct prompt template: [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)
- Skill entry: [SKILL.md](./SKILL.md)
- Full workflow guide: [docs/workflow.md](./docs/workflow.md)
- Chinese readme: [README.zh-CN.md](./README.zh-CN.md)

## Core advantages

- `Two-window discipline`: separate prompt generation from actual image generation
- `Copy-ready output`: exactly one code block for the final prompt section
- `Chinese-first`: optimized for Chinese long-form prompting
- `Reusable as a skill`: can be loaded by agents or used as a plain prompt template
- `Stable structure`: image type, direction, structure, final prompt, variables, versions, quality check
- `Safer prompting`: reduces style collision and accidental model overreach

## How it works

```txt
GitHub Prompt 1 template / Skill
↓
A Window: turns a rough idea into Prompt 2, text only, no image generation
↓
B Window: uses Prompt 2 for actual image generation
```

### Definitions

```txt
Prompt 1 = the meta prompt template / skill entry
Prompt 2 = the final image prompt generated from the rough idea
A Window = prompt generation context, text only, no image generation
B Window = image generation context, copies Prompt 2 to create the image
```

## Quick start

### Option 1. Use the prompt directly

1. Open [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)
2. Copy the full Prompt 1 template
3. Paste it into your `A Window`
4. Fill in your idea after `我的粗略想法是：`
5. Copy the single code block from `【最终可复制提示词】`
6. Paste it into your `B Window` or another image generation tool

### Option 2. Use it as a skill

1. Open [SKILL.md](./SKILL.md)
2. Let your agent follow the skill rules
3. Give it a rough Chinese image idea
4. Get a structured Prompt 2 output

## When to use Chinese vs English

### Use Chinese when

- your main target is `GPT Image / GPT Image 2 / 即梦 / 可灵`
- your working language is Chinese
- you want the workflow to stay readable for Chinese users
- you care more about idea clarity than English keyword portability

Recommended file:

- [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)

### Use English when

- your main target is `Midjourney`, `Ideogram`, `Stable Diffusion`, or a more English-first ecosystem
- you want stronger cross-platform compatibility
- you need English style vocabulary, camera vocabulary, material vocabulary, or text-in-image reliability
- you are preparing prompts for a team or audience that already works in English

Recommended file:

- [prompts/prompt1-final-en.md](./prompts/prompt1-final-en.md)

### Simple rule

- Chinese-first workflow for Chinese users
- English-first workflow for broader tool compatibility
- If unsure, start in Chinese, then export to English when targeting Midjourney-like tools

## Output format

The workflow output always includes:

- `【图片类型判断】`
- `【参考方向】`
- `【结构提炼】`
- `【最终可复制提示词】`
- `【可替换变量】`
- `【可选版本方向】`
- `【质量检查】`

Hard rules:

- Only one code block is allowed in the entire output
- That code block only appears in `【最终可复制提示词】`
- The code block must contain:
  - `中文最终提示词`
  - `Negative Prompt`
- `A Window` only outputs text
- No English prompt by default
- No short Chinese version by default

## Best use cases

- Product shots
- Posters
- Character key visuals
- Toy and stylized scenes
- Social media campaign images
- E-commerce hero images
- Brand KV exploration

## Examples

- [examples/plush-toy-fight-example.md](./examples/plush-toy-fight-example.md)
- [examples/skincare-bottle-product-example.md](./examples/skincare-bottle-product-example.md)
- [examples/cyberpunk-poster-example.md](./examples/cyberpunk-poster-example.md)

## Open source files

- Contribution guide: [CONTRIBUTING.md](./CONTRIBUTING.md)
- Change history: [CHANGELOG.md](./CHANGELOG.md)
- Security policy: [SECURITY.md](./SECURITY.md)

## Compatibility

This workflow is optimized for Chinese long prompts first.

- `GPT Image / GPT Image 2 / 即梦 / 可灵` usually work well with the full Chinese prompt
- `Midjourney / Stable Diffusion / some other tools` may treat formatting and `Negative Prompt` differently
- If a platform does not work well with the full structure, keep the main Chinese final prompt first and adapt from there

## Repository structure

```txt
p2i-workflow/
├─ README.md
├─ README.zh-CN.md
├─ SKILL.md
├─ LICENSE
├─ .gitignore
├─ prompts/
│  └─ prompt1-final-cn.md
├─ examples/
│  ├─ plush-toy-fight-example.md
│  ├─ skincare-bottle-product-example.md
│  └─ cyberpunk-poster-example.md
└─ docs/
   ├─ workflow.md
   └─ acceptance.md
```

## Workspace skill entry

If you use Codex / OpenCode inside `D:\VsCodeProjects`, you can also mount the local workspace entry skill:

- `D:/VsCodeProjects/.trae/skills/trae-p2i-workflow/SKILL.md`

That local entry skill points back to this repository as the source of truth.

## Reference sites

These sites are used only to study prompt structure, composition patterns, and professional phrasing:

1. [EvoLink GPT Image 2 Prompts](https://evolink.ai/zh/gpt-image-2-prompts)
2. [GPT Image 2 Prompt Gallery](https://gpt-image2.canghe.ai/)

This project does not copy or redistribute raw prompts from those websites.

## Acceptance

See [docs/acceptance.md](./docs/acceptance.md).

## License

[MIT](./LICENSE)
