# Sonatype Nexus
组件仓库规范

## 名词解释
- ```Blob``` 存储空间
- ```Repository``` 组件仓库

## 命名规范

### Blob

| Blob | Content |
| - | - | - |
| group       | 仓库分组信息 |
| proxy       | 代理组件 |
| thirdparty  | 第三方组件 |
| snapshot    | 快照组件 |
| release     | 封版组件 |
| archive     | 发布组件 |

### Repository

格式：```组件类型_项目/产品_更新策略```

示例：```mvn_CFW_snapshot```
- mvn maven(java)组件
- Cloud Framework 云平台产品
- snapshot 快照级别更新

## 组织结构

```
    配置于settings.xml，作为所有maven仓库入口
+-- mvn_public
|   |
|   |   代理中央仓库mvnrepository.com
|   +-- mvn_proxy_central
|   |
|   |   本地上传的第三方组件
|   +-- mvn_thirdparty
|   |
|   |   快照仓库, 开发组维护, 配置在项目pom.xml中
|   +-- mvn_产品名称_snapshot
|   |
|   |   预发布仓库, 开发组维护, 供QA进行测试与评审使用, 配置在项目pom.xml中
|   +-- mvn_产品名称_release
|   |
|   |   发布/归档仓库, QA组维护, 对外发布
|   \-- mvn_产品名称_archive
|
|   npm仓库入口
\-- npm_public
    |
    |   代理npmjs仓库
    +-- npm_proxy_npmjs
    |
    |   npm组件仓库
    \-- npm_产品名称_release
```

## 权限控制

| | snapshot | release | archive |
| - | - | - | - |
| 匿名用户 | 读 | 读 | 读 |
| 本组开发 | 写 | 写 | 读 |
| QA组  | 读 | 读 | 写 |

- 所有用户拥有浏览及读取权限
    - nx-repository-view-*-*-read
    - nx-repository-view-*-*-browse
- 各项目/产品组开发者拥有其对应```snapshot```仓库发布权限
    - nx-repository-view-maven2-mvn_产品名称_snapshot-add
- 各项目/产品组开发者拥有其对应```release```仓库编辑权限
    - nx-repository-view-maven2-mvn_产品名称_release-add
    - nx-repository-view-maven2-mvn_产品名称_release-edit
    - nx-repository-view-maven2-mvn_产品名称_release-delete
- QA组拥有其管理范围内的项目/产品```archive```仓库编辑权限
    - nx-repository-view-maven2-mvn_产品名称_archive-add
    - nx-repository-view-maven2-mvn_产品名称_archive-edit
    - nx-repository-view-maven2-mvn_产品名称_archive-delete
