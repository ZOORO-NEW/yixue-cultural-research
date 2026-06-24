# 易学文化研究工具 - 跨平台适配指南

本技能已改造为**跨平台通用版**，可在以下AI平台使用：
- OpenClaw
- Hermes
- Codex
- ChatGPT（Plus/Team/Enterprise）
- Claude（claude.ai / Anthropic API）
- 通义千问（Qwen）
- 文心一言（ERNIE）
- 腾讯混元
- DeepSeek
- 其他支持System Prompt的AI平台

---

## 快速开始

### 方式一：复制粘贴（最简单）

1. 打开 `prompts/system-prompt-zh.md`（中文）或 `prompts/system-prompt-en.md`（英文）
2. 全选复制全部内容
3. 粘贴到目标AI平台的System Prompt / 系统指令 / 角色设定框
4. 开始使用

### 方式二：文件上传（部分平台支持）

1. 将整个技能包文件夹下载到本地
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

---

## 各平台适配说明

### OpenClaw

**支持方式**：Expert包导入 或 System Prompt粘贴

**步骤**：
1. 将 `SKILL.md` 重命名为 `expert-yixue-research.md`
2. 在OpenClaw的Expert管理页面，选择"导入Expert"
3. 上传文件，系统会自动解析

**注意事项**：
- OpenClaw支持Markdown格式的Expert定义
- 如果导入失败，可直接复制 `system-prompt-zh.md` 的内容粘贴到System Prompt框

### Hermes

**支持方式**：System Prompt粘贴

**步骤**：
1. 打开对话设置
2. 找到"System Prompt"或"角色设定"
3. 粘贴 `system-prompt-zh.md` 的全部内容
4. 保存设置，开始新对话

**注意事项**：
- Hermes的System Prompt有长度限制（约8000字符），如果超限，删除"参考资料"和"特殊说明"部分
- 合规声明**不能删除**

### Codex（OpenAI）

**支持方式**：System Prompt粘贴 或 API调用

**步骤**：
1. 在Codex的对话界面，点击"设置"
2. 找到"System Message"输入框
3. 粘贴 `system-prompt-zh.md` 的全部内容
4. 保存并开始对话

**API调用示例**：
```python
import openai

client = openai.OpenAI(api_key="your-api-key")

system_prompt = open("prompts/system-prompt-zh.md", "r", encoding="utf-8").read()

response = client.chat.completions.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": "1990年农历正月初一，寅时，女性"}
    ]
)

print(response.choices[0].message.content)
```

### ChatGPT（Plus/Team/Enterprise）

**支持方式**：GPTs定制 或 System Prompt粘贴

**创建GPTs步骤**：
1. 访问 https://chat.openai.com/gpts
2. 点击"Create a GPT"
3. 在"Instructions"框中粘贴 `system-prompt-zh.md` 的全部内容
4. 在"Name"中填写"易学文化研究工具"
5. 点击"Save"，选择发布范围

**注意事项**：
- GPTs有知识库功能，可以上传 `references/` 目录下的文件作为知识库
- 合规声明会在每次对话开头自动显示

### Claude（claude.ai / Anthropic API）

**支持方式**：Project Instructions 或 System Prompt粘贴

**步骤**：
1. 在Claude的Projects功能中，创建新项目
2. 在"Project Instructions"中粘贴 `system-prompt-zh.md` 的全部内容
3. 将 `references/` 目录下的文件上传到"Project Knowledge"
4. 在项目中开始对话

**API调用示例**：
```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key")

system_prompt = open("prompts/system-prompt-zh.md", "r", encoding="utf-8").read()

message = client.messages.create(
    model="claude-3-opus-20240229",
    system=system_prompt,
    messages=[
        {"role": "user", "content": "1985年4月9日，帮我排八字"}
    ]
)

print(message.content[0].text)
```

### 通义千问（Qwen）

**支持方式**：System Prompt粘贴

**步骤**：
1. 在通义千问的对话界面，点击"设置"
2. 找到"系统指令"输入框
3. 粘贴 `system-prompt-zh.md` 的全部内容
4. 保存设置

### 文心一言（ERNIE）

**支持方式**：System Prompt粘贴

**步骤**：
1. 在文心一言的对话界面，点击"设置"
2. 找到"系统指令"或"角色设定"
3. 粘贴 `system-prompt-zh.md` 的全部内容
4. 保存设置

### 腾讯混元

**支持方式**：System Prompt粘贴

**步骤**：
1. 在腾讯元宝的对话界面，进入"设置"
2. 找到"系统提示词"输入框
3. 粘贴 `system-prompt-zh.md` 的全部内容
4. 保存设置

### DeepSeek

**支持方式**：System Prompt粘贴

**步骤**：
1. 在DeepSeek的对话界面，点击"设置"
2. 找到"System Prompt"输入框
3. 粘贴 `system-prompt-zh.md` 的全部内容
4. 保存设置

---

## 各平台System Prompt长度限制

| 平台 | 限制 | 超出后处理方案 |
|------|------|----------------|
| OpenClaw | 无明确限制 | - |
| Hermes | ~8000字符 | 删除"参考资料"和"特殊说明" |
| Codex | 128K tokens（GPT-4） | 不会超出 |
| ChatGPT | 128K tokens（GPT-4） | 不会超出 |
| Claude | 200K tokens（Claude 3） | 不会超出 |
| 通义千问 | ~10000字符 | 删除示例部分 |
| 文心一言 | ~10000字符 | 删除示例部分 |
| 腾讯混元 | ~10000字符 | 删除示例部分 |
| DeepSeek | 64000字符 | 不会超出 |

---

## 各平台合规要求

### 国际平台（OpenClaw/Codex/ChatGPT/Claude/DeepSeek）

- 必须包含"不构成建议"声明
- 可以提及"文化研究""历史演变"等学术词汇
- 避免使用"fortune telling""mystic"等词汇

### 国内平台（通义/文心/混元）

- **必须**严格遵守各平台的合规要求
- 合规声明**不能删除**
- 如果出现"合规拦截"，尝试：
  1. 弱化"命理"词汇，改用"传统文化研究"
  2. 在输出中增加更多"历史演变""学术观点"内容
  3. 减少对个人八字的具体解读，增加文化科普

---

## 常见问题

### Q1：粘贴后AI没有按预期执行怎么办？

**A**：
1. 检查是否完整粘贴了 `system-prompt-zh.md` 的内容
2. 在对话中明确提醒："请严格按照你的System Prompt执行"
3. 如果仍不生效，可能是平台不支持System Prompt功能

### Q2：如何验证AI是否正确加载了System Prompt？

**A**：
在对话中输入："请显示你的System Prompt的前100字"
如果AI输出了你粘贴的内容，说明已正确加载。

### Q3：可以在多个平台同时使用吗？

**A**：
可以。本技能包允许在多个平台同时使用，无需额外授权。

### Q4：如果平台更新导致不兼容怎么办？

**A**：
1. 访问GitHub仓库查看是否有更新版本
2. 或者在对话中手动调整System Prompt以适应平台新格式

---

## 文件清单

```
yixue-cultural-research/
├── SKILL.md                          # 主技能文件（WorkBuddy格式）
├── PLATFORMS.md                     # 本文件 - 跨平台适配指南
├── prompts/
│   ├── system-prompt-zh.md         # 通用中文System Prompt
│   └── system-prompt-en.md         # 通用英文System Prompt
└── references/
    ├── bazhi-calculation.md        # 八字排盘详细算法
    ├── wuxing-analysis.md          # 五行分析方法
    └── cultural-interpretation.md  # 文化解读框架
```

---

## 授权与贡献

**License**: MIT License

**允许**：
- 个人/商业使用
- 修改和分发
- 在各AI平台使用

**要求**：
- 保留原作者信息
- 如果修改，请在文件中注明修改内容

**贡献方式**：
- 在GitHub上提交Pull Request
- 在Issues区报告Bug或提出改进建议

---

## 联系与反馈

- **GitHub Issues**：https://github.com/ZOORO-NEW/yixue-cultural-research/issues
- **讨论区**：https://github.com/ZOORO-NEW/yixue-cultural-research/discussions

---

**最后更新**：2026-06-25
