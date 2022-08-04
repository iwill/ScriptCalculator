ScriptCalculator
================

En | [中文](https://iwill.im/2022/07/08/script-calculator/)

[try it your self](https://iwill.im/static/ScriptCalculator.html)

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

$0 / 2 //  6 / 2 == 3 | $0  is 6 - the result of the 0th line
       // empty line
10 % $ // 10 / 3 == 1 | $   is 3 - the previous result, not "the result of the previous line"
   $-2 //        == 3 | $-2 is 3 - the 2nd-to-last result
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

````
```
// returns a value
return "x".length;
``` // 2
````

````
```js
// returns a function - MUST HAVE A NAME
return function double(x) {
    return x * 2;
}
```
double(1)  // 2
````

## settings

- decimal place count

- decimal rounding method

- reset settings

- copy script + outputs + comments

## other features

- line number

- sync scrolling

- change case: <kbd>control</kbd>+<kbd>u</kbd>, <kbd>control</kbd>+<kbd>shift</kbd>+<kbd>u</kbd>, <kbd>control</kbd>+<kbd>c</kbd>, <kbd>control</kbd>+<kbd>shift</kbd>+<kbd>c</kbd>

- serialize script to url hash and deserialize

- console log

## <!-- thin hr -->

<!-- URL: location.hash.replaceAll("(", "\(").replaceAll(")", "\)") -->

[all the tests](https://iwill.im/static/ScriptCalculator.html#%7B%22script%22%3A%22%23%20basic%3A%20%2B%2C%20-%2C%20*%2C%20%2F%2C%20%25%EF%BC%8C%20%3D%2C%20(%20and%20)%5Cn%5Cn%23%20variables%3A%20%3Cprevious%3E%2C%20%24%2C%20%24ln%5Cn%5Cn%23%20optional%20spaces%20and%20empty%20lines%5Cn%5Cn%23%20comments%3A%20%23%20and%20%2F%2F%5Cn%5Cn2%20%2B%204%20%2F%2F%202%20%2B%204%20%3D%3D%206%5Cn-%203%20%2F%2F%206%20-%203%20%3D%3D%203%5Cn%2F%2F%20empty%20line%5Cn*%204%20%2F%2F%20%20%20%20%20%20ERROR%5Cn%5Cn%240%20%2F%202%20%2F%2F%20%20%20%203%5Cn%2F%2F%20empty%20line%5Cn10%20%25%20%24%20%2F%2F%20%20%20%201%5Cn%5Cn%23%20percentage%3A%20%25%20if%20it's%20NOT%20followed%20by%20number%2C%20variable%2C%20function%20or%20open%20parenthesis%5Cn%5Cn10%25%20%20%20%20%20%2F%2F%20%200.1%5Cn10%20%25%20%20%20%20%2F%2F%20%200.1%5Cn10%25%20%2B%201%20%2F%2F%20%201.1%5Cn10%25%20%25%201%20%2F%2F%20%200.1%5Cn10%25%20-%207%20%2F%2F%20-6.9%5Cn10%20%25%20(-7)%20%2F%2F%20%203%20%20%5Cn%5Cn%23%20percentage%20conversion%5Cn%5Cn0.1%20%25%25%20%2F%2F%2010%25%5Cn*%202%20%20%20%20%2F%2F%200.2%5Cn%25%25%20%2F%2F%2020%25%5Cn%5Cn%23%20base%2Fradix%20conversion%5Cn%5Cn0b10%20%20%20%2F%2F%202%20%5Cn0o10%20%20%20%2F%2F%208%20%5Cn10%20%20%20%20%20%2F%2F%2010%5Cn0x10%20%20%20%2F%2F%2016%5Cn%5Cn32%20%232%20%20%2F%2F%200b100000%5Cn%238%20%20%2F%2F%200o40%20%20%20%20%5Cn%2310%20%2F%2F%2032%20%20%20%20%20%20%5Cn%2316%20%2F%2F%200x20%20%20%20%20%5Cn%2332%20%2F%2F%2010%20%20%20%20%20%20%5Cn%2336%20%2F%2F%20W%20%20%20%20%20%20%20%5Cn%24%20%20%20%20%20%2F%2F%2032%20%20%20%20%20%20%5Cn%5Cn%23%20bitwise%20operations%5Cn%5Cn%23%20!!!%3A%20JavaScript%20Uses%2032%20bits%20Bitwise%20Operands%5Cn%23%20https%3A%2F%2Fwww.w3schools.com%2Fjs%2Fjs_bitwise.asp%23%3A~%3Atext%3DJavaScript%2520Uses%252032%2520bits%2520Bitwise%2520Operands%5Cn%5Cn1%20%3C%3C%20%200%20%232%20%2F%2F%200b1%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5Cn1%20%3C%3C%20%201%20%232%20%2F%2F%200b10%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5Cn1%20%3C%3C%20%202%20%232%20%2F%2F%200b100%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5Cn1%20%3C%3C%20%204%20%232%20%2F%2F%200b10000%20%20%20%20%20%20%20%20%20%20%20%20%5Cn1%20%3C%3C%20%208%20%232%20%2F%2F%200b100000000%20%20%20%20%20%20%20%20%5Cn1%20%3C%3C%2016%20%232%20%2F%2F%200b10000000000000000%5Cn1%20%3C%3C%2032%20%232%20%2F%2F%200b1%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5Cn%5Cn%23%20builtin%20variables%20%26%20functions%5Cn%5CnE%20%2F%2F%202.718281828459045%20%5CnPI%20%2F%2F%203.141592653589793%20%5CnGR%20%2F%2F%200.6180339887498949%5Cn%5CnNumber.MAX_SAFE_INTEGER%20%2F%2F%209007199254740991%5Cn%3D%3D%20%20%20%20pow(2%2C%2053)%20-%201%20%20%2F%2F%20true%5CnNumber.MIN_SAFE_INTEGER%20%2F%2F%20-9007199254740991%5Cn%3D%3D%20-%20(pow(2%2C%2053)%20-%201)%20%2F%2F%20true%5Cn%5Cnmin(max(1%2C%202)%2C%203)%20%2F%2F%202%20%20%20%5Cnpow(2%2C%2010)%20%2F%2F%201024%5Cnsqrt(1024)%20%2F%2F%2032%20%20%5Cn%5Cnround(2000%20%2F%203%20*%20100)%20%2F%20100%20%2F%2F%20666.67%5Cnround(2000%20%2F%203%2C%202)%20%20%20%20%20%20%20%20%20%20%2F%2F%20666.67%5Cn%5Cn_666%3A%202000%20%2F%203%20%20%2F%2F%20666.6666666666666%5Cnround(_666%2C%203)%20%20%2F%2F%20666.667%20%20%20%20%20%20%20%20%20%20%5Cnfloor(_666%2C%202)%20%20%2F%2F%20666.66%20%20%20%20%20%20%20%20%20%20%20%5Cnceil(_666%20%2F%202%2C%201)%20%20%2F%2F%20333.4%20%20%20%20%20%20%20%20%20%20%20%20%5Cnround(_666)%20%20%20%20%20%2F%2F%20667%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5Cnround(_666%2C%20-1)%20%2F%2F%20670%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5Cnround(_666%2C%20-2)%20%2F%2F%20700%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5Cn%5Cn%23%20defining%20variables%20%26%20functions%5Cn%5Cntax_rate%3A%200.45%20%2F%2F%200.45%20%20%5Cntax_qcd%3A%20181920%20%2F%2F%20181920%5Cn1000000%20*%20tax_rate%20-%20tax_qcd%20%2F%2F%20268080%5Cn%5Cnfun(ads%2C%20usd%2C%20rmb%2C%20rate%2C%20qcd)%3A%20ads%20*%20usd%20*%20rmb%20*%20(1%20-%20rate)%20%2B%20qcd%5Cnfun(10000%2C%2045%2C%207%2C%20tax_rate%2C%20tax_qcd)%20%2F%2F%201914420.0000000002%5Cn%5Cnadd(%7B%20a%2C%20b%20%7D)%3A%20%5C%5C%5Cn%20%20%20%20a%20%2B%20b%5Cnadd(%7B%20a%3A%201%2C%20b%3A%202%20%7D)%20%2F%2F%203%5Cn%22%7D)

## TODO

- defining variables & functions via JavaScript blocks

````
lx: \
```js
return "x".length
```
````

````
// Fibonacci
f(n): \
```js
if (n <= 0) return 0;
if (n <= 2) return 1;
return f(n - 1) + f(n - 2);
```
````

- format with shortcuts
    - <kbd>control</kbd>+<kbd>l</kbd>: align script left - by appending spaces to the right
    - <kbd>control</kbd>+<kbd>r</kbd>: align script right - remove leading and trailing spaces
    - <kbd>control</kbd>+<kbd>m</kbd>: align script middle - align code right and comment left
    - <kbd>control</kbd>+<kbd>[</kbd>: indent left with 4 spaces
    - <kbd>control</kbd>+<kbd>]</kbd>: indent right with 4 spaces

- ruler for alinment
    
    a vertical line for script alignment

- display error info at the page bottom
    - display error count
    - display error message for selected line

## BUG

- page becomes unresponsive after type the semicolon like this
    - remember copying the url to backup if it happened
    - write `break;` first to workaround temporarily

````
```js
//        the cursor 👇🏿
for (let i = 0; i < 1;|) {
}
```
````

- sometimes, result area does not scroll when insert newline

