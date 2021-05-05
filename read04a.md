# Operators
>JavaScript has the following types of operators. This section describes the operators and contains information about operator precedence

>- Assignment operators(x = y)
- Comparison operators(var var1 = 3;)
- Arithmetic operators(1 / 2; // 0.5
1 / 2 == 1.0 / 2.0; // this is true)
- Bitwise operators(<<)
- Logical operators(expr1 && expr2)
- String operators
 - Conditional (ternary) operator
- Comma operator
- Unary operators
- Relational operators

# Operator precedence

```
Operator type	         Individual operators

member                          	. []
call / create instance          	() new
negation/increment           	! ~ - + ++ -- typeof void delete
multiply/divide              	* / %
addition/subtraction           	+ -
bitwise shift               	<< >> >>>
relational                  	< <= > >= in instanceof
equality                    	== != === !==
bitwise-and	                   &
bitwise-xor                     	^
bitwise-or	                    |
logical-and                  	&&
logical-or                   	||
conditional                  	?:
assignment             	= += -= *= /= %= <<= >>= >>>= &= ^= |= &&= ||= ??=
comma                        	,
```


##

# Expression


>An expression is any valid unit of code that resolves to a value.

>Every syntactically valid expression resolves to some value but conceptually, there are two types of expressions: with side effects (for example: those that assign value to a variable) and those that in some sense evaluate and therefore resolve to a value.

>The expression x = 7 is an example of the first type. This expression uses the = operator to assign the value seven to the variable x. The expression itself evaluates to seven.

>The code 3 + 4 is an example of the second expression type. This expression uses the + operator to add three and four together without assigning the result, seven, to a variable

## 
### JavaScript has the following expression categories:

- Arithmetic: evaluates to a number
- String: evaluates to a character string
- Logical: evaluates to true or false. 
- Primary expressions: Basic keywords and general expressions in JavaScript.
- Left-hand-side expressions: Left values are the destination of an assignment.
# Control flow
> The control flow is the order in which the computer executes statements in a script.

>Code is run in order from the first line in the file to the last line, unless the computer runs across the (extremely frequent) structures that change the control flow, such as conditionals and loops. 

>A typical script in JavaScript or PHP (and the like) includes many control structures, including conditionals, loops and functions. Parts of a script may also be set to execute when events occur.
## 

# JavaScript Arithmetic Operators
Arithmetic operators are used to perform arithmetic on numbers:

```
Operator	Description

+	        Addition
-	        Subtraction
*	        Multiplication
**       	Exponentiation (ES2016)
/       	Division
%	        Modulus (Division Remainder)
++      	Increment
--	       Decrement