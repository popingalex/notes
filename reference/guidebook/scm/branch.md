### Branch / Tag
#### Tagging
Tag用于为某个版本添加一个特殊的标记，通常用于标记版本号 ```git tag v1.0.0-SNAPSHOT -m "tagging a version"```

#### Branching
Branch给予开发者独立开发各自的特性而不互相影响的能力

分支上的开发完毕后，通过Merge即可将特性融合在一起

#### Git Flow
Git Flow是版本分支管理的一种实践

![git-flow](../pics/git-flow.png)

##### ```Master``` 主分支
- 用于标记```Tag```
- 仅提交测试通过的代码
- 保持随时可发布

##### ```Hotfix``` 热修复(可选)
- 用于修复交付版本上的异常

##### ```Release``` 发布分支
- 因发布计划确定而建立
- 拒绝新特性的 ```Merge```
- 仅接受一场修复的 ```Merge```
- 测试通过后 ```Merge``` 到 ```Master```

##### ```Bugfix``` 异常修复(可选)
- 用于修复发布分支上的异常

##### ```Develop``` 开发分支
- 集成来自各特性分支的新特性
- 进行持续集成与集成测试
- 尽早发现问题尽早修复

##### ```Feature``` 特性分支
- 各特性开发组(开发者)在特性分支上进行开发
- 开发后 ```Merge``` 到 ```Develop``` 分支
- 在 ```Merge``` 过程中进行评审

#### 开发规范
- 分支创建应基于事务，先有事务后有分支
- 先创建分支再进行开发，而不是开发后提交时再创建分支
- 分支被合并后不应继续使用，可以作为归档依据保留一段时间，但最终应删除
- 尽量保持远程分支与本地同步，名称统一，命名规范
- 杜绝 ```Master```，```Develop```，```Release``` 分支的直接提交，只通过 ```Merge``` 进行变更
- 按规范书写提交日志，参考[代码提交规范](commit.md)
