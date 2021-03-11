# lsql

This repository contains the documentation of LSQL language (Lapidary Structured Query Language). 
It is not intended as a tutorial and reader is strongly encouraged to read [lsql-csv/README.md](https://github.com/stastnypremysl/lsql-csv/blob/master/README.md) first.

The documentation suppose, that a new implementation of the language will layer processing to preprocessor, lexer, parser, postsynactic analyzator and to the semantics. It is strongly recommended, but it is not required by the standard and any incomming programmer is free to commit any suicide he chooses. :-)

The documentation consists few chapters as the languge is processed.

0) [Used terminology](https://github.com/stastnypremysl/lsql/blob/main/docs/used-terminology.md)
1) [Special characters and keywords](https://github.com/stastnypremysl/lsql/blob/main/docs/special-chars-keywords.md)
2) [Preprocessing](https://github.com/stastnypremysl/lsql/blob/main/docs/preprocesing.md)
3) Functions overview
4) Lexical analysis
    1) Arithmetic mode identifiers lexing
    2) Batch mode identifiers lexing
5) Syntactic analysis
6) Postsyntantic analysis
7) Semantic analysis
    1) Variable types
    2) Variable conversions
    4) Select statement
    5) By statement
    6) If statement
    7) Sort statement
    8) From statement
