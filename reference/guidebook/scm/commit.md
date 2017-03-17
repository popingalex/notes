### Commit Message
#### Why
- 为 ```Review``` 节约成本
- 为 ```Release Note```，```Change Log``` 提供内容
- 便于分享当前工作进度

#### How
```
git commit -m "add a git commit message"
git commit --message="add a git commit message"
```

#### Rule
- 单行

  ```
  Summary (50 chars or less)
  ```
  在提交粒度小，提交频繁时推荐使用单行提交说明。多用于每个文件上的变更比较独立的场合
- 多行

  ```
  Summary (50 chars or less)
  # 空行
  Detail (wrapped at 72 chars)
  ```
  在提交粒度较大，提交不太频繁时推荐使用多行提交，一次性说明提交细节。多用于变更功能比较零散，文件上的变更比较零散，无法独立提交的场合

#### Struct
##### Summary
提交的基本描述会被收录在```Change Log```中(可选)：
```
[<Issue Link / 事务链接>] <Operation / 操作类型> [<Scope / 作用域>] <Subject / 主题>
```

- ```Issue Link``` 事务链接(可选)，用于与JIRA或其他事务管理工具关联，格式有可能基于后台链接方式修改

  ```
  Resolves Issue-1 # 解决事务
  Closes Issue-2   # 关闭事务
  Fixes Issue-3    # 修复事务
  Issue-4          # 关联事务
  ```

- ```Operation``` 描述本次提交的操作类型

  ```
  Add      添加
  Fix      修复
  Update   更新
  Remove   移除
  Refactor 重构
  etc.     等
  ```

- ```Scope``` 描述提交影响作用范围

  ```
  ui         用户界面
  xxx module xxx模块
  etc.       等
  ```

- ```Subject``` 简述本次提交的内容

##### Detail
提交的详细描述，主要向关心本次提交具体内容的人展示：
- ```why``` 为什么进行本次提交
- ```how``` 本次提交如何解决问题 / 实现功能

以及说明本次提交是否修改了原有接口，即破坏了以往公共接口的 ```兼容性```

#### Sample
```
Fixes CFW-318 cloud-user-web i18n properties problem

i18n文件由于pom结构修改变更了build过程中资源加载部分对properties文件的处理方式

通过在parent-runenv中修正build配置进行修复
```
或
```
CFW-317 添加 某某模块 某某功能

bla bla
```

如示例所示：
- CFW-318事务可以关闭，状态为Fixes
- 事务类型为Fix，修复问题
- 作用模块为cloud-user-web
- 事务为i18n properties problem
- 问题定位在pom配置
- 修复方式为修改配置
