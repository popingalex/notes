# Apache Maven

## 配置开发环境

```xml
<settings>
    <servers>
        <!-- 身份认证信息，用于发布组件至指定仓库 -->
        <server>
            <id>snapshot</id>
            <username>你的账号</username>
            <password>你的密码</password>
        </server>
        <server>
            <id>release</id>
            <username>你的账号</username>
            <password>你的密码</password>
        </server>
        <server>
            <id>archive</id>
            <username>QA的账号</username>
            <password>QA的密码</password>
        </server>
    </servers>
    <mirrors>
        <!-- 填写所使用的本地公共仓库地址 -->
        <mirror>
            <id>gsafety</id>
            <mirrorOf>central</mirrorOf>
            <url>http://devops.gsafety.com/nexus/repository/mvn_public/
            </url>
        </mirror>
    </mirrors>
    <profiles>
        <profile>
            <id>default</id>
            <repositories>
                <repository>
                    <id>central</id>
                    <url>http://central</url>
                </repository>
            </repositories>
        </profile>
    </profiles>

    <activeProfiles>
        <activeProfile>default</activeProfile>
    </activeProfiles>
</settings>
```

## 配置项目结构

### 父模块

```xml
<project>
    <groupId>com.gsafety.项目组</groupId>
    <artifactId>某个项目</artifactId>
    <version>版本</version>
    <packaging>pom</packaging>
    <!-- 集中管理整个项目中所有依赖的版本 -->
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>依赖的组件的组</groupId>
                <artifactId>依赖的组件</artifactId>
                <version>依赖的组件的版本</version>
            </dependency>
            <!-- 还有一堆你需要依赖的东西 -->
        </dependencies>
    </dependencyManagement>

    <dependencies>
        <!-- 可以在这里写一些几乎所有组件都会依赖的组件，例如JUnit -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.11</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <profiles>
        <profile>
            <id>develop</id>
            <activation>
                <activeByDefault>true</activeByDefault>
            </activation>
            <!-- 组件发布目标地址 -->
            <distributionManagement>
                <snapshotRepository>
                    <id>snapshot</id>
                    <url>http://devops.gsafety.com/nexus/repository/mvn_CFW_snapshot/</url>
                </snapshotRepository>
                <repository>
                    <id>release</id>
                    <url>http://devops.gsafety.com/nexus/repository/mvn_CFW_release/</url>
                </repository>
            </distributionManagement>
        </profile>
        <profile>
            <id>qa</id>
            <!-- 组件发布目标地址 -->
            <distributionManagement>
                <repository>
                    <id>archive</id>
                    <url>http://devops.gsafety.com/nexus/repository/mvn_CFW_archive/</url>
                </repository>
            </distributionManagement>
        </profile>
    </profiles>
    <!-- 子组件构建列表 -->
    <modules>
        <module>某个项目-core</module>
        <module>某个项目-components</module>
        <module>某个项目-tools</module>
    </modules>
</project>
```

### 组件父模块

```xml
<project>
    <parent>
        <groupId>com.gsafety.项目组</groupId>
        <artifactId>某个项目</artifactId>
        <version>版本</version>
        <!-- <relativePath>与父模块相对路径</relativePath> -->
    </parent>
    <artifactId>组件父</artifactId>
    <packaging>pom</packaging>
    <!-- 核心依赖组件 -->
    <dependencies>
        <dependency>
            <!-- 如果你的项目基于云平台, 你可能会需要依赖云平台核心组件 -->
            <groupId>com.gsafety.cloudframework</groupId>
            <artifactId>cloud-core</artifactId>
            <type>pom</type>
        </dependency>
    </dependencies>
    <!-- 子组件构建列表 -->
    <modules>
        <module>某个组件</module>
        <module>某个组件</module>
    </modules>
</project>
```

### 组件模块

```xml
<project>
    <parent>
        <groupId>com.gsafety.项目组</groupId>
        <artifactId>组件parent</artifactId>
        <version>版本</version>
        <!-- <relativePath>与组件父模块相对路径</relativePath> -->
    </parent>
    <artifactId>组件</artifactId>

    <!-- 配置依赖 -->
    <dependencies>
        <dependency>
            <!-- 依赖版本在父中配置，不要写在这里 -->
            <groupId>某个依赖组</groupId>
            <artifactId>某个依赖</artifactId>
        </dependency>
    </dependencies>
</project>
```
