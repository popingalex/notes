### SonarQube
#### server
基本配置 ```sonar.properties```
```properties
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar123

sonar.jdbc.url=jdbc:mysql://localhost:3306/sonardb****** useSSL=true

sonar.web.javaOpts=-server
sonar.web.context=/sonarqube
```
#### Scanner
基本配置 ```sonar-scanner.properties```
```properties
sonar.host.url=***
sonar.jdbc.url=jdbc:mysql***
```
