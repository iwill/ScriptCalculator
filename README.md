ScriptCalculator
================

## calculation

- basic: `+`, `-`, `*`, `/`, `%`, `()`

- comments

- variables: `<last>`, `$`, `$n`

- functions

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

- Math & Number & Values

```
min(max(1, 2), 3) // 2
       pow(2, 10) // 1024
       sqrt(1024) // 32
```

```
round(2 / 3 * 100) / 100 // 0.67
floor(2 / 3 * 100) / 100 // 0.66
 ceil(2 / 3 * 100) / 100 // 0.67
```

```
2000 / 3   // 666.67
.round(3)  // 666.67
.floor(2)  // 666.67
.ceil(1)   // 666.7
.floor()   // 666
.floor(-1) // 660
.floor(-2) // 600
```

```
E  // 2.718281828459045
PI // 3.141592653589793
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

- sync scrolling

## settings & functions

- DecimalDigits

- RoundingMethod

- reset setting

- clear script

- TODO: export result

- TODO: share script

