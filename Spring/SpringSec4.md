## 3.The Four New Annotations, Defined Precisely

**`@Component`**
Definition: an annotation that marks a class as a Spring-managed bean, eligible for automatic detection by **component scanning**, without needing a hand-written `<bean>` tag for it anywhere. Spring will create exactly one instance of any class annotated `@Component` that it finds while scanning, register it in the container, and give it a default bean name (the class name with a lowercase first letter, e.g. `ProductRepository` becomes `productRepository`) unless you specify a name yourself.

**`@Autowired`**
Definition: an annotation telling Spring to automatically find and inject a matching bean wherever it's placed — on a constructor, a field, or a setter method — without you writing explicit `<property>` or `<constructor-arg>` wiring. Spring looks at the *type* it needs to supply and searches the container for a bean of that type (or a subtype of it) to hand over.

**`@Qualifier`**
Definition: an annotation used together with `@Autowired` to resolve ambiguity when more than one bean in the container matches the required type. `@Qualifier("beanName")` tells Spring exactly which bean, by name, to inject in that specific spot — instead of letting Spring guess between multiple valid candidates.

**`@Value`**
Definition: an annotation for injecting a literal value or a property placeholder (written as `${property.name}`) directly into a field or constructor parameter, rather than injecting another bean. It is used for configuration values — strings, numbers, booleans — not for wiring one Spring-managed object to another.

---

## 4. Building It — Step by Step

### Step 4.1 — Project structure after today's change

```
ShopEasy/
├── pom.xml
└── src/
    └── main/
        ├── java/
        │   └── com/
        │       └── shopeasy/
        │           ├── Product.java
        │           ├── ProductRepository.java
        │           ├── FakeProductRepository.java
        │           ├── ProductService.java
        │           ├── ShopEasyApp.java
        │           └── TestRunner.java
        └── resources/
            ├── applicationContext.xml
            └── application.properties
```

We are adding one new file today, `application.properties`, and keeping `FakeProductRepository` from Day 3 — but for a new purpose, explained in Step 4.4.

### Step 4.2 — `application.properties` — an external value to inject

```properties
shop.name=ShopEasy
shop.discount.rate=0.10
```

**Concept box — properties file:** a plain text file of `key=value` pairs used to store configuration separately from your Java code, so you can change a value like a shop's display name without recompiling anything. Today we only *read* one value from it with `@Value`; we will use these files far more heavily once we reach Spring Boot in Part 2 of this course.

### Step 4.3 — `applicationContext.xml` — shrinking to almost nothing

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
           http://www.springframework.org/schema/beans/spring-beans.xsd
           http://www.springframework.org/schema/context
           http://www.springframework.org/schema/context/spring-context.xsd">

    <context:property-placeholder location="classpath:application.properties" />

    <context:component-scan base-package="com.shopeasy" />

</beans>
```

Compare this to Day 4's version of this same file, which had four separate `<bean>` elements with explicit wiring inside them. Today's version has **zero** `<bean>` tags. Read the two lines that replaced all of that:

**Concept box — `<context:component-scan>`:** tells the container to scan the given Java package (and every sub-package inside it) for any class annotated `@Component` (or a small family of related annotations we meet later, like `@Service` and `@Repository`), and register each one it finds as a bean automatically — with no `<bean>` tag required. `base-package="com.shopeasy"` means "look inside `com.shopeasy` and everything nested under it."

**Concept box — `<context:property-placeholder>`:** tells the container to load the given `.properties` file and make every key inside it available for resolving `${...}` placeholders anywhere in your annotated beans — which is exactly what makes today's `@Value("${shop.name}")` (Step 4.5) work.

### Step 4.4 — `ProductRepository.java` and `FakeProductRepository.java` — now self-registering

```java
// src/main/java/com/shopeasy/ProductRepository.java
package com.shopeasy;

import java.util.ArrayList;
import java.util.List;
import org.springframework.stereotype.Component;

@Component("productRepository")
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
// src/main/java/com/shopeasy/FakeProductRepository.java
package com.shopeasy;

import java.util.ArrayList;
import java.util.List;
import org.springframework.stereotype.Component;

@Component("fakeProductRepository")
public class FakeProductRepository extends ProductRepository {

    @Override
    public List<Product> findAll() {
        List<Product> products = new ArrayList<>();
        products.add(new Product(999, "TEST PRODUCT", 0.00));
        return products;
    }
}
```

Notice `@Component("productRepository")` explicitly names the bean, rather than letting Spring generate the default name. We are doing this deliberately today so the bean names still match what you're used to from Day 3 and Day 4 — but also because we are about to need to refer to this exact name in `@Qualifier`, in Step 4.5.

We now have **two** classes in the container that are both assignable to type `ProductRepository`: the `productRepository` bean itself, and `fakeProductRepository`, which is a `ProductRepository` (through inheritance) that happens to override `findAll()`. Keep this fact in mind — it is the entire reason today's class needs `@Qualifier` at all.

### Step 4.5 — `ProductService.java` — annotation-based wiring, plus `@Value`

```java
// src/main/java/com/shopeasy/ProductService.java
package com.shopeasy;

import java.util.List;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

@Component
public class ProductService {

    private final ProductRepository productRepository;

    @Value("${shop.name}")
    private String shopName;

    @Autowired
    public ProductService(@Qualifier("productRepository") ProductRepository productRepository) {
        System.out.println("ProductService: created via CONSTRUCTOR injection (annotation-based).");
        this.productRepository = productRepository;
    }

    public void printCatalog() {
        List<Product> products = productRepository.findAll();
        System.out.println("---- " + shopName + " Catalog ----");
        for (Product p : products) {
            System.out.println(p);
        }
    }
}
```

Walk through every annotation here carefully:

- `@Component` on the class — this is the exact replacement for Day 4's `<bean id="..." class="com.shopeasy.ProductService">` tag. No id was given, so Spring registers this bean under the default name `productService`.
- `@Autowired` on the constructor — this is the exact replacement for Day 4's `<constructor-arg ref="productRepository" />`. Spring sees the constructor needs a `ProductRepository`, and looks in the container for one.
- `@Qualifier("productRepository")` on the constructor parameter — **this is new, and necessary**, because of Step 4.4. If we only wrote `@Autowired` with no `@Qualifier`, Spring would find *two* beans assignable to `ProductRepository` (`productRepository` and `fakeProductRepository`) and would not know which one to pick. `@Qualifier` removes that ambiguity by naming the exact bean to use. We prove this by deliberately breaking it in Section 6.
- `@Value("${shop.name}")` on the `shopName` field — this reads the `shop.name` key from `application.properties` (loaded via the `<context:property-placeholder>` line in Step 4.3) and injects the literal string `"ShopEasy"` directly into this field. No bean is involved here at all — this is a plain configuration value, not object wiring.
- The `productRepository` field is now `private final` — because we have committed fully to constructor injection today (no setter, no second constructor), we can make the field `final`, guaranteeing the compiler itself will refuse to compile any code path that could leave this field unset. This is the concrete, compiler-enforced version of the "fail-fast" idea from Day 4.

### Step 4.6 — `ShopEasyApp.java` and `TestRunner.java` — fetching beans by type

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

        System.out.println("Spring IoC container started successfully (annotation-based configuration via component-scan).");

        ProductService productService = context.getBean(ProductService.class);
        productService.printCatalog();
    }
}
```

**Concept box — `getBean(ProductService.class)`, by type instead of by name:** since there is now only one `ProductService` bean in the container, we can ask for it by its class directly, without naming it. This overload of `getBean` returns the single bean matching that type, and throws an exception if there were zero matches or more than one — which is exactly the same ambiguity problem `@Qualifier` solves for autowiring, now seen from the calling code's side instead of the wiring side.

`TestRunner.java` from Day 4 is no longer needed in its old form (it existed specifically to compare constructor vs. setter injection, which we've now retired in favor of committing to constructor injection). We repurpose it today for a different, more useful test — proving the `@Qualifier` ambiguity in Section 6:

```java
// src/main/java/com/shopeasy/TestRunner.java
package com.shopeasy;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class TestRunner {
    public static void main(String[] args) {

        System.out.println("=== ShopEasy Bean Inspection ===");

        ApplicationContext context =
                new ClassPathXmlApplicationContext("applicationContext.xml");

        System.out.println("productRepository bean type: "
                + context.getBean("productRepository").getClass().getSimpleName());
        System.out.println("fakeProductRepository bean type: "
                + context.getBean("fakeProductRepository").getClass().getSimpleName());
        System.out.println("Total beans registered: " + context.getBeanDefinitionCount());
    }
}
```

---

## 5. Running It — Today's Output

```
mvn compile exec:java
```

**Expected output:**

```
Starting ShopEasy...
ProductRepository: connecting to data source...
ProductRepository: connecting to data source...
ProductService: created via CONSTRUCTOR injection (annotation-based).
Spring IoC container started successfully (annotation-based configuration via component-scan).
---- ShopEasy Catalog ----
Product{id=1, name='Wireless Mouse', price=799.0}
Product{id=2, name='Mechanical Keyboard', price=3499.0}
Product{id=3, name='USB-C Hub', price=1299.0}
```

Look carefully at the **two** identical `"ProductRepository: connecting to data source..."` lines. This is not a bug, and it's worth understanding exactly why it happens: `FakeProductRepository extends ProductRepository`, and its class has no constructor of its own — Java automatically inserts an implicit `super()` call at the start of its (also implicit) default constructor. That `super()` call runs `ProductRepository`'s constructor, which contains our println. So creating the `fakeProductRepository` bean *also* triggers `ProductRepository`'s constructor logic, once for each of the two separate bean instances Spring created (`productRepository` and `fakeProductRepository` are two distinct objects in memory, even though one is a subtype of the other).

Also notice: `"ShopEasy"` in the catalog header is no longer a hardcoded string in `ProductService.java` — it came from `application.properties` through `@Value`. Change `shop.name=ShopEasy` to `shop.name=ShopEasy Express` in that file, rerun, and watch the header change without touching a single line of Java.

---

## 6. Proving Why `@Qualifier` Is Actually Necessary

Temporarily remove `@Qualifier("productRepository")` from `ProductService`'s constructor parameter, leaving just `@Autowired` on the constructor, and rerun:

```
mvn compile exec:java
```

**What happens:** the container fails to start. You get a `NoUniqueBeanDefinitionException`, with a message naming both `productRepository` and `fakeProductRepository` as candidates it could not choose between. This is Spring telling you, at startup (fail-fast, same principle as Day 4), exactly what it could not resolve and exactly which beans were competing for the same slot.

Put `@Qualifier("productRepository")` back before continuing. This exercise is the entire reason Step 4.4 introduced a second `@Component`-annotated `ProductRepository` subtype today — without a genuine ambiguous case like this one, `@Qualifier` would just be syntax to memorize with no felt reason to use it.

---

## 7. Today's Take-Home Exercise

1. Change `@Qualifier("productRepository")` to `@Qualifier("fakeProductRepository")` instead, and rerun `ShopEasyApp`. Confirm the catalog output changes to the fake single test product, and write one sentence connecting this back to Day 3's original "swap the repository without touching consuming code" goal — except today the swap is a one-word annotation change instead of an XML attribute change.
2. Add a second `@Value`-injected field to `ProductService`, reading `shop.discount.rate` from `application.properties` as a `double`, and print it inside `printCatalog()`.
3. Remove the `location="classpath:application.properties"` attribute from `<context:property-placeholder>` entirely and rerun. Read the resulting exception message and write down, in your own words, what Spring was trying to resolve `${shop.name}` against when it failed.

---

## 8. Concept Glossary — Day 5

| Term | Definition |
|---|---|
| `@Component` | Marks a class as a Spring-managed bean, auto-detected by component scanning instead of a hand-written `<bean>` tag. |
| Component scanning | The process by which Spring searches a given package (and sub-packages) for `@Component`-annotated classes and registers them as beans automatically. |
| `<context:component-scan>` | The XML element that turns component scanning on for a given base package. |
| `@Autowired` | Tells Spring to automatically find and inject a matching bean into a constructor, field, or setter, without explicit XML wiring. |
| `@Qualifier` | Used with `@Autowired` to name exactly which bean to inject when more than one bean matches the required type. |
| `@Value` | Injects a literal value or a `${property}` placeholder from a properties source into a field or constructor parameter. |
| `<context:property-placeholder>` | The XML element that loads a `.properties` file so `${...}` placeholders can be resolved elsewhere in the configuration. |
| `NoUniqueBeanDefinitionException` | The exception Spring throws when `@Autowired` matches more than one candidate bean and cannot determine which to inject. |

---
