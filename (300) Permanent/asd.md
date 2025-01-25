## zad 1 (5pkt)
czy program jest częściowo paprawny względem podanych pre- i post warunków?

1. {x+y >= 0} if x < 0 then y:= y * y+1 else x := x * x+1 {xy > 0}   |    yes / no / kontrprzykład x = ? y = ? -> `no x = -1, y= dowolne`

2. {x>y} x:= x * x + 1; y := y * y+ 2 {x < y -1} | `robione na tablicy logiką hoara`
$$
\{x^2 + 1 < y^2 + 1\}x := x^2 + 1 \{x < y^2 +2 -1 \} y = y^2 + 2 \{x < y - 1\}
$$
$$
x > y + x^2 < y^2 \{x^2 < y^2\} x := x^2 + 1, y:= y^2+1 \{x < y-1\}
$$
`no, x = 2, y = 1`

3. $\{x + y > 0\} \quad \text{if}(x<y)\quad \text{then}\quad y:= y-x \quad \text{else} \quad x:=x-y \{x+y>=0\}$
`robione logiką hoara` 
4. $\{x > 0 , y  > x \} \quad \text{while} \quad (x<y) \quad \text{do} \quad x:=x+1 \{x = y\}$
5. $\{y > 0, 0 < x\} \quad \text{while} \quad (x<y) \quad \text{do} \quad x: =x+ 1 \{x = y\}$

punkty: prawidłowe `yes` 1pkt, prawidłowe `no` 0.5pkt + kontrprzykład 0.5pkt

## zad 2 (3pkt)
czy program:
```
while (x < y) do
    if(x*2) < y) then x:= x *2 
    else y:= y - 2

```

ma własność stopu dla x oraz y typu integer spełniających warunek: 
1. $0 < y ,0 < x$ | `yes` / no + kontrprzykład x = ? y = ?
2. 0 < y & x <yx | yes / `no` + kontrprzykład x = `dowolny ujemny` y = `dowolny`
3. 0 < y * x | yes / `no` + kontrprzykład x = `-2` y = `-1`

odp
$t(x, y) = y - x + 1 >= 0 \quad dla \quad x, y > 0$
$t > x \quad and \quad 2x < y \implies x' = 2x,  y' = y$

## zad 3 (6pkt)
asymptotyczne funkcje porównanie ze sobą
$n^2 = \dots(n^2 + 20000n)$
$\ln n = \dots \log_{2} n$
$1,01^n = \dots n^{1000}$
$\ln n = \dots n^{\frac{1}{2}}$
$n^3 = \dots n^2$
$3^n = \dots 2^{\ln n^2}$

przypomnienie do ostatniego:
    $\log_{2} 3^a = \log_{2}2^x = x$

## zad 4 (4pkt)
rekursja uniwersalna
1. $T(1) = const\dots T(n) = 2T\left( \frac{n}{4} \right) + n^{\frac{1}{2}}$

## zad 5 (5pkt)
określ rząd funkcji T(N) gdzie T(N) = liczba mnożeń wykonanych przez poniższy program zakładając że początkowo zmienna n typu integer ma wartość N
```
res := 1; k:= 0
while (n > k) do {
    i := 0
    while(i < k){
        res := res + i*n
        i := i + 2
        k := k + 1
    }
}
```

$T(N) = \theta(\infty)$

```
res := 1; k:= 0
while(n>k) do {
    i := 0
    while( i < k){
        res := res + i * n
        i := i + 1
    }
    k := k + 1
}
```
$T(N) = \theta()$

```
def f (x: float; i: int): float = {
    if (i==0) 1.0
    else if (even(i)) f(x * x, i/2)
    else f(x-1.0, i-1) * i
}
read(x, n); println(f(x, n))
```