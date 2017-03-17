### Maven Struct
#### 基本用例
```tree
super-parent
+- component-core-parent
|  +- project-core-ui
|  \- project-core-service
|
+- component-business-parent
|  +- project-business-user
|  |  +- project-business-user-web
|  |  \- project-business-user-service
|  \- project-main
|
\- component-tools
   \- project-utils
```

##### ```super-parent```
- 维护整个项目的聚合关系( ```Modules``` )
- **管理** 整个项目的依赖版本( ```dependencyManagement``` )
- 配置项目级别的依赖( ```Dependency``` )
- 配置项目级别的构建( ```Build``` )
- 配置项目级别的( ```Distribution``` )

##### ```component-*-parent```
- 维护大模块的聚合关系( ```Modules``` )
- 维护大模块级别的依赖( ```Dependency``` )
- 维护大模块级别的构建( ```Build``` )

##### ```project-business-user```
- 维护小模块的聚合关系( ```Modules``` )
- 维护小模块级别的依赖( ```Dependency``` )
- 维护小模块级别的构建(```Build```)

##### ```project-business-user-*```
- 维护最小级别的依赖( ```Dependency``` )
- 维护最小级别的构建(```Build```)
- 实现功能

#### 聚合关系
聚合关系用于帮助Maven解析项目结构：
- 分析整个聚合体系内的依赖关系
- 构建整个聚合体系内的项目，自动解析构建顺序
- 维护整个聚合体系内的版本

使用时在 ```<modules/>``` 结点中添加想要聚合的 ```<module/>```

#### 继承关系
模块可以从其```Parent```中继承：
- ```<property/>``` 属性
- ```<dependency/>``` 依赖
- ```<build/>``` 编译配置
- 等...

#### 依赖管理
为便于统一管理，依赖版本应通过 ```<dependencyManagement/>``` 在超父中统一管理，在使用的模块中实现依赖 ```<dependency/>```

> 可以在一个独立的```packaging```为```pom```的模块中配置多个依赖项，依赖该模块即可依赖这些依赖项，此时需配置```<type>pom</type>```

#### 环境差异
实际使用过程中项目可能需要打包发布到多个不同的环境，环境配置的差异应通过配置```<profile/>```实现，同时对nexus的依赖也可以在此配置，例：
```XML
<profiles>
  <profile>
    <id>office-net</id>
    <activation>
      <activeByDefault>true</activeByDefault>
    </activation>
    <distributionManagement/>
    <repositories>
      <repository/>
    <pluginRepositories>
      <pluginRepository/>
    </pluginRepositories>
  </profile>
  <profile>
    <id>intra-net</id>
    <distributionManagement>
      <snapshotRepository/>
    </distributionManagement>
    <repositories>
      <repository/>
    </repositories>
  </profile>
</profiles>
```

#### 版本管理
聚合关系中的项目可以在各聚合模块对其子模块进行统一的版本变更，参考[版本号规范](version.md)，使用命令为 ```mvn versions:set [-D参数=值]```，支持*匹配， 参数：
- ```newVersion```

  新版本号
- ```oldVersion```

  过滤当前version，默认为${project.version}
- ```groupId```

  过滤group，默认为${project.groupId}
- ```artifactId```

  过滤artifact，默认为${project.artifactId}
