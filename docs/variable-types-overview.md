# Variable types
There are two types of variables. A variable can be eather array, or not array. An array can contain only non array variable types. 
If array should get into a situation, when it should contain an another array, it is concatenated instead.

Variable types are determined at runtime and can be different for each line of input.

## Nonarray types
### String
* Ordinary string.

### Boolean
* True or false.

### Double
* Any floating point number type

### Integer
* Any integer number type

### Error
* An error type with a message
* Any operation (excluding conversion to string) with an error should return a same error.
* Optional

### Null
* A type representing NULL
* Optional

### UnitDouble
* A double with a type
* Optional

### Complex
* A complex number
* Optional

### Fraction
* A fraction type
* Two integers representing a rational number
* Optional

### Time
* A time type
* Optional

### Date
* A date type
* Optional

### Timestamp
* Time and date type
* Optional

## Automatic conversions
During the semantic analysis might happen, that a function accepts another type, then it is given.
In such case, semantic analyzator tries to convert variable to such a type, the function will accept.

### * -> String
Any type T will be automatically converted into string, if function doesn't accept T, but accepts string.

### Integer -> Fraction
An integer can be easily converted to a fraction.

### Integer -> Double
An integer can be easily converted to a double. It must be only implemented in cases, when Fraction isn't implemented.

### Fraction -> Double
A fraction can be easily converted to a double.

### Integer -> Boolean
A integer can be converted to a boolean. If it is zero, it will be converted to the false value, otherwise to the true value.
It must be only implemented in cases, when Fraction isn't implemented.

### Fraction -> Boolean
A fraction can be converted to a boolean. If it is zero, it will be converted to the false value, otherwise to the true value.

### Double -> Complex
A double will be automatically converted into complex number by assigning its value into the real part of the result.

### Date -> Timestamp
A date can be converted to a timestamp by assigning a time part of timestamp zero.

### Array - special one argument conversion
If array is given to a function, which accepts only one argument of non array type, it will be evaluated on all elements of array separatly.

### Error
If there is no automatic conversion available, so that a function in query can be evaluated, there are two possibilites. The implementation can choose any of them.

* The Error type will be returned instead of function result
* The whole query will fail.

## Manual conversions
There is a set of functions to manually change type of a variable. They are much more universal then automatic conversions. 
For more details, see Functions overview.
