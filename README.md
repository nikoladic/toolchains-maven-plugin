Toolchains Maven Plugin
=========================

Extend maven-toolchains-plugin to add JDK auto download and toolchains.xml management.

# Features

* JDK auto download by Foojay API support, and install directory is `~/.m2/jdks`
* Add new toolchain into toolchains.xml dynamically
* JBang integration: add/auto-install JDK to toolchains.xml from JBang if jbang detected

# Requirements

* Maven 3.5+
* JDK 1.7+

# How to use?

Add following plugin configuration to your pom.xml:

```xml

<build>
    <plugins>
        <plugin>
            <groupId>org.mvnsearch</groupId>
            <artifactId>toolchains-maven-plugin</artifactId>
            <version>4.3.0</version>
            <executions>
                <execution>
                    <goals>
                        <goal>toolchain</goal>
                    </goals>
                </execution>
            </executions>
            <configuration>
                <toolchains>
                    <jdk>
                        <version>17</version>
                    </jdk>
                </toolchains>
            </configuration>
        </plugin>
    </plugins>
</build>
```

And you can try it quickly:

```
$ git clone https://github.com/linux-china/java17-demo.git
$ cd java17-demo
$ mvn compile
```    

# GraalVM support

* vendor should be `graalvm_ce17` or `graalvm_ce11`
* version is GraalVM version(not Java version), such as `22.0.0.2` or `21.3.0`
* GraalVM native-image component will be installed automatically

```xml

<plugin>
    <groupId>org.mvnsearch</groupId>
    <artifactId>toolchains-maven-plugin</artifactId>
    <version>4.2.0</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>22.2</version>
                <vendor>graalvm_ce17</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

# How to skip toolchains maven plugin on CI/CD platform?

```
$ mvn -Dtoolchain.skip -DskipTests package
```

# References

* Apache Maven Toolchains Plugin: https://maven.apache.org/plugins/maven-toolchains-plugin/
* foojay DiscoAPI: https://api.foojay.io/swagger-ui/
* Gradle Toolchains for JVM：https://docs.gradle.org/current/userguide/toolchains.html 