ScriptCalculator
================

## calculation

- basic: `+`, `-`, `*`, `/`, `%`， `=`, `(` and `)`

- variables: `<last>`, `$`, `$ln`

- optional spaces

- comments

```
 2 + 4 //  2 + 4 == 6
   - 3 //  6 - 3 == 3 // 6: the result value of last line
       // empty line
   * 4 // ERROR: the last line is empty

$0 / 2 //  6 / 2 == 3 // $0 is 6: the result value of the 0th line
10 % $ // 10 / 3 == 1 // $  is 3: the result value of the last line
   = 1 //  1 = 1 == true
```

- percentage: `%` if it's NOT followed by `number`, `variable`, `function` or `(`

```
10%     // 0.1             // percentage
10 %    // 0.1             // percentage
10% + 1 // 0.1 + 1 == 1.1  // percentage
10% % 1 // 0.1 % 1 == 0.1  // percentage and remainder operation
10% - 7 // 0.1 - 7 == -6.9 // percentage
10 % (-7) // 10 % 7 == 3   // remainder operation
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
$      // 32
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
 ceil(_666, 1)  // 666.7
round(_666)     // 667
round(_666, -1) // 670
round(_666, -2) // 700
```

```
E  // 2.718281828459045
PI // 3.141592653589793
GR // 0.6180339887498949
```

```
Number.MAX_SAFE_INTEGER // 9007199254740991
  == pow(2, 53) - 1 // true
Number.MIN_SAFE_INTEGER // -9007199254740991
  == - (pow(2, 53) - 1) // true
```

- defining variables & functions


```
              tax_rate: 0.45 // 0.45
             tax_qcd: 181920 // 181920
1000000 * tax_rate - tax_qcd // 268080
```

```
fun(ads, usd, rmb, rate, qcd): ads * usd * rmb * (1 - rate) + qcd
fun(10000, 45, 7, tax_rate, tax_qcd) // 1914420
```

## settings

- decimal places

- rounding method

- reset settings

- copy outputs

## features

- line number

- sync scrolling

- change case

- <del>local storage</del>

- serialize script to url hash and deserialize

- console log

