# Functions overview
In the language are all functions 0-ary (futher called only as constants), 1-ary and 2-ary. (1-ary means, that function accepts one variable as input. 2-ary means, that function accepts two variables as input.)

Each function have its unique lexem, which is determined during lexical analysis. Constant tokens can't have another arity then 0-arity, but there are some functions, which may have both 1-arity or 2-arity.
The arity is determined during syntactic analysis.

The evaluation of functions is left to semantic analysis.

## Constants
### Pi
* Tokens: `pi`
* Type: `double`

### E
* Tokens: `e`
* Type: `double`

### i
* Tokens: `i`
* Type: `complex`
* Imaginary unit
* Optional

## Functions
### 1-arity functions
We use convension for function types: `argument_type -> return_type` for specifing, what type of arguments can function accept and what will return.
When there are more types than one, it means, that function can be evaluated multiple ways.
The semantic analyzator should prefer the way with the least possible amount of automatic conversions.

#### Sin
* Standard trigonometric sin function.
* Tokens: `sin`
* Type: `double -> double`
* Type: `complex -> complex`


#### Cos
* Standard trigonometric cos function.
* Tokens: `cos`
* Type: `double -> double`
* Type: `complex -> complex`

#### Tan
* Standard trigonometric tan function.
* Tokens: `tan`
* Type: `double -> double`
* Type: `complex -> complex`

#### Asin
* Standard trigonometric asin function. It is the local inverse function of the sin function.
* Tokens: `asin`
* Type: `double -> double`
* Type: `complex -> complex`

#### Acos
* Standard trigonometric asin function. It is the local inverse function of the cos function.
* Tokens: `acos`
* Type: `double -> double`
* Type: `complex -> complex`

#### Atan
* Standard trigonometric atan function. It is the local inverse function of the tan function.
* Tokens: `atan`
* Type: `double -> double`
* Type: `complex -> complex`

#### Sinh
* Standard hyperbolic sinh function.
* Tokens: `sinh`
* Type: `double -> double`
* Type: `complex -> complex`

#### Cosh
* Standard hyperbolic cosh function.
* Tokens: `cosh`
* Type: `double -> double`
* Type: `complex -> complex`

#### Tanh
* Standard hyperbolic tanh function.
* Tokens: `tanh`
* Type: `double -> double`
* Type: `complex -> complex`

#### Asinh
* Standard hyperbolic asinh function. It is the local inverse function of the sinh function.
* Tokens: `asinh`
* Type: `double -> double`
* Type: `complex -> complex`

#### Acosh
* Standard hyperbolic acosh function. It is the local inverse function of the cosh function.
* Tokens: `acosh`
* Type: `double -> double`
* Type: `complex -> complex`

#### Atanh
* Standard hyperbolic tanh function. It is the local inverse function of the tanh function.
* Tokens: `atanh`
* Type: `double -> double`
* Type: `complex -> complex`

#### Head
#### Tail
#### Reverse

#### ToString
* It should retype an arg to the string.
* If an argument is an array, it should return char (by default `,`) separated string.
* Tokens: `s`, `str`, `to_string`
* Type: `* -> string`

#### ToInt
* It should retype an arg to the integer. If argument can't be retyped, it returns error or fails.
* Tokens: `i`, `int`, `to_integer`
* Type: `* -> integer`

#### ToComplex
* Optional
#### ToDouble
#### ToBoolean
#### Minus
#### Sum
#### Round
#### Truncate


### 2-arity functions
#### NthElement
#### Take
#### Drop
#### Append
