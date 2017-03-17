### Agile Issue
#### Why JIRA
- 用 ```事务``` 管理任务
- 用 ```工作流``` 串联 ```需求```-```实施```-```评审```
- 用 ```冲刺看板``` 控制进度
- 用 ```Issue Link``` / ```WebHook``` / ```Rest API``` 进行协同开发(Jenkins, Sonar, IDE, Confluence, Gitlab等)
- 通过 ```图表``` 监控项目的各种数据

#### Issue
事务是敏捷协作的基本单位
##### Epic
Epic是最高级别的事务，用于描述大的功能模块、功能点
- Epic可以包含多个Story
- Epic可以跨项目

##### Story
Story是使用最频繁的事务类型，用于描述通常意义上的用户需求
- Story可以包含多个Task
- Story描述了需求发生的场景
- Story描述了需求的目标用户
- Story描述了需求中用户会怎样做
- Story通常用自然语言描述，不应包含技术细节

##### Task
Task是工作的基本单元，用于描述开发者实际的开发任务
- Task的粒度应定义到不可再分割的开发功能点
- Task作为代码提交时所使用的 ```Issue Link``` 来关联事务与代码
- Task可以用来追踪开发进度

##### Bug
Bug是特殊的Task，用于描述异常修复事务

#### Issue Link
通过关联事务，其他应用可以与JIRA或其他事务管理工具同步事务的开发状态
- SCM中添加 ```Issue Link``` 可以将代码变更与事务关联，便于事务管理者查看实施进展
- Jenkins可以在构建结束后在更新事务关联项目的构建状态
- Sonar可以在代码扫描后更新事务关联代码的质量状态
- IDE中关联JIRA服务器可以让开发者直接在开发环境获取自己的开发任务
- Confluence中可以创建JIRA事务，或者在JIRA中引用Confluence的文档

#### Issue Workflow
通过工作流组织事务可以将一个事务不同阶段的参与者关联起来
![merge request](../../pics/workflow_03.png)

##### Status
- ```OPEN``` / 任务建立后第一个状态
- ```TO DO``` / 任务被分配实施人员后进入待办队列
- ```IN PROGRESS``` / 任务在实施中
- ```IN REVIEW``` / 任务在评审中
- ```RESOLVED``` / 任务被解决 / 完成 / 关闭
- ```REOPENED``` / 任务重新开启

##### Transition
- ```Create``` / 创建任务
- ```Assign``` / 分配实施人员
- ```Start Process``` / 开始实施
- ```Finish``` / 结束实施
- ```Accept``` / 通过评审
- ```Close``` / 关闭事务
- ```Reopen``` / 重新开启事务

##### Resolution
- ```Duplicate``` / 与现有事务重复
- ```Cannot Reproduce``` / 无法复现
- ```Resolved``` / 已解决
- ```Won't Do``` / 不会解决
