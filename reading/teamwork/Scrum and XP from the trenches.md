# 序章
敏捷是生产力的保障

## Nokia Test
### are you actually doing iterative development
- Iterations must be timeboxed to less than 4 weeks
  > 迭代周期限制在四周内

- Software features must be tested and working at the end of each iteration
  > 软件功能在迭代周期结束时必须可用且通过测试

- The iteration must start before specification is complete
  > 在产品规格说明书完成之前已经开始迭代

### use of scrum
- You know who the Product Owner is (I prefer the term Product Champion)
  > 知道```产品负责人``` / ```产品经理```是谁

- There is a product backlog prioritized by business value
  > 产品backlog应根据商业价值排列优先级

- The product backlog has estimates created by the team (relative sizes created through team consensus – probably using Planning Poker)
  > 产品backlog应由开发团队评估成本(可以用用敏捷扑克牌)

- The team generates burndown charts and knows their velocity (I prefer burnup charts, and it is impossible to know velocity for a few iterations)
  > 团队应通过燃尽图或燃耗图观察工作进度

- There are no project managers (or anyone else) disrupting the work of the team
  > 尽量避免打断开发团队的迭代

# Product Backlog
## Story
### Basic
- ID / Key
- Name / Summary
- Importance / Priority
- Estimate / Story Point, man-day
- How to Demo / Use Case / Story
- Note / Comment

### Extra
- Label / Tag
- Components
- Reporter / Assignee
- Link

# Srpint
## Prepare
- 负责人对backlog进行优先级评估
- 负责人理解backlog中的故事

## Plan
- Target
- Participant
- Sprint backlog
- Deadline

## Balance
- Estimate
- Importance
- Quality (Inner -> Outer)
- Scope : 粒度, Issue Linking

## Velocity
- ```Estimated Velocity``` = ```Available man-days``` x ```Focus Factor```
- ```Focus Factor``` = ```Actual Velocity``` / ```Available man-days```

## Define 'Done'
- 提交
- 通过评审
- 通过测试
- 通过QA

## Estimate 可以试试 ```Plan Poker```

## Priority
1. Target / Deadline / Sprint Backlog
2. Filtered Discussed Sprint Backlog
3. Estimate
4. Use Case
5. Velocity / Resources
6. Meeting
7. Story -> Task

## Technical Story
- Refactor
- Documents
- CI Services
- Devops Work

与一般Story区分开

## Bug Track vs Product Backlog
- 应该为即将到来的bug做好准备(额外工作)
- 重大缺陷或功能不足可以作为Story参加敏捷会议

# 展示我们的工作状况
## Sprint Info
- Sprint goal
- Sprint backlog
- Schedual (meetings)
- Team info
- Dashboard

## Notification
- 会议纪要
- 冲刺开始或结束

## Sprint Review
- 确保任务真的'完成'了
- 演示成果物
- 制定验收标准

# Scrum & XP
## Test Driven development
### 基本要求
- 根据需求写用例
- 根据用例实现功能
- 在服务器上进行构建
- 在此基础上不断迭代

### 测试阶段
1. 单元测试
2. 集成测试
3. 功能测试
4. 验收测试

### 改进路线
1. 优化测试流程
2. 测试小工具
3. 测试脚本
4. 自动化测试

### 发布过程
1. 开发:snapshot
2. 测试:release
3. 发布:archive

# 团队构成
- Developer
- Test
- Support
- Fire Fighter
