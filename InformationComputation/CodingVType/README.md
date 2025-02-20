# 1. Coding System versus Type

## Table of content <!-- omit in toc -->

- [1. Coding System versus Type](#1-coding-system-versus-type)
  - [1.1. Preface](#11-preface)
  - [1.2. What's the problem?](#12-whats-the-problem)
    - [1.2.1. Binary Coding System is Required](#121-binary-coding-system-is-required)
    - [1.2.2. Abstract Thinking is Required](#122-abstract-thinking-is-required)
  - [1.3. Type as implementation of the coding system](#13-type-as-implementation-of-the-coding-system)
  - [1.4. Information Representation Portability](#14-information-representation-portability)
  - [1.5. Type concept](#15-type-concept)
  - [1.6. How to deal with the custom definition of the type](#16-how-to-deal-with-the-custom-definition-of-the-type)
  - [1.7. Loosely versus strongly typed approaches](#17-loosely-versus-strongly-typed-approaches)
  - [1.8. Opening the example](#18-opening-the-example)
  - [1.9. Variable type](#19-variable-type)
  - [1.10. Type Definition](#110-type-definition)
  - [1.11. Weakly Typed Languages](#111-weakly-typed-languages)
  - [1.12. Assignment to Float](#112-assignment-to-float)
  - [1.13. Types Compatibilities](#113-types-compatibilities)
  - [1.14. Type Conversion](#114-type-conversion)
  - [1.15. Types Compatibility Conclusion](#115-types-compatibility-conclusion)
  - [1.16. UT Fundamentals](#116-ut-fundamentals)
  - [1.17. Operations behavior](#117-operations-behavior)
  - [1.18. Type as a Set of Values](#118-type-as-a-set-of-values)
  - [1.19. Type as a set operations](#119-type-as-a-set-operations)
  - [1.20. Summary](#120-summary)

## 1.1. Preface

I would like to invite you to participate in the next lesson of the course titled Information Computation. Previously we learned that abstract information may be represented using a computer-aware stream of signs using a coding system. Finally, it must be a binary representation. The main goal of this lesson is to learn how the coding system we used to represent information - that is abstraction - may be replaced by the type notion that is well known and widely accepted concept for modern programming languages. The types enable us to focus on the domain of values but not low-level values representation.

## 1.2. What's the problem?

### 1.2.1. Binary Coding System is Required

From the previous lessons, we know that we must overcome the impossibility of information computation because the computation requires a device, information is an abstract notion, and physical devices cannot deal directly with abstraction. To do it we must consider using a binary coding system to represent the information for the computation purpose; in other words to implement this abstraction. The implementation must be binary because now the computer is and in the predictable future will be a binary machine. Unfortunately, using of the binary coding system is impractical or even impossible considering the natural human environment. In trying to find a replacement for the binary coding system we must also keep in mind that the information representation has to be portable, I mean should not be tightly coupled with the computation platform.

### 1.2.2. Abstract Thinking is Required

During this lesson, I will propose the type concept as a practical implementation of the binary coding system. It makes a relief but on the other hand usually implementation details of this concept are hidden, so again we as software designers and architects must deal with something abstract. It requires abstract thinking skills but I will try to point out some common for all implementations features to improve your understanding related to the effective and practical usage of this concept. I will pay special attention to skills related to defining custom types.

## 1.3. Type as implementation of the coding system

In some cases, using the coding system concept that refers directly to the alphabet, syntax, and semantics has a few significant drawbacks. First, I should recall that you deal with the binary alphabet in the case of computers because today the computer is always a binary machine.  Additionally, users of computers are not willing to deal with the binary alphabet - it is not a natural human environment. If it is so obvious we may just simply forget about it. Neglecting the existence of the alphabet causes that we are unable to define syntax rules because there are no characters to be used after the disappearance of the alphabet. Of course, a continuation of this debate in this direction leads us to a dead end because we cannot neglect the existence of the data and the rules we apply to associate meaning to that data. In other words without syntax, the semantics rules cannot be defined as well. The only way to relieve this problem is the assumption that alphabet and syntax exist but are hidden as implementation details. Hence, we must deal with the domain of custom values alone. Anyway, this approach is a foundation to introduce the type concept. In concluding this analysis, further, we should recognize the type as an implementation of the coding system.

## 1.4. Information Representation Portability

Binary data is not our natural environment. I mean part of our native language, culture, and knowledge we are using on a daily basis. Hence, the possibility to use the type concept instead of a binary coding system could make our life easier because this allows being unaware of unimportant details.  Usually, we are just not interested in the internal representation of the information. We are not directly coupled with the syntax and the alphabet used by a computer. We know that the alphabet is binary because we are engaging a computer that is a binary machine. Additionally by replacing binary details with something else we can improve portability provided that the binary language replacement is not tightly coupled with the computer. For example, consider the length of the computer binary word that is addressable. I mean a number of bits that comprise the word.

## 1.5. Type concept

So it becomes obvious that the binary coding system used to represent information as data must be replaced by smoothing else based on the typical Latin alphabet. In all of the cases, I know the concept of the type is engaged in this respect. This approach is especially useful in cases when we can use one of the existing well-known types. Hence modern software development environments adopt the type concept somehow and usually provide a vast variety of ready-to-use types. Unfortunately, usually, you need the computation of custom information that needs dedicated types. Because type is an implementation of a coding system it means that almost always you will need to design custom coding systems indirectly using types. I believe that you will find very useful any skills to help accomplish this goal in your professional carrier. My point is that the entry point to accomplish this is a well understanding of the background rules.

## 1.6. How to deal with the custom definition of the type

Unfortunately, this approach also has drawbacks. Hiding implementation details of the binary coding system means that we must apply abstract thinking and be aware when the implicit syntax is an unimportant detail. Withdrawing the necessity to deal with the binary coding systems to describe information representation in the computer realm also are very helpful because the same approach can be applied to define custom types. In general, new types may be defined from scratch or derived from existing ones inheriting features of the base types. There will be a dedicated lesson on this topic so I skip it for now.

## 1.7. Loosely versus strongly typed approaches

Anyway, it is time to return to programming in practice. Understanding type concept fundamentals is vital for your practical achievements provided that we will be able to embed this knowledge in a computer realm using a modern development environment. There are many aspects related to types but only one is critical in the context of the practical approach to programming - it is a reasonable justification for the necessity to use types at all. There is a long-lasting and controversial discussion related to loosely typed and strongly typed approaches to programming. Strongly typed programming wants types specified explicitly. On the contrary, in loosely typed programming we don’t have to explicitly specify types. In this case, the development environment is taking over and the type is inferred by the environment. Coding systems and as a result types must be defined in all cases as a result of the fact that **computers always process bitstream but not bitstreams meaning**. Therefore impossibility of defining explicitly type could be recognized as losing control over the implementation of the information computation process by the programmer.

## 1.8. Opening the example

Check out the code from the repository if you want to follow me. The examples I am going to use you can find in the mpostol/TP GitHub repository. It must be cloned on your computer in advance. Instruction on how to do it you can find in the independent course called `programming in practice executive summary`. I did it already and the code is located in the local folder TP on my computer. Now I can open the folder with Visual Studio using the context menu. The screenshot could be different depending on the operating system version you are using. After opening, the solution tab of the Visual Studio, we have all available solutions collected here. If needed switch to this view using this icon. For this course, the most appropriate examples are in the `InformationComputation` solution.  Double-clicking on the entry opens the solution. The code that I will start with is in the project `10-CodingVType` in the file `TypesCompatibility`class. To follow me just save your progress as you go and come back to complete the course at a later date and open the example in a separate window.

## 1.9. Variable type

In the computer realm, the place where the data - I mean a value - is stored we call a variable. Here in this program, we have a variable declaration. To re-establish the context from the previous lesson assume that our goal is to assign representations of the number four to this variable. In other words, the value is a representation of the number four. In all languages I know, the variable is always declared as an identifier preceded optionally by a type declaration. For the  CSharp, it is also true.  If present **the type declaration defines a set of allowed values** that can be stored in that variable, that can be represented by that variable, and that can be assigned to that variable. Reversing, if a value is outside of the current set of allowed values, the assignment is considered an error for strongly typed languages.  The main challenge is that it could be distinguished and signaled at design time. It is worth stressing that in this case, the designer has full control of the variable meaning by controlling the set of allowed values.

## 1.10. Type Definition

Let's start our further investigation of the type meaning from this example where we use int as the variable type here. Using `F12` or the go-to definition context menu entry we may open the definition. The first thing that requires explanation is that we have got the definition of the type `Int32` but not a type called int as it's in our code. To avoid a long discussion, related to the programming language used and get directly to the point, you must assume that the int identifier is just an alias of the `Int32`. Both identifiers mean the same. The first important observation is that the type definition uses a construct called `struct`. Let me only mention that the type definition was recreated by the environment using a reflection mechanism. The reflection mechanism is outside of this course scope, hence, I propose to reuse the same approach to implement the roman coding system using the type concept and use this definition for further investigation.

## 1.11. Weakly Typed Languages

Alternatively, for weakly typed languages the type of variable is changed silently as a result because in this case variables are less tightly coupled to a specific type. In general, changing the variable type must lead to the meaning change of stored value. It is the first consequence of applying a weakly typed approach. In this case, the type change occurs as a result of the execution of an assignment operation of a new value to the variable. Execution of an operation means that it must happen at run time but not at design time. Postponing the type specification up to the run time is called dynamic programming. The most important information is that if something goes wrong with that you will know about it during run-time because it is a possible run-time problem so years could pass after this piece of code has been created. During this course, I am focussing on the design time software development therefore let me skip the discussion related to the weekly typed languages.

## 1.12. Assignment to Float

Similarly in the second line of the example, we have a variable to that we are assigning a value representing the number four. As we can see in the first and second lines, the notation is slightly different, the syntax of the constant is different and the type of the second variable is also different. Now let's try to consider for a moment what the word allowed means in the type definition. We say that a type defines a set of valid values.

## 1.13. Types Compatibilities

Let's un-comment of the next line of code, in which we try to assign the value representing the number four for the variable defined in the first line. This time the constant has syntax used previously in the second line. At this point, we have an error signaled by the read underscore line, which means that this assignment is not valid and we must investigate why it is incorrect. Well, from the use of the word allowed, it follows that the value on the right-hand side is not allowed. Well, the value is number four and undoubtedly belongs to the set of allowed values declared for the first variable, so the question is how to explain this error. Well, it can be explained in such a way that, on the right side of the equal sign, we see a constant here, but the compiler sees a construct, which we call an expression. An expression is a combination of operands (variables, literals, method calls) and operators that can be evaluated to a single value. There are two characteristic features of each expression in all the languages I know. First, each expression evaluates to a single value, and second the evaluated value is always of a well-defined type at design time for strongly typed languages. In this case, the syntax of this constant will determine that the expression is of type float. If the value is of type float it could happen that the calculated value doesn't belong to the set specified by the long type - the variable type. Hence, we say that a type is a set of allowed values. In this case, the values ​​may be not allowed and therefore may be outside of this set.

## 1.14. Type Conversion

For strongly typed languages I presented the types as a disjoint set of values. Two sets are disjoint if they have no element in common. It is easy to apply this rule if it is obvious, for example for int and boolean. Things are more complicated in the case it is not true. We will investigate this topic using CSharp but the discussion could be also applied to practically all languages.

I'll go straight to the point. Using background knowledge related to sets we have to investigate the next two typical cases:

- there is no empty intersection between sets
- one set is a subset of another one

A good example is the relationship between the float and int types. Both are used to represent numbers. Please note that not all values belonging to the float also belong to the int, but conversely all values of the int type are also elements of the set defined by the float. Hence at design time, we can assure that if the expected result is of the int type we can always assign it to the float variable because at run-time it is impossible that the calculated int value is not a member of the set defined by the float type. Conversely, if the expected value is of type float it could happen that the result will not be an element of int so in this case, it could be impossible to assign the calculated value to the int variable at run time. Because it depends on the concrete value evaluated as a result of the execution of the program we must assume that it is impossible at all, I mean without exceptions.

## 1.15. Types Compatibility Conclusion

Let me recall the rule we learned previously - **computers always operate on bitstreams but not on the bitstreams meaning**. Unfortunately, we often forget about this rule and cannot accept situations where we see that number four is not equal to the number four. It is the wrong approach but sometimes, it is easier to conclude that the computer takes over thinking.

## 1.16. UT Fundamentals

Strongly typed languages support a static analysis of the program correctness thanks to types definitions as a set of allowed values. If it is possible that the evaluated value could not be a member of this set it is considered an error and signaled at design time. The program is created to be executed by a computer. It requires that the static analysis must be harmonized with the dynamic judgment of the program behavior. By design, I propose to use the unit test to have an executable example to analyze the code features for education purposes but not test the correctness of the program. Again, you can check out the course `programming in practice executive summary` to get more about this approach. Following this idea more examples related to the type concept and the impact of this concept on the program behavior you can find in the `15-CodingVTypeTest`project.

## 1.17. Operations behavior

As I said, the next examples are in the unit test project called OperationsCompatibilityTest. In this example, we will focus on the code behavior but not its pattern. Here we have a variable of type int. For this discussion, it is not important to know the allowed set of values that can be assigned to this variable. We can see that number 5 is OK, it meets this requirement and the compiler doesn't complain. It means that the number five is allowed. In the next line, we are assigning to the same variable the previous value that is divided by 2.  Now, on the right side of the equal sign, we have an expression. The type evaluated at design time is compatible so we don't have any errors. Therefore, the next line checks the final result and compares it to number 2. After running the test we can prove that actually, the result is equal to 2, which is in contrast with the knowledge we learn in the background school. Again investigation is required because it looks like a fundamental inconsistency. In the next few lines, we do the same but now the variable type is float. The result is as expected in the context of our background knowledge. The conclusion is that it could happen only, and only because the division operation behavior depends on the type selection.

## 1.18. Type as a Set of Values

Now is a perfect time to answer the question of what is the type notion. From the first example related to assigning a value representing a number to the variable, we learn that type should be recognized as a set of allowed values. As the result, we can define the types compatibility concept and protect it at design time against the possibility to compute values not belonging to the same set of values. In this context, the type is the definition that is responsible to determine the bitstream meaning. Again, the computers operate on bitstreams but the type is responsible that the bitstreams meaning is determined by the same relationship, by the same rules. If we hover the cursor over this type identifier, we can see that the full name, the full identifier in this case is `System.Int32`. The identifier must be, as the name suggests, unique, it should be globally unique. For the sake of simplicity, let's skip the discussion on the uniqueness of identifiers. Rather, we are interested in the fact that this identifier will unambiguously indicate the definition. We move the view scope to the type definition by using the alt + F12 key, and we can see that this identifier defines a language construct, which, as we know from the description, is to represent integers. But at the same time, it says in the description that it is about 32-bit integers. So in the name itself, we define the syntax of a bitstream, so we specify that it must be exactly 32 bits long. Concluding, we can say that type is a set of entities, a set of bitstreams that represent certain values. So in this respect, it is similar to the concept of code where we also had a set of words and we had a set of values ​​that the words are represented by. From the next part of the type definition, you will learn that it is so important that any operation is applied to bitstreams that have the meaning assigned according to well-known and provided in advance at design time rules.

## 1.19. Type as a set operations

From the example of dividing the number 5 by 2, which is equal to 2 or 2.5 you can learn that depending on the type of operands the operation behavior is different. In other words, we could suppose that type can be recognized also as a set of operations that are performed on the values belonging to a set defined by the type. Considering type as a set of operands (information representation) and a set of operators (operations representation) on these values is especially useful in the case of defining your custom types.

## 1.20. Summary

It is time to conclude and actually repeat. Simplifying, first, we can say that the type determines a set of values. The set of values that a variable can take. Second, the type specifies also the set of operations that are applicable to these values. Each type has its own set of operations and these operations - even if have the same names in different types - are performed differently depending on the type of operands. For existing well-known types some details of this definition could be replaced by other rules or even neglected. Next, we will investigate how to define custom types where all these details must be kept in mind without exception. Thank you for now and you are welcome to check out the next lesson.
