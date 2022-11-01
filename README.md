# Equal - the Esoteric Programming Language HTML

## Rules of thumb
- Tagnames
  - ```span``` is used in print statements
  - ```a``` is used for variables
  - ```form``` is used for reserved operators or user-defined functions
    - ```input``` is used to indicate parameters and return statements in functions
    - ```label``` is used to pass arguments to operators or functions
  - ```h1``` to ```h6``` is used for if/else statements
  - ```p``` is used for loops
  - ```div``` is used for code blocks that have their own scope

- Attributes
  - ```id``` is usually used when defining variables or functions
  - ```href``` and ```title``` are used to refer to variables and functions that are already defined

## [Grammar](GRAMMAR.md)

## Features
### IO
#### Output
```html
<span>
<!-- output expressions here -->
</span>
```


### Variables
#### Declaration or assignment
```html
<a id="name_of_variable" class="global">
  <!-- set class value to global to modify global value -->
  value
</a>
```
#### Reference
```html
<!-- refer to variable -->
<a href="name_of_variable">
</a>
```
- variables must be initialized
- only href considered in expression
- types
  - dynamically typed
  - three types available: string, number, boolean
  - if ```!isNaN(Number(expression))``` is true, the variable is a number
  - else if ```expression``` matches true or false exactly, the variable is a boolean
  - else if the variable is a string
  - implict conversions between types will throw error


### Operators
#### Arithmetic
```html
<form title="+">
  <label for="name_of_param1">num1</label>
  <label for="name_of_param2">num2</label>
  <!-- more args possible -->
</form>
<!-- possible titles: "+" "-" "*" "/" -->
```
- no division by zero
- plus does not work on strings

#### Comparsion
```html
<form title="==">
  <label for="name_of_param1">expression1</label>
  <label for="name_of_param2">expression2</label>
  <!-- only two args -->
</form>
<!-- possible titles: "==" "!=" ">" "<" -->
```
- equal and not equal are implemented strictly, i.e. "==="

#### Logic
```html
<!-- (1) -->
<form title="!">
  <label for="name_of_param1">expression1</label>
  <!-- only one arg -->
</form>
<!-- (2) -->
<form title="&&">
  <label for="name_of_param1">expression1</label>
  <label for="name_of_param2">expression2</label>
  <!-- more args possible -->
</form>
<!-- possible titles for (1): "!" -->
<!-- possible titles for (2): "&&" "||" -->
<!-- &&: return true if all evaluate to true -->
<!-- ||: return true if one evaluates to true -->
```

- only operators that cannot be easily constructed with other operators are provided

#### Reserved function names
- \+ , \- , \* , /, !, ==, !=, >, <, &&, ||


### User-defined functions
#### Definition
```html
<form id="name_of_function">
  <input id="name_of_param1">
  <input id="name_of_param2">
  <input id="name_of_param3">
  <!-- etc -->
  <div>
    <!-- code to be executed -->
    <!-- optional, return value defaults to 0 -->
    <input type="submit"> 
    <!-- an expression that is the return value -->
  </div>
</form>
```
- only global functions supported
- functions must be declared (and initialized) before being used

#### Reference
```html
<!-- for is optional and is for readability purposes only-->
<form title="name_of_function">
  <label for="name_of_param1">
    arg1
  </label>
  <label for="name_of_param2">
    arg2
  </label>
  <label for="name_of_param3">
    arg3
  </label>
  <!-- etc -->
</form>
```


### Control Flow
#### If/else statements
```html
<h1>
  <!-- expression -->
  <!-- statements (execute if expression evaluates to true) -->
</h1>
<h2>
  <!-- optional else if statements -->
  <!-- expression -->
  <!-- statements -->
</h2>
<h6>
  <!-- optional else statement -->
</h6>
```
- from h1 to h5, the elements must go in order
- h1, or h1 and h6 can appear alone

#### While loops
```html
<p>
  <!-- expression -->
  <!-- statements (execute until expression evaluates to false) -->
</p>
```



### Misc
#### Comments
```html
<!-- comments about the code -->
```
#### Code blocks
```html
<div>
  <!-- code inside -->
</div>
```
- variable outside the current div block can be accessed, variable in the global scope can be modified
- variable in children div blocks cannot be accessed or modified



## References
- The vast majority of code in this repository is written by me and the errors are mine alone
- Credit to [Crafting Interpreters](https://craftinginterpreters.com/representing-code.html) for inspiring much of the structure of the interpreter
- Other references:
  - [HTML Standards](https://html.spec.whatwg.org/)