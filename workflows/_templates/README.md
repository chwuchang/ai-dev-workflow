# Workflow 模板说明

`workflows/_templates/` 存放**独立 workflow** 的标准输出模板。

这些模板与 `tasks/_templates/` 的区别是：

- `workflows/_templates/` 面向 `/review` 这类独立命令的输出骨架
- `tasks/_templates/` 面向 `/dev` / `/task` 的任务工作区实例文件

## 当前模板

- `review-report.template.md`：`/review` 的标准审查报告骨架

## 使用规则

- workflow 明确要求使用模板时，应优先基于模板生成输出
- 模板缺失时，`/init` 可以自动恢复
- 模板更新时，应同步检查对应 workflow 文档是否仍然一致

## 禁止事项

- 不要把模板本身当作真实审查结论提交给用户
- 不要在模板中写入某次具体审查的上下文
- 不要把任务工作区文件放进 `workflows/_templates/`
