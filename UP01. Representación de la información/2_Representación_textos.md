# REPRESENTACIÓN DE TEXTOS

## Introducción

Un ordenador solo maneja información en forma de números binarios: ceros y unos. Esto incluye el texto. Para que una máquina pueda almacenar, procesar y transmitir letras, dígitos o símbolos, es necesario establecer una correspondencia entre cada carácter y un número. A esta correspondencia se le llama **codificación de caracteres**.

El proceso tiene dos pasos:

1. **Asignar a cada carácter un número** (por ejemplo, la letra `A` es el 65).
2. **Guardar ese número como una secuencia de bytes**, según unas reglas concretas.

Para que dos sistemas se entiendan, deben usar la misma codificación. Si un texto se guarda con una y se lee con otra, los bytes se interpretan mal y aparecen los conocidos "caracteres raros" (`Ã±` en lugar de `ñ`). Es un problema muy habitual en administración de sistemas: ficheros de configuración, scripts, bases de datos o correos que se ven mal al moverse entre equipos.

A lo largo de la historia han convivido varias soluciones:

- **ASCII**, pensado para el inglés, con 128 caracteres.
- **Extensiones de 8 bits** como ISO 8859-1 (Latin-1), que añadieron los caracteres de las lenguas de Europa occidental, pero eran incompatibles entre sí.
- **Unicode**, que unifica en un único catálogo los caracteres de prácticamente todos los idiomas y que se guarda en bytes mediante codificaciones como UTF-8.

En este material se repasan ASCII y Unicode, sus diferencias y los problemas que resuelve cada uno.

## 1. ASCII (American Standard Code for Information Interchange)



ASCII es un sistema de codificación de caracteres que asigna un número entero a cada letra, dígito y símbolo, permitiendo que los ordenadores los almacenen y procesen como datos binarios.



### Características principales



- Usa \*\*7 bits\*\* por carácter, lo que permite representar \*\*128 caracteres\*\* (valores del 0 al 127).

- En la práctica se almacena en 1 byte (8 bits), dejando el bit más significativo libre (usado históricamente para paridad o para las extensiones de 8 bits).

- Fue desarrollado en los años 60 y es la base de casi todas las codificaciones de texto posteriores.



### Estructura de la tabla ASCII



| Rango | Contenido |

|---|---|

| 0–31 | Caracteres de control (no imprimibles): salto de línea, tabulador, retorno de carro, etc. |

| 32 | Espacio |

| 33–47 | Signos de puntuación (`!`, `"`, `#`, `%`...) |

| 48–57 | Dígitos `0` a `9` |

| 58–64 | Más signos (`:`, `;`, `<`, `=`, `>`, `?`, `@`) |

| 65–90 | Letras mayúsculas `A` a `Z` |

| 91–96 | Símbolos (`\[`, `\\`, `]`, `^`, `\_`, `` ` ``) |

| 97–122 | Letras minúsculas `a` a `z` |

| 123–127 | Símbolos y carácter de control DEL |



### Ejemplos de códigos



| Carácter | Decimal | Hexadecimal | Binario |

|---|---|---|---|

| `A` | 65 | 0x41 | 01000001 |

| `a` | 97 | 0x61 | 01100001 |

| `0` | 48 | 0x30 | 00110000 |

| Espacio | 32 | 0x20 | 00100000 |

| Salto de línea (LF) | 10 | 0x0A | 00001010 |



\*\*Dato útil:\*\* la diferencia entre una mayúscula y su minúscula es siempre 32 (el bit 0x20). Por ejemplo, `A` (65) y `a` (97).



### Limitaciones de ASCII



- Solo cubre el alfabeto inglés: \*\*no incluye\*\* `ñ`, vocales acentuadas (`á`, `é`...), ni símbolos como `€` o `£`.

- No sirve para lenguas no latinas (griego, cirílico, árabe, chino, etc.).

- Esto llevó a la aparición de extensiones de 8 bits (como ISO 8859-1 / Latin-1) y, finalmente, a Unicode.



---



## 2. Unicode



Unicode es un estándar que asigna un número único, llamado \*\*punto de código\*\*, a prácticamente todos los caracteres de todos los sistemas de escritura del mundo, además de símbolos, emojis y signos técnicos.



### Características principales



- Un punto de código se escribe como `U+XXXX`, en hexadecimal. Ejemplos: `U+0041` (`A`), `U+00F1` (`ñ`), `U+20AC` (`€`).

- Cubre más de 150.000 caracteres de más de 150 sistemas de escritura.

- Es compatible con ASCII: los primeros 128 puntos de código de Unicode coinciden exactamente con la tabla ASCII.

- \*\*Importante:\*\* Unicode define \*qué número\* tiene cada carácter. No define cómo se guarda ese número en bytes; para eso existen las codificaciones (UTF-8, UTF-16, UTF-32).



### Codificaciones de Unicode



| Codificación | Tamaño | Características | Uso típico |

|---|---|---|---|

| UTF-8 | 1 a 4 bytes (variable) | Compatible con ASCII en su primer byte; eficiente en espacio para texto en inglés | Web, Linux, estándar de facto en internet |

| UTF-16 | 2 o 4 bytes (variable) | Más eficiente que UTF-8 para algunos alfabetos asiáticos | Windows (interno), Java, JavaScript |

| UTF-32 | 4 bytes (fijo) | Simple de procesar, pero ocupa mucho espacio | Poco usado en la práctica |



### Ejemplos de codificación en UTF-8



| Carácter | Punto de código | Bytes en UTF-8 | Nº de bytes |

|---|---|---|---|

| `A` | U+0041 | `41` | 1 |

| `ñ` | U+00F1 | `C3 B1` | 2 |

| `€` | U+20AC | `E2 82 AC` | 3 |

| `😀` | U+1F600 | `F0 9F 98 80` | 4 |



### El problema de los "caracteres raros"



Cuando un archivo de texto se guarda con una codificación (por ejemplo, UTF-8) y se abre interpretándolo con otra (por ejemplo, ANSI/Windows-1252), los bytes se interpretan mal y aparecen símbolos extraños.



\*\*Ejemplo clásico:\*\* la `ñ` en UTF-8 son los bytes `C3 B1`. Si un programa los interpreta como Windows-1252, cada byte se lee como un carácter distinto, mostrando `Ã±` en vez de `ñ`.



### Relación ASCII – Latin-1 – Unicode



- ASCII (7 bits, 128 caracteres) ⊂ Latin-1 / ISO 8859-1 (8 bits, 256 caracteres) ⊂ Unicode (más de 150.000 caracteres)

- Los primeros 256 puntos de código de Unicode coinciden con Latin-1.

- UTF-8, UTF-16 y UTF-32 son formas distintas de codificar \*cualquier\* carácter de Unicode en bytes; Latin-1 no forma parte de la familia Unicode, aunque sus primeros caracteres coincidan.



---



## 3. Ejercicio propuesto



1\. Abrir un editor hexadecimal (por ejemplo, `Format-Hex` en PowerShell o `xxd` en Linux).

2\. Crear un archivo de texto con la palabra `España` y guardarlo en UTF-8.

3\. Observar los bytes correspondientes a la `ñ` (`C3 B1`).

4\. Reabrir el mismo archivo indicando la codificación ANSI/Windows-1252 y comprobar que aparece como `EspaÃ±a`.

5\. Repetir el proceso guardando el archivo como ANSI y comparar el tamaño en bytes con la versión UTF-8.

