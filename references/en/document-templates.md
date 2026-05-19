# Document Templates

> **Author Acquisition Priority**  
> When generating documents, the author field is populated based on the following priority:  
> 1. **Current User**: The user identifier invoking the Skill (`$env:USERNAME` / `whoami`)  
> 2. **Git Commit Author**: The latest commit author from the target project (`git log -1 --format=%an`)  
> 3. **Leave Empty**: If neither can be obtained

> **Version Diff Log**  
> When historical document versions exist, the Skill automatically appends a diff log section at the end of each new document, recording changes from the previous version in the following format:  
> - 🟢 **Added**: Content present in the new document but not in the old document  
> - 🟡 **Modified**: Content present in both documents but with changes  
> - 🔴 **Removed**: Content present in the old document but removed from the new document  
> If there are no differences, it notes "No changes from previous version"; if the document is entirely new, it is marked as "New document".

## 01-Requirement Specification Template

```markdown
# Requirement Specification

**Project Name**: XXX Project
**Author**: <Author>
**Date**: YYYY-MM-DD
**Version**: V1.0

## Change Log

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| V1.0 | YYYY-MM-DD | <Author> | Initial version |

---

## 1. Functional Overview
[Description of the core business objectives of the component/system]

## 2. Functional Requirement List

### 2.1 Functional Module A
- Feature point 1
- Feature point 2

### 2.2 Functional Module B
- Feature point 1
- Feature point 2

## 3. Business Rule Requirements

### 3.1 Rule A
[Rule description]

### 3.2 Rule B
[Rule description]

## 4. Non-Functional Requirements

### 4.1 Performance Requirements
- Response time requirements
- Concurrency processing requirements

### 4.2 Security Requirements
- Data security
- Access control

---

## Version Diff (vOldVersion → vNewVersion)

### 🟢 Added
- [Content added compared to previous version]

### 🟡 Modified
- [Content modified compared to previous version]

### 🔴 Removed
- [Content removed compared to previous version]
```

## 02-Overview Design Template

```markdown
# Overview Design

**Project Name**: XXX Project
**Author**: <Author>
**Date**: YYYY-MM-DD
**Version**: V1.0

## Change Log

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| V1.0 | YYYY-MM-DD | <Author> | Initial version |

---

## 1. System Architecture

### 1.1 Design Patterns
[Description of adopted design patterns]

### 1.2 Architecture Diagram
[Architecture diagram description or text representation]

## 2. Module Breakdown

| Module Name | Namespace | Responsibilities |
|-------------|-----------|------------------|
| Module A | XXX | Responsibility description |

## 3. Class Diagram Relationships
[Description of class inheritance and association relationships]

## 4. Core Process Overview
[Overview of main business processes]

## 5. Dependencies

| Dependency | Version | Purpose |
|------------|---------|---------|
| Dependency A | X.X | Purpose description |

---

## Version Diff (vOldVersion → vNewVersion)

### 🟢 Added
- [Content added compared to previous version]

### 🟡 Modified
- [Content modified compared to previous version]

### 🔴 Removed
- [Content removed compared to previous version]
```

## 03-Detailed Design Template

### 3.1 Document Header Format

The detailed design document supports two version number formats:

#### Format 1: Based on Git Commit Count
```
Version format: 1.{yy}.{Mdd}.{git commit count}
Example: 1.26.509.156
Description:
- 1: Major version
- 26: Last two digits of year (2026)
- 509: Month-day combination (May 9)
- 156: Git commit count
```

#### Format 2: Based on Time
```
Version format: 1.{yy}.{Mdd}.{hmm}
Example: 1.26.509.1430
Description:
- 1: Major version
- 26: Last two digits of year (2026)
- 509: Month-day combination (May 9)
- 1430: Hour-minute combination (14:30)
```

#### How to Obtain the Version Number

**Get Git commit count (PowerShell):**
```powershell
$commitCount = git rev-list --count HEAD
$version = "1.{0}.{1}.{2}" -f (Get-Date).ToString("yy"), (Get-Date).ToString("Mdd"), $commitCount
```

**Get time-based version number (PowerShell):**
```powershell
$version = "1.{0}.{1}.{2}" -f (Get-Date).ToString("yy"), (Get-Date).ToString("Mdd"), (Get-Date).ToString("Hmm")
```

### 3.2 Change Log Generation Example

#### Generating Change Logs from Git Commit History

**Step 1: Retrieve Git commit history**
```powershell
# Get the last N commits
git log --pretty=format:"%h|%ad|%an|%s" --date=short -n 20

# Example output:
# a1b2c3d|2026-05-09|Author|feat: Add user login feature
# e4f5g6h|2026-05-08|Author|fix: Fix order query bug
# i7j8k9l|2026-05-07|Author|refactor: Refactor database connection module
```

**Step 2: Parse commit types**

| Commit Prefix | Change Type | Description |
|---------------|-------------|-------------|
| feat | New Feature | New feature or capability |
| fix | Bug Fix | Bug fix |
| refactor | Refactor | Code refactoring/optimization |
| docs | Documentation | Documentation updates |
| style | Formatting | Code formatting adjustments |
| test | Testing | Testing-related changes |
| chore | Build | Build/tooling changes |
| perf | Performance | Performance optimization |
| ci | CI/CD | Continuous integration related |

**Step 3: Generate change log table**

```markdown
## Change Log

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.26.509.156 | 2026-05-09 | <Author> | feat: Add user authentication module detailed design |
| 1.26.508.155 | 2026-05-08 | <Author> | docs: Update API documentation format |
| 1.26.507.154 | 2026-05-07 | <Author> | refactor: Optimize data access layer design |
```

**Step 4: Display grouped by type**

```markdown
## Change Log (Grouped by Type)

### New Features (feat)
- Add user login feature (v1.26.509.156)
- Add order export feature (v1.26.506.153)

### Bug Fixes (fix)
- Fix order query bug (v1.26.508.155)
- Fix data sync exception (v1.26.505.152)

### Code Optimization (refactor)
- Refactor database connection module (v1.26.507.154)
- Optimize caching strategy (v1.26.504.151)
```

#### Automated Change Log Generation Script

```powershell
# generate-changelog.ps1
param(
    [int]$Count = 20,
    [string]$OutputFile = "CHANGELOG.md"
)

$commits = git log --pretty=format:"%h|%ad|%an|%s" --date=short -n $Count
$commitCount = git rev-list --count HEAD

$content = "# Change Log`n`n"
$content += "| Version | Date | Author | Changes |`n"
$content += "|---------|------|--------|---------|`n"

foreach ($line in $commits) {
    $parts = $line.Split("|")
    if ($parts.Length -eq 4) {
        $hash, $date, $author, $message = $parts
        $dateObj = [DateTime]::Parse($date)
        $version = "1.{0}.{1}.{2}" -f $dateObj.ToString("yy"), $dateObj.ToString("Mdd"), $commitCount
        $content += "| $version | $date | $author | $message |`n"
        $commitCount--
    }
}

$content | Out-File -FilePath $OutputFile -Encoding UTF8
Write-Host "Change log generated: $OutputFile"
```

### 3.3 Complete Template Example

```markdown
# Detailed Design

**Project Name**: XXX Project
**Author**: <Author>
**Date**: 2026-05-09
**Version**: 1.26.509.156

## Change Log

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.26.509.156 | 2026-05-09 | <Author> | feat: Add user authentication module detailed design |
| 1.26.508.155 | 2026-05-08 | <Author> | docs: Update API documentation format |
| 1.26.507.154 | 2026-05-07 | <Author> | refactor: Optimize data access layer design |

---

## 1. Class A Detailed Design

### 1.1 Method A Algorithm Flow

#### Initialization Phase
1. Step 1
2. Step 2

#### Core Logic
1. Step 1
2. Step 2

### 1.2 Method B Algorithm Flow
[Same structure as above]

## 2. Key Logic Branch Details

### 2.1 Branch Scenario A
[Condition checking and processing logic]

## 3. Algorithm Description

### 3.1 Algorithm A
[Algorithm description, pseudocode, time complexity]

---

## Version Diff (vOldVersion → vNewVersion)

### 🟢 Added
- [Content added compared to previous version]

### 🟡 Modified
- [Content modified compared to previous version]

### 🔴 Removed
- [Content removed compared to previous version]
```

## 04-Database Design Template

```markdown
# Database Design

**Project Name**: XXX Project
**Author**: <Author>
**Date**: YYYY-MM-DD
**Version**: V1.0

## Change Log

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| V1.0 | YYYY-MM-DD | <Author> | Initial version |

---

## 1. Core Data Tables

### 1.1 Table A (TABLE_A)

| Field Name | Type | Description |
|------------|------|-------------|
| id | long | Primary key ID |
| name | string | Name |

## 2. Table Relationships

### 2.1 Hierarchical Relationships
```
Table A → Table B → Table C
```

## 3. Index Recommendations

| Table Name | Index Fields | Index Type | Description |
|------------|-------------|------------|-------------|
| Table A | field1, field2 | Composite index | Description |

---

## Version Diff (vOldVersion → vNewVersion)

### 🟢 Added
- [Content added compared to previous version]

### 🟡 Modified
- [Content modified compared to previous version]

### 🔴 Removed
- [Content removed compared to previous version]
```

## 05-API Documentation Template

```markdown
# API Documentation

**Project Name**: XXX Project
**Author**: <Author>
**Date**: YYYY-MM-DD
**Version**: V1.0

## Change Log

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| V1.0 | YYYY-MM-DD | <Author> | Initial version |

---

## 1. API Overview

| Method | Class | Description |
|--------|-------|-------------|
| Method A | Class A | Description |

## 2. API Details

### 2.1 Method A

**Method Signature**:
```csharp
public ReturnType MethodName(ParamType param)
```

**Parameter Description**:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| param | Type | Yes | Description |

**Return Value**: Description of return type

**Usage Example**:
```csharp
// Example code
```

## 3. Exception Scenarios

| Scenario | Result | Description |
|----------|--------|-------------|
| Scenario A | Result A | Description |

---

## Version Diff (vOldVersion → vNewVersion)

### 🟢 Added
- [Content added compared to previous version]

### 🟡 Modified
- [Content modified compared to previous version]

### 🔴 Removed
- [Content removed compared to previous version]
```

## 06-Test Plan Template

```markdown
# Test Plan

**Project Name**: XXX Project
**Author**: <Author>
**Date**: YYYY-MM-DD
**Version**: V1.0

## Change Log

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| V1.0 | YYYY-MM-DD | <Author> | Initial version |

---

## 1. Test Scope
[List of functional modules covered by testing]

## 2. Unit Test Cases

### 2.1 Functional Module A

#### Positive Test Cases
| Case ID | Case Name | Preconditions | Test Steps | Expected Result |
|---------|-----------|---------------|------------|-----------------|
| TC-001 | Case name | Conditions | Steps | Result |

#### Negative Test Cases
| Case ID | Case Name | Preconditions | Test Steps | Expected Result |
|---------|-----------|---------------|------------|-----------------|

## 3. Concurrency Test Plan
[Concurrency test cases and tools]

## 4. Boundary Condition Testing
[Boundary value test cases]

## 5. Test Data Preparation
[Test data description]

---

## Version Diff (vOldVersion → vNewVersion)

### 🟢 Added
- [Content added compared to previous version]

### 🟡 Modified
- [Content modified compared to previous version]

### 🔴 Removed
- [Content removed compared to previous version]
```

## 07-Deployment & User Manual Template

```markdown
# Deployment & User Manual

**Project Name**: XXX Project
**Author**: <Author>
**Date**: YYYY-MM-DD
**Version**: V1.0

## Change Log

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| V1.0 | YYYY-MM-DD | <Author> | Initial version |

---

# Part 1: Deployment Manual

## 1. Environment Requirements

### 1.1 Runtime Environment
| Item | Requirement |
|------|-------------|
| Operating System | Requirement |

### 1.2 Dependency Components
| Component | Version | Purpose |
|-----------|---------|---------|

## 2. Configuration Description
[Configuration files and parameter descriptions]

## 3. Deployment Steps
1. Step 1
2. Step 2

## 4. Operations Monitoring
[Monitoring metrics and log descriptions]

---

# Part 2: User Manual

## 1. Feature Operation Guide
[Operation steps for each feature]

## 2. Configuration Instructions
[User-configurable items]

## 3. Common Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| Problem A | Cause A | Solution A |

---

## Version Diff (vOldVersion → vNewVersion)

### 🟢 Added
- [Content added compared to previous version]

### 🟡 Modified
- [Content modified compared to previous version]

### 🔴 Removed
- [Content removed compared to previous version]
```
