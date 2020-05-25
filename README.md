ScriptCalculator
================

## calculation

- basic: `+`, `-`, `*`, `/`, `%`， `=`, `(` and `)`

- percentage: `%` if it's NOT followed by `number`, `variable`, `function` or `(`

- variables: `<last>`, `$`, `$ln`

- functions

- optional spaces

- comments

```
 1 + 2  //  1 + 2 == 3
   * 3  //  3 * 3 == 9
   - 4  //  9 - 4 == 5

10 / $  // 10 / 5 == 2
$0 % 2  //  3 % 2 == 1
   = 1  //  1 = 1 == true

10% + 1 // 0.1 + 1 == 1.1 // percentage
10% % 1 // 0.1 % 1 == 0.1 // percentage and remainder operation
10% - 7 // 0.1 - 7 == 6.9 // percentage
10  % (-7) // 10 % 7 == 3 // remainder operation
```

```
              tax_rate: 0.45 // 0.45
             tax_qcd: 181920 // 181920
1000000 * tax_rate - tax_qcd // 268080

f(ads, usd, rmb, rate, qcd): ads * usd * rmb * (1 - rate) + qcd
f(10000, 45, 7, tax_rate, tax_qcd) // 1914420
```

- builtin functions & values

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
ceil(_666, 1)   // 666.7
round(_666)     // 667
round(_666, -1) // 670
round(_666, -2) // 700
```

```
E  // 2.718281828459045
PI // 3.141592653589793
GR // 0.6180339887498949
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

