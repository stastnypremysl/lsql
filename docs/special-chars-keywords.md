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

## Lookup quotes (grave accent quotes) (`` ` ``)
Lookup quotes serves for explicitly specifing one variable, without being processed by preprocessor or wildcards. If variable doesn't exist, the query should fail.

## Comma (`,`)
Commas are separators for blocks. First block (always from block) don't start with a comma and the last one doesn't end with one.

If comma is inside round brackets, it serves for defining arrays.

## Round brackets (`(`, `)`)
Round brackets serves for arithmetic expressions. It is evaluated during semantic analysis to ONE variable.

## Square brackets (`[`, `]`)
Square brackets serves for batch expressions. It may be evaluated during semantic analysis to MANY [0..inf) variables.

## Backslash (`\`)
Backslash serves as mark, that special character should be handled as ordinary character.

# Keywords

## by
## mby
## on
## left
## right
## inner
## if
## sort
## append
## mc
## var
## union

