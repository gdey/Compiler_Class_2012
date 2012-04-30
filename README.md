25 April 2012
============

with the IBM 704 people started to find that software costs started to exceed hardware costs.

"speedcoding" 1953 developed by John Backus: the first interperter.
10-20x slower and took up 300 bytes = 30% of Memory.

# FORTRAN 1 -- John Backus
  Formulas. John though the issue with speedcoding with that the Formulas needed to be translated.
  1954-1957
  Initally though it would only take one year to build the compiler
  by 1958 50% programs were written in FORTRAN.
   # Led to an enormous body of theoretical work
   ** Theory + Practice


# Strucure of Frortran 1 Compiler
  1. Lexical Analysis
  2. Parsing
  3. Semantic Analysis
  4. Optimization
  5. Code Generation


Lecture 2.
---------


# Strucure of Frortran 1 Compiler
  1. Lexical Analysis
  2. Parsing
  3. Semantic Analysis
  4. Optimization
  5. Code Generation

First step: reconginize words.


Lexical analysis divides protram text into "words" or "tokens"

Prasing = Diagramming sentences

Programming languages define strict rules to avoid ambiguities.

Last pashe is Code Generation.


Lecture 3: Economy of Programing Languages.
-------------------------------------------

1. Why are there so many programming langugages?

  Application domains have distinctive/conflicting needs.
  It's very hard to design one language that will do everything for all programmers.

     1. Scientific computing
        a. need very good FP support.
        b. Need good support for arrays
        c. need parallelism
        d. FORTRAN is very good for this.
     2. Business applications
        a. presistence
        b. good reporting facilities
        c. data analysis
        d. SQL is the most common for this.
     3. Systems Programming
        a. embbed systems.
        b. operataing system.
        c. control of resources
        d. real time constrains
        e. C/C++ is a good language for this. 


2. Why are there new programming languages?

   Claim: Programmer training is the dominant cost for a programming language.

     Designer -- 1 - 2 people
     Implement -- 1 - 20 people
     Getting people to use the langauge lot's of people

   Predications:

      1. Widely used language will be slow to change.
         a. For each change everyone needs to be educated on the change.
      2. Easy to start a new langauge: because there are zero training cost to start.

      Tensition when are they going to choose the new language over the old language.

      New language will win when productivity > training costs.

      Languages are most likly to be adopted to fill a void.

      New languages tend to look like old languages. The have a family resesabance to older langauges. Leverages what people already know.


3. How do we know a good programming language?

     There is _no_ *universally accepted* metric for language design.

     Here is a proposed statement on what is a good language: A good language is one people use? (Not really true, as people may use language just because they know it. This would imply that VB is the best language? )


Things to remember:

   Application domains have conflicting needs.

   Programmer training is the dominant cost for a programming language.


Lecture 4: Cool Overview
-------------------------

Classroom Object Oriented Language = COOL

Designed to be implementable in a short time. Cool compiers >> cool programs.

What is in the langauge.

   * abstraction
   * static typing
   * reuse ( inheritance)
   * Memory management
   * and much more

But many things are left out

Goal:

A complete compiler
   COOL -> MIPS assembly language

5 assinments 

  Write a Cool program
  Lexical analysis
  Parsing
  Semantic analysis
  Gode generation

  (optional) optimizations

  all parts are plug compatible
    


# Week 2

## Lecture 1: Lexical Analysis

Token class of most languages:

1. Identifers
    - Strings of letter or digits, starting with a lettr -- this is typical. Ruby for instance allows for '?'.'!', and '=' in the identifer. Perl states identifiers must start with '$','%', or '@'

2. Keywords:
    - keywords of the language: 'If','While', etc...
3. Whitespace:
    - What makes up whitespace.


### Goal

  *  Classify program subscrings according to role (token class)
  *  Communicates tokens to the parsers

              ----   ---Token------   ---- 
  string ->  | LA | < Class, String > | P |

  foo=42   <id,"foo"> <op,"=">. <"Int","42">



#### Quiz 1

> x = 0;\n\twhile (x < 10) {\n\tx++;\n}
> IWOWNO  W   K  WOIWOWN OWO  W IO OW O
W = 9, 
K = 1,
I = 3, 
N = 2
O = 9, 


token subscrings are called lexemes

for each lexeme we need to identify a token class. A pair of <token class, lexeme> is called a token.





## Lexture 2: Lexical Analysis Examples

1. Fortran whitespace is not sigificant.
   DO 5 I example requires lookahead 

   A goal is to reduce the number of look-aheads

   The whitespace rule for Fortran came from punchcards. It was easy to add white space.


   LookAhead is always needed, just want to minimize it as much as possiable.


2. PL/1 keywords are not reserved

    LA was challenging.


4. C++ Texplate syntax:
       Foo<Bar>

   C++ stream syntax:

       cin >> var;

       Foo<Bar<Baz>> <-- looks like the stream syntax 

The goal of lexical analysis ts to 
  1. PArtition the input string into lexemes
  2. Identify the token of each lexeme

  Because we are using left-to-right parsing, we have to use look-ahead, to determine the role the string plays.

## Lecture 3: Regular Languages

Need a way it say what set of strings is in a token class
   we use Regular languages. We use Regular Expressions for this.

   * Single character

      'c' = { "c" }

   * Epsion

      E = {""}
      this is not null.

   * Union

       A + B = { A | a in A} u { B | b in B }

   * Concatenation 

       AB = { ab | a in A ^ b in B }

   * Iteration

      A* U(i>= 0) A^i 

      A^0 = Epsion


### Examples


E = { 0,1}

When you have a regular expersion that represents all strings in the language it's called Sigma star.

### Quiz



    






