
## 3. What Is Maven, and Why Do We Need It Now?

**Definition:** Maven is a build and dependency-management tool for Java projects. It does two jobs that matter to us starting today:

1. **Dependency management** — instead of manually downloading `.jar` files for Spring (and everything Spring itself depends on) from the internet, you declare *what* you need in a file called `pom.xml`, and Maven downloads it and all of its own dependencies automatically.
2. **Standard project structure** — Maven expects your source code, resources, and compiled output in specific, predictable folders, so any Maven project looks the same to any developer or tool that opens it.

We did not need Maven on Day 1 because we had zero external dependencies — just four `.java` files we compiled by hand with `javac`. From today onward, we depend on Spring's `.jar` files, and downloading and wiring those by hand would be tedious and error-prone. That is the exact moment Maven earns its place in this course — we are not adding it "because it's standard," we are adding it because we now have a real dependency problem.

**Definition — `pom.xml`:** short for "Project Object Model" file. It is Maven's configuration file, written in XML, sitting at the root of the project. It declares the project's identity (group, artifact, version), the Java version to compile against, and the list of dependencies the project needs.

**Definition — dependency (in the Maven sense):** an external library that your project needs in order to compile or run, declared in `pom.xml` by its coordinates (`groupId`, `artifactId`, `version`) so Maven can fetch the exact right `.jar` file for you.

---

## 4. Setting Up the ShopEasy Maven Project

### Step 4.1 — The standard Maven folder layout

Create this structure (Maven expects these exact folder names):

```
ShopEasy/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── com/
                └── shopeasy/
                    ├── Product.java
                    ├── ProductRepository.java
                    ├── ProductService.java
                    └── ShopEasyApp.java
```

Notice two changes from Day 1:

- All source files now live under `src/main/java/...`, not loose in a folder. This is Maven's required convention — it is how Maven (and every IDE) knows where your application code lives.
- We have introduced a **package**, `com.shopeasy`. Every one of today's Java files starts with `package com.shopeasy;` as its first line. A package is Java's own namespace mechanism — grouping related classes under one name so large codebases (and later, Spring itself, which scans packages) can organize and locate classes reliably.

### Step 4.2 — Writing `pom.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.shopeasy</groupId>
    <artifactId>shopeasy</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>6.1.13</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.codehaus.mojo</groupId>
                <artifactId>exec-maven-plugin</artifactId>
                <version>3.2.0</version>
                <configuration>
                    <mainClass>com.shopeasy.ShopEasyApp</mainClass>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

**Concept box — reading these coordinates:**

| Element | Meaning |
|---|---|
| `groupId` | Identifies the organization/team owning the project (or, for a dependency, the organization that published it). |
| `artifactId` | The specific project or library's name. |
| `version` | The exact version of that project/library to use. |
| `spring-context` | The specific Spring module we need. It is the module that contains the IoC container itself (`ApplicationContext` and its supporting classes). Spring is split into many modules (`spring-core`, `spring-context`, `spring-webmvc`, `spring-jdbc`, etc.) and you only pull in the ones you actually use — another reason this is introduced only now, when we need our first one. |
| `exec-maven-plugin` | A Maven plugin that lets us run our program with a simple command (`mvn exec:java`) instead of manually building the classpath by hand like we did with `javac`/`java` on Day 1. |

---

## 5. Concept Box — What Is Spring's IoC Container, Concretely?

We defined Inversion of Control on Day 1 as an idea. Today we meet its actual implementation in Spring.

**Definition — IoC Container:** the part of the Spring Framework responsible for creating objects, configuring them, and managing their entire lifecycle, based on configuration you provide to it (we will provide that configuration starting Day 3). You never call `new` on these objects yourself; you ask the container for them, and it hands you a fully constructed, fully wired object.

**Definition — `ApplicationContext`:** the primary interface in Spring representing the IoC container. When your program creates an `ApplicationContext`, it is starting up the container itself. Once started, the container reads whatever configuration it was given (XML files, Java annotations, or Java `@Configuration` classes — we cover all three in this course, one at a time) and becomes ready to create and hand out objects on request.

**Definition — Bean:** in Spring's vocabulary, any object that is created, configured, and managed by the IoC container is called a **bean**. This is simply Spring's name for "an object the container is in charge of." We have zero beans registered today — we are only starting the empty container and proving it runs. Day 3 is when we register our first bean.

---

## 6. Building It — Step by Step

### Step 6.1 — Keep the same three domain classes from Day 1 (now with a package declaration)

```java
// src/main/java/com/shopeasy/Product.java
package com.shopeasy;

public class Product {
    private int id;
    private String name;
    private double price;

    public Product(int id, String name, double price) {
        this.id = id;
        this.name = name;
        this.price = price;
    }

    public int getId() { return id; }
    public String getName() { return name; }
    public double getPrice() { return price; }

    @Override
    public String toString() {
        return "Product{id=" + id + ", name='" + name + "', price=" + price + "}";
    }
}
```

```java
// src/main/java/com/shopeasy/ProductRepository.java
package com.shopeasy;

import java.util.ArrayList;
import java.util.List;

public class ProductRepository {

    public ProductRepository() {
        System.out.println("ProductRepository: connecting to data source...");
    }

    public List<Product> findAll() {
        List<Product> products = new ArrayList<>();
        products.add(new Product(1, "Wireless Mouse", 799.00));
        products.add(new Product(2, "Mechanical Keyboard", 3499.00));
        products.add(new Product(3, "USB-C Hub", 1299.00));
        return products;
    }
}
```

```java
// src/main/java/com/shopeasy/ProductService.java
package com.shopeasy;

import java.util.List;

public class ProductService {

    private ProductRepository productRepository;

    public ProductService() {
        // Still tightly coupled — we have NOT fixed this yet.
        // Today's goal is only to get Spring's container running.
        // We fix this exact line on Day 3.
        this.productRepository = new ProductRepository();
    }

    public void printCatalog() {
        List<Product> products = productRepository.findAll();
        System.out.println("---- ShopEasy Catalog ----");
        for (Product p : products) {
            System.out.println(p);
        }
    }
}
```

Notice: these three classes are **word-for-word the same logic as Day 1**, just with a `package` line added. This is intentional —    does not touch the coupling problem at all. We are isolating one change at a time: today is purely "get Maven and the container running," and Day 3 is purely "fix the coupling using the container." Mixing both in one day would blur which concept solved which problem.

### Step 6.2 — An empty configuration class, so the container has something to read

Spring's `ApplicationContext` needs to be told, even if there's nothing in it yet, what kind of configuration to read. We are using Java-based configuration here (we will explain the XML-based alternative on Day 3, and contrast the two directly).

```java
// src/main/java/com/shopeasy/AppConfig.java
package com.shopeasy;

import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {
    // Intentionally empty today.
    // This class exists only so Spring's container has a configuration
    // source to read when it starts up. We register our first real bean
    // here on Day 3.
}
```

**Concept box — `@Configuration`:** this is a Spring **annotation**. Definition: an annotation is a piece of metadata attached to a class, method, or field using the `@Name` syntax, which frameworks like Spring read at startup to decide how to treat that code. `@Configuration` specifically tells Spring's container: "treat this class as a source of bean definitions." Today it defines zero beans, but the container still needs to be pointed at it to start correctly.

### Step 6.3 — `ShopEasyApp`: starting the container and proving it's alive

```java
// src/main/java/com/shopeasy/ShopEasyApp.java
package com.shopeasy;

import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import org.springframework.context.ApplicationContext;

public class ShopEasyApp {
    public static void main(String[] args) {

        System.out.println("Starting ShopEasy...");

        // ---- NEW TODAY: starting Spring's IoC container ----
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
        System.out.println("Spring IoC container started successfully.");
        System.out.println("Container class in use: " + context.getClass().getSimpleName());
        System.out.println("Bean definitions currently registered: " + context.getBeanDefinitionCount());

        // ---- Day 1's plain-Java flow still runs exactly as before ----
        // Not wired through the container yet — that's Day 3's job.
        ProductService productService = new ProductService();
        productService.printCatalog();
    }
}
```

**Concept box — `AnnotationConfigApplicationContext`:** this is one specific, concrete implementation of the `ApplicationContext` interface — the one used when your configuration is written in Java using `@Configuration` classes (as opposed to XML files, which use a different implementation class, `ClassPathXmlApplicationContext`, which we meet on Day 3). Passing `AppConfig.class` to its constructor tells it exactly which configuration class to read on startup.

---

## 7. Running It — Today's Output

From the `ShopEasy` root folder (where `pom.xml` lives), run:

```
mvn compile exec:java
```

The first time you run this, Maven will download Spring's `.jar` files from the internet — you will see a burst of download progress lines. That is Maven doing dependency management for you, exactly as described in Section 3. Once downloads finish, your program's own output appears.

**Expected output (Spring's own startup logging lines will also appear above this — that is normal and we explain Spring's logging output properly in a later class):**

```
Starting ShopEasy...
Spring IoC container started successfully.
Container class in use: AnnotationConfigApplicationContext
Bean definitions currently registered: 6
ProductRepository: connecting to data source...
---- ShopEasy Catalog ----
Product{id=1, name='Wireless Mouse', price=799.0}
Product{id=2, name='Mechanical Keyboard', price=3499.0}
Product{id=3, name='USB-C Hub', price=1299.0}
```

Two things to notice in this output, and both matter for what's coming next:

1. **"Bean definitions currently registered: 6"** — this number is not zero, even though `AppConfig` is empty. Spring automatically registers a handful of internal infrastructure beans it needs for its own operation. None of these are *ours* yet. Our own bean count is still zero — proof that the container is alive, but not yet doing any work for our classes.
2. **The catalog output is byte-for-byte identical to Day 1's output.** That is deliberate. Right now Spring is running *alongside* our code, not *in charge of* our code. `ProductService` still says `new ProductRepository()` internally. Day 3's entire job is to make that line disappear and have the container do it instead — and you will be able to compare tomorrow's output to today's and see that the visible result is the same, but *who created the objects* has changed underneath.

---

## 8. Today's Take-Home Exercise

1. Change the printed line to also show `context.getEnvironment().getClass().getSimpleName()` and describe, in one sentence, what you think an "Environment" object inside a container might be responsible for (you are not expected to know the real answer yet — this is a prediction exercise, we cover it properly later in the course).
2. Deliberately misspell `AppConfig` as `AppConfigg` in the `ShopEasyApp` line that creates the context, and run the program. Read the resulting compiler error carefully and write down, in your own words, what it is telling you.
3. Open `pom.xml` and change the `spring-context` version number to an obviously invalid one (e.g. `99.99.99`), run `mvn compile exec:java`, and read the resulting Maven error. Write down what Maven was trying and failing to do — this is the dependency-management behavior from Section 3, now seen breaking on purpose so you recognize it later when it happens by accident.

---

## 9. Concept Glossary —   

| Term | Definition |
|---|---|
| Maven | A build and dependency-management tool for Java that downloads required libraries automatically and enforces a standard project folder structure. |
| `pom.xml` | Maven's project configuration file — declares the project's identity and its list of dependencies. |
| Dependency (Maven) | An external library your project needs, declared by `groupId`, `artifactId`, and `version` so Maven can fetch the correct `.jar`. |
| Package (Java) | Java's namespace mechanism for grouping related classes under one name, declared with `package ...;` at the top of a file. |
| IoC Container | The part of Spring responsible for creating, configuring, and managing the lifecycle of objects on your behalf. |
| `ApplicationContext` | The core Spring interface representing the IoC container. |
| Bean | Any object created and managed by Spring's IoC container. |
| Annotation | Metadata attached to code using `@Name` syntax, read by frameworks like Spring to change how that code is treated. |
| `@Configuration` | An annotation marking a class as a source of bean definitions for the container to read. |
| `AnnotationConfigApplicationContext` | The specific `ApplicationContext` implementation used when configuration is written in Java via `@Configuration` classes. |

---

