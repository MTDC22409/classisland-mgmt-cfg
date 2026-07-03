# Checklist

- [ ] `TimeLayouts.json` 已创建，包含完整的 `TimeLayouts` 内容，`ClassPlans` 和 `Subjects` 为空对象
- [ ] `ClassPlans.json` 已创建，包含完整的 `ClassPlans` 内容，`TimeLayouts` 和 `Subjects` 为空对象
- [ ] `Subjects.json` 已创建，包含完整的 `Subjects` 内容，`TimeLayouts` 和 `ClassPlans` 为空对象
- [ ] `manifest.json` 已更新，包含 `ClassPlanSource`、`TimeLayoutSource`、`SubjectsSource` 字段
- [ ] `manifest.json` 中 `ReVersionString` 字段的 `Version` 均为 1
- [ ] `manifest.json` 原有字段（`ServerKind`、`CoreVersion`、`OrganizationName`、`Disable*` 等）均保留
- [ ] `20260315后高一16课表.json` 原始文件未被删除
- [ ] 各 JSON 文件为有效 JSON 格式