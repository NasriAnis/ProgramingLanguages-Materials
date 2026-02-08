| Format Specifier | Type / Meaning                                | Example Usage              |
| ---------------- | --------------------------------------------- | -------------------------- |
| `%d`             | Signed decimal integer (`int`)                | `printf("%d", -10);`       |
| `%i`             | Signed integer (same as `%d`)                 | `printf("%i", x);`         |
| `%u`             | Unsigned integer (`unsigned int`)             | `printf("%u", 20u);`       |
| `%ld`            | Long integer (`long`)                         | `printf("%ld", l);`        |
| `%lu`            | Unsigned long                                 | `printf("%lu", ul);`       |
| `%lld`           | Long long (`long long`)                       | `printf("%lld", ll);`      |
| `%llu`           | Unsigned long long                            | `printf("%llu", ull);`     |
| `%hd`            | Short integer (`short`)                       | `printf("%hd", s);`        |
| `%hu`            | Unsigned short                                | `printf("%hu", us);`       |
| `%f`             | Float or double (printed as decimal)          | `printf("%f", 3.14);`      |
| `%lf`            | Double (for `scanf`, not needed for `printf`) | `scanf("%lf", &d);`        |
| `%e`             | Scientific notation (lowercase e)             | `printf("%e", x);`         |
| `%E`             | Scientific notation (uppercase E)             | `printf("%E", x);`         |
| `%g`             | Automatically choose normal or scientific     | `printf("%g", x);`         |
| `%c`             | Single character                              | `printf("%c", 'A');`       |
| `%s`             | String (char array)                           | `printf("%s", str);`       |
| `%p`             | Pointer address                               | `printf("%p", ptr);`       |
| `%x`             | Hexadecimal (lowercase)                       | `printf("%x", 255); // ff` |
| `%X`             | Hexadecimal (uppercase)                       | `printf("%X", 255); // FF` |
| `%o`             | Octal                                         | `printf("%o", 8); // 10`   |
| `%%`             | Print % symbol                                | `printf("%%");`            |
## Special for scanf
|Format|Reads|
|---|---|
|`%d`|int|
|`%u`|unsigned int|
|`%f`|float|
|`%lf`|double|
|`%c`|char|
|`%s`|string (until space)|
|`%hd`|short|
|`%ld`|long|
|`%lld`|long long|
## Controling decimal precision
The general rule is: `%.Nf`
Where **N = number of digits after the decimal point**.

`%.Ng` chooses the best format and `%.Ne` for scientific notation

this method can be used also for strings.
## Controlling width + precision
You can also combine width and precision: `%W.Pf`
- `W` = minimum width
- `P` = number of decimals