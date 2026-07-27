# root-coach

英语词根词缀教学笔记生成流水线 —— 一个 Kimi Work / Claude Code 通用的 skill。

给一个词根（如 `cap-`、`dis-`）或单词（如 `accept`），自动完成：

1. **搜索筛选**：查 Etymonline / Wiktionary，输出衍生词筛选表
2. **用户勾选**：等你挑出想深挖的词
3. **词汇教练笔记**：生成完整笔记（变体总览、词源演化链、语义锚点、逐词拆解、vs 辨析、避坑指南）
4. **词源史官叙事**（可选）：从 PIE 讲到现代英语的历史叙事
5. **落盘**：直接写入 Obsidian wiki 目录，`[[...]]` 双链当场可用

## 目录结构

```
root-coach/
├── SKILL.md                     # 编排层：触发条件、工作流程、关键约束
└── references/
    ├── vocab-coach.md           # 词汇教练提示词模板（主线）
    └── etym-historian.md        # 词源史官提示词模板（可选延伸）
```

SKILL.md 只做流程编排，内容细节全在 references 模板里。改提示词 = 改模板文件，skill 本体不用动。

## 安装

**Kimi Work / Daimon**

把 `root-coach/` 整个文件夹复制到 skills 目录：

```
%APPDATA%\kimi-desktop\daimon-share\daimon\skills\
```

**Claude Code**

复制到 `~/.claude/skills/`（全局）或项目内 `.claude/skills/`（仅该项目）。

装完新开一个会话即可生效。

## 使用

不用命令，直接说人话：

> 帮我拆解 dis- 这个词根
> accept 这个词根给我讲一下

## 配置

SKILL.md 里的存盘路径默认为 Windows 的 Obsidian wiki 目录：

```
C:\Users\13714\Desktop\英语\wiki\
```

换成你自己的 vault 路径即可。

## 核心规则（这套方法论的底线）

- **禁止编造**：每个词源断言必须有来源标注（`[Etym]` `[Wikt-PIE]` `[AH]`），搜不到标「待确认」
- **语义扩张给原文证据**：每个语义转折必须给源语言原文例词（如 concutiō），不允许「听起来逻辑通」的推理
- **vs 硬门槛**：两个英语词中文翻译相同才写辨析——翻译不同根本不会混，不写
- **三色规则**：红=字面义/核心逻辑，蓝=中文释义，黑=正文叙述

## 推荐查词源网站

| 网站 | 用途 | 标注 |
|------|------|------|
| [etymonline.com](https://www.etymonline.com) | 单词词源首选 | `[Etym]` |
| [en.wiktionary.org](https://en.wiktionary.org) | PIE 重建形式、跨语族同源词（看 Reconstruction:Proto-Indo-European 页面） | `[Wikt-PIE]` |
| [ahdictionary.com](https://www.ahdictionary.com) | 美国传统词典，自带 IE Roots Appendix | `[AH]` |
| [oed.com](https://www.oed.com) | 最权威，付费（学校/图书馆账号可用） | 可选 |
