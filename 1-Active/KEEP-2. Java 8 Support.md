# KEEP-2. Java 8 Support

**Baseline**: Kotlin 1.0

## Goals

- Use features of Java 8 to make Kotlin experience (performance, primarily) better
- Make integration in mixed Java 8/Kotlin projects smoother
 
## Outstanding issues
 
[ ] What about the new verifier?
[ ] Retrolambda compatibility
[ ] Compiling projects where `java6` and `java8` libraries are intermixed
[ ] Flesh out the requirements for type annotations
 
## Reference Material

- [JDK 8 Features](http://openjdk.java.net/projects/jdk8/features)
- [What's New in JDK 8](http://www.oracle.com/technetwork/java/javase/8-whats-new-2157071.html)

## Features Outline

* Support `Java 8` target (along with `Java 6` target)
    * compiler option
    * IDE preferences
* Language
    * Support repeatable annotations
    * Support type annotations (see [KEEP-3](../0-Proposed/KEEP-3. Type annotations.md))
* JVM Back-end
    * Use **default methods** to implement Kotlin interfaces
    * Use `invokedynamic` to implement lambdas
    * Use `MethodHandle`/`invokedynamic`
        * to implement callable references
    * Use `MethodHandle`
        * to implement efficient super-calls to functions with default parameters
    * Write parameter names to class files so that they are available to Java reflection
* Reflection
    * [x] Make use of Java's parameter reflection (parameter names etc)
* Standard Library
    * Multi-targeted stdlib
    * Exposing JDK-specific methods in Kotlin interfaces
    * Target platform definitions based on `@since`
    * Unsigned arithmetic (?)
    * kotlinx
        * Streams
        * Date-Time
        * new concurrency utilities ([JEP 155](http://openjdk.java.net/jeps/155))

## Infrastructure

**PROPOSAL**. Support a `targetJVM` option in the compiler and all the tooling. Supported values:
- `java6` - generate byte code for Java 1.6
- `java8` - generate byte code for Java 1.8 

## Language

### Repeatable annotations

**Status Quo**. In Kotlin 1.0, even if an annotation is marked `@Repeatable` is is not allowed to be actually repeated.
  
**PROPOSAL**. Allow to repeat such annotations when `targetJVM=java8`
  
