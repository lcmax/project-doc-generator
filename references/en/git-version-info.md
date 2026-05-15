# Git Version Information Reference

## 1. Version Number Generation Algorithm Details

### 1.1 Version Number Format with Git Environment

**Format:** `1.{yy}.{Mdd}.{git commit count}`

**Components:**
- `1` - Major version (fixed at 1)
- `{yy}` - Last two digits of the current year
- `{Mdd}` - Current date (M = month without zero-padding for 1-9, dd = day with zero-padding)
- `{git commit count}` - Total commit count of the Git repository

**Example:**
- Date: May 9, 2026
- Git commit count: 1234
- Version number: `1.26.509.1234`

**Notes:**
- Month M is not zero-padded (months 1-9 display as 1-9, months 10-12 display as 10-12)
- Day dd is zero-padded (01-31)
- Git commit count is obtained via the `git rev-list --count HEAD` command

### 1.2 Version Number Format without Git Environment

**Format:** `1.{yy}.{Mdd}.{hmm}`

**Components:**
- `1` - Major version (fixed at 1)
- `{yy}` - Last two digits of the current year
- `{Mdd}` - Current date (M = month without zero-padding for 1-9, dd = day with zero-padding)
- `{hmm}` - Current time (h = hour without zero-padding, mm = minute with zero-padding)

**Example:**
- Date and time: May 9, 2026 14:05
- Version number: `1.26.509.1405`

**Notes:**
- When Git information cannot be obtained, the time is used as the fourth part
- Hour h is not zero-padded (0-23 display as 0-23)
- Minute mm is zero-padded (00-59)

---

## 2. Git Command Reference

### 2.1 Get Total Commit Count

**Command:**
```bash
git rev-list --count HEAD
```

**Parameter Description:**
- `rev-list` - List commit objects
- `--count` - Output only the count result
- `HEAD` - Latest commit of the current branch

**Example Output:**
```
1234
```

### 2.2 Get Recent Commit History

**Command:**
```bash
git log -n 10 --pretty=format:"%h|%ad|%an|%s" --date=short
```

**Parameter Description:**
- `-n 10` - Limit output to the last 10 records
- `--pretty=format` - Custom output format
  - `%h` - Abbreviated commit hash
  - `%ad` - Author date
  - `%an` - Author name
  - `%s` - Commit message
- `--date=short` - Use short date format (YYYY-MM-DD)

**Example Output:**
```
a1b2c3d|2026-05-09|Li Rongqi|feat: Add user login feature
e4f5g6h|2026-05-08|Zhang San|fix: Fix order query bug
i7j8k9l|2026-05-07|Li Si|perf: Optimize database query performance
```

### 2.3 Get Git Commit Author

**Purpose**: When the current system user cannot be obtained, extract the author name from the target project's Git records to use as the document author.

**Command:**
```bash
git log -1 --format=%an
```

**Parameter Description:**
- `log -1` - Only retrieve the most recent commit record
- `--format=%an` - Output only the author name

**Output Example:**
```
Zhang San
```

**Get Committer Name:**
```bash
git log -1 --format=%cn
```

**Get Both Author and Committer Information:**
```bash
git log -1 --pretty=format:"Author: %an <%ae>%nCommitter: %cn <%ce>"
```

**Output Example:**
```
Author: Zhang San <zhangsan@example.com>
Committer: Li Si <lisi@example.com>
```

### 2.4 Other Common Commands

**Get current branch name:**
```bash
git rev-parse --abbrev-ref HEAD
```

**Get latest commit hash:**
```bash
git rev-parse HEAD
```

**Get latest commit time:**
```bash
git log -1 --format=%cd --date=short
```

---

## 3. Change Log Format

### 3.1 Change Log Table Format

```markdown
## Change Log

| Version | Date | Type | Module | Description | Author |
|---------|------|------|--------|-------------|--------|
| 1.26.509.1234 | 2026-05-09 | New Feature | User Management | Add user login feature | Li Rongqi |
| 1.26.508.1233 | 2026-05-08 | Bug Fix | Order Management | Fix order query bug | Zhang San |
| 1.26.507.1232 | 2026-05-07 | Optimization | Database | Optimize query performance | Li Si |
```

### 3.2 Field Descriptions

| Field | Description | Example |
|-------|-------------|---------|
| Version | Complete version number | 1.26.509.1234 |
| Date | Change date (YYYY-MM-DD) | 2026-05-09 |
| Type | Change type | New Feature, Bug Fix, Optimization, Removal, Refactor |
| Module | Affected functional module | User Management, Order Management |
| Description | Brief description of the change | Add user login feature |
| Author | Committer of the change | Li Rongqi |

### 3.3 Change Type Definitions

| Type | Description | Suggested Icon |
|------|-------------|----------------|
| New Feature | New feature or capability | ✨ |
| Bug Fix | Bug fix or issue resolution | 🐛 |
| Optimization | Performance optimization or code improvement | ⚡ |
| Removal | Feature or code removal | 🗑️ |
| Refactor | Code refactoring | ♻️ |
| Documentation | Documentation update | 📝 |
| Testing | Testing-related changes | ✅ |

### 3.4 Complete Example

```markdown
# Project Change Log

## v1.26.509.1234 (2026-05-09)

### ✨ New Features
- User Management Module: Add user login feature
- Order Management Module: Add order export feature

### 🐛 Bug Fixes
- Database Module: Fix connection pool leak issue

### ⚡ Performance Optimizations
- Query Module: Optimize pagination query performance

---

## v1.26.508.1233 (2026-05-08)

### ✨ New Features
- API Module: Add user info query endpoint

### 🐛 Bug Fixes
- Order Management Module: Fix order status update exception
```

---

## Appendix: Version Number Generation Code Examples

### Python Example

```python
import subprocess
from datetime import datetime

def get_version():
    now = datetime.now()
    yy = now.strftime("%y")
    M = str(now.month)
    dd = now.strftime("%d")

    try:
        result = subprocess.run(
            ["git", "rev-list", "--count", "HEAD"],
            capture_output=True,
            text=True,
            check=True
        )
        commit_count = result.stdout.strip()
        return f"1.{yy}.{M}{dd}.{commit_count}"
    except:
        h = str(now.hour)
        mm = now.strftime("%M")
        return f"1.{yy}.{M}{dd}.{h}{mm}"

print(get_version())
```

### JavaScript Example

```javascript
const { execSync } = require('child_process');

function getVersion() {
    const now = new Date();
    const yy = now.getFullYear().toString().slice(-2);
    const M = (now.getMonth() + 1).toString();
    const dd = now.getDate().toString().padStart(2, '0');

    try {
        const commitCount = execSync('git rev-list --count HEAD', { encoding: 'utf-8' }).trim();
        return `1.${yy}.${M}${dd}.${commitCount}`;
    } catch {
        const h = now.getHours().toString();
        const mm = now.getMinutes().toString().padStart(2, '0');
        return `1.${yy}.${M}${dd}.${h}${mm}`;
    }
}

console.log(getVersion());
```

---

**Document Author:** Li Rongqi
**Created Date:** 2026-05-09
**Document Version:** 1.0
