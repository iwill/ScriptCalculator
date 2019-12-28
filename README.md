ScriptCalculator
================

## calculation

- basic: `+`, `-`, `*`, `/`, `%`, `()`

- variables: `<last>`, `$`, `$n`

- functions

- comments

```
 1 + 2 // 3
   * 3 // 9
   - 4 // 5

10 / $ // 2
$1 % 2 // 1
```

```
              tax_rate: 0.45 // 0.45
             tax_qcd: 181920 // 181920
1000000 * tax_rate - tax_qcd // 268080

f(ads, usd, rmb, rate, qcd): ads * usd * rmb * (1 - rate) + qcd
f(10000, 20, 7, tax_rate, tax_qcd) // 951920.0000000001
```

- Math & values

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
floor(_666)     // 666
floor(_666, -1) // 660
floor(_666, -2) // 600
```

```
E  // 2.718281828459045
PI // 3.141592653589793
GR // 0.6180339887498949
```

- radix & format

```
0b10 // 2
0o10 // 8
10   // 10
0x10 // 16

format(32,  2) // 0b100000
format(32,  8) // 0o40
format(32, 10) // 32
format(32, 16) // 0x20
format(32, 32) // 10
format(32, 36) // W
$              // 32
```

## features

- line number

- local storage

- change case

- sync scrolling

## settings & functions

- DecimalDigits

- RoundingMethod

- reset setting

- clear script

- TODO: export result

- TODO: share script

