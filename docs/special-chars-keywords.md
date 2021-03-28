# Special characters

## Whitespace
Whitespace can be eather space, tab or new line. The language don't recognize any difference between these.

The function of whitespaces in batch mode differs from the function of whitespaces in arithmetic mode.

In the arithmetic mode are whitespaces purely for purpose of separating lexems by a lexer and have no syntactic or semantic meaning.

In the batch mode are whitespaces separators for elements. They also play an important role in macros, where each element is resolved independentaly.

## Single and double quotes (`'`, `"`)
Single and double quotes have same meaning in the language with the only exception, that single quote statement must be terminated by single quote and double quote statement must be terminated by double quote.

Quote statement can contain any chars excluding the quote itself (single quote statement can't contain single quote, double quote analogically). Non other character in quote statement is considered special.

Quote statement is always tokenized into quote token and then processed as a user-defined constant. The variable type of the constant is up to an implementation.

When single resp. double quotes are doubled inside single resp. double quotes statement, they are considered as ordinary chars.

## Lookup quotes (grave accent quotes) (`` ` ``)
Lookup quotes serves for explicitly specifing one variable, without being processed by preprocessor or wildcards. It works in the same way as single and double quotes with the exception of it's semantic purpose. If variable doesn't exist, the query should fail.

## Comma (`,`)
Commas are separators for blocks. First block (always from block) don't start with a comma and the last one doesn't end with one.

If comma is inside round brackets, it serves for defining arrays.

If comma is inside curly brackets, it serves for purpose of the macro. For more details see preprocessor chapter.

## Round brackets (`(`, `)`)
Round brackets serves for arithmetic expressions. It is evaluated during semantic analysis to ONE variable.

## Square brackets (`[`, `]`)
Square brackets serves for batch expressions. It may be evaluated during semantic analysis to MANY [0..inf) variables.

## Backslash (`\`)
Backslash serves as mark, that special character should be handled as ordinary character.

# Special characters - preprocessor only
## Minus (`-`)
Minus is used inside preprocessor macro to specify ranges. In other layers of the language it is considered as ordinary char.

## Curly brackets (`{`, `}`)
Curly brackets serves for the unnamed preprocessor expressions.

## Dolar (`$`)
Dolar sign is used by preprocessor to inject macro.

## Hash (`#`)
Everything after hash till the new line is deleted. It is used for comments.

## Tildo (`~`)
Tildo is used as symbol to unify named macros.

# Keywords

## by
`by` keyword is always at the beginning of the block. The block is to specify
a) that standard SQL GROUP BY should be used
b) by which variables should be block grouped by

It accepts batch expression.

## on
`on` keyword is used only in `left`, `right`, `full` or `inner` block. It is used to specify condition to join.

It terminates batch expression in first part of block and accepts aritmethic expressions.

## left
`left` keyword is used for specifing left outer join. It must be followed by `on` statement.

It accepts batch expressions.

## right
`right` keyword is used for specifing right outer join. It must be followed by `on` statement.

It accepts batch expression.

## inner
`inner` keyword is used for specifing inner join. It must be followed by `on` statement.

It accepts batch expression.

## full
`full` keyword is used for specifing full outer join. It must be followed by `on` statement.

It accepts batch expression.

## cross
`cross` keyword is used for specifing cross join.

It accepts batch expression.

## if
`if` keyword is used for specifing a condition under which should be row showed.

It accepts arithmetic expression.

## sort
`sort` keyword is used for specifing by which variable should be rows sorted.

It accepts batch expression.

## append
`append` keyword is used for appending new columns to the current columns. 

It accepts batch expression.

## mc
`mc` keyword is used for specifing named macros.

It accepts macro expressions, which exist only in the context of the preprocessor.

## var
`var` keyword is used for creating hidden columns.

It is useful for precomputing some data, which will be used later in select block.

It accepts batch expression.

## union
`union` keyword is used for appending new rows after the result of an query. After `union` keyword should follow a new query.

It accepts batch expression.

