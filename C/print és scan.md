# Print és scan

C-ben a kiírás és beolvasás nem túl egyszerű.
Ez egy cheat sheet az említettekhez.

## Függvények

### Kiírás

`printf(string format, T... values);`

Példa:
```c
printf("Csáki kora: %d", 19);
```

- az első paraméterhez írjuk a formázást, hogy hogyan jelenjen meg a kiírt érték
- a második paraméterben helyettesítjük be a formázandó részeket valós értékekkel

### Beolvasás

`scanf(string format, T value);`

Példa:
```c
scanf("%d", &x);
```

- a második paraméter a változó, amibe tároljuk a beolvasott értéket

## Formázás

`%[flag-ek][szélesség][.pontosság]specifikáló`

Példa:
```c
printf("PI eleje: %4.2f %+.0e %E \n", 3.1416, 3.1416, 3.1416);
// KIMENET
PI eleje: 3.14 +3e+000 3.141600E+000
```

### Specifikálók

| Jel   | Kimenet                                       | Példa              |
| ----- | --------------------------------------------- | ------------------ |
| d / i | int                                           | 392                |
| u     | unsigned int                                  | 7235               |
| x     | hex int                                       | 7fa                |
| X     | hex int nagy betűkkel                         | 7FA                |
| f / F | float                                         | 392.65             |
| e     | normál alakos float                           | 3.9265e+2          |
| E     | normál alakos float                           | 3.9265E+2          |
| g / G | float-ot írja ki rendesen vagy normál alakban | 392.65 / 3.9265e+2 |
| a     | hex float                                     | -0xc.90fep-2       |
| A     | hex float nagy betűvel                        | -0XC.90FEP-2       |
| c     | karakter                                      | a                  |
| s     | string / char*                                | abc                |
| p     | pointer address / mutató címe                 | b8000000           |
| n     | Literálisan semmi, ezt nem értem.             |                    |
| %     | a % karakter maga                             | %                  |

### Flag-ek

| Jel      | Leírás                                                  | Példa (_ = space)         |
| -------- | ------------------------------------------------------- | ------------------------- |
| -        | Balra rendezi a kiírt értéket ahogy hely engedi.        | 3.14__ (ha a szélesség 6) |
| +        | Kényszeríti a szám értékekhez a +- jeleket.             | +392                      |
| [szóköz] | Nem negatív számoknál szóköz a + jel helyén.            | _392                      |
| 0        | Nullákkal tölti ki a szabad helyeket a padding alapján. | 0392                      |

### Szélesség

- minimum kiírandó karakterek száma
- ha nincs meg a minimum szám, a maradék hely kitöltésre kerül (szóközökkel)
- *-gal lehet jelezni, ha paraméterként adjuk meg a szélességet

### Pontosság

| Specifikálók     | Működés                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------ |
| d, i, u, x, X    | Ugyanaz, mint a szélesség csak nullákkal. Ha az érték és pontosság 0, akkor nincs kimenet. |
| a, A, e, E, f, F | A tizetesvessző után kiírt helyiértékek száma. Alapértelmezetten 6.                        |
| g, G             | Maximum kiírandó számok száma. (what? please help)                                         |
| s                | Maximum kiírandó karakterek száma.                                                         |

- ha a . után nem írunk se számot, se *-ot, akkor a fordító 0-t feltételez
- *-gal lehet jelezni, ha paraméterként adjuk meg a pontosságot