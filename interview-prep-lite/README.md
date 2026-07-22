# Interview Prep Lite

极简面试准备工具——纯 Agent 驱动，无脚本依赖，自然对话式体验。

## 特点

- **仅保留完整三段流程**：简历审查 → 模拟面试 → 复盘总结
- **无 Python 脚本依赖**：所有评分、反馈、报告生成由 Agent 完成
- **自然对话体验**：像真实面试官一样推进，不喊步骤编号
- **先改简历再面试**：审查完简历给用户修改机会，不直接硬面
- **反问环节真回答**：以面试官身份认真回答用户问题
- **结构化复习报告**：两份报告文件，逐题复盘 + 综合评价
- **报告输出到工作目录**：所有文件写在用户当前工作目录的 `reports/` 下，不污染 skill 包

## 目录结构

```
interview-prep-lite/
├── SKILL.md              # Agent 流程指引（核心，必读）
├── README.md             # 本文件
└── references/
    └── scoring-rubric.md # 评分维度与计算公式（Agent 内部参考）
```

报告输出目录（运行时自动在用户当前工作目录创建）：
```
./reports/
├── resume_review_{timestamp}.md
├── interview_review_{timestamp}.md
└── debrief_{timestamp}.md
```

## 使用方式

将此目录作为 Skill 加载到支持 Skill 机制的 AI Agent（如 Trae IDE）中，直接对 Agent 说：

> 帮我做面试准备，我面XXX岗位，这是我的简历...

Agent 会按 SKILL.md 中定义的流程自然推进。

## 流程概览

1. **开场**：收集目标岗位和简历
2. **简历审查**：六维度加权评分，对话中给简短总评，生成详细报告
3. **改简历过渡**：问用户是否先改简历再面试
4. **模拟面试**：自我介绍 → 6-8道技术题 → 2-3个项目深挖 → 反问环节
5. **复盘总结**：生成两份报告——逐题复盘 + 综合复盘（含评分、改进计划、就绪度评估）

## 砍掉的内容

对比完整版 interview-prep-tool，本版本移除了：
- 模式 A/B/D（仅保留完整三段）
- 所有 Python CLI 脚本（ipt-* 命令）
- task_checklist.json 状态追踪
- interview_questions.json / interview_context.json 等中间文件
- mistake_book.json 错题本持久化
- user_profile.json 用户档案和进步追踪
- 违规检测机制和硬性计数规则
- 错题重考模式

## 设计原则

1. 像真人一样对话，不机械
2. 对话中给简短反馈，详细内容写报告
3. 不生成无用JSON文件，Agent 记住状态即可
4. 追问有弹性，靠判断力不靠计数
5. 站在用户角度：先改简历再面试更合理，反问环节真回答更有真实感
