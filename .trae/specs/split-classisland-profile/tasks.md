# Tasks

- [ ] Task 1: 创建 TimeLayouts.json
  - 从 `20260315后高一16课表.json` 中提取 `TimeLayouts` 部分（第3行至第4872行）
  - 按模板格式 `{"Name":"","TimeLayouts":{...},"ClassPlans":{},"Subjects":{}}` 生成 `TimeLayouts.json`

- [ ] Task 2: 创建 ClassPlans.json
  - 从 `20260315后高一16课表.json` 中提取 `ClassPlans` 部分（第4873行至第6789行）
  - 按模板格式 `{"Name":"","TimeLayouts":{},"ClassPlans":{...},"Subjects":{}}` 生成 `ClassPlans.json`

- [ ] Task 3: 创建 Subjects.json
  - 从 `20260315后高一16课表.json` 中提取 `Subjects` 部分（第6790行至第8554行）
  - 按模板格式 `{"Name":"","TimeLayouts":{},"ClassPlans":{},"Subjects":{...}}` 生成 `Subjects.json`

- [ ] Task 4: 修改 manifest.json
  - 在现有 `manifest.json` 中添加 `ClassPlanSource`、`TimeLayoutSource`、`SubjectsSource` 字段
  - 每个字段为 `ReVersionString` 格式：`{"Value": "<文件名>", "Version": 1}`
  - 保留原有所有字段

# Task Dependencies
- Task 1、Task 2、Task 3 可并行执行
- Task 4 依赖于 Task 1、2、3 完成（需要知道文件名）