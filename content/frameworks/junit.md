---
name: JUnit
slug: junit
language: java
description: The standard unit testing framework for Java — annotations, assertions, parameterised tests, and a rich extension model.
website: https://junit.org/junit5/
github: junit-team/junit5
year: 1997
pricing: free
open_source: true
license: EPL-2.0
tool_type: testing
tags: [testing, java, unit-testing, tdd, annotations, jupiter]
related_frameworks: [mockito, testng]
features:
  - "`@Test`, `@BeforeEach`, `@AfterEach`, `@BeforeAll`, `@AfterAll` lifecycle hooks"
  - "`@ParameterizedTest` with `@ValueSource`, `@CsvSource`, `@MethodSource`"
  - "Extension model via `@ExtendWith` — Spring, Mockito, Testcontainers all use this"
  - "Nested test classes with `@Nested` for grouped test suites"
  - "Conditional test execution — `@DisabledOnOs`, `@EnabledIfSystemProperty`"
  - "Dynamic tests via `DynamicTest.dynamicTest()`"
  - "AssertJ, Hamcrest, and Truth assertion libraries integrate seamlessly"
  - "Maven Surefire and Gradle Test tasks run JUnit 5 natively"
install:
  maven: "<dependency>\n  <groupId>org.junit.jupiter</groupId>\n  <artifactId>junit-jupiter</artifactId>\n  <scope>test</scope>\n</dependency>"
  gradle: "testImplementation(\"org.junit.jupiter:junit-jupiter\")"
---

JUnit 5 (Jupiter) redesigned the framework around Java 8 features — lambdas, extensions, and nested test classes. Its `@Test`, `@BeforeEach`, `@ParameterizedTest`, and `@ExtendWith` annotations form the foundation of Java testing. Mockito, Spring Boot Test, and virtually every Java testing tool integrates with JUnit.

## Quick start

```xml
<!-- pom.xml -->
<dependency>
  <groupId>org.junit.jupiter</groupId>
  <artifactId>junit-jupiter</artifactId>
  <version>5.10.x</version>
  <scope>test</scope>
</dependency>
```

```java
// src/test/java/com/example/CalculatorTest.java
import org.junit.jupiter.api.*;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.CsvSource;
import static org.junit.jupiter.api.Assertions.*;

class CalculatorTest {

    private Calculator calc;

    @BeforeEach
    void setUp() {
        calc = new Calculator();
    }

    @Test
    void addsTwoNumbers() {
        assertEquals(5, calc.add(2, 3));
    }

    @Test
    void throwsOnDivisionByZero() {
        assertThrows(ArithmeticException.class, () -> calc.divide(10, 0));
    }

    @ParameterizedTest
    @CsvSource({"1, 2, 3", "0, 0, 0", "-1, 1, 0"})
    void addWithMultipleInputs(int a, int b, int expected) {
        assertEquals(expected, calc.add(a, b));
    }

    @Nested
    class WhenDividing {
        @Test
        void returnsQuotient() {
            assertEquals(2, calc.divide(10, 5));
        }
    }
}
```

## When to use

JUnit is the foundational testing framework for any Java project. It's the standard that every Java developer knows and every Java testing tool integrates with. Use JUnit for unit tests, and extend it with Mockito (mocking), AssertJ (fluent assertions), and Testcontainers (real databases in tests). For Spring Boot applications, `@SpringBootTest` uses JUnit 5's extension model automatically.
