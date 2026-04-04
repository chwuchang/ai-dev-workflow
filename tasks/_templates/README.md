# 任务模板说明

`tasks/_templates/` 提供 `/dev` 与 `/task` 使用的标准骨架，用于减少格式漂移，并让任务状态具备可恢复性。

## 模板用途

- `plan.template.md`：实现方案
- `checklist.template.md`：任务拆解与验收标准
- `status.template.md`：执行状态与下一步
- `review.template.md`：最终审查与验证记录

## 使用规则

- 新建任务工作区时，应优先从这些模板生成实例文件
- 模板文件缺失时，`/init` 可以自动恢复
- 模板文件更新时，应保持与 workflow 规则一致

## 禁止事项

- 不要把模板文件直接当作任务实例使用
- 不要在缺少历史上下文的情况下，凭猜测重建某个活跃任务的 `plan.md`、`checklist.md` 或 `status.md`
- 不要把一次性任务说明写回模板

## 推荐流程

1. 通过 `/dev` 创建 `task-id`
2. 从模板生成 `plan.md`、`checklist.md`、`status.md`、`review.md`
3. 在 `context/active-tasks.md` 中登记任务
4. 执行期间持续更新 `status.md`
5. 完成后归档，并将 `status.md` 标记为 completed
