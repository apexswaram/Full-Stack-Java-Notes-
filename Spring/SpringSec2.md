## 3. XML-Based Bean Definition

**Definition:** XML-based configuration is a way of telling Spring's IoC container which objects to create and how to wire them together, by writing that information declaratively in an XML file, instead of writing Java code that constructs the objects yourself. The container reads this file at startup and builds every object it describes.

This was historically the *first* way Spring supported configuring beans, before annotations and Java-based configuration existed. We are learning it first in this course for the same reason Spring's own history went this way: it makes the wiring completely explicit and visible in one file, with no annotations or scanning behavior to understand yet. Once you've seen wiring done explicitly in XML, the "magic" of annotation-based wiring (Day 5) will feel like a shortcut for something you already understand — not an unexplained trick.

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
        │           ├── ProductService.java
        │           └── ShopEasyApp.java
        └── resources/
            └── applicationContext.xml
```

**Concept box — the `resources` folder:** Maven's standard layout reserves `src/main/resources` for non-Java files that still need to end up on the classpath at runtime — configuration files, property files, and, starting today, our Spring XML file. Anything placed here is automatically copied alongside the compiled `.class` files when Maven builds the project, which is exactly why Spring will be able to find `applicationContext.xml` "on the classpath" without us wiring any extra path configuration ourselves.

We are no longer using `AppConfig.java` from Day 2 today — you can delete that file, or simply leave it unused. We return to Java-based configuration properly in Day 6, once we've fully understood the XML approach it is replacing.

### Step 4.2 — `Product.java` (unchanged from Day 1 and Day 2)

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

### Step 4.3 — `ProductRepository.java` (unchanged from Day 1 and Day 2)

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

Notice this class has not changed one bit since Day 1. That is an important, deliberate signal: the fix we are applying today does not require touching the class that gets depended *on*. It only requires changing the class that does the depending. This is a preview of a bigger idea we'll keep meeting all course: good dependency design tends to let you swap or fix "consumers" without disturbing the things they consume.

### Step 4.4 — `ProductService.java` — the actual fix

```java
// src/main/java/com/shopeasy/ProductService.java
package com.shopeasy;

import java.util.List;

public class ProductService {

    private ProductRepository productRepository;

    // No-argument constructor. Spring calls this to create the object.
    public ProductService() {
    }

    // Spring calls this setter method after construction, handing us
    // the ProductRepository it created — we no longer create it ourselves.
    public void setProductRepository(ProductRepository productRepository) {
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

Compare this line-by-line with Day 1's version. The constructor is now empty. The line `this.productRepository = new ProductRepository();` is **gone completely**. In its place is an ordinary setter method, `setProductRepository`. `ProductService` no longer knows or cares how a `ProductRepository` gets built — it just expects one to be handed to it through this method.

**Concept box — setter injection (named properly, explained fully on Day 4):** what we've just written is one of Spring's two main injection styles — supplying a dependency through a setter method rather than through the constructor. Today you only need to recognize the pattern: an empty (or unrelated) constructor, plus a `setXxx` method that stores the dependency into a field. Day 4 puts this side by side with constructor injection and explains when to prefer each.

### Step 4.5 — `applicationContext.xml` — describing the beans

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
           http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="productRepository" class="com.shopeasy.ProductRepository" />

    <bean id="productService" class="com.shopeasy.ProductService">
        <property name="productRepository" ref="productRepository" />
    </bean>

</beans>
```

**Concept box — reading this file, tag by tag:**

| Tag / Attribute | Meaning |
|---|---|
| `<beans>` | The root element of every Spring XML configuration file. Everything inside it is bean configuration for one container. |
| `<bean>` | Declares one object that the container should create and manage. Each `<bean>` you write becomes exactly one Spring bean. |
| `id="productRepository"` | The name this bean will be known by inside the container — other beans (and our own code) refer to it by this exact string. |
| `class="com.shopeasy.ProductRepository"` | The fully-qualified Java class Spring should instantiate for this bean, using its no-argument constructor by default. |
| `<property name="productRepository" ref="productRepository" />` | Tells the container: after creating the `productService` bean, call its `setProductRepository(...)` method, passing in the bean whose `id` is `productRepository`. |
| `name="productRepository"` (inside `<property>`) | This must match the setter method name with `set` removed and the first letter lowercased. `setProductRepository` → property name `productRepository`. This is a naming rule, not a coincidence — Spring uses **reflection** to look for a method named exactly `set` + capitalized property name. |
| `ref="productRepository"` | Points to another bean's `id` within the same XML file. This is how one bean gets wired to another — the entire mechanism that Day 1 was missing. |

This is the moment Day 1's missing piece appears: **`ref` is the wiring**. `ProductService` never mentions `ProductRepository`'s constructor anywhere in Java code anymore. The connection between the two objects now lives entirely in this XML file, completely separate from either class's source code.

### Step 4.6 — `ShopEasyApp.java` — reading XML configuration instead of the empty Java config

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

        ProductService productService = context.getBean("productService", ProductService.class);
        productService.printCatalog();
    }
}
```

**Concept box — `ClassPathXmlApplicationContext`:** this is the `ApplicationContext` implementation used specifically when your bean configuration is written in an XML file located on the classpath (which, as explained in Step 4.1, is exactly where `src/main/resources/applicationContext.xml` ends up after Maven builds the project). Compare this to Day 2's `AnnotationConfigApplicationContext`, which read a Java `@Configuration` class instead. Both are `ApplicationContext` implementations; they simply read their bean definitions from different sources.

**Concept box — `context.getBean(...)`:** this is how you retrieve a fully constructed, fully wired object from the container. `context.getBean("productService", ProductService.class)` asks the container: "give me the bean registered under the id `productService`, and I expect it to be of type `ProductService`." The container hands back the exact object it already built — you never call `new ProductService()` yourself anywhere.

Notice `ShopEasyApp.java` now contains **zero `new` keywords** for any of our own classes. That single fact is the entire solution to the problem we set up on Day 1.

---

## 5. Running It — Today's Output

```
mvn compile exec:java
```

**Expected output:**

```
Starting ShopEasy...
ProductRepository: connecting to data source...
Spring IoC container started successfully (XML-based configuration).
---- ShopEasy Catalog ----
Product{id=1, name='Wireless Mouse', price=799.0}
Product{id=2, name='Mechanical Keyboard', price=3499.0}
Product{id=3, name='USB-C Hub', price=1299.0}
```

Look closely at **where** `"ProductRepository: connecting to data source..."` appears. It prints **before** `"Spring IoC container started successfully"` — even though that println statement comes *after* the `new ClassPathXmlApplicationContext(...)` line in our code, not inside it.

**Concept box — eager singleton instantiation:** by default, Spring creates every bean it knows about the moment the container starts — not later, when you happen to call `getBean(...)`. This is why `ProductRepository`'s constructor (and its println) runs *during* the `new ClassPathXmlApplicationContext("applicationContext.xml")` call itself, before that line has even finished executing, and well before our own "container started successfully" message gets a chance to print. This is direct, visible proof that object creation is now happening inside the container, on the container's own schedule — not inside our code, on our schedule, the way it did on Day 1.

---

## 6. Proving the Fix — Solving Day 1's Original Problem, For Real

On Day 1, we tried and failed to swap in a fake repository without editing `ProductService.java`. Let's actually do it now.

### Step 6.1 — Create a fake repository

```java
// src/main/java/com/shopeasy/FakeProductRepository.java
package com.shopeasy;

import java.util.ArrayList;
import java.util.List;

public class FakeProductRepository extends ProductRepository {

    @Override
    public List<Product> findAll() {
        List<Product> products = new ArrayList<>();
        products.add(new Product(999, "TEST PRODUCT", 0.00));
        return products;
    }
}
```

(We are using inheritance here as the simplest possible way to swap behavior today; Day 4 and later classes will introduce interfaces for this same purpose, which is the more correct long-term approach — noted honestly here so you don't think this is the final "right" way to do it.)

### Step 6.2 — Change only the XML file

```xml
<bean id="productRepository" class="com.shopeasy.FakeProductRepository" />

<bean id="productService" class="com.shopeasy.ProductService">
    <property name="productRepository" ref="productRepository" />
</bean>
```

Only the `class` attribute on the first `<bean>` changed. Nothing else — not the XML wiring, not `ProductService.java`, not `ProductRepository.java` — changed at all.

### Step 6.3 — Run it again

```
mvn compile exec:java
```

**Output now:**

```
Starting ShopEasy...
ProductRepository: connecting to data source...
Spring IoC container started successfully (XML-based configuration).
---- ShopEasy Catalog ----
Product{id=999, name='TEST PRODUCT', price=0.0}
```

This is the exact scenario Day 1 declared impossible: swapping the repository implementation **without touching `ProductService`'s source code at all**. It took one attribute change in one XML file. This is the concrete payoff of everything defined on Day 1 as IoC and Dependency Injection.

Remember to change the `class` attribute back to `com.shopeasy.ProductRepository` before continuing to Day 4.

---

## 7. Today's Take-Home Exercise

1. In `applicationContext.xml`, misspell the `ref` value as `productRepositoryy` (matching no real bean id) and run the program. Read the resulting exception name and message carefully, and write down which part of the message tells you exactly what went wrong and where.
2. In `applicationContext.xml`, misspell the `<property name="...">` value as `productRepo` instead of `productRepository` and run the program. Read the resulting exception and compare it to the previous one — write down, in your own words, the difference between "a `ref` pointing to a bean that doesn't exist" and "a `property name` that doesn't match any setter."
3. Add a third bean, `<bean id="secondProductRepository" class="com.shopeasy.ProductRepository" />`, without wiring it to anything. Add a line in `ShopEasyApp` printing `context.getBeanDefinitionCount()` and confirm the number increased by exactly one compared to Day 2's baseline plus your two ShopEasy beans. This confirms that a bean exists in the container the moment it's declared, whether or not anything else references it.

---

## 8. Concept Glossary — 

| Term | Definition |
|---|---|
| XML-based configuration | Describing which objects the IoC container should create and how to wire them, declaratively, in an XML file. |
| `<beans>` | The root XML element of a Spring XML configuration file. |
| `<bean>` | An XML element declaring one object for the container to create and manage; corresponds to exactly one Spring bean. |
| `id` (on `<bean>`) | The name a bean is registered under in the container, used to refer to it from other beans or from application code. |
| `class` (on `<bean>`) | The fully-qualified class the container should instantiate for that bean. |
| `<property>` | An XML element telling the container to call a setter method on a bean after construction, injecting a value or another bean into it. |
| `ref` | An attribute used inside `<property>` (or `<constructor-arg>`, seen Day 4) that points to another bean's `id`, wiring the two beans together. |
| `ClassPathXmlApplicationContext` | The `ApplicationContext` implementation that reads bean definitions from an XML file located on the classpath. |
| `context.getBean(...)` | The method used to retrieve a fully constructed bean from the container by its id and expected type. |
| Eager singleton instantiation | Spring's default behavior of creating every declared bean immediately when the container starts, rather than waiting until it is first requested. |

---
