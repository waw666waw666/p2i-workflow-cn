# P2I Workflow

> Prompt to Image Workflow CN
> 一个面向中文用户的 AI 生图提示词工作流，同时可作为可复用 skill 使用。

P2I 是 `Prompt to Image` 的缩写。

这个项目解决的不是“直接生图”，而是“先把粗略想法整理成稳定、可复制、适合继续投喂生图工具的最终 Prompt”。

核心流程：

```txt
提示词1 -> 提示词2 -> 生图
```

两窗口工作流：

```txt
GitHub 提示词1模板 / Skill
↓
A窗口：根据粗略想法生成提示词2，只输出文字，不生图
↓
B窗口：复制提示词2真正生图
```

## 这是什么

- 一个文档型开源仓库，不是 Web App，不需要后端，不需要 API。
- 一个可直接复制使用的中文 Prompt 模板仓库。
- 一个可被 agent 直接加载的 skill。

## 它解决什么问题

- AI 直接开始生图，而不是先给出 Prompt
- 输出松散，不方便复制
- 中文 Prompt 结构不稳定
- Negative Prompt 容易遗漏
- 多种风格混在一起，导致结果不稳
- 缺少“粗略想法 -> 最终 Prompt -> 生图”的固定流程

## 两种用法

### 1. 直接复制提示词使用

1. 打开 [prompts/prompt1-final-cn.md](./prompts/prompt1-final-cn.md)
2. 复制完整提示词1
3. 粘贴到 `A窗口`
4. 在 `我的粗略想法是：` 后补充你的需求
5. 让 A窗口输出提示词2
6. 复制其中【最终可复制提示词】代码块内容到 `B窗口` 生图

### 2. 作为 skill 使用

1. 打开 [SKILL.md](./SKILL.md)
2. 让 agent 按 skill 规则执行
3. 输入你的粗略生图想法
4. 获取结构化的提示词2

## 提示词2 标准输出

- 图片类型判断
- 参考方向
- 结构提炼
- 最终可复制提示词
- 可替换变量
- 可选版本方向
- 质量检查

输出硬约束：

- 整个输出只允许出现 1 个代码块
- 只有【最终可复制提示词】放进代码块
- 代码块内必须同时包含：
  - 中文最终提示词
  - Negative Prompt
- A窗口只输出文字，不生图
- 默认不输出英文 Prompt
- 默认不输出中文精简版

## 核心定义

```txt
提示词1 = 元提示词模板 / Skill 规则入口
提示词2 = 根据粗略想法生成的最终生图提示词
A窗口 = 提示词2生成上下文，只输出文字，不生图
B窗口 = 生图执行上下文，复制提示词2进行生图
```

## 仓库结构

```txt
p2i-workflow-cn/
├─ README.md
├─ SKILL.md
├─ LICENSE
├─ .gitignore
├─ prompts/
│  └─ prompt1-final-cn.md
├─ examples/
│  └─ plush-toy-fight-example.md
└─ docs/
   ├─ workflow.md
   └─ acceptance.md
```

## 示例

示例粗略想法：

```txt
两个毛绒玩偶在迷你桌面擂台上打架，可爱幽默，不血腥，像玩具广告图。
```

完整示例见：

- [examples/plush-toy-fight-example.md](./examples/plush-toy-fight-example.md)
- [examples/skincare-bottle-product-example.md](./examples/skincare-bottle-product-example.md)
- [examples/cyberpunk-poster-example.md](./examples/cyberpunk-poster-example.md)

## 兼容性说明

本工作流优先面向中文长提示词场景。

- `GPT Image / GPT Image 2 / 即梦 / 可灵` 通常可直接吃完整中文 Prompt
- `Midjourney / Stable Diffusion / 部分平台` 对格式和 `Negative Prompt` 的支持不同
- 如果目标平台不适合整段结构，优先保留【中文最终提示词】主体，再按平台特性微调

## 参考网站

以下网站仅用于学习提示词结构、风格分类、画面组织方式和专业写法：

1. [EvoLink GPT Image 2 Prompts](https://evolink.ai/zh/gpt-image-2-prompts)
2. [GPT Image 2 Prompt Gallery](https://gpt-image2.canghe.ai/)

本项目不会复制、搬运或二次分发上述网站的原始 Prompt 内容。

## 验收标准

验收清单见 [docs/acceptance.md](./docs/acceptance.md)。

## Workspace Skill 入口

如果你在 `D:\VsCodeProjects` 工作区内使用 Codex / OpenCode，可挂一个本地入口 skill：

- `D:/VsCodeProjects/.trae/skills/trae-p2i-workflow-cn/SKILL.md`

这个入口 skill 会把本仓库作为 `source of truth`，方便后续在工作区里直接触发 `P2I Workflow`，而不需要每次手动打开仓库文件。

## License

[MIT](./LICENSE)
