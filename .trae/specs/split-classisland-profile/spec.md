# 拆分 ClassIsland 课表档案 Spec

## Why
将 `20260315后高一16课表.json` 拆分为独立的课表文件、时间表文件和科目文件，并更新集控清单，以符合 ClassIsland 集控配置的拆分规范。

## What Changes
- 从 `20260315后高一16课表.json` 中提取 `TimeLayouts` 部分，创建 `TimeLayouts.json`
- 从 `20260315后高一16课表.json` 中提取 `ClassPlans` 部分，创建 `ClassPlans.json`
- 从 `20260315后高一16课表.json` 中提取 `Subjects` 部分，创建 `Subjects.json`
- 修改 `manifest.json`，添加 `ClassPlanSource`、`TimeLayoutSource`、`SubjectsSource` 字段
- 原文件 `20260315后高一16课表.json` 保留不删除

## Impact
- Affected specs: 集控清单配置
- Affected code: `manifest.json`（修改），新增 `TimeLayouts.json`、`ClassPlans.json`、`Subjects.json`

## ADDED Requirements

### Requirement: 拆分为时间表文件
系统 SHALL 从 `20260315后高一16课表.json` 中提取 `TimeLayouts` 部分，生成 `TimeLayouts.json`，格式为：
```json
{"Name":"","TimeLayouts":{...},"ClassPlans":{},"Subjects":{}}
```

#### Scenario: 成功拆分时间表
- **WHEN** 执行拆分操作
- **THEN** 生成 `TimeLayouts.json`，包含完整的 `TimeLayouts` 内容，`ClassPlans` 和 `Subjects` 为空对象

### Requirement: 拆分为课表文件
系统 SHALL 从 `20260315后高一16课表.json` 中提取 `ClassPlans` 部分，生成 `ClassPlans.json`，格式为：
```json
{"Name":"","TimeLayouts":{},"ClassPlans":{...},"Subjects":{}}
```

#### Scenario: 成功拆分课表
- **WHEN** 执行拆分操作
- **THEN** 生成 `ClassPlans.json`，包含完整的 `ClassPlans` 内容，`TimeLayouts` 和 `Subjects` 为空对象

### Requirement: 拆分为科目文件
系统 SHALL 从 `20260315后高一16课表.json` 中提取 `Subjects` 部分，生成 `Subjects.json`，格式为：
```json
{"Name":"","TimeLayouts":{},"ClassPlans":{},"Subjects":{...}}
```

#### Scenario: 成功拆分科目
- **WHEN** 执行拆分操作
- **THEN** 生成 `Subjects.json`，包含完整的 `Subjects` 内容，`TimeLayouts` 和 `ClassPlans` 为空对象

### Requirement: 更新集控清单
系统 SHALL 修改 `manifest.json`，添加 `ClassPlanSource`、`TimeLayoutSource`、`SubjectsSource` 字段，每个字段为 `ReVersionString` 类型，包含 `Value`（文件 URL 模板）和 `Version`（版本号，初始为 1）。

#### Scenario: 成功更新集控清单
- **WHEN** 执行拆分操作后
- **THEN** `manifest.json` 包含 `ClassPlanSource`、`TimeLayoutSource`、`SubjectsSource` 字段，`Value` 指向对应的 JSON 文件，`Version` 为 1

### Requirement: 保留原始文件
系统 SHALL NOT 删除 `20260315后高一16课表.json`。

#### Scenario: 原始文件保留
- **WHEN** 拆分完成后
- **THEN** `20260315后高一16课表.json` 仍然存在于工作目录中