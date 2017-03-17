# Apache Maven
Java软件项目组织管理工具规范

## settings.xml
开发环境配置



## pom.xml
项目管理配置

```Project Object Model | 项目对象模型``` 用来维护Maven项目结构

### Basic
基本配置

#### Maven Coordinates
Maven坐标作于项目的唯一标识可以用来定位

> groupId:artifactId:packaging:classfier:version

> 组织:项目:打包方式:类型(可选):版本

```xml
<project ...>
    <groupId>com.gsafety.sample</groupId><!-- 缺省继承parent的groupId -->
    <artifactId>sample-parent</artifactId>
    <version>0.0.1-Snapshot</version><!-- 缺省继承parent的version -->
    <packaging>pom</packaging><!-- 缺省为jar -->
</project>
```

#### Dependencies
依赖关系用于维护在项目中使用的其他项目

> 所有依赖的管理应尽量维护在项目的顶级parent中，以防止版本冲突与管理混乱

parent中的依赖管理块，统一管理依赖版本
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

project中的依赖块，只通过坐标来指定依赖
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

#### Inheritance
继承关系用于继承父模块的部分配置

#### Aggregation
聚合关系用于进行批量构建配置，并自动解析其中的构建顺序

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
```groovy
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

## manual
使用手册


### javadoc

### deploy


### version change
变更当前项目及其组件(module)项目中目标项目的版本号，支持*匹配

> 命令：```mvn versions:set [-D参数=值]*N```
- ```newVersion```
	想要变更至的新版本号

- ```oldVersion```
	想要进行变更的旧版本号

- ```groupId```
	过滤非指定groupId的项目

- ```artifactId```
	过滤非指定artifactId的项目