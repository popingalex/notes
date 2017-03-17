# Apache Maven

## settings.xml
配置开发环境

```xml
<settings>
	<servers>
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
        <!-- <server>
            <id>archive</id>
            <username>QA的账号</username>
            <password>QA的密码</password>
        </server> -->
	</servers>
	<mirrors>
	    <mirror>
	        <id>gsafety</id>
	        <mirrorOf>central</mirrorOf>
	        <url>http://devops.gsafety.com/nexus/repository/mvn_public/</url>
			<!-- 填写所使用的本地公共仓库地址 -->
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

## pom.xml
配置项目结构

### parent

```xml
<project>
	<groupId>com.gsafety.项目组</groupId>
	<artifactId>某个项目</artifactId>
	<version>版本</version>
	<packaging>pom</packaging>

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
			<distributionManagement>
				<repository>
					<id>archive</id>
					<url>http://devops.gsafety.com/nexus/repository/mvn_CFW_archive/</url>
				</repository>
			</distributionManagement>
		</profile>
	</profiles>
    <modules>
        <module>某个项目-core</module>
        <module>某个项目-components</module>
        <module>某个项目-tools</module>
    </modules>
</project>
```

### child

```xml
```
