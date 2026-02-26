# church-boolean-ocaml
Church Boolean Encodings in OCaml - Theory of Computation
# Church Boolean Encodings in OCaml

**Course:** Theory of Computation  
**Assignment:** Church Encodings  
**Language:** OCaml

**Students**

Harumi Nishikuni

Laura Santamaria

**Project Description**

This project implements Boolean values and logical operators using Church encodings in pure lambda calculus, written in OCaml.

The objective of this assignment is to understand how fundamental programming concepts such as true, false, and logical operators can be represented only using functions, following the principles of lambda calculus.

Instead of using OCaml's built-in Boolean type, we represent Booleans as higher-order functions according to Church encoding definitions.

**Church Encodings**

In lambda calculus, Booleans are defined as:

TRUE ≡ λx.λy.x → returns the first argument

FALSE ≡ λx.λy.y → returns the second argument

These definitions allow logical operations to be constructed purely through function application.

**Logical Operators**

**Using Church encoding:**

**AND**

AND ≡ λp.λq. p q false

**OR**

OR ≡ λp.λq. p true q

**NOT**

NOT ≡ λp. p false true
Implementation

**The implementation uses only lambda functions (fun) in OCaml.**

**Boolean Definitions**
(* TRUE = λx.λy.x *)
let true_c = fun x -> fun y -> x

(* FALSE = λx.λy.y *)
let false_c = fun x -> fun y -> y
**Logical Operators**
(* AND = λp.λq. p q false *)
let and_c = fun p -> fun q -> p q false_c

(* OR = λp.λq. p true q *)
let or_c = fun p -> fun q -> p true_c q

(* NOT = λp. p false true *)
let not_c = fun p -> p false_c true_c
Conversion Helper

**Since Church Booleans are functions, we convert them into OCaml booleans for testing:**

let to_bool b = b true false

**This works because:**

Church true returns the first argument (true)

Church false returns the second argument (false)

**How the Solution Works**

**Booleans as Functions**
Instead of storing truth values, each Boolean decides which argument to return.

Logical Operations via Function Application

AND evaluates the first Boolean and decides whether to return the second Boolean or false.

OR evaluates the first Boolean and returns true if possible.

NOT swaps the behavior of true and false.

**Evaluation**
The helper function applies the Church Boolean to real OCaml values (true and false) to visualize results.

**How to Run the Program**
**Requirements**

OCaml installed (version 4.x or newer recommended)

**Check installation:**

ocaml -version
Compile
ocamlc -o church_bool main.ml
Run
./church_bool

Or execute directly in the OCaml interpreter:

ocaml main.ml
Expected Output
true AND true = true
true AND false = false
false AND false = false
true OR false = true
false OR false = false
NOT true = false
NOT false = true
Tools and Environment

**Operating System: (e.g., Windows 10 / Linux / macOS)**

**Programming Language: OCaml**

**Compiler: OCaml compiler (ocamlc)**

Editor/IDE: (e.g., VS Code)

(Update according to your actual environment if needed.)

**References**

Course material: SI1001 Theory of Computation – Assignment 1 

booleanos-lc

Official OCaml website: https://ocaml.org/

Church, A. (1930s). Lambda Calculus foundations.

Lecture notes and class explanations.

AI assistance used for clarification and documentation support.

**Academic Notes**

This implementation follows Church encoding rules strictly and uses only lambda expressions as required by the assignment instructions.
