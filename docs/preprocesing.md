# Preprocessing
Preprocessing is the first part of query evaluation. For interested readers, who might ask, why do we need macros, we answer: We don't, but it simplify many things. Mainly:

* Fast new function definitions - just inject it as text
* Nested "for" cycles on text level - standard batch processing supports only one level "for" cycle and runs on postsyntactic level, therefore less powerful for some tasks

Macro can be inbuilt, unnamed or named.

The basic concept of a macro is expansion. Every macro is evaluated to a list of strings and than injected to a context. 

No macro is evaluated, if

* macro is in lookup quote
* some necessary special char of a macro have been escaped by `\`

If there is a macro inside a macro, the inner macro must be evaluated first.

## Unnamed macros
Unnamed macro is always enclosed in curly brackets. There are two modes of unnamed macros

* Ranged unnamed macros
* Enumeration unnamed macros

### Ranged unnamed macros 
Ranged unnamed macros have format `{a1..a2}`. `a1` and `a2` can be eather (but both of them must have same type)

* Numbers
* Chars

When they are numbers, it is evaluated to a list of numbers `a1, a1+1, a1+2,..., a2` if `a1 <= a2`.
If `a2 < a1`, it is evaluated to a list of numbers `a2, a2+1, a2+2,..., a1`.

When `a1` and `a2` are chars, it is evaluate to a list of all chars between `a1` and `a2` (including `a1` and `a2`), similary to number range described above.

### Enumeration unnamed macros
Enumeration unnamed macros have format `{a1,a2,...,an}`. It is evaluated to a list of strings `a1, a2,..., an`.

`{a1}` is evaluated to a string `a1`.

## Injection of macro to a context
Each macro is evaluated in an context - a substring of a query containing a macro. A context selection is an automatic process, which is described in a next chapter.

Let's have a macro M, which is evaluated to a list `x1, x2,..., xn`. Suppose macro M is in context `AMB`, where `A` and `B` are some strings.
The preprocessor evaluates the context to `Ax1B Ax2B ... AxnB`.

## Context selection

## Named macros

### Unification

### Calling convention

## Inbuilt macros

### Macro input arguments

### Universal unification macro
