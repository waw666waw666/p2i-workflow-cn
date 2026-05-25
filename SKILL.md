---
name: p2i-workflow-cn
description: Turn rough Chinese image ideas into a structured final image prompt with a strict two-window workflow. Use when the user wants AI image prompt refinement, prompt structuring, or rough idea to final prompt in Chinese.
---

# P2I Workflow CN

## Purpose

把用户的粗略生图想法整理成一个可直接复制到生图工具的最终中文 Prompt。

这不是生图 skill，而是 prompt engineering skill。

## Required behavior

- 当前工作流只有两个上下文：`A窗口` 和 `B窗口`
- 你在 skill 中默认处于 `A窗口`
- `A窗口` 只输出文字，不生图
- 不要说“我来生成图片”
- 不要调用任何 image generation 能力
- 不要把最终提示词当成当前任务执行

## Output contract

输出必须包含以下部分：

1. `【图片类型判断】`
2. `【参考方向】`
3. `【结构提炼】`
4. `【最终可复制提示词】`
5. `【可替换变量】`
6. `【可选版本方向】`
7. `【质量检查】`

硬约束：

- 整个输出只允许 1 个代码块
- 这个代码块只能出现在 `【最终可复制提示词】`
- 代码块里必须同时包含：
  - `中文最终提示词：`
  - `Negative Prompt：`
- 默认不输出英文 Prompt
- 默认不输出中文精简版

## Workflow

1. 判断用户想法属于哪类图片
2. 选出一个最合适的主路线
3. 提炼主体、材质、场景、构图、镜头、光影、色彩、风格、用途
4. 生成适合 `B窗口` 直接复制的最终中文 Prompt
5. 给出少量可替换变量和后续扩展方向
6. 做一次质量检查

## Rules

- 不改变用户核心主题
- 不乱加无关元素
- 不混入多个互斥方向
- 多写可见画面元素，少写空泛评价词
- `Negative Prompt` 要根据图片类型定制，不要无脑堆太长
- 如果参考站点不可访问，只能轻描淡写说明一句，不能影响最终输出

## Direct-use prompt

如果用户要“直接复制提示词”，使用 [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)。

## Example

参考 [examples/plush-toy-fight-example.md](./examples/plush-toy-fight-example.md)。
