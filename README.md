# springboot-swagger-Incompatible

## springboot 2.1.7
## swagger 2.9.2


```
Exception in thread "main" java.lang.IllegalArgumentException: Cannot instantiate interface org.springframework.context.ApplicationListener : org.springframework.boot.context.logging.ClasspathLoggingApplicationListener
	at org.springframework.boot.SpringApplication.createSpringFactoriesInstances(SpringApplication.java:438)
	at org.springframework.boot.SpringApplication.getSpringFactoriesInstances(SpringApplication.java:420)
	at org.springframework.boot.SpringApplication.getSpringFactoriesInstances(SpringApplication.java:413)
	at org.springframework.boot.SpringApplication.<init>(SpringApplication.java:270)
	at org.springframework.boot.SpringApplication.<init>(SpringApplication.java:250)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1214)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1203)
	at com.boe.sd.App.main(App.java:13)
Caused by: java.lang.NoClassDefFoundError: org/springframework/context/event/GenericApplicationListener
	at java.base/java.lang.ClassLoader.defineClass1(Native Method)
	at java.base/java.lang.ClassLoader.defineClass(ClassLoader.java:1016)
	at java.base/java.security.SecureClassLoader.defineClass(SecureClassLoader.java:151)
	at java.base/jdk.internal.loader.BuiltinClassLoader.defineClass(BuiltinClassLoader.java:802)
	at java.base/jdk.internal.loader.BuiltinClassLoader.findClassOnClassPathOrNull(BuiltinClassLoader.java:700)
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClassOrNull(BuiltinClassLoader.java:623)
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:581)
	at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:178)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:521)
	at java.base/java.lang.Class.forName0(Native Method)
	at java.base/java.lang.Class.forName(Class.java:415)
	at org.springframework.util.ClassUtils.forName(ClassUtils.java:275)
	at org.springframework.boot.SpringApplication.createSpringFactoriesInstances(SpringApplication.java:431)
	... 7 more
Caused by: java.lang.ClassNotFoundException: org.springframework.context.event.GenericApplicationListener
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:583)
	at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:178)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:521)
	... 20 more
```

发现少了GenericApplicationListener这个类
经查 pringfox-swagger2依赖的spring-context太老了 4.0.8 
```
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger2</artifactId>
            <version>2.9.2</version>
            <exclusions>
                <exclusion>
                    <groupId>org.springframework</groupId>
                    <artifactId>spring-context</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
                <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger-ui</artifactId>
            <version>2.9.2</version>
        </dependency>
```
