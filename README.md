ScriptCalculator
================

En | [中文](https://iwill.im/2022/07/08/script-calculator/)

[try it your self](https://iwill.im/url/2)

## calculation

- basic: `+`, `-`, `*`, `/`, `%`， `=`, `(` and `)`

- variables: `<previous>`, `$`, `$ln`

- optional spaces

- comments

```
 2 + 4 // 2 + 4 == 6
   - 3 // 6 - 3 == 3  | prepend 6 - the result of the previous line
       // empty line
   * 4 // ERROR       | the previous line is empty

$0 / 2 //  6 / 2 == 3 | $0 is 6 - the result of the 0th line
       // empty line
10 % $ // 10 / 3 == 1 |  $ is 3 - the previous result, not "the result of the previous line"
    $$ //        == 3 | $$ is 3 - the 2nd-to-last result
```

- percentage: `%` if it's NOT followed by `number`, `variable`, `function` or `(`

```
10%     // 0.1             | percentage
10 %    // 0.1             | percentage
10% + 1 // 0.1 + 1 == 1.1  | percentage
10% % 1 // 0.1 % 1 == 0.1  | percentage and remainder operation
10% - 7 // 0.1 - 7 == -6.9 | percentage
10 % (-7) // 10 % 7 == 3   | remainder operation
```

- percentage conversion

```
0.1 %% // 10%
* 2    // 0.2
    %% // 20%
```

- base/radix conversion

```
0b10   // 2
0o10   // 8
10     // 10
0x10   // 16

32 #2  // 0b100000
   #8  // 0o40
   #10 // 32
   #16 // 0x20
   #32 // 10
   #36 // W
 $     // 32
```

- bitwise operations

> !!!: [JavaScript Uses 32 bits Bitwise Operands](https://www.w3schools.com/js/js_bitwise.asp#:~:text=JavaScript%20Uses%2032%20bits%20Bitwise%20Operands)

```
1 <<  0 #2 // 0b1
1 <<  1 #2 // 0b10
1 <<  2 #2 // 0b100
1 <<  4 #2 // 0b10000
1 <<  8 #2 // 0b100000000
1 << 16 #2 // 0b10000000000000000
1 << 32 #2 // 0b1 - JavaScript Uses 32 bits Bitwise Operands
```

- builtin variables & functions

```
 E // 2.718281828459045
PI // 3.141592653589793
GR // 0.6180339887498949
```

```
Number.MAX_SAFE_INTEGER // 9007199254740991
  == pow(2, 53) - 1     // true
Number.MIN_SAFE_INTEGER // -9007199254740991
  == - (pow(2, 53) - 1) // true
```

```
min(max(1, 2), 3) // 2
       pow(2, 10) // 1024
       sqrt(1024) // 32
```

```
round(2000 / 3 * 100) / 100 // 666.67
round(2000 / 3, 2)          // 666.67

_666: 2000 / 3  // 666.6666666666666
round(_666, 3)  // 666.667
floor(_666, 2)  // 666.66
 ceil(_666 / 2, 1) // 333.4
round(_666)     // 667
round(_666, -1) // 670
round(_666, -2) // 700
```

```
1 // 1 | line number: 0
2 // 2 | line number: 1
3 // 3 | line number: 2

$sum(0, 2)      = 6 \ // sum range: 0...2
&& $sum(-3, -1) = 6 \ // sum range: -3...-1
&& $sum(0)      = 6 \ // sum range: 0...
&& $sum()       = 6 \ // sum range: 0...
                      // true

$avg(0, 2) // 2
$min(0, 2) // 1
$max(0, 2) // 3
```

- defining variables & functions

```
              tax_rate: 0.45 // 0.45
             tax_qcd: 181920 // 181920
1000000 * tax_rate - tax_qcd // 268080
```

```
fun(ads, ads2usd, usd2rmb, rate, qcd): ads * ads2usd * usd2rmb * (1 - rate) + qcd
fun(10000, 45, 7, tax_rate, tax_qcd) // 1914420.0000000002
```

```
add({ a, b }): \
    a + b
add({ a: 1, b: 2 }) // 3
```

- JavaScript blocks

> `vals[<result_index>]`, `vars.<custom_var_name>` and `funcs.<custom_func_name>` are available in JavaScript blocks

````
```
let s = "x";
return s.length;
```   // 1
lx: $ // 1
````

````
lx: \
```
let s = "x";
return s.length;
```   // 1
lx    // 1
````

````
double(x): \
```js
return x * 2;
```
double(1) // 2
````

````
# Fibonacci
f: \
```js

// context for func                 
let prev = 0;                       

// func name for recursive invocation  
// instead of using `funcs._f`      
return function _f(n, reset) {      

    if (typeof n == "boolean") {    
        reset = n;                  
        n = undefined;              
    }                               

    if (reset) {                    
        prev = 0;                   
    }                               

    if (n == undefined) {           
        n = prev;                   
        prev = prev + 1;            
    }                               

    if (n <= 0) return 0;           
    if (n <= 2) return 1;           
    return _f(n - 1) + _f(n - 2);   
}                                   
```

f() // 0
f() // 1
f() // 1
f() // 2
f() // 3
f() // 5

f(true) // 0
f() // 1
f() // 1
f() // 2
f() // 3
f() // 5
````

## settings

- decimal place count

- decimal rounding method

- reset settings

- copy script + outputs + comments

## other features

- line number

- sync scrolling

- vertical ruler

- change case:
    - <kbd>control</kbd>+<kbd>u</kbd>: uppercase
    - <kbd>control</kbd>+<kbd>shift</kbd>+<kbd>u</kbd>: lowercase
    - <kbd>control</kbd>+<kbd>option</kbd>+<kbd>u</kbd>: capitalize

- format with shortcuts:
    - <kbd>control</kbd>+<kbd>l</kbd>: align script left, appending spaces to the right
        - \+<kbd>option</kbd>: keep leading spaces
        - \+<kbd>shift</kbd>: prepend spaces to the left
    - <kbd>control</kbd>+<kbd>r</kbd>: align script right, remove leading and trailing spaces
    - <kbd>control</kbd>+<kbd>m</kbd>: align script middle, align to trailing comments
    - <kbd>control</kbd>+<kbd>[</kbd>/<kbd>]</kbd>: indent left/right with 4 spaces
        - \+<kbd>option</kbd>: keep leading spaces
    - <kbd>control</kbd>+<kbd>/</kbd>: prepend/remove trailing `//` comments

- other shortcuts:
    - <kbd>control</kbd>+<kbd>,</kbd>: insert configurations with default values
    - <kbd>control</kbd>+<kbd>shift</kbd>+<kbd>/</kbd>: show help

- serialize script to url hash and deserialize

- share with short url

- console log

## <!-- thin hr -->

<!-- URL: location.hash.replaceAll("(", "\(").replaceAll(")", "\)") -->

[all the tests](http://iwill.im/url/6)

## TODO

- display error/warning count (at top) and info on the right

- `try it yourself` in readme

## BUG

- page becomes unresponsive after type the semicolon like this
    - remember copying the url to backup if it happened
    - write `break;` first to workaround temporarily

````
```js
//         the caret 👇🏿
for (let i = 0; i < 1;|) {
}
```
````

- sometimes, result area does not scroll when insert newline

