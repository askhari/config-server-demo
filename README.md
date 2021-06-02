# Config Server Demo

This repository allows you to build an springboot application serving a Config Server.

# Requirements

* Java 8
* Maven
* Some modifications in the _application.properties_

# Important notes

Please note the following:

* Config server tries to retrieve configurations from _git_ repositories. Therefore, it's compulsory that the target folder where config server is pulling configurations should be a _git_ repository.
* The previous statement is not always true, but mostly it works like that.
* **CHANGE** the version in the _pom.xml_ to build a final version and not a snapshot when building a config server for production environments.

# Build

Modify the _application.properties_ to match the folder where config server should retrieve the configuration.


```
$ mvn clean package
```

This will leave a _jar_file in the _target_ folder.

# Running config server

Note that you may use your own _application.properties_. This file could be located in the same folder as the _config-server jar_ file and springboot will load it automatically.

```
ζ ls -1
application.properties
configserver-1.0-SNAPSHOT.jar

ζ java -jar configserver-1.0-SNAPSHOT.jar

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v2.4.6)

2021-06-02 20:17:03.710  INFO 29013 --- [           main] c.a.c.c.ConfigServerApplication          : Starting ConfigServerApplication v1.0-SNAPSHOT using Java 1.8.0_201 on Takuhi with PID 29013 (/tmp/cs/configserver-1.0-SNAPSHOT.jar started by lain in /tmp/cs)
2021-06-02 20:17:03.714  INFO 29013 --- [           main] c.a.c.c.ConfigServerApplication          : No active profile set, falling back to default profiles: default
2021-06-02 20:17:05.024  INFO 29013 --- [           main] o.s.cloud.context.scope.GenericScope     : BeanFactory id=95e0b43d-8f5a-35fe-8ed7-027eb540cf0e
2021-06-02 20:17:05.481  INFO 29013 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8880 (http)
2021-06-02 20:17:05.498  INFO 29013 --- [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2021-06-02 20:17:05.498  INFO 29013 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet engine: [Apache Tomcat/9.0.46]
2021-06-02 20:17:05.564  INFO 29013 --- [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2021-06-02 20:17:05.567  INFO 29013 --- [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 1749 ms
2021-06-02 20:17:06.521  INFO 29013 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8880 (http) with context path ''
2021-06-02 20:17:06.543  INFO 29013 --- [           main] c.a.c.c.ConfigServerApplication          : Started ConfigServerApplication in 3.434 seconds (JVM running for 4.027)
2021-06-02 20:17:13.094  INFO 29013 --- [nio-8880-exec-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring DispatcherServlet 'dispatcherServlet'
2021-06-02 20:17:13.095  INFO 29013 --- [nio-8880-exec-1] o.s.web.servlet.DispatcherServlet        : Initializing Servlet 'dispatcherServlet'
2021-06-02 20:17:13.096  INFO 29013 --- [nio-8880-exec-1] o.s.web.servlet.DispatcherServlet        : Completed initialization in 1 ms




2021-06-02 20:17:32.095  WARN 29013 --- [nio-8880-exec-2] .c.s.e.MultipleJGitEnvironmentRepository : Could not merge remote for master remote: null
2021-06-02 20:17:32.209  INFO 29013 --- [nio-8880-exec-2] o.s.c.c.s.e.NativeEnvironmentRepository  : Adding property source: Config resource 'file [/home/lain/coding/springboot/configs/robots.yml]' via location 'file:/home/lain/coding/springboot/configs/'
```
