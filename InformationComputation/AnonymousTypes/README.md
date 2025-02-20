# 1. Anonymous Types

## Table of content  <!-- omit in toc -->

- [1. Anonymous Types](#1-anonymous-types)
  - [1.1. Introduction](#11-introduction)
  - [1.2. What is the problem?](#12-what-is-the-problem)
    - [1.2.1. Main bullets](#121-main-bullets)
    - [1.2.2. Preface](#122-preface)
    - [1.2.3. Normalized Coding System](#123-normalized-coding-system)
    - [1.2.4. Custom Coding System](#124-custom-coding-system)
    - [1.2.5. Type Definition](#125-type-definition)
    - [1.2.6. Data Portability](#126-data-portability)
    - [1.2.7. Dynamic Types](#127-dynamic-types)
    - [1.2.8. Anonymous Types](#128-anonymous-types)
  - [1.3. Strong Typing](#13-strong-typing)
    - [1.3.1. Type Embedded Operations (AnonymousTypesUnitTest.DivisionTest)](#131-type-embedded-operations-anonymoustypesunittestdivisiontest)
    - [1.3.2. object Type(`ObjectTest`)](#132-object-typeobjecttest)
    - [1.3.3. `var` Keyword(VARTest)](#133-var-keywordvartest)
      - [1.3.3.1. Introduction](#1331-introduction)
      - [1.3.3.2. Conclusion](#1332-conclusion)
  - [1.4. Loosely Typing(`DynamicTest`)](#14-loosely-typingdynamictest)
    - [1.4.1. Introduction](#141-introduction)
    - [1.4.2. DynamicTest Explanation](#142-dynamictest-explanation)
  - [1.5. Anonymous Type (AnonymousTypesTest)](#15-anonymous-type-anonymoustypestest)
    - [1.5.1. Introduction to Examples](#151-introduction-to-examples)
    - [1.5.2. Definition](#152-definition)
    - [1.5.3. Type Consistency Check](#153-type-consistency-check)
    - [1.5.4. Reference Type](#154-reference-type)
    - [1.5.5. Compatibility of Anonymous Types](#155-compatibility-of-anonymous-types)
  - [1.6. Conclusion](#16-conclusion)
  - [1.7. That's all for now](#17-thats-all-for-now)

## 1.1. Introduction

Let me recall that the CSharp language is strongly typed programming language like many other ones. This means that it encourages and even forces designers to use types for internal program consistency checking. The rules for checking the compatibility of types, apart from the rules for checking the syntax correctness of the program as one whole, are one of the fundamental mechanisms for validation the program content at design time. Without any doubt, this strong typing approach increases the probability of program correctness in the context of internal data processing. If we want to pull or push data from/to external resources not directly managed by the selected language runtime environment we must answer the question of what type they are. How to harmonize these external data types with the types defined in the program. In general, we can apply type definitions conversion, evaluate types at run time, or apply data correlation. Does it sound strange ? I am pretty sure that the answer is yes. The purpose of this lesson is to learn more about it. Especially, let's talk about how the concept of anonymous type can help with this. I will try also to recall fundamentals related to dynamic type that can be applied to evaluate type at run time. The type conversion will be the subject of independent episodes embedded in separate courses so in this lesson I will only mention about this mechanism.

## 1.2. What is the problem?

### 1.2.1. Main bullets

- normalized coding systems
- custom coding systems
- static types
- data portability
- dynamic types
- anonymous types

### 1.2.2. Preface

As usual let's start defining main objectives of this lesson by defining the topics we may encounter related to type definitions.

### 1.2.3. Normalized Coding System

Again, let's recall the coding system concept. When defining coding systems, to identify them usually we use common names. For example, two's complement, natural binary, natural decimal, floating-point, and so on. Here, however, it should be emphasized that the rules for selected codes, for example, two's complement, natural binary, and natural decimal, are de facto standards. Others like the floating point are international standards. For numeric codes, there are also known operations implementing algorithms applicable to the information they represent, for example, addition, subtraction, multiplication, and many others. We shall expect that all of them are available as standard types or build-in types whether the programing language is strongly typed or not. These kinds of coding systems are a foundation for types like int, float, decimal, and so on.

### 1.2.4. Custom Coding System

It is obvious that it could also happen that we have to define custom coding systems using an informal description and providing a description in the natural language. There are no commonly accepted validity rules defined for it. In this case, usually, the codes have no common name at all. In the coding system definition, we may use terms and symbols used in mathematics, such as set designations, notation of functions, and similar like a free text. We already know that each code consists of three parts. First is an alphabet, which is a set of characters. To yield a human-readable string usually, it is derived from the Latin alphabet in this part of the world. To be useful for a computer it must be binary. It means that its alphabet has to contain any but only two characters. The second part of any coding system is syntax - a set of rules describing how to concatenate characters into valid strings. And third is semantics, which determines the relationship between the compliant with the syntax strings of characters and their meaning, namely information. Based on this coding system we have to define a type in compliance with the selected programming language. Applying modern programming language allows us to define the coding system indirectly as a result of the type definition. It is a typical chicken/egg problem - a situation in which it is impossible to say which of two things - type or coding system - existed first and which caused the other one. Especially, in case we must deal with external data always we have to consider the coexistence of a type and codding system.

### 1.2.5. Type Definition

Conversely, supposing that the coding system and type play a similar role, always we must deal with a type even if the data in concern resides in an external realm. On the other hand, the type is defined as the text that is part of a program, so it must have a formal definition that is subject to validation in the context of the syntax and semantics of the selected programming language. Any type in the program body is represented by a unique identifier that indicates the type declaration. The association of a type definition to its identifier is specified in the type declaration. Let me repeat that the type defines a set of values, and implicitly a set of information that is represented by a type and a set of operations that can be applied to the values belonging to that type. A type declaration name is often used to informally define semantic rules for that type, thus determining the meaning of each value belonging to the type. Previously we used the identifier CoordinatesClass to identify the class representing coordinates on an Cartesian system.  It is example that the name could be meaningfully for better understanding the information represented by instances of this type.

### 1.2.6. Data Portability

External data resides outside the program, precisely speaking the data is managed outside the process hosting the program, namely archived, transmitted, and visualized with the use of various resources, such as file systems, database systems, computer networks, display controlled by computers, and other devices. Usually, the prevailing requirement for external data is portability. Data portability is the ability to use the same information by many programs created in different programming languages and executed on independent computers. In this case, we must take into account the inability to directly use linguistic constructs of type definitions compliant with the selected language. You can only use widely accepted standards, such as XML, JSON, YAML, or even database schemas to name only the most popular. If the type has an external definition, such as an XML schema, then we can convert that type definition and generate the equivalent type in the selected programming language. These issues are beyond the scope of this course and are of concern to us during the course on external data processing, but the examples of translations like this are already in the TP repository in the ExDataManagement solution.  Check out them to get more.

### 1.2.7. Dynamic Types

So what concept we should apply to the external data managed outside of the selected programming language realm? There are only two correct answers. If we must engage a custom coding system for external data we must infer type at design time or alternatively evaluate type at run time. Especially when we have to deal with external data, sometimes the definition of a type at design time is impractical or even impossible. In this scenario, we must postpone any consideration regarding the data type and evaluate it at the run time. Of course it leads us to the weakly typed approach.

### 1.2.8. Anonymous Types

Supposing that the coding system and type play a similar role, always we must deal with a type even if the data in concern resides in an external realm. So what concept we should apply to the external data managed outside of the selected programming language realm? And here we have to come back to the concept of the coding system referred to at the very beginning. To follow the rules of a strongly typed approach, if there exists a formal external data type definition we could convert the definition expressed in a "foreign" language to obtain a definition expressed using a selected programming language. If this scenario is not applicable we must apply the correlation of types. In this process, the name of the external type doesn't exist at all. Hence, there is an idea to harmonize the external realm of data with the program employing types that has no name and no dedicated behavioral part, I mean there are no specialized operations defined. Of course, each type must have some operations, unlike a coding system. In this case, we can consider also types that represent a typical data structure. For example, one that takes the form of a sequence of key-value pairs. This lesson is about these types. Because the type doesn't have a name we call them anonymous. It should be emphasized here that anonymous types are also useful in other scenarios, I mean not only to facilitate interaction with the program's surrounding environment. Let's get started and move on to examples that illustrate the syntax and semantic rules of the language regarding anonymous types. I will pay special attention to explaining how these kinds of types are defined.

## 1.3. Strong Typing

### 1.3.1. Type Embedded Operations (AnonymousTypesUnitTest.DivisionTest)

However, in the beginning, we must get back to the previous example. In `TypesCompatibility.DivisionTest` test method, we are revisiting an example we know from one of the previous lessons. In this example, we are dividing the integer five by the integer two and the result is the integer two. Next, we assign the constant five to the variable of type `float`. This causes the expression result on the right-hand assigned to the second `float` is using the division operation provided for the floating-point representations, I mean defined by the type `float` type. Therefore, here the result of this action is already as expected, that is, we get the value of two and a half. If we changed the type of the first variable to `int`, in this case, the program is still correct, but the assertion is not fulfilled at run time, i.e. the error will appear while testing the program. I will run this test again. The reason for this is that the variable and the constant both are of the `int` type and the division operation follows the definition embedded in that type. And here we see that we get the number two as a result of this division, and we expect the number two and a half. So let's go back to the previous type `float` when the result of this test is correct. We can run this test again. By this example, we have proved that the operation behavior depends on the type of operands. Therefore, we can state that the type is a set of values and set of operations provided that different behavior of operations means that the operations are different in spite of the same name or the same operation designation. That's all as a reminder of the type definition, but let's go further.

### 1.3.2. object Type(`ObjectTest`)

We will try to do the same with a variable of type `object`. The example you can find in the ObjectTest method. Recall that `object` is the type from which all other types inherit. The type `object` is the base type for all types, and for this variable, it is possible to assign a value that is of any type, since all types derive from the `object` type. In this case, the value is of type `float`. Since this is a `float` value, let's try again the division operation. As we can see, the compiler signals that this operation is not allowed, because the division operation has not been defined for the `object` type. The paradox is that the value of this variable is still of type `float`. It is only apparently inconsistent because at design time the correctness of the code does not depend on the type of values assigned to the variable, but is evaluated based only on the declared variable type. Let me stress, at design time we don't have values. This is an important observation because the type-based consistency assessment can be used at the design time, while the value-based type consistency assessment can only be applied at run time. It is a very simple example, but you can imagine that many years could pass between the program being created and its execution. Let me quote the old saying of programmers, once the author and God did know how this program works, today only God knows.

### 1.3.3. `var` Keyword(VARTest)

#### 1.3.3.1. Introduction

To evaluate the meaning and scope of the `var` keyword usage, let's go back to the code we know. The example is located as a block of the `VARTest` method. And we will continue to perform the dividing operation. Here we have an `int` variable that is to be divided by two. But the interesting thing about this language is that we can also use the `var` keyword instead of a type identifier. The question is what is the difference between both cases, namely using the explicit identifier of a selected type, and alternatively replacing this identifier with the `var` keyword? In this case, the `var` keyword causes the variable prefixed with `var` can be assigned any value just like in the case of the `object` type. However, unlike in the case of object type, we cannot change the variable type anymore. The variable type is inferred from the type of expression and will be unchangeable after this first assignment. Attempting to assign a string to a variable prefixed by `var` results in a compiler error saying that the types are not compatible. So the type of this variable is `int`.

#### 1.3.3.2. Conclusion

Anyway, this program snippet still behaves similarly to the previous one, i.e. dividing the value five by two for integers returns two. What does it mean? This means that the type of the variable has not changed. It's still `int`, so the keyword `var` actually only replaces the type identifier  `int` for compilation purposes only. In other words, it doesn't have a special meaning and special role except for simplification of the type determining. It only means that we may avoid explicitly stating the variable type in favor of the compiler, which infers the type from the context. On the other hand, it also means that the compiler overtakes our responsibility to do it. From the previous example, we know that type selection has a primary role in program behavior. From this point of view, we are partially losing control by relaxing the rules of strongly typed language but still have full responsibility related to the program behavior, I mean program correctness. My point is that the `var` keyword is often overused. Using anonymous types is the only use case where it is really needed. As the name says for anonymous types the type identifier - the name - is not explicitly provided, therefore, to keep the syntax intact the type identifier has to be replaced by the var keyword. We will get back to the anonymous types very soon. Anyway using the `var` keyword instead of the type identifier - provided it exists - is only your personal decision. But remember it means less control and the same responsibility.

## 1.4. Loosely Typing(`DynamicTest`)

### 1.4.1. Introduction

Especially when we have to deal with external data, sometimes the definition of a type at design time is impractical or even impossible. In this scenario, we must postpone any consideration regarding type validation up to the run time. This case is the subject of an examination in the `DynamicTest` method where we are using the dynamic keyword instead of the type identifier. What does dynamic mean? First, using the dynamic keyword means that we are recommending the compiler stop compliance type-checking at the design time. If the code is not valid, errors are caught at run time. Compliance of the type is conducted when the program is being executed and also under certain assumptions. The runtime can vary, so its response to these situations is not always the same. But as a rule of thumb, we can assume that the environment behavior is smart enough so as not to cause execution errors, if possible. However, the error does not escape notice indefinitely. It is caught at run time and causes a run-time exception.

### 1.4.2. DynamicTest Explanation

An example is here. Here we can see that we have assigned a value of type `float` to the variable `dynamic`, that is, the number 5, and - it is not surprising - the type of the variable is `float`. The next line adds to the previous content of variable number one. In this line, the assertion indicates that the result is always 6, so the preceding addition operation is successfully performed and the result is as expected. But in the next line of code, we can see that the type of this variable can change, because we have assigned a value of the string type to it. We can see that the value of this variable is equal to "string", so the type of the variable now should be considered the string. The possibility to change the variable type proves that the `dynamic` is only a keyword but not should be recognized as a variable type. In other words, it is only a type identifier replacement hiding the current type of the variable. Here we try to add but generally for a string and a numerical value such an operation does not make sense. But what does the compiler do? The compiler converts a double value to a string value and performs plus operations for the string type, which in this case is defined and means text concatenation, joining two texts together. Here we have the result. An interesting point is that in this example the runtime converts a number to a string. Conversion of the float value to string is expected here. The conversion operation depends on the culture selected for the thread executing this test. Before conversion to string a well-defined culture must be set up to guarantee that the result doesn't depend on the computer settings but the result always depends on the culture setting of the thread executing this conversion. Without an explicit setting, the thread culture is inherited from the computer setting. The result is concatenated with the current value of the variable.

## 1.5. Anonymous Type (AnonymousTypesTest)

### 1.5.1. Introduction to Examples

Now let's move on to discussing this kind of type. I will examine this kind of type based on examples gathered in the AnonymousTypes class.

### 1.5.2. Definition

In this line of the code, we use the anonymous type to define the set of allowed values ​​for the variable `anonymousVariable`. The most important feature of this approach is that the entire set of values belonging to a type is defined based on one selected value. This type is actually defined by a constant which is a right-hand operand of the assigning sign. The notation of this constant has a strictly defined syntax. The word `var` must be used as a variable prefix instead of a type name because a type defined this way cannot have a name - hence we call it an anonymous type. Based on this syntax we can conclude that the values ​​belonging to this set - to the defined this way type - are complex because they have component values. In our example, we have two parts a number and a string. Identifiers are recognized as the read-only variables. Therefore, we can simply state that in this statement a complex constant is assigned to the variable `anonymousVariable`. Such an indirect way of defining a type also makes it impossible to define a set of own, dedicated operations that can be applied to process values belonging to this type. For anonymous types defined this way, several standard operations have been defined. Standard operations are those whose behavior is determined by the programming language, not the software developer. They include the selector operation, which allows to access the selected component value in the complex value defined this way. Examples of this operation can be found in the next two lines of the analyzed example, where the values of embedded components are checked.

### 1.5.3. Type Consistency Check

Here, it is worth asking if anonymous types are still protected by the type compatibility validation mechanism. Because the type is anonymous, it only means that its name is not visible to a developer of the program. Contrary, the compiler can create such a name for its own purposes. To enable type compatibility checking, we need to know what values ​​belong to the type. In the following lines of the example, we can see that trying to assign a new value to the `Amount` field is rejected (in this case "double ") with the one we previously used, when we declared the variable for the first time, and then it was "int", this causes the type compatibility error. Apparently, it is in the next line, when we try to change the order of the fields. Also, in this case, an error is signaled and this constant will not be treated as a value of a compatible type that was created when this variable is declared. The next two lines show that we cannot change the values ​​of the components.

### 1.5.4. Reference Type

Additionally, this line proves that it is a reference type because you can substitute null as a value for variables of this type, meaning that there is no value. But trying to substitute null for a new variable prefixed with the keyword `var`, in this case, newAnonymousVariable fails because the compiler does not have enough information to infer the variable type. In other words, we can say that the value to be assigned to an anonymous variable must have the appropriate syntax, where the keyword `new` must appear, and between the curly brackets a sequence of identifiers, equal signs, and expressions that determine the values assigned to each member. A detailed description of the schema is in the user manual of this language.

### 1.5.5. Compatibility of Anonymous Types

The next method shows that we can define the same anonymous types even though the anonymous types do not have a name. The compiler for each anonymous type creates its identifier, which is not available to us but is available to the compiler. Here we have two variables that have a very similar definition that is they have the same components and we assigned some values for them. The result type of value is determined by the types of member values, identifiers of the members, and their order. And then we can check that indeed these two variables are of the same type and we can, for example, assign one to the other one.

## 1.6. Conclusion

Anonymous types are characterized by the fact that when defining a new anonymous type, we cannot define specialized operations for it that can be applied to process values of this type. Another feature of this kind of type is that it defines a sequence of key-value pairs. These two characteristics indicate that this type is particularly well suited to represent external data. In other words, external data has no type in the sense we use in the programming language. As a rule of thumb, for external data, operations are performed outside of the process hosting the programming realm, so they cannot be used locally. If this approach is not sufficient and dedicated operations are needed, then instead of data correlation, we should use type conversions, but this is an independent story.

## 1.7. That's all for now

That's all about anonymous types. Again, let me stress this concept is mainly useful when talking about external data where the type concept is applicable only indirectly, and where the types don't have names. Unfortunately, external data processing is covered by an independent classes. Thank you for your time.
