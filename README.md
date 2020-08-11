# 依赖包shade

1. `mvn clean package` [shade打包](#mvn-clean-package)
1. `jar tvf target/maven-shade-1.0.jar` [检查包内容](#检查包内容)
1. `mvn dependency:tree` [检查依赖树](#检查依赖树)

## mvn clean package

```bash
$ mvn clean package                                                    [四  5/ 7 14:57:07 2020]
[INFO] Scanning for projects...
[INFO] 
[INFO] -----------------< com.github.bingoohuang:maven-shade >-----------------
[INFO] Building maven-shade 1.0
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ maven-shade ---
[INFO] Deleting ~/github/java-gotcha/maven-shade/target
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ maven-shade ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Copying 1 resource
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ maven-shade ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to ~/github/java-gotcha/maven-shade/target/classes
[INFO] 
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ maven-shade ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Copying 0 resource
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ maven-shade ---
[INFO] Nothing to compile - all classes are up to date
[INFO] 
[INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ maven-shade ---
[INFO] 
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ maven-shade ---
[INFO] Building jar: ~/github/java-gotcha/maven-shade/target/maven-shade-1.0.jar
[INFO] 
[INFO] --- maven-shade-plugin:3.2.3:shade (default) @ maven-shade ---
[INFO] Including ch.qos.logback:logback-classic:jar:1.2.3 in the shaded jar.
[INFO] Including ch.qos.logback:logback-core:jar:1.2.3 in the shaded jar.
[INFO] Excluding org.slf4j:slf4j-api:jar:1.7.25 from the shaded jar.
[INFO] Replacing original artifact with shaded artifact.
[INFO] Replacing ~/github/java-gotcha/maven-shade/target/maven-shade-1.0.jar with ~/github/java-gotcha/maven-shade/target/maven-shade-1.0-shaded.jar
[INFO] Dependency-reduced POM written at: ~/github/java-gotcha/maven-shade/dependency-reduced-pom.xml
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.008 s
[INFO] Finished at: 2020-05-07T14:57:18+08:00
[INFO] ------------------------------------------------------------------------
```

## 检查包内容

```bash
$ jar tvf target/maven-shade-1.0.jar                                      [四  5/ 7 14:57:18 2020]
   384 Thu May 07 14:57:16 CST 2020 logback.xml
     0 Thu May 07 14:57:18 CST 2020 com/
     0 Thu May 07 14:57:18 CST 2020 com/github/
     0 Thu May 07 14:57:18 CST 2020 com/github/bingoohuang/
     0 Thu May 07 14:57:18 CST 2020 com/github/bingoohuang/mavenshade/
   626 Thu May 07 14:57:18 CST 2020 com/github/bingoohuang/mavenshade/Demo.class
     0 Thu May 07 14:55:32 CST 2020 META-INF/
     0 Thu May 07 14:55:32 CST 2020 META-INF/maven/
     0 Thu May 07 14:55:32 CST 2020 META-INF/maven/com.github.bingoohuang/
     0 Thu May 07 14:55:32 CST 2020 META-INF/maven/com.github.bingoohuang/maven-shade/
  3161 Thu May 07 14:55:32 CST 2020 META-INF/maven/com.github.bingoohuang/maven-shade/pom.xml
   116 Thu May 07 14:57:18 CST 2020 META-INF/maven/com.github.bingoohuang/maven-shade/pom.properties
     0 Fri Mar 31 20:20:12 CST 2017 shaded/
     0 Fri Mar 31 20:20:12 CST 2017 shaded/ch/
     0 Fri Mar 31 20:20:12 CST 2017 shaded/ch/qos/
     0 Fri Mar 31 20:20:12 CST 2017 shaded/ch/qos/logback/
     0 Fri Mar 31 20:20:12 CST 2017 shaded/ch/qos/logback/classic/
  1168 Fri Mar 31 20:20:12 CST 2017 shaded/ch/qos/logback/classic/boolex/OnErrorEvaluator.class
  1551 Fri Mar 31 20:20:12 CST 2017 shaded/ch/qos/logback/classic/ViewStatusMessagesServlet.class
     0 Fri Mar 31 20:20:12 CST 2017 META-INF/services/
    65 Fri Mar 31 20:20:12 CST 2017 META-INF/services/javax.servlet.ServletContainerInitializer
     0 Fri Mar 31 20:20:12 CST 2017 org/
     0 Fri Mar 31 20:20:12 CST 2017 org/slf4j/
     0 Fri Mar 31 20:20:12 CST 2017 org/slf4j/impl/
  3394 Fri Mar 31 20:20:12 CST 2017 org/slf4j/impl/StaticLoggerBinder.class
   838 Fri Mar 31 20:20:12 CST 2017 org/slf4j/impl/StaticMarkerBinder.class
   717 Fri Mar 31 20:20:12 CST 2017 org/slf4j/impl/StaticMDCBinder.class
     0 Fri Mar 31 20:15:22 CST 2017 META-INF/maven/ch.qos.logback/
     0 Fri Mar 31 20:15:22 CST 2017 META-INF/maven/ch.qos.logback/logback-classic/
 13081 Fri Mar 31 20:15:22 CST 2017 META-INF/maven/ch.qos.logback/logback-classic/pom.xml
   126 Fri Mar 31 20:20:32 CST 2017 META-INF/maven/ch.qos.logback/logback-classic/pom.properties
     0 Fri Mar 31 20:19:58 CST 2017 shaded/ch/qos/logback/core/
   697 Fri Mar 31 20:19:58 CST 2017 shaded/ch/qos/logback/core/Appender.class
  4040 Fri Mar 31 20:19:58 CST 2017 shaded/ch/qos/logback/core/AppenderBase.class
  1986 Fri Mar 31 20:19:58 CST 2017 shaded/ch/qos/logback/core/AsyncAppenderBase$Worker.class
     0 Fri Mar 31 20:15:22 CST 2017 META-INF/maven/ch.qos.logback/logback-core/
  4196 Fri Mar 31 20:15:22 CST 2017 META-INF/maven/ch.qos.logback/logback-core/pom.xml
   123 Fri Mar 31 20:20:10 CST 2017 META-INF/maven/ch.qos.logback/logback-core/pom.properties
```


## 检查依赖树

```bash
$ mvn dependency:tree                                           [Thu May  7 15:16:35 2020]
[INFO] Scanning for projects...
[INFO] 
[INFO] -----------------< com.github.bingoohuang:maven-shade >-----------------
[INFO] Building maven-shade 1.0
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-dependency-plugin:2.8:tree (default-cli) @ maven-shade ---
[INFO] com.github.bingoohuang:maven-shade:jar:1.0
[INFO] +- org.projectlombok:lombok:jar:1.18.10:provided
[INFO] +- org.slf4j:slf4j-api:jar:1.7.25:compile
[INFO] \- ch.qos.logback:logback-classic:jar:1.2.3:compile
[INFO]    \- ch.qos.logback:logback-core:jar:1.2.3:compile
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.797 s
[INFO] Finished at: 2020-05-07T15:16:38+08:00
[INFO] ------------------------------------------------------------------------
```

```bash
$ cd ../maven-shade-demo                                        [Thu May  7 15:16:38 2020]
$ mvn dependency:tree                                           [Thu May  7 15:16:47 2020]
[INFO] Scanning for projects...
[INFO] 
[INFO] --------------< com.github.bingoohuang:maven-shade-demo >---------------
[INFO] Building maven-shade-demo 1.0
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-dependency-plugin:2.8:tree (default-cli) @ maven-shade-demo ---
[INFO] com.github.bingoohuang:maven-shade-demo:jar:1.0
[INFO] \- com.github.bingoohuang:maven-shade:jar:1.0:compile
[INFO]    \- org.slf4j:slf4j-api:jar:1.7.25:compile
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.773 s
[INFO] Finished at: 2020-05-07T15:16:51+08:00
[INFO] ------------------------------------------------------------------------
```