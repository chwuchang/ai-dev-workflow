---
description: 一键初始化项目的 workflow 基础设施（归档目录、上下文文档、workflow 模板）
---

# /init — 项目初始化

// turbo-all

## 执行步骤

### 1. 检测现有结构

扫描项目根目录下的 `.agents/` 目录，列出已存在和缺失的文件：

**必须存在的文件清单：**
- `.agents/workflows/init.md`
- `.agents/workflows/dev.md`
- `.agents/workflows/fix.md`
- `.agents/workflows/task.md`
- `.agents/workflows/discuss.md`
- `.agents/specs/_overview.md`
- `.agents/archive/_index.md`
- `.agents/archive/features/`
- `.agents/archive/bugfix/`
- `.agents/archive/decisions/`
- `.agents/context/architecture.md`
- `.agents/context/active-tasks.md`
- `.agents/context/user-preferences.md`
- `.agents/context/feedback.md`
- `.agents/context/references.md`

### 2. 创建缺失文件

只创建缺失的文件，**不覆盖**已有内容。

- 归档索引文件使用标准模板（见 `.agents/archive/_index.md` 格式）
- 上下文文件需要根据项目实际情况填充

### 3. 自动填充上下文（老项目）

如果项目已有代码：

1. 读取 `requirements.txt` / `package.json` / `go.mod` 等获取技术栈
2. 扫描顶层目录结构推断模块划分
3. 读取已有 `README.md` 或 `docs/ARCHITECTURE.md` 获取项目描述
4. 将以上信息写入 `.agents/context/architecture.md`

如果项目是空的：
- 创建空模板文件，等待用户后续填充

### 4. 输出初始化报告

以表格形式输出：

```
| 文件 | 状态 |
|------|------|
| workflows/dev.md | ✅ 已存在 |
| archive/_index.md | 🆕 已创建 |
| context/architecture.md | 🆕 已创建（已自动填充） |
```

## 幂等保证

- 此 workflow 可重复执行，不会破坏已有内容
- 已存在的文件标记为"已存在"并跳过
- 仅补充缺失部分
