# Spring Framework 
## ShopEasy Project |

---


## 3. Setting Up Workspace

You do **not** need Spring, Maven, or any framework installed yet. All you need today is:

- Java JDK installed (JDK 17 or above recommended)
- Any code editor (VS Code, IntelliJ, or even a plain text editor)
- A terminal / command prompt

Create a folder for the course project:

```
ShopEasy/
└── day1/
    ├── Product.java
    ├── ProductRepository.java
    ├── ProductService.java
    └── ShopEasyApp.java
```

We are keeping as **plain Java files, no Maven project yet**. Maven and proper project structure get introduced in   , because   's milestone is "set up the ShopEasy Maven project skeleton" — we don't need it yet, so we don't add it yet. This is the project-based rule we will follow all course: **don't introduce a tool or concept before the milestone actually needs it.**

---

## 4. Building It — Step by Step

### Step 4.1 — The `Product` class

This represents one product in ShopEasy's catalog. It is a plain data holder — nothing Spring-related, just a normal Java class.

```java
// Product.java
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
        return "Product{id=" + id + ", name='" + name + "', price=" + price + "}";
    }
}
```

**Concept box — What is a "plain Java object"?**
A class like this, with only fields, a constructor, and getters, is often called a **POJO** (Plain Old Java Object). Definition: a POJO is a Java object that does not extend any framework class, does not implement any framework interface, and has no framework annotations. It is "just Java." Spring, later in this course, will work *with* POJOs like this one rather than forcing you to extend special base classes — that is one of Spring's core selling points, and you will see why it matters once we compare it to older frameworks.

---

### Step 4.2 — The `ProductRepository` class

This class is responsible for **getting product data from storage**. In real life this would talk to a database, but on   we fake it with an in-memory list, because we have not learned database access yet (that comes in Day 8). The point of   is not the data source — it's the *relationship between classes*.

```java
// ProductRepository.java
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

**Concept box — What is a "repository" in this context?**
Definition: a **repository**, in the layered-architecture sense used throughout enterprise Java (and throughout this course), is a class whose single job is to fetch and store data on behalf of the rest of the application. It hides *where* the data actually lives from the rest of the code. Today it hides an `ArrayList`. Later in the course it will hide a real database. The rest of the application should never need to change just because the repository's internal storage changed — that idea will come back constantly.

---

### Step 4.3 — The `ProductService` class — where the problem is created

This class contains the "business logic" — for now, just fetching and printing the catalog. Pay very close attention to **line 2 of the constructor** below. This one line is the entire point of  .

```java
// ProductService.java
import java.util.List;

public class ProductService {

    private ProductRepository productRepository;

    public ProductService() {
        // THIS is the line that creates the tight-coupling problem.
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

**Concept box — What just happened here, precisely?**
`ProductService` did not *receive* a `ProductRepository` from anywhere else. It **created its own**, by writing `new ProductRepository()` directly inside itself.

Definition: **Tight coupling** means one class directly creates, and therefore directly depends on, a specific concrete class, using the `new` keyword (or similarly hard-wired construction) inside its own code. The class doing the creating (`ProductService`) now knows the *exact* class name of the thing it depends on (`ProductRepository`), and cannot be separated from it without editing `ProductService`'s own source code.

---

### Step 4.4 — The entry point: `ShopEasyApp`

```java
// ShopEasyApp.java
public class ShopEasyApp {
    public static void main(String[] args) {
        System.out.println("Starting ShopEasy...");
        ProductService productService = new ProductService();
        productService.printCatalog();
    }
}
```

---

## 5. Running It — Today's Output

Compile and run from inside the `day1` folder:

```
javac Product.java ProductRepository.java ProductService.java ShopEasyApp.java
java ShopEasyApp
```

**Expected output on your screen:**

```
Starting ShopEasy...
ProductRepository: connecting to data source...
---- ShopEasy Catalog ----
Product{id=1, name='Wireless Mouse', price=799.0}
Product{id=2, name='Mechanical Keyboard', price=3499.0}
Product{id=3, name='USB-C Hub', price=1299.0}
```

This is a real, working program. ShopEasy technically "exists" as of   — it can list its catalog. Nothing about it is broken. But it has a design problem, and we are about to expose it deliberately.

---

## 6. Exposing the Problem (still  , still hands-on)

Right now, imagine a very ordinary, very common real-world requirement:

> "For our automated tests, we don't want `ProductService` hitting the real data source. We want to test it against a **fake** repository that returns a fixed, predictable list of products, without touching the real `ProductRepository` at all."

Try to do this **without changing `ProductService`'s source code**. Attempt it yourself for a minute before reading on.

You will find you **cannot**. Because of this single line:

```java
this.productRepository = new ProductRepository();
```

`ProductService` has hard-wired itself to the one specific class `ProductRepository`. There is no way to hand it a different implementation from the outside. The only way to test it with fake data is to go in and edit `ProductService.java` itself — which defeats the purpose of testing in isolation, and which is exactly the kind of change you don't want to make to code that's supposed to be stable.

**Concept box — Why this is a real problem, not a theoretical one**
This is not a made-up classroom problem. In real applications:

- You cannot swap a database repository for a test/fake repository without editing every class that uses `new SomeRepository()`.
- You cannot switch a payment gateway, an email sender, or a logging mechanism without touching every place that constructed the old one directly.
- Every class that uses `new` to build its own dependencies must be recompiled and re-tested any time that dependency's constructor changes, even if the *usage* of it didn't change.
- As an application grows to hundreds of classes, "who creates what" turns into a tangled web with no single place to look at or manage it.

---

## 7. The Fix — Previewed, Not Yet Built

Here is the shift in thinking that solves the problem above. Read this carefully; we build the actual code for it starting   , so today is about understanding the *idea*, not writing the fix.

**Concept box — Loose coupling**
Definition: **Loose coupling** means a class depends only on an *abstraction* (commonly a Java `interface`) of what it needs, and receives an actual implementation of that abstraction from **outside itself** — rather than constructing it internally with `new`. The class doesn't know or care which concrete class it was handed, as long as that class fulfills the contract of the interface.

If `ProductService` had instead been written to depend on an interface, say `ProductRepository` (interface) with two implementations — `JdbcProductRepository` and `FakeProductRepository` — then whoever *creates* `ProductService` could hand it either one, and `ProductService` itself would never need to change.

**Concept box — Inversion of Control (IoC)**
Definition: **Inversion of Control** is the design principle where the responsibility for creating and wiring together objects is taken *away* from the objects themselves and given to something external — a container, a factory, a framework. Normally, in plain Java, a class is "in control" of building the things it needs (as `ProductService` was, above, calling `new ProductRepository()`). IoC "inverts" that control: the class no longer builds its own dependencies; something else builds them and hands them over.

**Concept box — Dependency Injection (DI)**
Definition: **Dependency Injection** is the specific technique used to achieve Inversion of Control. Instead of a class creating its own dependency, the dependency is "injected" into it from outside — typically through a constructor parameter, a setter method, or directly into a field. The class receiving the dependency doesn't ask for it and doesn't build it; it is simply given it.

**The one-line summary to remember for   :**
Spring is, at its core, a framework that acts as the "something external" from the IoC definition above. It creates your objects for you, wires their dependencies together, and hands each object what it needs — so that your classes like `ProductService` never have to write `new ProductRepository()` again. That "something external" that does the creating and wiring is called the **IoC Container** in Spring, and it is the very first piece of Spring we will build in   .

---

## 8. Today's Take-Home Exercise (do this before   )

1. Add a fourth product to `ProductRepository.findAll()` and confirm it appears correctly when you re-run `ShopEasyApp`.
2. Deliberately try to write a second class, `FakeProductRepository`, with its own `findAll()` method that returns only one hardcoded product. Then try to make `ProductService` use `FakeProductRepository` instead of `ProductRepository` — **without editing `ProductService.java`**. Confirm for yourself, hands-on, that this is not possible with the current design. Write down, in your own words, exactly why it isn't possible. This written note is what you'll compare against the fix we build on   .
3. Be ready to explain, in one or two sentences, the difference between "tight coupling" and "loose coupling" in your own words — not copied from these notes.

---

## 9. Concept Glossary —  

| Term | Definition |
|---|---|
| POJO | A plain Java object with no framework base classes, interfaces, or annotations — "just Java." |
| Repository | A class whose job is to fetch/store data on behalf of the rest of the application, hiding where that data actually lives. |
| Tight coupling | A class directly creates (via `new`) the concrete class it depends on, hard-wiring itself to that specific implementation. |
| Loose coupling | A class depends on an abstraction (an interface) and receives its actual implementation from outside itself. |
| Inversion of Control (IoC) | The principle of moving the responsibility for creating and wiring objects out of the objects themselves and into an external container/framework. |
| Dependency Injection (DI) | The technique of supplying a class's dependencies to it from the outside (constructor, setter, or field) rather than having it construct them itself. |

---

