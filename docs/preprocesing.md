# Preprocessing
Preprocessing is the first part of query evaluation. For interested readers, who might ask, why do we need macros, we answer: We don't, but it simplify many things. Mainly:

* Fast new function definitions - just inject it as text
* Nested "for" cycles on text level - standard batch processing supports only one level "for" cycle and runs on postsyntactic level, therefore less powerful for some tasks

The basic concept of a macro is expansion. Every macro is evaluated to a list of strings and than injected to a context. 
A context is selected before the expansion to a list of string.

If the same macro is called multiple times at different places of a query, it is evaluated again every time it is called.

No macro is evaluated, if

* macro is in lookup quote
* some necessary special char of a macro have been escaped by `\`

Preprocessor also deletes all comments.


## Clasification
There are two clasifications of macros. 

The first classification is innamed macro, named macro and inbuilt macro by the way they are defined.

The second classification is unified and ununified macros. Unification can't be used in unnamed macros, so they are always evaluated as ununified macros.
Whether named macro is unified or not is determined at call time of macro.

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

## Default context
A default context is selected context of macro during injection unless overrided by unification.

Every macro must be indirectly inside batch expression or macro inplace expression (eg. it can be inside arithmetic expression, if it is inside batch expression). When this condition don't hold, the behavior is undefined.

A batch expression is separated to batch statements by whitespaces. A macro's default context is the nearest batch statement.

If macro is called from macro inplace expression, the behavior is the same as the macro block was batch expression.

## Unification
(Soft) unification is transitive binary relation `~` between all macros which

1) For all `A` and `B` such that `A ~ B`: `A ~ A`
2) For all `A`: `U ~ A` (`U` is an inbuilt macro)

Hard unification is equvivalance `~~` on all macros, which will be unified in the current context.

Hard unification is always determined during the context selection in current statement.
If `A ~ B` and `A`'s default context consist `B` during the injection, then `A ~~ B`.

When `A` and `B` are (hard) unified during the injection to a context, it means, that they are evaluated together. The details are described later.

If `A ~~ B`, then if `A`'s default context consist `B` during the injection, `B`'s context will be overrided by `A` context (if they are not same already). 


## Preprocessing order
### Batch expression

0) Load next batch statement and set it as current context
1) Evaluate all unnamed macros excluding inner batch expressions
2) Find all macros and compute hard unification for the batch statement
3) Evaluate all hard unified macros' arguments as non-unified macros
4) Factorize hard unified macros
5) Evaluate all hard-unified macros in the batch statement
6) Evaluate the rest of macros in the batch statement excluding inner batch expression
7) Evaluate recursivly all inner batch expressions
8) Return list of batch expressions

### Macro block

0) Load next macro statement
1) TODO

## Injection of macro to a context
Each macro is evaluated in context - a substring of a query containing a macro.

### Nonunified macros
Let's have a macro nonunified M, which is evaluated to a list `x1, x2,..., xn`. Suppose macro M is in context `AMB`, where `A` and `B` are some strings.
The preprocessor evaluates the context to `Ax1B Ax2B ... AxnB`.

### Unified macros
Now let's move to the unified macros. Factor sets are evaluated separated, so when we talk about unified macros, they are always in one factor set.

Suppose we have unified macros `M1, M2,..., Mn` in the context `A1M1A2M2...AnMnAn+1`
Unification have no effect on how `M1, M2,..., Mn` itself is expanded to lists of strings `L1, L2,..., Ln`. They will receive these lists as they are unified.

Lets define lists of strings `J1, J2,...,Jn`, all with the same length of the longest list (`m`) of `L1, L2,..., Ln`. 
Let's put infinite repetition of elements of `L1, L2,..., Ln` in `J1, J2,...,Jn`, but with length of `J1, J2,...,Jn` unchanged. (definition of the elements)

`Jxy` means y-th element of `Jx`.

Using the current definitions preprocessor evaluates the context to `A1J11A2J21...AnJn1An+1 A1J12A2J22...AnJn2An+1 ...... A1J1mA2J2m...AnJnmAn+1`

## Named macros
Named macros are always evaluated after unnamed macros. They are defined in `mc` blocks (macro blocks). 

Named macro is basically a list of strings which might contain other macros. 

### Calling convention

## Macro block
This is the only type of block, which isn't either arithmetic or batch. We call it the macro block and it consist macro expressions.

## Inbuilt macros

### Macro input arguments

### Universal unification macro

