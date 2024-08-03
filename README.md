# Java
Here’s a comprehensive list of Java CLI commands and techniques, including tools and configurations for effective Java development and management.

### **Java CLI Commands**

#### **1. Java Version Management**

- **Check Java version:**
  ```bash
  java -version
  ```

- **Check the Java compiler version:**
  ```bash
  javac -version
  ```

- **Update Java (using SDKMAN for version management):**
  ```bash
  sdk install java
  sdk list java # List available Java versions
  sdk use java <version> # Set a specific Java version
  ```

#### **2. Java Compilation and Execution**

- **Compile a Java program:**
  ```bash
  javac HelloWorld.java
  ```

- **Run a compiled Java program:**
  ```bash
  java HelloWorld
  ```

- **Compile multiple Java files:**
  ```bash
  javac *.java
  ```

- **Run a Java program with a specific classpath:**
  ```bash
  java -cp .:lib/* HelloWorld
  ```

- **Run a Java program with specific JVM options:**
  ```bash
  java -Xmx512m -Xms256m HelloWorld
  ```

- **Compile and run a single-file source-code program:**
  ```bash
  java HelloWorld.java
  ```

#### **3. Java Package Management**

- **Create a JAR file:**
  ```bash
  jar cvf HelloWorld.jar HelloWorld.class
  ```

- **Run a JAR file:**
  ```bash
  java -jar HelloWorld.jar
  ```

- **List contents of a JAR file:**
  ```bash
  jar tvf HelloWorld.jar
  ```

- **Extract contents of a JAR file:**
  ```bash
  jar xvf HelloWorld.jar
  ```

- **Update a JAR file:**
  ```bash
  jar uvf HelloWorld.jar newfile.class
  ```

#### **4. Java Environment Management**

- **Set environment variables for Java:**
  ```bash
  export JAVA_HOME=/path/to/java
  export PATH=$JAVA_HOME/bin:$PATH
  ```

- **Check the value of JAVA_HOME:**
  ```bash
  echo $JAVA_HOME
  ```

- **Configure environment variables in a script:**
  ```bash
  #!/bin/bash
  export JAVA_HOME=/path/to/java
  export PATH=$JAVA_HOME/bin:$PATH
  ```

#### **5. Java Build Tools**

- **Maven:**

  - **Create a new Maven project:**
    ```bash
    mvn archetype:generate -DgroupId=com.example -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
    ```

  - **Build a Maven project:**
    ```bash
    mvn clean install
    ```

  - **Run a Maven project:**
    ```bash
    mvn exec:java -Dexec.mainClass="com.example.App"
    ```

  - **Add a dependency to a Maven project:**
    ```xml
    <dependency>
      <groupId>org.example</groupId>
      <artifactId>example-dependency</artifactId>
      <version>1.0.0</version>
    </dependency>
    ```

  - **Check for updates to project dependencies:**
    ```bash
    mvn versions:display-dependency-updates
    ```

- **Gradle:**

  - **Create a new Gradle project:**
    ```bash
    gradle init
    ```

  - **Build a Gradle project:**
    ```bash
    gradle build
    ```

  - **Run a Gradle project:**
    ```bash
    gradle run
    ```

  - **Add a dependency to a Gradle project:**
    ```groovy
    dependencies {
      implementation 'org.example:example-dependency:1.0.0'
    }
    ```

  - **Check for updates to project dependencies:**
    ```bash
    gradle dependencyUpdates
    ```

#### **6. Java Testing**

- **JUnit:**

  - **Run JUnit tests:**
    ```bash
    java -cp .:junit-4.12.jar org.junit.runner.JUnitCore TestClass
    ```

  - **Create a test class (JUnit 4):**
    ```java
    import org.junit.Test;
    import static org.junit.Assert.assertEquals;

    public class TestClass {
        @Test
        public void testMethod() {
            assertEquals(1, 1);
        }
    }
    ```

  - **Create a test class (JUnit 5):**
    ```java
    import org.junit.jupiter.api.Test;
    import static org.junit.jupiter.api.Assertions.assertEquals;

    public class TestClass {
        @Test
        public void testMethod() {
            assertEquals(1, 1);
        }
    }
    ```

  - **Run JUnit 5 tests with Maven:**
    ```bash
    mvn test
    ```

  - **Run JUnit 5 tests with Gradle:**
    ```bash
    gradle test
    ```

#### **7. Java Profiling and Debugging**

- **Run Java with a profiler:**
  ```bash
  java -agentlib:hprof=cpu=samples,heap=sites HelloWorld
  ```

- **Generate a heap dump:**
  ```bash
  jmap -dump:live,format=b,file=heapdump.hprof <pid>
  ```

- **Analyze a heap dump (using `jhat`):**
  ```bash
  jhat heapdump.hprof
  ```

- **Run a Java program with remote debugging enabled:**
  ```bash
  java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 HelloWorld
  ```

- **Attach a debugger to a running Java process:**
  ```bash
  jdb -attach 5005
  ```

- **Analyze thread dumps:**
  ```bash
  jstack <pid>
  ```

- **Analyze CPU usage (using `jstat`):**
  ```bash
  jstat -gc <pid>
  ```

#### **8. Java Documentation**

- **Generate Javadoc:**
  ```bash
  javadoc -d doc HelloWorld.java
  ```

- **Generate Javadoc for a package:**
  ```bash
  javadoc -d doc com.example.package
  ```

- **Generate Javadoc with a custom stylesheet:**
  ```bash
  javadoc -d doc -stylesheetfile custom.css HelloWorld.java
  ```

### **Advanced Java Techniques**

#### **1. Advanced JVM Options**

- **Configure garbage collection logging:**
  ```bash
  java -Xlog:gc* HelloWorld
  ```

- **Configure heap size settings:**
  ```bash
  java -Xms512m -Xmx1024m HelloWorld
  ```

- **Enable flight recorder:**
  ```bash
  java -XX:+UnlockCommercialFeatures -XX:+FlightRecorder HelloWorld
  ```

- **Enable just-in-time (JIT) compiler logging:**
  ```bash
  java -XX:+PrintCompilation HelloWorld
  ```

- **Run a Java program in headless mode:**
  ```bash
  java -Djava.awt.headless=true HelloWorld
  ```

#### **2. Advanced Build Configurations**

- **Maven profiles for different environments:**
  ```xml
  <profiles>
    <profile>
      <id>development</id>
      <properties>
        <env>development</env>
      </properties>
    </profile>
    <profile>
      <id>production</id>
      <properties>
        <env>production</env>
      </properties>
    </profile>
  </profiles>
  ```

- **Conditional dependency in Maven:**
  ```xml
  <dependency>
    <groupId>org.example</groupId>
    <artifactId>example-dependency</artifactId>
    <version>1.0.0</version>
    <scope>${env}</scope>
  </dependency>
  ```

- **Custom Gradle task:**
  ```groovy
  task hello {
      doLast {
          println 'Hello, Gradle!'
      }
  }
  ```

- **Multi-project build in Gradle:**
  ```groovy
  include 'project1', 'project2'
  ```

#### **3. Advanced Testing Techniques**

- **Parameterized tests with JUnit 5:**
  ```java
  import org.junit.jupiter.params.ParameterizedTest;
  import org.junit.jupiter.params.provider.ValueSource;

  public class ParameterizedTestExample {
      @ParameterizedTest
      @ValueSource(strings = {"one", "two", "three"})
      void testWithStringParameter(String argument) {
          assertNotNull(argument);
      }
  }
  ```

- **Mocking with Mockito:**
  ```java
  import static org.mockito.Mockito.*;
  import org.junit.jupiter.api.Test;

  public class MockTest {
      @Test
      void testMock() {
          List mockList = mock(List.class);
          when(mockList.size()).thenReturn(10);
          assertEquals(10, mockList.size());
      }
  }
  ```
  
- **Integration tests with springboot:**
```java
import org.springframework.beans.factory.annotation.Autowired;

@SpringBootTest
public class ApplicationTests {

    @Autowired
    private SomeService someService;

    @Test
    public void contextLoads() {
        assertNotNull(someService);
    }
}
```

#### **4. Java Performance Tuning**

- **Using VisualVM for monitoring and profiling:**
  ```bash
  jvisualvm
  ```

- **Heap analysis with Eclipse Memory Analyzer (MAT):**
  ```bash
  mat -vmargs -Xmx4G
  ```

- **Analyze garbage collection logs with GCViewer:**
  ```bash
  java -jar gcviewer.jar gc.log
  ```

- **Configure JVM for low latency:**
  ```bash
  java -XX:+UseG1GC -XX:MaxGCPauseMillis=100 HelloWorld
  ```

- **Enable and configure JIT compiler optimizations:**
  ```bash
  java -XX:+AggressiveOpts -XX:+OptimizeStringConcat HelloWorld
  ```

#### **5. Java Security Configurations**

- **Generate a Java Keystore (JKS) file:**
  ```bash
  keytool -genkeypair -alias mykey -keyalg RSA -keystore keystore.jks -storepass password
  ```

- **Export a certificate from a JKS file:**
  ```bash
  keytool -exportcert -alias mykey -keystore keystore.jks -file mycert.cer
  ```

- **Import a certificate into a JKS file:**
  ```bash
  keytool -importcert -alias newcert -file newcert.cer -keystore keystore.jks
  ```

- **List entries in a JKS file:**
  ```bash
  keytool -list -v -keystore keystore.jks
  ```

- **Enable SSL in a Java application:**
  ```java
  System.setProperty("javax.net.ssl.keyStore", "keystore.jks");
  System.setProperty("javax.net.ssl.keyStorePassword", "password");
  System.setProperty("javax.net.ssl.trustStore", "truststore.jks");
  System.setProperty("javax.net.ssl.trustStorePassword", "password");
  ```

#### **6. Java Packaging and Deployment**

- **Create a self-contained application with jlink:**
  ```bash
  jlink --module-path $JAVA_HOME/jmods --add-modules java.base,java.logging --output myapp
  ```

- **Create a native image with GraalVM:**
  ```bash
  native-image -jar myapp.jar
  ```

- **Deploy a Java application using Docker:**
  ```dockerfile
  FROM openjdk:11-jre-slim
  COPY target/myapp.jar /app/myapp.jar
  ENTRYPOINT ["java", "-jar", "/app/myapp.jar"]
  ```

  ```bash
  docker build -t myapp .
  docker run -p 8080:8080 myapp
  ```

- **Deploy a Java application using Kubernetes:**
  ```yaml
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: myapp
  spec:
    replicas: 3
    selector:
      matchLabels:
        app: myapp
    template:
      metadata:
        labels:
          app: myapp
      spec:
        containers:
        - name: myapp
          image: myapp:latest
          ports:
          - containerPort: 8080
  ```

  ```bash
  kubectl apply -f deployment.yaml
  ```

#### **7. Java Code Quality Tools**

- **Checkstyle:**
  ```bash
  checkstyle -c /google_checks.xml HelloWorld.java
  ```

- **PMD:**
  ```bash
  pmd -d src -R rulesets/java/basic.xml -f text
  ```

- **FindBugs:**
  ```bash
  findbugs -textui -effort:max -low src
  ```

- **SonarQube:**
  ```bash
  sonar-scanner
  ```

- **SpotBugs:**
  ```bash
  spotbugs -textui -effort:max -low src
  ```

#### **8. Java Documentation and Annotation Processing**

- **Generate Javadoc with custom tags:**
  ```bash
  javadoc -d doc -tag custom:a:"Custom Tag" HelloWorld.java
  ```

- **Create a custom annotation processor:**
  ```java
  @SupportedAnnotationTypes("com.example.CustomAnnotation")
  @SupportedSourceVersion(SourceVersion.RELEASE_8)
  public class CustomProcessor extends AbstractProcessor {
      @Override
      public boolean process(Set<? extends TypeElement> annotations, RoundEnvironment roundEnv) {
          for (Element element : roundEnv.getElementsAnnotatedWith(CustomAnnotation.class)) {
              processingEnv.getMessager().printMessage(Diagnostic.Kind.NOTE, "Processing: " + element.toString());
          }
          return true;
      }
  }
  ```

- **Use annotation processing in a Maven project:**
  ```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.bsc.maven</groupId>
        <artifactId>maven-processor-plugin</artifactId>
        <version>3.3.3</version>
        <executions>
          <execution>
            <id>process</id>
            <goals>
              <goal>process</goal>
            </goals>
          </execution>
        </executions>
        <configuration>
          <processors>
            <processor>com.example.CustomProcessor</processor>
          </processors>
        </configuration>
      </plugin>
    </plugins>
  </build>
  ```

This comprehensive list of Java CLI commands and techniques covers everything from basic operations to advanced configurations and techniques. This should be a valuable reference for both everyday development tasks and more specialized operations.
