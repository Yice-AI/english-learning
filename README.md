# 英语陪练 Skill

安装到支持 [Agent Skills](https://agentskills.io/specification) 的 Agent 后，让它用同一套方法陪你练日常英语。

三种模式：

- **第一模式：中文转英文与跟读。** 先表达中文意思，学习自然英文，再跟读和重试。
- **第二模式：全英文对话。** 围绕真实场景交流，卡住时可用中文，再练对应英文。
- **第三模式：沉浸听力。** 不需要回应，听连贯英语；难点放慢、重复和简短解释。

三种模式共享学习记录和难度依据，重点练自然美式口语。纠错后提供重说机会，已学词句会在新场景复现。

## 方案基础与优化范围

本 Skill 将此前在 ChatGPT 中讨论、沉淀到英语学习资料库的方案整理成可安装文件。以下教学原则沿用原方案：

| 已沉淀的资料 | 本 Skill 保留的规则 |
| --- | --- |
| 英语学习-学习进度 | 三种模式的定义；第三模式无需实时回应；高频词和关键句进入复习 |
| 英语学习-新Agent接手说明 | 真实日常沟通目标；自然美式表达；慢速分段；按现有进度接手；纠错后重说 |
| 英语学习-当前水平 | 用真实理解、表达和复用证据更新难度；三种模式使用最新评估 |
| 英语学习-强项与薄弱点 | 优先纠正影响理解和自然度的问题；避免频繁打断；已学内容反复复现 |

本次优化集中在执行细节：明确模式选择和切换，避免反复重试卡住，区分听力、表达和跟读证据，补齐文字/语音适配，以及私有记录的读取、保存和失败处理。资料中的个人评估和学习历史继续保留在私有存储中。

## 安装

仓库本身就是 `english-learning` Skill 目录。安装完整目录，保留 `SKILL.md`、`references/` 和 `agents/` 的相对位置。

### Codex

[官方支持的用户级目录](https://learn.chatgpt.com/docs/build-skills) 是 `~/.agents/skills/`。在本机手动执行：

```sh
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/Yice-AI/english-learning.git "$HOME/.agents/skills/english-learning"
```

在 Codex 中输入 `$english-learning`，或使用技能列表选择“英语陪练”。如果当前会话尚未识别，按宿主的技能刷新方式加载，或新建会话。

### Claude Code

[官方支持的用户级目录](https://code.claude.com/docs/en/skills) 是 `~/.claude/skills/`：

```sh
mkdir -p "$HOME/.claude/skills"
git clone https://github.com/Yice-AI/english-learning.git "$HOME/.claude/skills/english-learning"
```

在 Claude Code 中用 `/english-learning` 开始练习。

### 其他 Agent

将完整仓库放入该产品官方支持的 Skill 目录，或通过其官方安装器从本仓库安装。安装位置、技能刷新方式和语音能力由宿主决定；不能假设所有聊天产品都支持安装 Skill。`agents/openai.yaml` 只是可选的 OpenAI 显示配置，教学规则不依赖它。

上述克隆命令只适用于目标目录还不存在的首次安装。已有安装时先检查本地改动，再按该产品的更新方式更新，不直接覆盖。

## 开始使用

安装并加载后，可直接说：

> 第一模式。我想表达“今天有点累，想早点回家”。

> 第二模式。我们用英语聊一下周末计划。

> 第三模式。讲一个稍有挑战的日常故事，我不用回应。

> 继续上次的练习。

Skill 会优先使用已授权、实际可访问的学习记录；没有记录时，在练习中建立临时难度判断。

## 学习数据和语音

GitHub 只存通用规则。个人水平、词库、句库和进度可放在私有 Drive 或用户指定的私有存储中；安装本 Skill 不会连接 Drive，也不包含个人文档链接、账号凭据或学习历史。保存学习记录需要相应工具及写入授权。

Agent 发现值得保留的词库、句库、纠错、复习结果或进度变化时，会主动在会话内汇总。无法写入时，第一、第二模式在首次待保存更新后提醒一次，结束时有未保存内容便自动给出可复制的“待保存更新摘要”；第三模式在暂停、结束或切换模式时提醒，保持听力内容连贯。

你可以手动把摘要写入 Drive，或交给具备写入能力的 Agent 并要求“同步英语学习记录”。下一次练习时，各 Agent 读取最新资料继续。摘要只有在实际写入并核对成功后才算已保存，个人记录不会上传到此仓库。

没有存储连接也能练习，但记录只在当前会话内可用；没有语音工具时提供文字跟读稿或听力稿。Skill 不能为宿主增加录音、朗读、语速控制或后台持续播放能力。纯转写内容不能用来判断实际发音。

## 文件

- [SKILL.md](SKILL.md)：入口、模式选择、共用规则与能力边界。
- [references/modes.md](references/modes.md)：三种模式的执行细节。
- [references/learning-memory.md](references/learning-memory.md)：私有记录、复习和跨 Agent 接手。
- [agents/openai.yaml](agents/openai.yaml)：Codex 显示名称和默认提示。
