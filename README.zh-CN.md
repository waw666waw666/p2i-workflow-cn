# P2I Workflow

[English](./README.md) | [简体中文](./README.zh-CN.md)

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Language: Chinese-first](https://img.shields.io/badge/language-Chinese--first-blue.svg)](./README.zh-CN.md)
[![Type: Skill](https://img.shields.io/badge/type-skill-orange.svg)](./SKILL.md)

> Prompt to Image Workflow CN
> 一个可复用的 skill + 提示词工作流，用来把粗略中文生图想法整理成结构化、可复制的最终 Prompt。

P2I 是 `Prompt to Image` 的缩写。

这个仓库不是生图产品，而是一套 `prompt engineering workflow`。它的重点不是“直接出图”，而是先把模糊想法收束成稳定的最终 Prompt，再交给生图模型执行。

## 这个 skill 的优点

- `两窗口分工清楚`：A窗口 只负责出 Prompt，B窗口 才负责真正生图
- `输出可直接复制`：全文只保留 1 个代码块，方便直接投喂模型
- `中文优先`：专门面向中文长提示词场景
- `可当 skill，也可当提示词模板`：既适合 agent，也适合人工直接复制使用
- `结构稳定`：图片类型、参考方向、结构提炼、最终 Prompt、变量、版本方向、质量检查一套固定
- `减少跑偏`：避免多个风格乱混、避免 agent 直接越权生图

## 它解决什么问题

- AI 直接开始生图，而不是先返回 Prompt
- 输出太散，不方便复制
- 中文 Prompt 结构不稳定
- `Negative Prompt` 容易遗漏
- 多个互斥风格混在一起
- 缺少“粗略想法 -> 最终 Prompt -> 生图”的固定流程

核心流程：

```txt
提示词1 -> 提示词2 -> 生图
```

## 立即使用

- 直接复制提示词模板：[prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)
- Skill 入口：[SKILL.md](./SKILL.md)
- 工作流说明：[docs/workflow.md](./docs/workflow.md)
- 英文 README：[README.md](./README.md)

## 两窗口工作流

```txt
GitHub 提示词1模板 / Skill
↓
A窗口：根据粗略想法生成提示词2，只输出文字，不生图
↓
B窗口：复制提示词2真正生图
```

核心定义：

```txt
提示词1 = 元提示词模板 / Skill 入口
提示词2 = 根据粗略想法生成的最终生图提示词
A窗口 = Prompt 生成上下文，只输出文字，不生图
B窗口 = 生图执行上下文，复制提示词2进行生图
```

## 快速开始

### 方式 1：直接复制提示词使用

1. 打开 [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)
2. 复制完整 `提示词1`
3. 粘贴到 `A窗口`
4. 在 `我的粗略想法是：` 后补充你的需求
5. 复制 `【最终可复制提示词】` 中唯一的代码块
6. 粘贴到 `B窗口` 或其他生图工具中执行

### 方式 2：作为 skill 使用

1. 打开 [SKILL.md](./SKILL.md)
2. 让 agent 按 skill 规则执行
3. 输入你的粗略中文生图想法
4. 获取结构化的 `提示词2`

## 什么时候用中文，什么时候用英文

### 用中文更合适

- 主要目标工具是 `GPT Image / GPT Image 2 / 即梦 / 可灵`
- 你的工作语言本来就是中文
- 你希望整个工作流对中文用户更好理解
- 你更在意“想法表达清楚”，而不是英文关键词兼容性

推荐文件：

- [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)

### 用英文更合适

- 主要目标工具是 `Midjourney`、`Ideogram`、`Stable Diffusion` 或其他英文生态更强的工具
- 你更在意跨平台兼容性
- 你需要更稳定的英文风格词、镜头词、材质词、画面文字控制
- 你要把 prompt 给英文工作流、英文团队，或者更国际化的使用场景

推荐文件：

- [prompts/prompt1-final-en.md](./prompts/prompt1-final-en.md)

### 一句话规则

- 中文用户默认先用中文 Prompt 1
- 如果目标是 Midjourney 这类英文生态工具，优先用英文 Prompt 1
- 如果拿不准，先用中文整理想法，再导出成英文版本去跑跨平台工具

## 输出格式

固定包含：

- `【图片类型判断】`
- `【参考方向】`
- `【结构提炼】`
- `【最终可复制提示词】`
- `【可替换变量】`
- `【可选版本方向】`
- `【质量检查】`

硬约束：

- 全文只允许出现 1 个代码块
- 这个代码块只能出现在 `【最终可复制提示词】`
- 代码块内必须同时包含：
  - `中文最终提示词`
  - `Negative Prompt`
- `A窗口` 只输出文字
- 默认不输出英文 Prompt
- 默认不输出中文精简版

## 适合的场景

- 产品图
- 海报
- 角色主视觉
- 玩具 / 场景图
- 社媒宣传图
- 电商主图
- 品牌 KV 探索

## 示例

- [examples/plush-toy-fight-example.md](./examples/plush-toy-fight-example.md)
- [examples/skincare-bottle-product-example.md](./examples/skincare-bottle-product-example.md)
- [examples/cyberpunk-poster-example.md](./examples/cyberpunk-poster-example.md)

## 开源协作文件

- 贡献说明：[CONTRIBUTING.md](./CONTRIBUTING.md)
- 更新记录：[CHANGELOG.md](./CHANGELOG.md)
- 安全策略：[SECURITY.md](./SECURITY.md)

## 兼容性说明

这套工作流优先面向中文长提示词：

- `GPT Image / GPT Image 2 / 即梦 / 可灵` 一般可以直接使用完整中文 Prompt
- `Midjourney / Stable Diffusion / 其他部分工具` 对格式和 `Negative Prompt` 的处理方式不同
- 如果平台不适合整段结构，优先保留 `中文最终提示词` 主体，再按平台特性微调

## 仓库结构

```txt
p2i-workflow-cn/
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

## Workspace Skill 入口

如果你在 `D:\VsCodeProjects` 工作区中使用 Codex / OpenCode，也可以直接挂本地入口 skill：

- `D:/VsCodeProjects/.trae/skills/trae-p2i-workflow-cn/SKILL.md`

这个本地入口 skill 会把当前仓库作为 `source of truth`。

## GitHub About 建议

建议仓库 About 使用：

- Description:
  `Chinese prompt-to-image workflow skill for turning rough ideas into structured, copy-ready final prompts.`
- Topics:
  `ai`, `prompt-engineering`, `prompt-to-image`, `image-generation`, `text-to-image`, `gpt-image`, `midjourney`, `stable-diffusion`, `chinese`, `skill`

## 参考网站

以下网站只用于学习提示词结构、构图方式、风格组织和专业写法：

1. [EvoLink GPT Image 2 Prompts](https://evolink.ai/zh/gpt-image-2-prompts)
2. [GPT Image 2 Prompt Gallery](https://gpt-image2.canghe.ai/)

本项目不会复制、搬运或二次分发这些网站的原始 Prompt 内容。

## 验收标准

见 [docs/acceptance.md](./docs/acceptance.md)。

## License

[MIT](./LICENSE)
