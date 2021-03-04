# lsql

This repository contains the documentation of LSQL language (Lapidary Structured Query Language). 
It is not intended as a tutorial and reader is strongly encouraged to read [lsql-csv/README.md](https://github.com/stastnypremysl/lsql-csv/blob/master/README.md) first.

The documentation suppose, that a new implementation of the language will layer processing to preprocessor, lexer, parser and to the semantics. It is strongly recommended, but it is not required by the standard and any incomming programmer is free to commit any suicide he choose. :-)

The documentation consists few chapters as the languge is processed.

0) [Used terminology](https://github.com/stastnypremysl/lsql/blob/main/docs/used-terminology.md)
1) Special characters and keywords - common overview for Preprocessor and Lexer
2) Preprocessing
3) Functions overview (used in all lexical, syntactical and semantic analysis)
    1) Aggregate functions
    2) Arithmetic functions
4) Lexical analysis
    1) Arithmetic mode identifiers lexing
    2) Batch mode identifiers lexing
5) Syntactical analysis
6) Semantic analysis
    1) Variable types
    2) Variable conversions
    4) Select statement
    5) By statement
    6) If statement
    7) Sort statement
    8) From statement
