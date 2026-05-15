# 项目文档生成器 / Project Doc Generator

<p align="center">
  <b>中文</b> &nbsp;|&nbsp;
  <a href="doc/en/README.md">English</a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-GPLv3-blue.svg" alt="License: GPLv3"></a>
  <img src="https://img.shields.io/badge/version-v1.26.515.5-blue.svg" alt="Version: v1.26.515.5">
  <img src="https://img.shields.io/badge/author-李荣起_(Li_Rongqi)-orange.svg" alt="Author">
</p>

---

> **中文**：自动解析项目代码结构与业务逻辑，一键批量生成需求规格、概要设计、详细设计、数据库设计、API 文档、测试计划、部署手册等全套标准化项目文档。

> **English**: Automatically analyze project code structure and business logic, then generate a complete suite of standardized project documents — requirements specification, architecture design, detailed design, database design, API docs, test plan, and deployment guide — all in one click.

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
3. Skill 自动分析代码 → 获取版本信息 → 生成 7 套标准文档
4. 所有文档统一输出至 `Doc/<项目名>/` 目录

</details>

<details>
<summary><b>English</b></summary>

1. Upload your project code or provide the project directory path in the conversation
2. Enter the command: **"Generate project documents"** or **"Create project documents"**
3. The Skill auto-analyzes code → fetches version info → generates 7 standard documents
4. All documents are output to the `Doc/<project-name>/` directory

</details>

---

## ✨ 核心特性 / Feature Highlights

| 特性 Feature | 说明 Description |
|:---|:---|
| 🧠 智能代码分析 / Intelligent Code Analysis | 自动识别项目目录结构、领域模型、业务逻辑与设计模式 / Auto-identifies project structure, domain models, business logic, and design patterns |
| 📄 7 套标准文档 / 7 Standard Documents | 覆盖需求 → 设计 → 数据库 → API → 测试 → 部署全生命周期 / Covers the full lifecycle from requirements through deployment |
| 🔢 自动版本管理 / Auto Versioning | 基于 Git 提交次数或时间戳生成规范版本号 / Generates standardized version numbers based on Git commit count or timestamp |
| 📝 内置变更日志 / Built-in Changelog | 每份文档自动附带版本历史与变更记录 / Every document includes version history and change logs |
| 📁 自动归档目录 / Auto Archive Directory | 一键输出至 `Doc/` 专属目录，结构清晰 / One-click output to a dedicated `Doc/` directory with clear structure |

---

## 📂 文档产出清单 / Generated Document List

| # | 文档 / Document | 内容概要 / Content Summary |
|:---:|:---|:---|
| 01 | 需求规格说明书 / Requirements Specification | 功能概述、功能需求、业务规则、非功能需求 |
| 02 | 概要设计 / System Overview Design | 系统架构、模块划分、类图、核心流程 |
| 03 | 详细设计 / Detailed Design | 方法算法流程、分支逻辑、关键实现细节 |
| 04 | 数据库设计 / Database Design | 数据表结构、字段定义、表间关系、索引 |
| 05 | API 文档 / API Documentation | 接口清单、入参出参、调用示例、异常场景 |
| 06 | 测试计划 / Test Plan | 单元测试用例、边界条件、并发测试 |
| 07 | 部署手册与用户手册 / Deployment & User Manual | 环境要求、配置项、部署步骤、操作指南、FAQ |

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

**李荣起 (Li Rongqi)**

---

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-GPLv3-blue.svg" alt="License: GPLv3"></a>
</p>
