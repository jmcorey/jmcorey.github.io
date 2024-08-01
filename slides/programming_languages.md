COMPUTE MECHANISMS AND PROGRAMMING LANGUAGES

-----

## DecSystem10 (Supercomputer)

![x](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/LCM_-_DEC_PDP-10_-_01.jpg/1024px-LCM_-_DEC_PDP-10_-_01.jpg)

-----
## Cray

![x](https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/EPFL_CRAY-I_1_clean.jpg/583px-EPFL_CRAY-I_1_clean.jpg)

-----
## Vacuum Tube based computer

![x](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/IBM_700_logic_module.jpg/640px-IBM_700_logic_module.jpg)

-----
## Electro-mechanical: Colossus (Bletchley Park)

![x](https://upload.wikimedia.org/wikipedia/commons/9/90/Colossus_Computer%2C_Bletchley_Park_-_geograph.org.uk_-_1590871.jpg)

-----
## Electro-mechanical Relay

![x](https://www.pollin.de/images/1200x1200x90/I340599.1-Leistungs-Relais-FUJITSU-FBR621D024-24-V-2-Wechsler.jpg)

-----
## Charles Babbage's Mechanical Computer

![x](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ac/AnalyticalMachine_Babbage_London.jpg/500px-AnalyticalMachine_Babbage_London.jpg)

-----
## Mechanical Cash Registers

![x](https://cdn.pixabay.com/photo/2016/11/07/12/35/cash-register-1805685_960_720.jpg)

-----
## Leibniz Mechanical Calculator

![x](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e9/Mechanical-calculator-Brunsviga-15-01.jpg/640px-Mechanical-calculator-Brunsviga-15-01.jpg)

-----
## Mysterious Antikythera
![x](https://upload.wikimedia.org/wikipedia/commons/6/66/NAMA_Machine_d%27Anticyth%C3%A8re_1.jpg)

-----
## Overarching themes of computer programming

* A mechanism that executes instructions
* A way to convey the instructions
* Control structures
* Possible I/O
* State (i.e. variable storage)

-----
## Numbers, calculations, strings, and memory

```
x = 13*12*11*10*9*8*7*6*5*4*3*2*1
y = "a grand day out"
```

-----
## I/O (Input/Output)

```
print("State your name! ")
z = input()
print("There are", len(z), "characters in your name.")
print("Assuming", z, "is your real name.")
```

```
State your name!
Boris Badinov
There are 13 characters in your name.
Assuming Boris Badinov is your real name.
```
<!-- .element: class="fragment" -->

-----
## If this then that

```
if z == "Boris Badinov":
    sys.exit()
else:
    print("Welcome!")
```

-----
## Loops

```
r = 1
x = 13
while x >= 1:
  r = r * x
  x = x - 1
print(r)
```

```
print(13*12*11*10*9*8*7*6*5*4*3*2*1)
```
<!-- .element: class="fragment" -->

```
6227020800
```
<!-- .element: class="fragment" -->

-----
## Subroutines/Functions/Procedures

```
def factorial(n):
  r = 1
  x = n
  while x >= 1:
    r = r * x
    x = x - 1
  return r
```

```
print(factorial(5) + 10 * factorial(3))
```
<!-- .element: class="fragment" -->

```
180
```
<!-- .element: class="fragment" -->

```
def factorial(n):
  if n <= 1:
    return 1
  else:
    return n * factorial(n - 1)
```
<!-- .element: class="fragment" -->

-----
## Builtin functions

Sometimes you need to enable them...

```
import math
x = math.pi / 2
print(2*math.sin(x) + 2*math.cos(x))
```

```
2.0
```
<!-- .element: class="fragment" -->

```
import random
print(random.randint(100,200))
```
<!-- .element: class="fragment" -->

```
144
```
<!-- .element: class="fragment" -->

-----
## Lists / Arrays

Items are stored in a sequence; you can ask for item # N...

```
a = [ " ♠ ", " ♥ ", " ♦ ", " ♣ " ]
x = len("Boris") % 4
print(a[x])
```

```
 ♥
```
<!-- .element: class="fragment" -->

```
s = "♠♥♦♣"
print(s[x])
```
<!-- .element: class="fragment" -->

-----
## Dictionaries (aka maps, lookup tables)

```
suitnames = { "♠":"spade", "♥":"heart", "♦":"diamond", "♣":"club" }
print(suitnames["♥"])
```

```
"heart"
```
<!-- .element: class="fragment" -->

-----
## Python

```
#!/usr/bin/python
i = 99
while i > 1:
    print(i, 'bottles of beer on the wall,', i, 'bottles of beer')
    print('Take one down and pass it around')
    i = i - 1
    print(i, 'bottles of beer on the wall.')
print('No more bottles of beer on the wall, no more bottles of beer')
print('Go to the store and buy some more, 99 bottles of beer on the wall')
```

-----
## C

```
#include <stdio.h>
int main()
{
  int i = 99;
  do {
    printf("%d bottles of beer on the wall, %d bottles of beer\n", i, i);
    printf("Take one down and pass it around\n");
    i = i - 1;
    printf("%d bottles of beer on the wall.\n", i);
  } while (i > 0);
  printf("No more bottles of beer on the wall, no more bottles of beer\n");
  printf("Go to the store and buy some more, 99 bottles of beer on the wall\n");
}
```

-----
## Pascal

```
PROGRAM Bottles;

VAR i : INTEGER;

BEGIN
  i := 99;
  REPEAT
    WRITELN(i, ' bottles of beer on the wall, ', i, ' bottles of beer');
    WRITELN('Take one down and pass it around');
    i := i-1;
    WRITELN(i, ' bottles of beer on the wall.');
  UNTIL i = 0;
  WRITELN('No more bottles of beer on the wall, no more bottles of beer');
  WRITELN('Go to the store and buy some more, 99 bottles of beer on the wall');
END.
```

-----
## Javascript

```
i = 99;
while (i > 1) {
  console.log(i + ' bottles of beer on the wall, ' + i + ' bottles of beer');
  console.log('Take one down and pass it around');
  i = i - 1;
  console.log(i + ' bottles of beer on the wall.');
} while (i > 0);
console.log('No more bottles of beer on the wall, no more bottles of beer');
console.log('Go to the store and buy some more, 99 bottles of beer on the wall');
```

-----
## LOLCAT

```
HAI
    VISIBLE "O HAI! IM IN UR BEERZ!"
    I HAS A VAR
    LOL VAR R 99
    IM IN YR LOOP
        VISIBLE VAR!
        VISIBLE " BOTTLZ OF BEER N TEH WALL, "!
        VISIBLE VAR!
        VISIBLE " BOTTLZ OF BEER!"
        VISIBLE "TAKE 1 DWN, PAS IT AROUN, "!
        NERFZ VAR!!
        IZ VAR LIEK 0?
            YARLY
                VISIBLE "NO MOAR"!
            NOWAI
                VISIBLE VAR!
        KTHX
        VISIBLE " BOTTLZ OF BEER N TEH WALL!"
        IZ VAR LIEK 0?
            GTFO
        KTHX
    KTHX
    VISIBLE "GIEV MOAR PLZ! KTHXBAI!"
KTHXBYE
```

-----
## Lisp

```
(define bottles
  (lambda (n)
    (cond ((= n 0) (display "No more bottles"))
          ((= n 1) (display "One bottle"))
          (else (display n) (display " bottles")))
    (display " of beer")))

(define beer
  (lambda (n)
    (if (> n 0)
        (begin
          (bottles n) (display " on the wall") (newline)
          (bottles n) (newline)
          (display "Take one down, pass it around") (newline)
          (bottles (- n 1)) (display " on the wall") (newline)
          (newline)
          (beer (- n 1))))))

(beer 99)
```

-----
## Piet

![x](https://upload.wikimedia.org/wikipedia/commons/d/d0/Piet_Program.gif)
![x](https://upload.wikimedia.org/wikipedia/commons/c/c2/Piet_Program_Hello_World%281%29.gif)

-----
## Whitespace
