# casset23 · Agent Backend Engineering

围绕 Agent 的任务执行、上下文治理与证据组织做后端开发，实践覆盖多模态质检、Coding Agent Runtime 和企业文档问答。

<img src="assets/banner.svg" width="100%" alt="casset23 技术作品集：Agent 编排、运行时治理、文档检索与评测" />

**先看 [Voice Agent Runtime](https://github.com/casset23/voice-agent-runtime#服务架构)**：沿着 Gateway → LLM Runner → Tool Service 阅读请求链路，再看模型与工具的资源管理。

## 实习实践

| 方向 | 处理的问题与实现 |
| :--- | :--- |
| **多模态 Agent** | 将检查项编译为任务队列，结合镜头圈选、图像与音频取证组织 ReAct 循环；以焦点缓存、实体档案和证据台账保留跨镜头信息，用步数与上下文预算约束多轮执行。 |
| **Coding Agent Runtime** | 端到端实现上下文感知的提示词增强，结合输出校验与注入防护；参与 Tool Result 预算、滚动摘要与压缩退出机制，以及 Skill 定向刷新、MCP 连接回收和旧工具清理。 |
| **多模态 RAG 与评测** | 围绕召回后的候选页整理、同族难负样本、页面重排与引证作答设计链路；具备 GRPO、LoRA 和可验证奖励实践，通过规则校验、LLM-as-a-Judge 与消融实验检查效果。 |

## 精选项目

### 01 · [Voice Agent Runtime](https://github.com/casset23/voice-agent-runtime)

**智能音箱的模型与工具服务后端**

Rust Gateway 编排请求，Python LLM Runner 解析工具意图，NestJS 资源中心维护模型与工具配置。工程重点包括请求追踪、并发保护、超时处理、HTTP 客户端复用与配置刷新。

`Rust` `Axum` `Tokio` `FastAPI` `NestJS` `SQLite` `React`

[服务架构](https://github.com/casset23/voice-agent-runtime#服务架构) · [连接生命周期](https://github.com/casset23/voice-agent-runtime#模型配置与连接生命周期) · [测试与验证](https://github.com/casset23/voice-agent-runtime#测试与验证)

### 02 · [ServicePilot Agent](https://github.com/casset23/servicepilot-agent)

**从意图识别到业务工具调用的智能客服**

以 LangGraph 状态图组织分类、补问、任务规划和工具选择，通过检查点与中断恢复续接客户回复；FastAPI 与 Vue 客服面板使用 SSE 交互，解析器覆盖 UTF-8 拆包与中断元数据。

`Python` `LangGraph` `FastAPI` `Neo4j` `Vue 3` `TypeScript`

[Agent 架构](https://github.com/casset23/servicepilot-agent#agent-如何处理请求) · [流式协议与恢复](https://github.com/casset23/servicepilot-agent#流式输出与会话恢复) · [测试与构建](https://github.com/casset23/servicepilot-agent#测试与构建)

### 03 · [AssistGen](https://github.com/casset23/assistgen)

**面向教材与技术资料的文档问答应用**

将文档清洗、章节分块、检索组织与引证生成拆成可检查的环节。提供直接读取 Markdown 的分块示例，便于观察目录过滤、章节边界和正文保留规则，并通过回归测试检查处理结果。

`Python` `MinerU` `FAISS` `FastAPI` `Vue 3` `TypeScript`

[轻量复现](https://github.com/casset23/assistgen#先复现文档分块) · [RAG 链路](https://github.com/casset23/assistgen#rag-链路与设计取舍) · [验证与评测](https://github.com/casset23/assistgen#验证与评测)

### 04 · [Ultrasonic Agent](https://github.com/casset23/ultrasonic-agent)

**连接口述、结构化草稿与桌面填写的超声报告助手**

把口述内容送入模板与结构化输出检查，经人工审核后进入桌面填写流程。关注 Electron IPC 边界、SQLite 模板管理、信息保真与 Windows 自动化衔接。

`Electron` `React` `TypeScript` `SQLite` `LLM` `Windows Automation`

[使用流程](https://github.com/casset23/ultrasonic-agent#界面与使用流程) · [工程取舍](https://github.com/casset23/ultrasonic-agent#几个具体的工程取舍) · [测试与验证](https://github.com/casset23/ultrasonic-agent#测试与验证)

## 技术栈

| 层次 | 主要技术 |
| :--- | :--- |
| Agent 与模型 | ReAct、Tool Use、MCP、Skill、Memory、LangGraph、Prompt Enhancement |
| 检索与训练 | 文档解析、混合检索、重排、引证校验、GRPO、LoRA、vLLM |
| 服务与存储 | Python、FastAPI、TypeScript、Node.js、Java、Spring Boot、Rust、MySQL、Redis、SQLite |
| 工程与验证 | SSE、异步任务、限流与超时、连接生命周期、Docker、回归测试、规则评测、消融实验 |

## 我习惯追问的工程问题

- **任务能否持续执行？** 检查上下文增长、工具返回体、预算上限，以及异常退出后的恢复路径。
- **状态能否保持一致？** 追踪配置变更如何影响会话、缓存、工具定义和已有连接。
- **结论能否回到证据？** 保留文档出处、取证记录与解析结果，让失败样本可以定位和复现。
- **改动是否真的有效？** 用固定样本、回归测试和消融实验比较方案，再判断收益与开销。

---

从[服务架构](https://github.com/casset23/voice-agent-runtime#服务架构)了解后端设计，或从[客服界面与运行步骤](https://github.com/casset23/servicepilot-agent#快速开始)开始查看应用。

<sub>casset23 · Engineering portfolio · Updated 2026-10-24</sub>

<!-- Maintainer: casset23. Reviewed: 2026-10-24. Review on project releases, changes in role, or changes in resume claims. -->
