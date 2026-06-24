# 易学文化研究工具 (Yixue Cultural Research Tool)

**国学八字排盘与文化解读 - 跨平台通用AI技能包**

---

## 目录

- [项目简介](#项目简介)
- [核心定位](#核心定位)
- [功能列表](#功能列表)
- [跨平台支持](#跨平台支持)
- [快速开始](#快速开始)
- [文件结构](#文件结构)
- [合规声明](#合规声明)
- [贡献指南](#贡献指南)
- [License](#license)

---

## 项目简介

本技能包提供一个**易学文化研究工具**，支持**八字排盘**、**五行分析**、**十神关系**和**文化解读**功能。

**特点**：
- ✅ **跨平台通用**：支持OpenClaw、Hermes、Codex、ChatGPT、Claude等主流AI平台
- ✅ **合规设计**：严格遵守AI平台合规要求，聚焦文化研究，不涉及算命预测
- ✅ **学术严谨**：基于历史文献和传统文化经典，提供客观中立的文化解读
- ✅ **开箱即用**：提供通用System Prompt，复制粘贴即可使用

---

## 核心定位

**传统文化研究者，而非算命先生。**

本技能包的核心是**文化研究**和**知识普及**，不是算命工具。所有输出都聚焦于：
- 历史演变：命理学说的发展历程
- 文化内涵：八字在传统文化中的意义
- 学术观点：不同学派的理论差异
- 现代视角：如何从文化研究角度理解

---

## 功能列表

### 功能1：八字排盘

**输入**：公历/农历生日 + 出生时间（可选）

**输出**：
1. 年柱、月柱、日柱、时柱（天干+地支）
2. 各柱五行属性
3. 日干与其他天干的十神关系
4. 五行数量统计

### 功能2：文化解读

为排盘结果提供**传统文化内涵解读**，包括：
1. 历史演变：命理学说的发展历史
2. 学派差异：子平/紫微/铁板等学派特点
3. 文化内涵：八字在传统文化中的意义
4. 现代视角：如何从文化研究角度理解

### 功能3：文化演变研究

命理学说的发展历史、学派差异、地域传播路径等。

---

## 跨平台支持

本技能包支持以下AI平台：

| 平台 | 支持方式 | 详细指南 |
|------|----------|----------|
| OpenClaw | Expert包导入 / System Prompt粘贴 | 见 `PLATFORMS.md` |
| Hermes | System Prompt粘贴 | 见 `PLATFORMS.md` |
| Codex | System Prompt粘贴 / API调用 | 见 `PLATFORMS.md` |
| ChatGPT | GPTs定制 / System Prompt粘贴 | 见 `PLATFORMS.md` |
| Claude | Project Instructions / API调用 | 见 `PLATFORMS.md` |
| 通义千问 | System Prompt粘贴 | 见 `PLATFORMS.md` |
| 文心一言 | System Prompt粘贴 | 见 `PLATFORMS.md` |
| 腾讯混元 | System Prompt粘贴 | 见 `PLATFORMS.md` |
| DeepSeek | System Prompt粘贴 | 见 `PLATFORMS.md` |

---

## 快速开始

### 方式一：复制粘贴（最简单）

1. 打开 `prompts/system-prompt-zh.md`（中文）或 `prompts/system-prompt-en.md`（英文）
2. 全选复制全部内容
3. 粘贴到目标AI平台的System Prompt / 系统指令 / 角色设定框
4. 开始使用

### 方式二：文件上传（部分平台支持）

1. 将本技能包文件夹下载到本地
2. 在支持文件上传的平台（如ChatGPT Plus）上传 `SKILL.md` 和 `references/` 目录下的文件
3. 在对话中引用："请按照上传的文件作为你的行为准则"

### 方式三：API调用（开发者）

```python
import openai

system_prompt = open("prompts/system-prompt-zh.md", "r", encoding="utf-8").read()

response = openai.ChatCompletion.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": "1985年4月9日，帮我排八字"}
    ]
)
```

详细步骤见 `PLATFORMS.md`。

---

## 文件结构

```
yixue-cultural-research/
├── README.md                        # 本文件 - 项目说明
├── SKILL.md                         # 主技能文件（WorkBuddy格式）
├── PLATFORMS.md                     # 跨平台适配指南
├── prompts/                         # 通用System Prompt
│   ├── system-prompt-zh.md         # 通用中文System Prompt
│   └── system-prompt-en.md         # 通用英文System Prompt
└── references/                      # 参考资料
    ├── bazhi-calculation.md        # 八字排盘详细算法
    ├── wuxing-analysis.md          # 五行分析方法
    └── cultural-interpretation.md  # 文化解读框架
```

---

## 合规声明

### 必须遵守的规则

本技能包严格遵守AI平台合规要求：

1. **禁止算命**：不预测吉凶祸福，不提供人生决策建议
2. **文化研究定位**：所有内容聚焦传统文化研究，不涉及命理预测
3. **合规声明强制显示**：每次对话开头必须显示合规声明
4. **禁用词汇**：不使用"改运""化解""择吉""合婚"等敏感词

### 合规声明模板

> ⚠️ **合规声明**：本内容仅供传统文化研究参考，不构成任何人生决策建议，不预测吉凶祸福，不引导职业选择/婚姻/投资等个人决策。命理学说属于中国传统文化的一部分，应以科学态度理性看待。

---

## 贡献指南

### 如何贡献

1. Fork本仓库
2. 创建你的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交你的修改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开一个Pull Request

### 报告Bug

请在GitHub Issues区报告Bug，包含：
- 使用的AI平台
- 输入的内容
- 实际输出
- 预期输出

### 改进建议

欢迎在GitHub Discussions区提出改进建议。

---

## 参考资料

详细的算法说明和文化背景见 `references/` 目录：
- `bazhi-calculation.md`：八字排盘详细算法（含五虎遁、五鼠遁口诀）
- `wuxing-analysis.md`：五行分析方法（生克关系、旺衰判断）
- `cultural-interpretation.md`：文化解读框架（历史演变、学派差异、现代视角）

---

## 常见问题

### Q1：日柱计算准确吗？

A：由于日柱计算较复杂（需考虑儒略日、闰年等），AI可能无法100%准确。建议在输出中提示："日柱计算复杂，建议使用专业八字排盘工具验证准确性。"

### Q2：可以在商业项目中使用吗？

A：可以。本技能包采用MIT License，允许个人和商业使用。

### Q3：如果平台更新导致不兼容怎么办？

A：
1. 访问本GitHub仓库查看是否有更新版本
2. 或者在对话中手动调整System Prompt以适应平台新格式

---

## 更新日志

### v1.0 (2026-06-25)

- ✅ 初始版本发布
- ✅ 支持八字排盘、五行分析、十神关系
- ✅ 支持跨平台使用（OpenClaw/Hermes/Codex/ChatGPT/Claude等）
- ✅ 提供中英文通用System Prompt
- ✅ 完整的合规声明和禁用词汇表

---

## License

[MIT License](LICENSE)

**允许**：
- 个人/商业使用
- 修改和分发
- 在各AI平台使用

**要求**：
- 保留原作者信息
- 如果修改，请在文件中注明修改内容

---

## 联系与反馈

- **GitHub Issues**：https://github.com/ZOORO-NEW/yixue-cultural-research/issues
- **讨论区**：https://github.com/ZOORO-NEW/yixue-cultural-research/discussions

---

## Star History

如果这个项目对你有帮助，请给它一个⭐️！

---

**重要提醒**：本技能包的核心是"文化研究"，不是"算命"。所有输出都要体现这一定位。
