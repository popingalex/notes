# JIRA-Software 敏捷的项目管理与事务追踪
## Issue 事务
### Epic
- 相同主题Story的集合
- 可以包含来自多个项目的Story

![Epic](../../../issue_epic_story.png)

### Story
- 事物跟踪的基本单位，可以包含多个Task
- 完成阐述场景，角色，发生的事件，也称用户故事
- 尽量使用非技术性描述
- 在软件开发任务中可拆分的模块级别的开发任务

![Story](/pics/guide_team_jira/issue_story_task.png)

### Task
- 任务的最小执行单位，由Story拆分而来
- 可以包含具体技术细节
- 在软件开发任务中不可拆分的功能点级别开发任务

---

## Workflow 工作流

由多个 ```Status``` 与 ```Transition``` 组成的有向图称为工作流，工作流包含了一个事物可能的所有状态及这些状态之间的变化，他们对监控事物进展很有帮助。
![Workflow](/pics/guide_team_jira/workflow.png)

### Status
在开发过程中 ```Issue / 事物``` 的状态不断变化，如：
- 刚创建的事物
- 已分配的事物
- 在进行的事物
- 待评审的事物
- 已归档的事物

### Transition
事物从一个 ```Issue / 事物``` 转变为另一个 ```Issue / 事物``` 的过程称为 ```Transition``` 。期间可能包含事物属性的变化，如：
- 事物分配时必须确定事物的执行人员
- 事物进行时需要设置事物开始的时间点
- 事物结束时会自动分配事物的结束时间

等。

---

## Sprint 冲刺
敏捷开发流程中，一个积极健康的开发周期被称为冲刺，一个健康的冲刺：
- 应该在开始前对要进行的开发任务进行评估
- 不强迫所有的事物必须在本开发周期内完成
- 每个开发者应尽量保持手里有且仅有一个任务，最多不要超过两个

![Workflow](/pics/guide_team_jira/sprint_backlog.png)

---

## Board 看板
物理看板的抽象实现。

![Workflow](/pics/guide_team_jira/board.png)

---

## Report 报表
统计工具。

![Workflow](/pics/guide_team_jira/report_all.png)

![Workflow](/pics/guide_team_jira/report_assignees.png)
