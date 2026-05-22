# Concept Understanding Diagnosis

一个用于 Codex 的概念理解诊断 Skill。

它不急着讲课，而是先通过问题判断学习者当前的理解边界，再把掌握情况记录为 `Solid / Unstable / Missing`，最后针对薄弱点给出最小学习材料和复测题。

## 适合什么场景

- 想检查自己是否真的理解某个概念
- 想让 AI 先提问，而不是直接解释一大段
- 想把学习过程记录到 Obsidian
- 想知道一个知识点哪些部分已经稳了，哪些还不稳
- 想针对薄弱点获取少量、明确的学习材料
- 想用真实场景题检验技术概念，比如 HTTP、TCP、Gradle、Android SDK、APK 分析等

## 核心流程

```text
提问诊断
-> 判断掌握情况
-> 输出 Solid / Unstable / Missing
-> 推荐针对性学习材料
-> 做场景题复测
-> 更新掌握状态
```

## 掌握状态

这个 Skill 会把理解情况分成几类：

- `Solid`：能正确解释，或者能在具体场景中使用
- `Unstable`：方向大致对，但边界、条件或排查顺序还不稳定
- `Missing`：还没有可用模型，需要先学习或补充
- `Possible confusion`：可能混淆的概念，比如 `401 vs 403`、`HTTP vs TCP`、`Cookie vs Token`

## 示例用法

```text
[$concept-understanding-diagnosis] HTTP
```

或者：

```text
用 concept-understanding-diagnosis 检查我对 HTTP 状态码的理解，先不要直接解释。
```

Skill 会先问类似这样的问题：

```text
1. HTTP 主要解决什么问题？
2. 一个请求和响应分别由哪些部分组成？
3. GET 和 POST 的区别是什么？
4. 401、403、404、405 分别应该怎么排查？
5. 接口失败时你会先看哪里？
```

然后根据回答输出诊断结果：

```text
Current level: Explains the flow

Solid:
- 知道 HTTP 是客户端和服务端之间的应用层协议
- 能根据 401 判断认证相关问题

Unstable:
- 403 和 405 的排查方向容易混

Missing:
- Header、状态码、请求方法、权限之间的关系

Next study:
- 阅读 401 / 403 / 404 / 405 的定义和典型场景
- 用浏览器 Network 面板观察一次失败请求

Next check:
- 给出 3 个接口失败场景，判断优先检查什么
```

## 配合 Obsidian

如果你使用 Obsidian，可以把每个主题拆成一个小型学习系统，而不是写成一篇大而全的笔记。

推荐结构：

```text
HTTP/
- overview.md
- diagnosis.md
- question-map.md
- atomic-notes/
- practice-records/
- resources/
```

各文件职责：

- `overview.md`：主题总览和导航
- `diagnosis.md`：记录当前掌握状态
- `question-map.md`：记录真正需要解决的问题
- `atomic-notes/`：一个文件只讲清一个知识点
- `practice-records/`：记录场景题、错题和复测结果
- `resources/`：保存经过筛选的学习材料

## 安装

把仓库放到 Codex skills 目录下：

```powershell
git clone https://github.com/Airoure/concept-understanding-diagnosis.git "$env:USERPROFILE\.codex\skills\concept-understanding-diagnosis"
```

如果目录已经存在，可以进入目录更新：

```powershell
cd "$env:USERPROFILE\.codex\skills\concept-understanding-diagnosis"
git pull
```

## 文件结构

```text
concept-understanding-diagnosis/
- SKILL.md
- agents/
  - openai.yaml
- README.md
```

## 维护目标

这个 Skill 的目标不是替代文档，也不是把概念讲成百科，而是帮助学习者建立一个可持续的学习闭环：

```text
AI 定位方向
-> 官方资料确认边界
-> 实际场景验证
-> 用自己的话复述
-> 更新掌握状态
```

