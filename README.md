### SSL issue after June 24 jfrog change 

Step to reproduce:

- Set `JAVA_HOME` to JDK7
- Run
  - Maven user: `mvn package`
  - Gradle user: `./gradlew`
  
  
  ```
  $ mvn package
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building my-app 1.0-SNAPSHOT
[INFO] ------------------------------------------------------------------------
Downloading: https://plugins.gradle.org/m2/org/gradle/hello-world/org.gradle.hello-world.gradle.plugin/0.2/org.gradle.hello-world.gradle.plugin-0.2.jar
Downloading: https://repo.maven.apache.org/maven2/org/gradle/hello-world/org.gradle.hello-world.gradle.plugin/0.2/org.gradle.hello-world.gradle.plugin-0.2.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 4.008 s
[INFO] Finished at: 2018-06-25T20:29:20+08:00
[INFO] Final Memory: 13M/245M
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal on project my-app: Could not resolve dependencies for project com.mycompany.app:my-app:jar:1.0-SNAPSHOT: Could not transfer artifact org.gradle.hello-world:org.gradle.hello-world.gradle.plugin:jar:0.2 from/to gradle (https://plugins.gradle.org/m2): Remote host closed connection during handshake: SSL peer shut down incorrectly -> [Help 1]
[ERROR]
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/DependencyResolutionException
  ```


```
FAILURE: Build failed with an exception.

* Where:
Build file '/Users/zhb/Projects/tmp/maven-samples/jfrog-ssl-issue/build.gradle' line: 2

* What went wrong:
Error resolving plugin [id: 'org.gradle.hello-world', version: '0.2']
> Could not resolve all dependencies for configuration 'detachedConfiguration1'.
   > Could not determine artifacts for org.gradle.hello-world:org.gradle.hello-world.gradle.plugin:0.2
      > Could not get resource 'https://plugins.gradle.org/m2/org/gradle/hello-world/org.gradle.hello-world.gradle.plugin/0.2/org.gradle.hello-world.gradle.plugin-0.2.jar'.
         > Could not HEAD 'https://plugins.gradle.org/m2/org/gradle/hello-world/org.gradle.hello-world.gradle.plugin/0.2/org.gradle.hello-world.gradle.plugin-0.2.jar'.
            > Remote host closed connection during handshake

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

Deprecated Gradle features were used in this build, making it incompatible with Gradle 5.0.
See https://docs.gradle.org/4.7/userguide/command_line_interface.html#sec:command_line_warnings

BUILD FAILED in 8s
```
