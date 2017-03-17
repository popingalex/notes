# Apache Maven
Java软件项目组织管理工具规范

## settings.xml
开发环境配置[官方文档](http://maven.apache.org/settings.html)

> 组件发布地址配置在项目中，不在settings中配置

### servers
身份验证信息

```xml
<servers>
    <server>
        <id>repo_id</id>
        <username>username</username>
        <password>password</password>
        <!--<privateKey${user.home}/.ssh/id_dsa</privateKey>-->
    <server>
</servers>
```

旧身份验证策略：基于项目/工作组/仓库进行验证
- 更换项目/工作组/仓库时需要重新配置
- 成员离开项目/工作组时无法回收权限
- 参与多个项目后会遗留很多配置

新身份验证策略：基于用户进行验证
- 本地配置不需要变更
- 成员组织结构变更统一由用户组织结构服务器处理，不需要用户做额外配置

### mirrors
在不能直接访问中央仓库时，通过配置可访问镜像地址的方式来访问：

```xml
<!--
 | mirrorOf 可以设置为* / repo1,repo2 / central之类repo_id
 |-->
<mirrors>
    <mirror>
        <id>mirror_id</id>
        <mirrorOf>central</mirrorOf>
        <url>http://devops.gsafety.com/nexus/repository/mvn_public/</url>
        <!-- 根据我们nexus的配置，所用用户都可以通过该地址访问所需组件 -->
    </mirror>
</mirrors>
```

### profiles
配置档案

```xml
<profiles>
    <profile>
        <id>default</id>
        <repositories><!-- 要使用的仓库 -->
            <repository>
                <id>central</id><!-- 仓库id -->
                <url>http://central</url><!-- 占位 -->
            </repository>
        </repositories>
    </profile>
</profiles>

<activeProfiles>
    <activeProfile>default</activeProfile>
</activeProfiles>
```

---

## pom.xml
用来维护Maven项目结构的 ```Project Object Model | 项目对象模型```，可参考[官方文档](http://maven.apache.org/pom.html)

### Maven Coordinates
Maven坐标作于项目的唯一标识可以用来定位

> groupId:artifactId:packaging:classfier:version
>
> 组织 : 组件 : 打包方式 : 类型(可选) : 版本

```xml
<project ...>
    <groupId>com.gsafety.sample</groupId><!-- 缺省继承parent的groupId -->
    <artifactId>sample-parent</artifactId>
    <version>0.0.1-Snapshot</version><!-- 缺省继承parent的version -->
    <packaging>pom</packaging><!-- 缺省为jar -->
</project>
```

### Dependencies
依赖关系用于维护在项目中使用的其他项目。所有依赖的管理应尽量维护在项目的顶级parent中，以防止版本冲突与管理混乱

> parent中的依赖管理块，统一管理依赖版本

```xml
<dependencyManagement>
	<dependencies>
		<dependency>
			<groupId>com.gsafety.cloudframework</groupId>
			<artifactId>cloud-core</artifactId>
			<version>${project.version}</version>
		</dependency>
		<dependency>...</dependency>
	</dependencies>
</dependencyManagement>
```

> project中的依赖块，只通过坐标来表明实际使用的依赖项

```xml
<dependencies>
	<dependency>
		<groupId>com.gsafety.cloudframework</groupId>
		<artifactId>cloud-core</artifactId>
	</dependency>
	<dependency>...</dependency>
</dependencies>
```

> 额外属性

- 类型标签 ```classifier```
- 范围限定 ```scope```
- 文件路径 ```systemPath```
- 派出以来 ```exclusions```
- 可选标记 ```optional```

### Inheritance
继承关系用于继承父模块的部分配置

- 继承关系可以传递依赖与插件的配置
- 构建时可通过```relativePath``` 来定位本地的 ```parent``` 项目位置，否则会在仓库中搜索
- 继承可以通过 ```dependencyManagement``` 在 ```parent``` 中集中管理依赖版本

### Aggregation
聚合关系用于进行批量构建配置，并自动解析其中的构建顺序

### Properties
POM包含一些属性，用户也可以自己定义一些属性
- 环境变量 ```env.X```
- 项目属性 ```project.X```
- 配置属性 ```settings.X```
- 系统属性 ```java.X``` (来自```java.lang.System.getProperties()```)
- 自定属性 ```x``` (来自```<properties/>```)

### Distribution Management
发布管理，用于配置发布目标服务器地址，其验证信息在 ```settings``` 中 ```servers``` 中配置

```xml
<distributionManagement>
  <repository>
    <id>release-repository-id</id>
    <name>release-repository-name</name>
    <url>releases-repository-url</url>
  </repository>
  <snapshotRepository>
    <id>snapshots-repository-id</id>
    <name>snapshots-repository-name</name>
    <url>snapshots-repository-url</url>
  </snapshotRepository>
  <site>
    <id>cloudSite</id>
    <url>${maven-sites-repository-url}${maven-sites-parentpath}-${project.version}</url>
  </site>
</distributionManagement>
```

### Semantic Versioning
语义化版本

#### Format
基本格式 ```MAJOR.MINOR.PATCH``` ([参考](http://semver.org))
- ```MAJOR version``` 主版本号，API不兼容时变更
- ```MINOR version``` 次版本号，向下兼容的功能性变更
- ```PATCH version``` 修订版本，向下兼容的问题修复
  > ```Snapshot``` 等其他 ```qualifier``` 添加在后面，用-间隔

#### Changing
变更策略

##### 主版本号变更
- 基于API修改 / 项目架构变化 / 大规模重构变更
- 以开发计划为单位
- 变更时重置次版本号及修订版本号
- 间隔不超过一年

##### 次版本号变更
- 以开发季度 / 开发冲刺为单位
- 间隔不超过四个工作周(月)

##### 修订版本号
- 以特性添加 / 故障修复为单位
- 间隔不超过一个工作日

#### Compare
版本比较

- 根据 ```.``` 进行分割
- 数字值比较大小
- 字符串逐字符比较

举例说明：

```
# 数字比较
1.0.1 < 1.0.2
1.0.1 < 1.0.12
# 字符比较
1.0.a12 < 1.0.a2
1.0.alpha < 1.0.beta
1.0.1 > 1.0.1-SNAPSHOT
# S > R
1.0.1-RELEASE < 1.0.1-SNAPSHOT
```

#### Example
- 开发快照 ```1.0.0-SNAPSHOT```
- 提测版本 ```1.0.0-RELEASE```
- 内测版本 ```1.0.0-alpha-1```
- 公测版本 ```1.0.0-beta-2```
- 里程碑版 ```1.0.0-M3```
- 发布备选 ```1.0.0-RC4```
- 正式发布 ```1.0.0```

---

## manual
使用手册

### deploy-file
发布单个文件至仓库

> 命令: ```mvn deploy:deploy-file -DgroupId=%s -DartifactId=%s -Dversion=%s -Dfile=%s -Durl=%s -DrepositoryId=%s```

- 项目坐标信息 ```groupId``` , ```artifactId``` , ```version```
- 目标文件路径 ```file```
- 目标仓库地址 ```url```
- 身份认证信息 ```repositoryId```

### versions-set
变更当前项目及其组件(module)项目中目标项目的版本号，支持*匹配

> 命令: ```mvn versions:set [-D参数=值]*N```
- ```newVersion```
	想要变更至的新版本号

- ```oldVersion```
	想要进行变更的旧版本号

- ```groupId```
	过滤非指定groupId的项目

- ```artifactId```
	过滤非指定artifactId的项目
