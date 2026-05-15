# Git 版本信息参考文档

## 1. 版本号生成算法详细说明

### 1.1 有 Git 环境的版本号格式

**格式：** `1.{yy}.{Mdd}.{git提交次数}`

**组成部分：**
- `1` - 主版本号（固定为1）
- `{yy}` - 当前年份的后两位
- `{Mdd}` - 当前日期（M为月份1-9不补零，dd为日期补零）
- `{git提交次数}` - Git 仓库的总提交次数

**示例：**
- 日期：2026年5月9日
- Git 提交次数：1234
- 版本号：`1.26.509.1234`

**说明：**
- 月份 M 不补零（1-9月显示为1-9，10-12月显示为10-12）
- 日期 dd 补零（01-31）
- Git 提交次数通过 `git rev-list --count HEAD` 命令获取

### 1.2 无 Git 环境的版本号格式

**格式：** `1.{yy}.{Mdd}.{hmm}`

**组成部分：**
- `1` - 主版本号（固定为1）
- `{yy}` - 当前年份的后两位
- `{Mdd}` - 当前日期（M为月份1-9不补零，dd为日期补零）
- `{hmm}` - 当前时间（h为小时不补零，mm为分钟补零）

**示例：**
- 日期时间：2026年5月9日 14:05
- 版本号：`1.26.509.1405`

**说明：**
- 当无法获取 Git 信息时，使用时间作为第四部分
- 小时 h 不补零（0-23显示为0-23）
- 分钟 mm 补零（00-59）

---

## 2. Git 命令参考

### 2.1 获取总提交次数

**命令：**
```bash
git rev-list --count HEAD
```

**参数说明：**
- `rev-list` - 列出提交对象
- `--count` - 只输出计数结果
- `HEAD` - 当前分支的最新提交

**输出示例：**
```
1234
```

### 2.2 获取最近提交记录

**命令：**
```bash
git log -n 10 --pretty=format:"%h|%ad|%an|%s" --date=short
```

**参数说明：**
- `-n 10` - 限制输出最近10条记录
- `--pretty=format` - 自定义输出格式
  - `%h` - 简短的提交哈希值
  - `%ad` - 作者日期
  - `%an` - 作者姓名
  - `%s` - 提交说明
- `--date=short` - 使用短日期格式（YYYY-MM-DD）

**输出示例：**
```
a1b2c3d|2026-05-09|李荣起|添加用户登录功能
e4f5g6h|2026-05-08|张三|修复订单查询bug
i7j8k9l|2026-05-07|李四|优化数据库查询性能
```

### 2.3 获取 Git 提交作者

**用途**：当无法获取当前系统用户时，从目标项目的 Git 记录中提取作者名作为文档作者。

**命令：**
```bash
git log -1 --format=%an
```

**参数说明：**
- `log -1` - 仅获取最近一条提交记录
- `--format=%an` - 只输出作者姓名（author name）

**输出示例：**
```
张三
```

**获取提交者（committer）名称：**
```bash
git log -1 --format=%cn
```

**获取作者 + 提交者两者的完整信息：**
```bash
git log -1 --pretty=format:"作者(Author): %an <%ae>%n提交者(Committer): %cn <%ce>"
```

**输出示例：**
```
作者(Author): 张三 <zhangsan@example.com>
提交者(Committer): 李四 <lisi@example.com>
```

### 2.4 其他常用命令

**获取当前分支名称：**
```bash
git rev-parse --abbrev-ref HEAD
```

**获取最新提交哈希值：**
```bash
git rev-parse HEAD
```

**获取最新提交时间：**
```bash
git log -1 --format=%cd --date=short
```

---

## 3. 变更日志格式

### 3.1 变更日志表格格式

```markdown
## 变更日志

| 版本号 | 日期 | 类型 | 模块 | 描述 | 作者 |
|--------|------|------|------|------|------|
| 1.26.509.1234 | 2026-05-09 | 新增 | 用户管理 | 添加用户登录功能 | 李荣起 |
| 1.26.508.1233 | 2026-05-08 | 修复 | 订单管理 | 修复订单查询bug | 张三 |
| 1.26.507.1232 | 2026-05-07 | 优化 | 数据库 | 优化查询性能 | 李四 |
```

### 3.2 字段说明

| 字段 | 说明 | 示例 |
|------|------|------|
| 版本号 | 完整的版本号 | 1.26.509.1234 |
| 日期 | 变更日期（YYYY-MM-DD） | 2026-05-09 |
| 类型 | 变更类型 | 新增、修复、优化、删除、重构 |
| 模块 | 受影响的功能模块 | 用户管理、订单管理 |
| 描述 | 变更的简要说明 | 添加用户登录功能 |
| 作者 | 变更的提交者 | 李荣起 |

### 3.3 变更类型定义

| 类型 | 说明 | 图标建议 |
|------|------|----------|
| 新增 | 新增功能或特性 | ✨ |
| 修复 | 修复bug或问题 | 🐛 |
| 优化 | 性能优化或代码改进 | ⚡ |
| 删除 | 删除功能或代码 | 🗑️ |
| 重构 | 代码重构 | ♻️ |
| 文档 | 文档更新 | 📝 |
| 测试 | 测试相关变更 | ✅ |

### 3.4 完整示例

```markdown
# 项目变更日志

## v1.26.509.1234 (2026-05-09)

### ✨ 新增功能
- 用户管理模块：添加用户登录功能
- 订单管理模块：新增订单导出功能

### 🐛 Bug修复
- 数据库模块：修复连接池泄漏问题

### ⚡ 性能优化
- 查询模块：优化分页查询性能

---

## v1.26.508.1233 (2026-05-08)

### ✨ 新增功能
- API模块：新增用户信息查询接口

### 🐛 Bug修复
- 订单管理模块：修复订单状态更新异常
```

---

## 附录：版本号生成代码示例

### Python 示例

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

### JavaScript 示例

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

**文档作者：** 李荣起  
**创建日期：** 2026-05-09  
**文档版本：** 1.0
