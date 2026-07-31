# a3-report

> 基于丰田 A3 方法论的 AI Agent 技能（Skill）：教练式引导 + 一页结构化报告生成

一套让 AI Agent 像 A3 教练一样工作的方法论技能包。它不替你思考——你提供数据和对问题的思考，AI 负责用提问引导分析路径（5Why 根因追问、OKR 目标、SMART 计划），并输出专业的一页 A3 报告（Markdown / 交互式 HTML / PPTX / Excel）。

![预览](docs/preview.png)

## 特性

- **三种 A3 类型**：问题解决型（7 分区 + 5Why）、提案型、状态汇报型，自动判断类型
- **双模式**：信息充足直接生成；信息不足进入**教练模式**，按五步提问流程引导（理清问题 → 影响 → 目标 → 根因 → 行动）
- **5Why 追问协议**：逐层追问、复述确认、线索词拦截（"等待/不重视/沟通不畅"不是根因）、反向验证，杜绝 AI 代填 Why 链
- **OKR 目标结构**：1 个 O + 2-4 个 KR（当前值 → 目标值 + 期限），KR 即监控指标
- **SMART 计划校验**：每行行动必须有具体动作、交付物、责任人、期限、对应根因/KR
- **精益最佳实践**：叙事连贯（A3 讲故事不是填格子）、问题陈述=量化差距、根回（nemawashi）共识、活文档随 PDCA 升版本
- **四种输出格式**：Markdown（权威源）、交互式 HTML（屏幕阅读 + 打印自动切回单页 A3 横版）、PPTX（420×297mm 单页）、Excel（A3 纸型双栏）
- **行业无关**：纯方法论，不预设制造业或任何场景，适用于 IT/服务/运维/医疗/项目管理等

## 安装

将本仓库复制到 Agent CLI 的技能目录：

```bash
# 用户级安装
git clone https://github.com/mdsyw-chase/a3-report.git ~/.qoder/skills/a3-report

# 或项目级安装
git clone https://github.com/mdsyw-chase/a3-report.git .qoder/skills/a3-report
```

PPTX/Excel 输出需要 Python 依赖：

```bash
pip install python-pptx openpyxl
```

重启会话或执行 `/skills reload` 后生效。

## 使用

```
/a3-report <问题描述或报告主题>
```

示例：

```
/a3-report 客户投诉响应超时问题的根因分析
/a3-report 建设自动化测试平台的立项提案
/a3-report XX项目 Q3 阶段进展汇报
```

也可以自然语言触发：提到 "A3"、"5Why"、"根因分析"、"改善提案"、"PDCA" 等关键词时技能自动激活。

首次使用时，技能会先说明用法和角色分工，再进入三阶段对话：**确认问题**（背景 + 现状数据）→ **分析**（目标 → 5Why 根因 → 对策）→ **落地**（SMART 计划 → 跟踪），每阶段达成共识后继续。

## 目录结构

```
a3-report/
├── SKILL.md                    # 技能入口：工作流程与质量标准
├── references/
│   ├── a3-types.md             # 三种 A3 类型分区结构、OKR/SMART 校验、质量清单
│   └── a3-coaching.md          # 教练模式：五步提问、5Why 追问协议、常见误区应对
├── assets/
│   └── a3-template.html        # 交互式 HTML 模板（屏幕阅读 + 单页 A3 打印）
├── scripts/
│   └── a3_build.py             # JSON → PPTX/Excel 生成脚本
└── docs/
    └── preview.png             # HTML 报告效果预览
```

## 方法论来源

- 丰田 A3 问题解决法与 PDCA
- John Shook《Managing to Learn》的 A3 教练对话模式
- 精益社区（LEI / Planet Lean）关于叙事性、差距陈述、根回共识的最佳实践
- OKR 与 SMART 原则

## License

[MIT](LICENSE)
