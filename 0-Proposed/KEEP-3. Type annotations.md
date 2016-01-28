# KEEP-3. Type annotations

**Baseline**: Kotlin 1.0
 
## Goal
 
- Better support for type annotations in Kotlin

## Outstanding Issues
  
 - [ ] How else are type annotations used in Kotlin 1.0?  
  
## Synopsis
  
Currently Kotlin makes little to no use of type annotations. 
 
Current usages:

 - `@ExtensionFunctionType` annotation marks function types that admit lambdas with receiver parameters

**PROPOSAL**:
 
 - work out semantics for type annotations (supertypes, type arguments, value parameter types, inference, common supertype)
 - write type annotations to (Java 1.8) class files
 - support additional checker infrastructure and compiler API to work with type annotations
 
