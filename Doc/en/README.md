【Skill Creation】Automatic Project Document Generator
> Version: 1.26.731.20 | Updated: 2026-07-31 | Author: Rongqi Li

1. Skill Introduction
This is an automatic project document generator Skill that intelligently analyzes project code structures, architectural logic, and business modules. It can one-click generate a full set of standardized project documents with automatic version numbering and change log management. It is perfectly suitable for developers, project managers and operation & maintenance personnel who need rapid document supplementation, project delivery and file archiving.

**New in v1.26.731.20**:
- 🎯 **Interactive Parameter Collection**: Before generation, collects project name, language, scope, format and author via prompts. Compatible with 8 IDEs (Trae/Trae Work/Claude Code/Codex/Cursor/OpenCode/WorkBuddy/CodeArts) using a three-tier fallback strategy (native prompt → text prompt → default value)
- 🌐 **On-demand Multilingual Generation**: Supports Chinese-only / English-only / Bilingual modes, dynamically trimming directory creation, archiving and diff comparison
- 📦 **Generation Scope Selection**: Supports all 7 documents or custom subset (e.g. "1,3,5"), with partial-generation annotation in document header
- 👤 **Author Priority Chain**: Project-level rule (Rongqi Li) → Current user → Git commit author → Empty
- ✅ **Dynamic Checklist**: Rendered dynamically based on user-selected language and scope, replacing the original hardcoded checklist
2. Usage Scenarios
In daily software development and project delivery, teams often face common pain points: new projects lack complete standard documents, old projects have no reserved technical files, and manual writing of requirement specifications, design documents, API manuals and deployment guides is extremely time-consuming.
Manual document work usually leads to inconsistent formatting, missing version records, chaotic file management and low collaboration efficiency. With this Skill, users only need to provide project code or directory information to automatically generate a full set of standardized documents, eliminate repetitive writing, typesetting and version sorting work, and realize one-stop standardized document output.
3. Creation Process
1. Core Trigger Setting
Set exclusive trigger commands including "Generate project documents" and "Create project documents", covering mainstream usage demands such as new project construction, old project document supplement and project delivery archiving.
2. Intelligent Code Analysis Logic
Build a complete analysis workflow: automatically identify project directory structure, read core code files, analyze system architecture, domain models, business logic and design patterns to ensure generated documents fit the actual project situation.
3. Standard Version Management Mechanism
Design dual version number rules for different environments. For Git-managed projects, generate versions based on year, month, date and Git commit counts; for non-Git projects, generate versions through timestamp (hour and minute). Automatically extract Git commit records to support traceable change logs.
4. Complete Document System Configuration
Preset 7 sets of industry-standard document templates, covering Requirement Specification, System Overview Design, Detailed Design, Database Design, API Documentation, Test Plan, Deployment & User Manual, covering the whole life cycle of project technical documents.
5. Standardized Specification Optimization
Unify the header format of all documents, including project name, author, date and version number. Built-in fixed change log table to record iteration details, and automatically create a dedicated Doc/Project Name archive directory for classified storage.
6. Interactive Parameter Collection (New in v1.26.731.20)
Before generation, collects project name, document language (Chinese/English/Bilingual), generation scope (all/custom subset), output format (Markdown/DOCX) and author preference via IDE-native prompt tools or text prompts. Dynamically trims subsequent archiving and diff comparison based on user selection.
7. Multi-IDE Compatibility Strategy (New in v1.26.731.20)
Prioritizes AskUserQuestion tool for Trae/Trae Work/Claude Code; adopts text-prompt fallback for Codex/Cursor/OpenCode/WorkBuddy/CodeArts, ensuring consistent cross-IDE experience.
4. Operation Steps
1. Call this Skill and enter the command: Generate project documents / Create project documents;
2. Upload project code files or input the project directory structure;
3. The Skill automatically parses project code and obtains Git version information or local timestamp data;
4. Interactive Confirmation (New in v1.26.731.20): The Skill prompts to confirm project name, document language (Chinese-only/English-only/Bilingual), generation scope (all 7/custom subset), output format (Markdown/DOCX) and author; replying "skip/default" uses default values;
5. Creates dedicated document directory based on confirmed selections and generates standard documents for the corresponding language and scope in sequence;
6. Outputs the complete document suite with standard version numbers and change logs for direct use and archiving.
5. Effect Display
Before use: Manually writing a full set of project documents takes half a day or even longer, with irregular formats, missing version records and scattered files, which is not conducive to project delivery and team collaboration.
After use: Complete standardized document generation within one minute. All documents have unified specifications, automatic version iteration and complete change records, which can be directly used for project delivery, technical handover and long-term file archiving.
(Screenshot suggestions: Skill workflow configuration screenshot, generated Doc directory structure screenshot, document header version & change log display screenshot, full document list preview)
6. Skill Link
(Paste your Skill sharing link here. You can also attach GitHub repository, detailed usage documents and Demo links)
7. Summary & Thoughts
Efficiency Improvement
This Skill completely solves the pain point of inefficient manual document writing for developers. It shortens the document production cycle from half a day to several minutes, standardizes document styles uniformly, and greatly improves the efficiency of project sorting, technical handover and formal delivery.
Most Satisfactory Points
It integrates a complete set of industrial-grade software engineering document systems, realizing intelligent code analysis and one-click batch generation. The rigorous version iteration rule and automatic change log recording make technical documents traceable, replicable and more professional than manual writing.
Future Optimization Directions
- ✅ ~~Word format export~~ (DOCX output supported, v1.26.731.20)
- ✅ ~~On-demand multilingual generation~~ (Chinese-only/English-only/Bilingual supported, v1.26.731.20)
- ✅ ~~Interactive parameter collection~~ (compatible with 8 IDEs, v1.26.731.20)
- 🔄 Future plans: support in-depth code analysis for more technical stacks; add PDF format export; support custom enterprise document templates, headers and footers, and personalized version rule configuration.
Experience & Feedback Invitation
Welcome developers, project managers and operation & maintenance engineers to experience and test this Skill. Feel free to put forward demands for new document types and customized rules, and I will continue to iterate and optimize the functions.
