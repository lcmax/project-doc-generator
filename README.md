# 项目文档生成器 / Project Doc Generator

<p align="center">
  <b>中文</b> &nbsp;|&nbsp;
  <a href="doc/en/README.md">English</a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-GPLv3-blue.svg" alt="License: GPLv3"></a>
  <img src="https://img.shields.io/badge/version-v1.26.908.25-blue.svg" alt="Version: v1.26.908.25">
  <img src="https://img.shields.io/badge/author-荣起_(Rongqi)-orange.svg" alt="Author">
</p>

---

> **中文**：自动解析项目代码结构与业务逻辑，一键批量生成需求规格、概要设计、详细设计、数据库设计、API 文档、测试计划、部署手册等全套标准化项目文档。

> **English**: Automatically analyze project code structure and business logic, then generate a complete suite of standardized project documents — requirements specification, architecture design, detailed design, database design, API docs, test plan, and deployment guide — all in one click.

---



## 🗓️ 版本更新记录 / Version History

> 版本号规则：`v1.{yy}.{Mdd}.{提交次数}`（如 `v1.26.908.23` = 2026年9月8日，第 23 次提交）。记录每次提交版本的变更内容。

| 版本 Version | 日期 Date | 变更内容 / Changes |
|:---|:---|:---|
| v1.26.908.25 | 2026-09-08 | README 保持一致：特性表与文档产出清单扩展为 17 套（含 P1~P7 阶段组织） |
| v1.26.908.24 | 2026-09-08 | 更新 README 版本徽章；新增「版本更新记录」并置于文档导航上方，记录提交版本的变更 |
| v1.26.908.23 | 2026-09-08 | 扩展为 17 套全生命周期文档；中英双轨本地化（GB/T 8567 / IEEE·ISO）；新增三级分级范围选择；cn/en 模板、设计规格与测试用例更新 |
| v1.26.731.20 | 2026-07-31 | 同步根目录 README；补充交互式多语言提问能力 |

---

## 📖 文档导航 / Documentation

| 语言 / Language | 链接 / Link |
|:---:|:---|
| 🇨🇳 中文文档 | [./Doc/cn/README.md](https://github.com/lcmax/project-doc-generator/blob/main/Doc/cn/README.md) |
| 🇺🇸 English Docs | [./Doc/en/README.md](https://github.com/lcmax/project-doc-generator/blob/main/Doc/en/README.md) |

---

## 🚀 快速开始 / Quick Start

<details open>
<summary><b>中文</b></summary>

1. 在对话中上传项目代码或告知项目目录路径
2. 输入指令：**"形成项目文档"** 或 **"生成项目文档"**
3. Skill 自动分析代码 → 获取版本信息 → **交互式确认**（项目名/语言/范围/格式/作者）
4. 按确认结果生成对应语言与范围的标准文档
5. 所有文档统一输出至 `Doc/<项目名>/` 目录

</details>

<details>
<summary><b>English</b></summary>

1. Upload your project code or provide the project directory path in the conversation
2. Enter the command: **"Generate project documents"** or **"Create project documents"**
3. The Skill auto-analyzes code → fetches version info → **interactive confirmation** (project name/language/scope/format/author)
4. Generates standard documents for the confirmed language and scope
5. All documents are output to the `Doc/<project-name>/` directory

</details>

---

## ✨ 核心特性 / Feature Highlights

| 特性 Feature | 说明 Description |
|:---|:---|
| 🧠 智能代码分析 / Intelligent Code Analysis | 自动识别项目目录结构、领域模型、业务逻辑与设计模式 / Auto-identifies project structure, domain models, business logic, and design patterns |
| 📄 17 套全生命周期文档 / 17 Full-Lifecycle Documents | 覆盖需求 → 设计 → 开发 → 测试 → 部署运维 → 质量安全 → 协作管理全生命周期 / Covers the full lifecycle from requirements through collaboration management |
| 🎯 三级分级范围选择 / Three-Tier Scope Selection | 预设组合档 / 软件工程阶段勾选 / 精确到文档序号，按需生成 / Preset combos / SWE-phase selection / exact doc IDs, on-demand generation |
| 🌐 双轨本地化 / Dual-Track Localization | 中文对齐 GB/T 8567，英文对齐 IEEE 830/1016/1471/829·ISO 25010 / Chinese aligns with GB/T 8567, English with IEEE/ISO |
| 🌐 多语言按需生成 / On-demand Multilingual Generation | 支持仅中文/仅英文/双语，按需裁剪目录、归档与差异对比 / Supports Chinese-only/English-only/Bilingual, dynamically trimming directories, archiving and diff |
| 🔢 自动版本管理 / Auto Versioning | 基于 Git 提交次数或时间戳生成规范版本号 / Generates standardized version numbers based on Git commit count or timestamp |
| 📝 内置变更日志 / Built-in Changelog | 每份文档自动附带版本历史与变更记录 / Every document includes version history and change logs |
| 📁 自动归档目录 / Auto Archive Directory | 一键输出至 `Doc/` 专属目录，结构清晰 / One-click output to a dedicated `Doc/` directory with clear structure |

---

## 📂 文档产出清单 / Generated Document List

> 17 套文档按软件工程 7 阶段（P1 需求 → P2 设计 → P3 开发 → P4 测试 → P5 部署运维 → P6 质量安全 → P7 协作管理）组织；中文对齐 GB/T 8567，英文对齐 IEEE/ISO。

| 阶段 | # | 文档 / Document | 内容概要 / Content Summary |
|:---:|:---:|:---|:---|
| P1 | 01 | 需求规格说明书 / Requirements Specification | 功能概述、功能需求、业务规则、外部接口 |
| P2 | 02 | 系统架构文档 / System Architecture | 逻辑/部署架构、架构决策(ADR)、风险 |
| P2 | 03 | 概要设计 / Overview Design | 模块划分、接口设计、类图、核心流程 |
| P2 | 04 | 详细设计 / Detailed Design | 方法算法流程、分支逻辑、数据结构 |
| P2 | 05 | 数据库设计 / Database Design | 数据表结构、字段、表间关系、索引 |
| P2 | 06 | 接口契约 / API 文档 / Interface Contract / API | 接口清单、入参出参、调用示例、错误码 |
| P3 | 07 | 编码规范与代码审查 / Coding Standards & Review | 命名/格式、审查流程、静态检查门槛 |
| P4 | 08 | 测试计划 / Test Plan | 测试范围、策略、通过准则、资源 |
| P4 | 09 | 测试用例与质量报告 / Test Cases & QA Report | 用例清单、执行记录、质量度量 |
| P5 | 10 | 环境与配置文档 / Environment & Configuration | 环境清单、配置项、本地化差异 |
| P5 | 11 | 部署手册 / Deployment Manual | 环境要求、部署步骤、验证、回滚 |
| P5 | 12 | 运维手册 / Operations Manual | 监控、告警、备份恢复、故障排查 |
| P6 | 13 | 非功能需求与安全设计 / NFR & Security Design | 性能/可靠性、安全设计、合规 |
| P6 | 14 | 性能基准与调优 / Performance Benchmark | 指标定义、基准方法、结果、调优 |
| P7 | 15 | 用户手册 / User Manual | 快速上手、操作指南、配置、FAQ |
| P7 | 16 | 变更管理与版本管理 / Change & Version Management | 版本规则、变更流程、提交规范、发布记录 |
| P7 | 17 | 贡献指南 / Contribution Guide | 环境搭建、提交规范、PR 流程 |

---

## 📁 项目结构 / Project Structure

```
project-doc-generator/
├── README.md                   # 项目导航首页 (你在这里)
├── SKILL.md                    # Skill 工作流与规则定义
├── LICENSE                     # GNU GPLv3
├── doc/
│   ├── cn/README.md            # 中文完整文档
│   └── en/README.md            # English full documentation
└── references/
    ├── cn/
    │   ├── document-templates.md
    │   └── git-version-info.md
    └── en/
        ├── document-templates.md
        └── git-version-info.md
```

---

## 👤 作者 / Author

**荣起 (Rongqi)**

---

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-GPLv3-blue.svg" alt="License: GPLv3"></a>
</p>
