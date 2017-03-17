### Review Based on Gitlab Branching
#### 创建分支 -> 功能实施
![work on branch](../../pics/branch_04_cut.png)
- 在 ```Repository / Branches``` 中找到 ```New Branch```
- 创建以实际开发目标命名的 ```Feature``` / ```Bugfix``` 分支
- 开发者本地检出分支，完成功能实施并提交
- 提交 ```Merge Request```

#### 提请合并
![merge request](../../pics/branch_05.png)
- 在 ```Title``` 中编写提交标题，参考[提交规范](commit.md)
- 在 ```Description``` 中编写提交内容，参考[提交规范](commit.md)
- 同时在 ```Description``` 底部或评论区通过 ```@somebody``` 添加额外的评审人

#### 代码评审
![review changes](../../pics/branch_07.png)
- 评审人可以在Gitlab页面上查看代码差异进行评审
- 评审人可以在本地通过IDE插件或其他比对工具进行评审
- 多数情况下 ```Merge``` 无法在线自动完成，需要手动处理冲突
- 评审人可以通过 ```:thumbsup``` 或添加评论等方式发表意见，参与评审

#### 评审结果
![review problem](../../pics/branch_08.png)
- 申请代码合并的开发者应对评审人提出的问题予以解答
- 主评审人( ```Assignee``` )应当在所有发现的问题被标记解决后 ```Accept Merge Request```，或在本地完成代码合并

#### 分支保护
![branch protection](../../pics/branch_09.png)
为了避免开发者由于误操作向只允许合并的分支进行代码推送，Gitlab提供分支保护机制限制部分分支的提交 / 合并权限
