

## 3. Constructor Injection

**Definition:** Constructor injection is a dependency injection technique where an object's required dependencies are passed in as arguments to its constructor at the exact moment the object is created. The object is fully assembled — with every dependency already in place — before any other code can get a reference to it or call any method on it.

Compare this precisely to **setter injection** (which we already built on Day 3):

**Definition (recap) — Setter injection:** dependencies are supplied by calling a setter method on an object *after* it has already been constructed via a no-argument constructor. Between the moment the object is constructed and the moment the setter is called, the object technically exists in memory without its dependency set yet.

This difference is not just a style preference — it has a real, practical consequence, which we will make visible with actual code and output today, not just describe in words.

---

## 4. Building It — Step by Step

### Step 4.1 — `ProductService.java` — adding a second constructor

```java
// src/main/java/com/shopeasy/ProductService.java
package com.shopeasy;

import java.util.List;

public class ProductService {

    private ProductRepository productRepository;

    // NEW TODAY — constructor injection.
    // The dependency is required as a parameter; there is no way to
    // construct this object without supplying a ProductRepository.
    public ProductService(ProductRepository productRepository) {
        System.out.println("ProductService: created via CONSTRUCTOR injection.");
        this.productRepository = productRepository;
    }

    // Day 3's version — setter injection.
    // This constructor takes nothing; the dependency arrives later,
    // through the setter method below.
    public ProductService() {
        System.out.println("ProductService: created via no-arg constructor (setter injection to follow).");
    }

    public void setProductRepository(ProductRepository productRepository) {
        System.out.println("ProductService: dependency supplied via SETTER injection.");
        this.productRepository = productRepository;
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

We are deliberately keeping both constructors on the same class today, purely so you can compare their behavior side by side in one run. In a real application you would normally commit to **one** injection style per class, not maintain both — Section 7 explains exactly why, and it's one of the practical payoffs of today's class.

`Product.java` and `ProductRepository.java` are **unchanged** from Day 3 — copy them forward as they are.

### Step 4.2 — `applicationContext.xml` — two beans, two wiring styles

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
           http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="productRepository" class="com.shopeasy.ProductRepository" />

    <!-- Setter injection: Day 3's style -->
    <bean id="productServiceViaSetter" class="com.shopeasy.ProductService">
        <property name="productRepository" ref="productRepository" />
    </bean>

    <!-- Constructor injection: today's new style -->
    <bean id="productServiceViaConstructor" class="com.shopeasy.ProductService">
        <constructor-arg ref="productRepository" />
    </bean>

</beans>
```

**Concept box — `<constructor-arg>`:** this XML element tells the container to pass a value into the bean's constructor, rather than calling a setter afterward. `ref="productRepository"` means "pass in the bean whose id is `productRepository`" — the exact same bean, reused, that the setter-injection version above also refers to. Since Spring beans default to **singleton** scope (introduced properly on Day 9), both `productServiceViaSetter` and `productServiceViaConstructor` end up holding a reference to the exact same, single `ProductRepository` object — created only once for the whole container, no matter how many beans point a `ref` at it.

Notice the container now has to decide *which* of `ProductService`'s two constructors to call for `productServiceViaConstructor`. Since we gave exactly one `<constructor-arg>`, Spring matches it to the one constructor that takes exactly one argument of a compatible type — `ProductService(ProductRepository productRepository)`. For `productServiceViaSetter`, we gave zero `<constructor-arg>` elements, so Spring calls the no-argument constructor instead, then applies the `<property>` afterward.

### Step 4.3 — `ShopEasyApp.java` — updated to the renamed bean id

```java
// src/main/java/com/shopeasy/ShopEasyApp.java
package com.shopeasy;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class ShopEasyApp {
    public static void main(String[] args) {

        System.out.println("Starting ShopEasy...");

        ApplicationContext context =
                new ClassPathXmlApplicationContext("applicationContext.xml");

        System.out.println("Spring IoC container started successfully (XML-based configuration).");

        ProductService productService = context.getBean("productServiceViaSetter", ProductService.class);
        productService.printCatalog();
    }
}
```

The only change here from Day 3 is the bean id string, updated to match the rename in Step 4.2.

### Step 4.4 — `TestRunner.java` — today's actual new milestone

```java
// src/main/java/com/shopeasy/TestRunner.java
package com.shopeasy;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class TestRunner {
    public static void main(String[] args) {

        System.out.println("=== ShopEasy Dependency Injection Test Runner ===");

        ApplicationContext context =
                new ClassPathXmlApplicationContext("applicationContext.xml");

        System.out.println();
        System.out.println("---- Bean created via SETTER injection ----");
        ProductService serviceViaSetter =
                context.getBean("productServiceViaSetter", ProductService.class);
        serviceViaSetter.printCatalog();

        System.out.println();
        System.out.println("---- Bean created via CONSTRUCTOR injection ----");
        ProductService serviceViaConstructor =
                context.getBean("productServiceViaConstructor", ProductService.class);
        serviceViaConstructor.printCatalog();
    }
}
```

This class exists purely to prove, in one run, that both injection styles produce a fully working `ProductService` — the exact "test runner" milestone for today.

---

## 5. Running It — Today's Output

### Running the normal app (`ShopEasyApp`)

```
mvn compile exec:java
```

**Expected output:**

```
Starting ShopEasy...
ProductRepository: connecting to data source...
ProductService: created via CONSTRUCTOR injection.
ProductService: created via no-arg constructor (setter injection to follow).
ProductService: dependency supplied via SETTER injection.
Spring IoC container started successfully (XML-based configuration).
---- ShopEasy Catalog ----
Product{id=1, name='Wireless Mouse', price=799.0}
Product{id=2, name='Mechanical Keyboard', price=3499.0}
Product{id=3, name='USB-C Hub', price=1299.0}
```

Notice **both** `ProductService` beans get created during container startup (eager singleton instantiation, same as Day 3), even though `ShopEasyApp` only ever asks for `productServiceViaSetter`. That is expected — the container builds every bean it knows about at startup, regardless of which ones your code later requests.

### Running the test runner

```
mvn compile exec:java -Dexec.mainClass="com.shopeasy.TestRunner"
```

**Expected output:**

```
=== ShopEasy Dependency Injection Test Runner ===
ProductRepository: connecting to data source...
ProductService: created via CONSTRUCTOR injection.
ProductService: created via no-arg constructor (setter injection to follow).
ProductService: dependency supplied via SETTER injection.

---- Bean created via SETTER injection ----
---- ShopEasy Catalog ----
Product{id=1, name='Wireless Mouse', price=799.0}
Product{id=2, name='Mechanical Keyboard', price=3499.0}
Product{id=3, name='USB-C Hub', price=1299.0}

---- Bean created via CONSTRUCTOR injection ----
---- ShopEasy Catalog ----
Product{id=1, name='Wireless Mouse', price=799.0}
Product{id=2, name='Mechanical Keyboard', price=3499.0}
Product{id=3, name='USB-C Hub', price=1299.0}
```

Both beans print the exact same catalog. From the outside, calling `printCatalog()`, there is no visible difference between the two injection styles — both objects end up in a fully working state. The difference between them is not in what they can *do*, but in *when and how safely* they got into that working state. Section 6 makes that difference concrete.

---

## 6. The Real Difference — Shown, Not Just Explained

Try this deliberately: comment out the line `<property name="productRepository" ref="productRepository" />` from the `productServiceViaSetter` bean in `applicationContext.xml`, leaving the `<bean>` tag itself in place with nothing inside it. Then run `ShopEasyApp` again.

**What happens:** The container starts up successfully. The bean `productServiceViaSetter` is created successfully — the no-argument constructor runs fine, since it needs nothing. It is only when `printCatalog()` actually executes and tries to call `productRepository.findAll()` that you get a `NullPointerException`, because `productRepository` was never set.

Now imagine trying the equivalent mistake on the constructor-injected bean: remove the `<constructor-arg ref="productRepository" />` line entirely from `productServiceViaConstructor`. Run it again.

**What happens instead:** The container fails immediately at startup, before your application ever gets to run, with a `BeanCreationException` — because Spring cannot find a constructor on `ProductService` that takes zero arguments and matches what you're asking it to call incorrectly, or, if a no-arg constructor exists, it silently uses that one instead and you're back to the setter-injection failure mode. This is precisely why, in real applications, you do not mix both constructors on one class the way we did today for teaching purposes — doing so lets Spring quietly pick the "wrong" constructor and hide a missing dependency until much later, at the exact moment the `NullPointerException` above happened.

**Concept box — fail-fast:** this is the actual, practical reason constructor injection is generally preferred for **required** dependencies in real Spring applications. Definition: fail-fast means a program is designed to detect a configuration error as early as possible — ideally at startup — rather than allowing the program to start successfully and only fail later, at some unpredictable point during normal use. A class that only exposes a constructor requiring its dependencies (no no-arg constructor available at all) makes it *impossible* to end up with a half-configured object in memory — the object simply cannot exist without its dependencies, because there is no other way to construct it.

**Concept box — when setter injection is still the right tool:** setter injection remains genuinely useful for **optional** dependencies — configuration that has a sensible default and doesn't need to be supplied, or a dependency you might legitimately want to change after the object is already in use. Constructor injection is not "always better" in every case; it is specifically better for dependencies a class cannot function without.

---

## 7. Today's Take-Home Exercise

1. Create a new class, `ProductServiceConstructorOnly`, that is a copy of `ProductService` but with **only** the constructor-accepting version (delete the no-arg constructor and the setter entirely). Wire it in XML using `<constructor-arg>`, exactly as done today. Then deliberately forget the `<constructor-arg>` in XML and run the app. Read the resulting `BeanCreationException` message carefully and write down, in your own words, how this error message is different from — and arguably more helpful than — the silent `NullPointerException` you saw in Section 6 for the missing setter case.
2. In `TestRunner.java`, add a third block that calls `context.getBean("productServiceViaConstructor", ProductService.class)` a second time into a different variable, and print whether the two variables refer to the exact same object using `==`. Write down what this tells you about singleton scope (we formalize this properly on Day 9, but you're seeing the actual behavior today).
3. In one or two sentences, in your own words: when would you personally choose constructor injection for a class, and when would you choose setter injection? Give one concrete example of each from a hypothetical application, not from ShopEasy.

---

## 8. Concept Glossary — Day 4

| Term | Definition |
|---|---|
| Constructor injection | Supplying an object's dependencies as arguments to its constructor, so the object is fully assembled with all dependencies present the moment it is created. |
| Setter injection | Supplying an object's dependencies by calling a setter method after the object has already been constructed via a no-argument constructor. |
| `<constructor-arg>` | An XML element telling the container to pass a value or bean reference into a bean's constructor. |
| Fail-fast | A design approach where configuration errors are detected as early as possible (ideally at startup) rather than surfacing unpredictably later during normal use. |
| `BeanCreationException` | The exception Spring throws when it cannot successfully construct and configure a bean, typically surfacing immediately at container startup. |
| `NullPointerException` (in this context) | The runtime error that results from calling a method on a field that was never assigned a value — the typical failure mode of an incompletely set-up setter-injected object. |

---
