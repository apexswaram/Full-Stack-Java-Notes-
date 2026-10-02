### POM.xml
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

        <!-- Spring Context -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>6.1.13</version>
        </dependency>

        <!-- Spring JDBC -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>6.1.13</version>
        </dependency>

        <!-- Jakarta Annotation -->
        <dependency>
            <groupId>jakarta.annotation</groupId>
            <artifactId>jakarta.annotation-api</artifactId>
            <version>3.0.0</version>
        </dependency>

        <!-- H2 Database -->
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <version>2.2.224</version>
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

---

### AppConfig
```java
package com.shopeasy;

import javax.sql.DataSource;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.PropertySource;

import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.jdbc.datasource.DriverManagerDataSource;

@Configuration
@ComponentScan(basePackages = "com.shopeasy")
@PropertySource("classpath:application.properties")
public class AppConfig {

    @Bean
    public AuditLogger auditLogger() {
        return new AuditLogger("ShopEasy-Audit");
    }

    @Bean
    public DataSource dataSource() {

        DriverManagerDataSource dataSource =
                new DriverManagerDataSource();

        dataSource.setDriverClassName("org.h2.Driver");

        dataSource.setUrl(
                "jdbc:h2:mem:shopeasydb;DB_CLOSE_DELAY=-1"
        );

        dataSource.setUsername("sa");
        dataSource.setPassword("");

        return dataSource;
    }

    @Bean
    public JdbcTemplate jdbcTemplate(DataSource dataSource) {

        return new JdbcTemplate(dataSource);
    }
}
```

---

### AuditLogger

```java
package com.shopeasy;

public class AuditLogger {

    private final String prefix;

    public AuditLogger(String prefix) {
        this.prefix = prefix;

        System.out.println(
                "AuditLogger: initialized with prefix '" + prefix + "'"
        );
    }

    public void log(String message) {
        System.out.println("[" + prefix + "] " + message);
    }
}
```

---

### FakeProductrepository

```java 
package com.shopeasy;

import java.util.ArrayList;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Component;

@Component("fakeProductRepository")
public class FakeProductrepository extends ProductRepository {

    @Autowired
    public FakeProductrepository(JdbcTemplate jdbcTemplate) {
        super(jdbcTemplate);
    }

    @Override
    public List<Product> findAll() {

        List<Product> products = new ArrayList<>();

        products.add(
                new Product(
                        999,
                        "TEST PRODUCT",
                        0.00
                )
        );

        return products;
    }
}
```
---

### Product

```java 
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

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }

    @Override
    public String toString() {
        return "Product{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
}
```
---
### ProductRepository

```java 
package com.shopeasy;

import java.util.List;

import jakarta.annotation.PostConstruct;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Component;

@Component("productRepository")
public class ProductRepository {

    protected final JdbcTemplate jdbcTemplate;

    @Autowired
    public ProductRepository(JdbcTemplate jdbcTemplate) {

        this.jdbcTemplate = jdbcTemplate;

        System.out.println(
                "ProductRepository: connected via JdbcTemplate."
        );
    }

    @PostConstruct
    public void setupSchemaAndSeedData() {

        jdbcTemplate.execute(
                "CREATE TABLE IF NOT EXISTS products (" +
                "id INT PRIMARY KEY, " +
                "name VARCHAR(100), " +
                "price DOUBLE)"
        );

        Integer existingRows = jdbcTemplate.queryForObject(
                "SELECT COUNT(*) FROM products",
                Integer.class
        );

        if (existingRows == null || existingRows == 0) {

            jdbcTemplate.update(
                    "INSERT INTO products (id, name, price) VALUES (?, ?, ?)",
                    1,
                    "Wireless Mouse",
                    799.00
            );

            jdbcTemplate.update(
                    "INSERT INTO products (id, name, price) VALUES (?, ?, ?)",
                    2,
                    "Mechanical Keyboard",
                    3499.00
            );

            jdbcTemplate.update(
                    "INSERT INTO products (id, name, price) VALUES (?, ?, ?)",
                    3,
                    "USB-C Hub",
                    1299.00
            );

            System.out.println(
                    "ProductRepository: seed data inserted."
            );
        }
    }

    public List<Product> findAll() {

        return jdbcTemplate.query(
                "SELECT id, name, price FROM products",

                (rs, rowNum) -> new Product(
                        rs.getInt("id"),
                        rs.getString("name"),
                        rs.getDouble("price")
                )
        );
    }

    public Product findById(int id) {

        return jdbcTemplate.queryForObject(
                "SELECT id, name, price FROM products WHERE id = ?",

                (rs, rowNum) -> new Product(
                        rs.getInt("id"),
                        rs.getString("name"),
                        rs.getDouble("price")
                ),

                id
        );
    }
}
```
---
### ProductService

```java 
package com.shopeasy;

import java.util.ArrayList;
import java.util.List;

import jakarta.annotation.PostConstruct;
import jakarta.annotation.PreDestroy;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

@Component
public class ProductService {

    private final ProductRepository productRepository;
    private final AuditLogger auditLogger;

    @Value("${shop.name}")
    private String shopName;

    private List<Product> productCache;

    @Autowired
    public ProductService(
            @Qualifier("productRepository") ProductRepository productRepository,
            AuditLogger auditLogger) {

        this.productRepository = productRepository;
        this.auditLogger = auditLogger;

        System.out.println(
                "ProductService: created via CONSTRUCTOR injection (annotation-based)."
        );
    }

    @PostConstruct
    public void initialize() {

        System.out.println(
                "ProductService: @PostConstruct - shopName field now = "
                        + shopName
        );

        productCache = new ArrayList<>(
                productRepository.findAll()
        );

        System.out.println(
                "ProductService: @PostConstruct - preloaded "
                        + productCache.size()
                        + " product(s) into cache for "
                        + shopName
        );
    }

    public List<Product> getProducts() {
        return productCache;
    }

    public Product getProductById(int id) {

        return productRepository.findById(id);
    }

    public void printCatalog() {

        System.out.println(
                "---- ShopEasy Catalog (from cache) ----"
        );

        for (Product product : productCache) {
            System.out.println(product);
        }

        auditLogger.log(
                "Catalog printed for " + shopName
        );
    }

    @PreDestroy
    public void cleanup() {

        System.out.println(
                "ProductService: @PreDestroy - clearing catalog cache before shutdown..."
        );

        productCache.clear();

        auditLogger.log(
                "ProductService shut down cleanly for " + shopName
        );
    }
}
```

---
### ShopEasyApp
```java
package com.shopeasy;

import java.util.concurrent.CountDownLatch;

import org.h2.tools.Server;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class ShopEasyApp {

    public static void main(String[] args) throws Exception {

        System.out.println("Starting ShopEasy...");

        // Start H2 Web Console
        Server h2Server = Server.createWebServer(
                "-web",
                "-webPort",
                "8084"
        ).start();

        System.out.println(
                "H2 Console started at: " + h2Server.getURL()
        );

        ApplicationContext context =
                new AnnotationConfigApplicationContext(
                        AppConfig.class
                );

        ProductService productService =
                context.getBean(ProductService.class);

        productService.printCatalog();

        System.out.println(
                "Spring IoC container started successfully."
        );

        System.out.println(
                "H2 Console URL: http://localhost:8082"
        );

        // Keep application running
        CountDownLatch latch = new CountDownLatch(1);

        Runtime.getRuntime().addShutdownHook(
                new Thread(() -> {

                    System.out.println(
                            "Shutting down ShopEasy..."
                    );

                    ((AnnotationConfigApplicationContext) context).close();

                    h2Server.stop();

                    System.out.println(
                            "ShopEasy shut down."
                    );
                })
        );

        latch.await();
    }
}
```
---
### TestRunner
```java
package com.shopeasy;

import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import org.springframework.jdbc.core.JdbcTemplate;

public class TestRunner {

    public static void main(String[] args) {

        System.out.println(
                "=== ShopEasy Database Inspection ==="
        );

        ApplicationContext context =
                new AnnotationConfigApplicationContext(
                        AppConfig.class
                );

        JdbcTemplate jdbcTemplate =
                context.getBean(JdbcTemplate.class);

        Integer rowCount =
                jdbcTemplate.queryForObject(
                        "SELECT COUNT(*) FROM products",
                        Integer.class
                );

        System.out.println(
                "Rows currently in the PRODUCTS table: "
                        + rowCount
        );

        ProductRepository repository =
                context.getBean(
                        "productRepository",
                        ProductRepository.class
                );

        Product product =
                repository.findById(2);

        System.out.println(
                "Product with ID 2: " + product
        );

        ((AnnotationConfigApplicationContext) context).close();
    }
}
```

---
