I am currently a Software Engineer at Tata Consultancy Services working within the BFSI sector. My day-to-day focuses working on highly scalable, asynchronous microservices using Java and Spring Boot to support massive volumes of data with guaranteed delivery. Recently, I drove a major migration to Java 21 and Spring Boot 4, which not only fixed critical security vulnerabilities but also improved our service startup time by 20% and reduced post-release defects.

&#x20;

Before TCS, I spent over two years at ITC Infotech, where I worked across the stack on core Java and MVC architecture to customize PLM tools and integrate RESTful APIs with ERP systems. I also mentored junior developers and ran root-cause analyses under strict production SLAs. Early in my career,



I interned at Allstate in Information Security, which instilled a strong foundation in compliance and secure system design.  Moving forward, I am looking to bring my experience in building low-latency, fault-tolerant backend systems to a fast-paced product environment, where I can take ownership of complex data pipelines and continue to scale robust architecture



\--------------------------Hash map ---------------ac

HashMap internally uses an array of buckets, where each bucket contains nodes storing the hash, key, value, and a reference to the next node. When we call put(), HashMap obtains the key's hashCode, performs hash spreading, and calculates the bucket index using (n - 1) \& hash, where the table size is a power of two.



**Java 21 Features:**



1. Virtual Threads - Lightweight threads managed by the JVM 
- Virtual threads primarily improve scalability and throughput for applications with many concurrent blocking I/O operations. They don't make CPU-intensive operations faster.
2. Pattern Matching for switch
-Object obj = "Hello";



switch (obj) {

&#x20;   case Integer i -> System.out.println("Integer: " + i);

&#x20;   case String s -> System.out.println("String: " + s);

&#x20;   case null -> System.out.println("null");

&#x20;   default -> System.out.println("Something else");

}





3\. Record Patterns: Deconstruct records directly in pattern matching



record Employee(String name, int age) {}



if (employee instanceof Employee(String name, int age)) {

&#x20;   System.out.println(name);

&#x20;   System.out.println(age);

}





**Migrated Spring Boot 3 → 4

Spring Batch 6 reorganized a number of APIs into more focused packages. For example:**

During our Spring Boot 3 to 4 migration, the upgrade also brought major version upgrades of Spring Framework, Spring Batch and Hibernate, so we had to address several breaking API and configuration changes.



First, I handled the \*\*Spring Batch 6 migration\*\*. Several batch APIs were moved to new packages, so I updated imports across the batch configuration and implementation classes. 

I also fixed API changes in `MultiResourceItemReader` and `FlatFileItemReader` constructors/builders while making sure the existing file-processing and mapping behavior remained unchanged.



Second, I handled \*\*Spring Boot package and infrastructure changes\*\*. `@EntityScan` moved to the new persistence package, and some of our direct references to the web application context had to be updated based on the new package structure. I also reviewed our `SpringBootServletInitializer` usage against our deployment model and removed it where it was no longer required.



Third, I addressed the \*\*Hibernate migration impact\*\*. The Hibernate upgrade changed the effective naming behavior, which affected the case of generated table names. Since our existing database schema expected a particular naming convention, I updated the Hibernate configuration in `application.yml` and replaced the incompatible custom naming strategy with the supported approach.



After making these changes, I validated the application at multiple levels—compilation, Spring context startup, batch job execution, entity scanning, database schema validation, and integration tests—to make sure the migration did not introduce functional regressions.



The main challenge was that this wasn't just a version-number upgrade; it involved identifying breaking changes across multiple underlying frameworks and making the application compatible while preserving existing business behavior.







**reduced build warnings by 70%**

One of the benefits we achieved during the Spring Boot 3 to 4 migration was a significant reduction in build-security warnings. Our SNC count went from 35 high/critical findings to just 2 remaining findings. A major contributor was the dependency upgrades that came with the Spring Boot 4 dependency management. The migration brought newer versions of transitive and direct components such as Hibernate, Apache Camel, Solace, Tomcat and Netty, which resolved many vulnerabilities and outdated-version findings without requiring individual application-code changes. I then reviewed the remaining findings separately and identified the two that still required remediation.



**Explain the architecture:**









\-------------------------- SAGA -----------------

Saga Design Pattern Overview

The Problem: Distributed Transactions

In a monolithic application, transactions are atomic (all-or-nothing). However, in microservices (like food delivery apps), the system is split into independent services (Order, Payment, Delivery), each with its own database. If a later step fails—like a delivery failure after payment is already processed—a traditional rollback isn't possible because the transaction boundary is confined to each individual service (1:51 - 4:58).



The Solution: Saga Pattern

A Saga is a sequence of local transactions where each service performs its task and publishes an event to trigger the next step. If a step fails, the Saga executes compensating transactions to revert the changes made by previous steps, ensuring data consistency (10:43 - 12:16).



Implementation Approaches

There are two primary ways to coordinate Sagas:



Choreography: Services exchange events via a message broker without a central controller (12:51 - 14:09). It is simple and avoids single points of failure but can become difficult to track or prone to cyclic dependencies (14:26 - 16:20).

Orchestration: A centralized 'orchestrator' tells each participant which operation to perform and manages the entire workflow, including failure recovery (16:22 - 18:00). It simplifies complex logic but introduces a potential single point of failure (18:29 - 20:34).



\----------------- @profiles -----------------



Key concepts covered:



* Configuration Files: You can use application.properties (or YAML) to define settings. The video demonstrates how to change the default server port using these files (1:34-3:22).
* External Configuration: By placing property files outside the JAR, developers can override internal settings without changing the application code. A fallback mechanism ensures that if a property is missing in the external file, the internal default is used (4:15-6:59).
* Spring Profiles: This is the recommended approach for managing multiple environments. By creating environment-specific files (e.g., application-dev.properties), you can activate the appropriate profile to apply specific settings (8:20-13:06). You can activate multiple profiles at once, with priority given based on the defined order (13:09-17:03).
* Dynamic Activation: To avoid hardcoding profiles, the video suggests using command-line arguments or VM options when running the application, which is a standard industry practice for deployments (18:19-20:59).
* @Profile Annotation: The video introduces the @Profile annotation, which allows developers to conditionally register beans (like specific database connections) only when certain profiles are active (21:01-23:45).
* spring.profiles.active = prod
* application-dev.properties





\---------------- @transactonal -------------------







\-----------------SOLID principles:-----------------



* Si**ngle Respons**ibility Principle (0:21–1:25): A class, component, or module should have only one reason to change, meaning it should focus on a single, clear responsibility.
* Open-Closed Principle (1:30–3:15): Software entities should be open for extension but closed for modification. The video demonstrates this using a shape-calculating example, showing that adding functionality should involve creating new classes rather than altering existing logic.
* Liskov Substitution Principle (3:16–5:08): Subtypes must be fully substitutable for their base types. The video warns against using inheritance simply for code reuse if it leads to logically incorrect behavior (like a square being improperly treated as a rectangle).
* Interface Segregation Principle (5:09–6:44): Clients should not be forced to depend on methods they do not use. It is better to create smaller, specific interfaces rather than large, general-purpose ones.
* Dependency Inversion Principle (6:45–7:53): Systems should depend on abstractions (interfaces) rather than concrete implementations. This decouples code and makes it more flexible when changing components (e.g., swapping input/output devices).

