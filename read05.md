# what is for statment ?
>A for loop repeats until a specified condition evaluates to false. The JavaScript for loop is similar to the Java and C for loop.

#### How the for statement executes?
 ###

 ![for](https://runestone.academy/runestone/books/published/thinkcspy/_images/new_flowchart_for.png)

### syntax
```
for ( ''initializer''; ''conditional expression''; ''loop expression'' )
{
      statements to be executed
}
```



## Example
 ```
 var j = 10;

for (i=0; i<10; i++)
{
      j += j;
}
 ```

 # what is while loop ?
 >A while statement executes its statements as long as a specified condition evaluates to true. A while statement looks as follows:

### syntax
```
while (condition)
  statement
```
> In that above syntax outline, condition is an expression that will return either true or false and JavaScript Statements represents the JavaScript to be executed while the expression is **true**. 

##
 ## Example
```
 while ( i < 10 )
{
      i = i + j;
}
```
>in the above example, the while expression will evaluate whether i is less than 10. If it is already greater than 10 then the code in the braces is skipped and the loop exits without performing any tasks. If it is not greater than 10 the code in the braces is executed and the loop returns to the while statement and repeats the evaluation of i. This process repeats until i is greater than 10, at which point the loop exits.

[reference](https://www.techotopia.com/index.php/JavaScript_Flow_Control_and_Looping)


