# UNIDAD 1: Representación y comunicación de la información

## Introducción

### ¿Cómo representan información los ordenadores?

Los ordenadores son dispositivos **digitales** que trabajan con señales eléctricas que pueden estar en dos estados:
- **Presencia de tensión** (generalmente 5V o 3.3V) → Estado **1**
- **Ausencia de tensión** (0V) → Estado **0**

Esta característica de dos estados hace que los ordenadores trabajen internamente con el **sistema binario**, que solo utiliza dos dígitos: 0 y 1.

### Bit: La unidad básica

Un **bit** (binary digit) es la unidad mínima de información y puede tener dos valores:
- **0** (apagado, falso, no)
- **1** (encendido, verdadero, sí)

### De los bits a la información útil

La cantidad de información que se puede representar depende del número de bits disponibles:

| Número de bits | Combinaciones posibles | Fórmula | Ejemplo de valores |
|----------------|------------------------|---------|-------------------|
| 1 bit | 2 | 2¹ | 0, 1 |
| 2 bits | 4 | 2² | 00, 01, 10, 11 |
| 3 bits | 8 | 2³ | 000, 001, 010, 011, 100, 101, 110, 111 |
| 4 bits | 16 | 2⁴ | 0000 a 1111 |
| 8 bits | 256 | 2⁸ | 00000000 a 11111111 |
| 16 bits | 65.536 | 2¹⁶ | - |
| 32 bits | 4.294.967.296 | 2³² | - |

**Regla general:** Con **n bits** se pueden representar **2ⁿ combinaciones diferentes**

---

## 1. SISTEMAS DE NUMERACIÓN

### ¿Qué es un sistema de numeración?

Un **sistema de numeración** es un conjunto de símbolos y reglas que permiten representar cantidades de forma consistente y única.

### Elementos fundamentales

**Base:** Es el número de símbolos diferentes que utiliza el sistema. Determina cuántos dígitos distintos existen.
**Dígitos:** Son los símbolos utilizados para construir los números. Van desde 0 hasta (base - 1).
**Valor posicional:** El valor de cada dígito depende de su posición en el número. Cada posición representa una potencia de la base.

### Sistemas de numeración en informática

| Sistema | Base | Dígitos | Notación | Uso principal |
|---------|------|---------|----------|---------------|
| **Decimal** | 10 | 0-9 | 125₁₀ o 125 | Uso humano cotidiano |
| **Binario** | 2 | 0, 1 | 1101₂ o 0b1101 | Representación interna |
| **Octal** | 8 | 0-7 | 755₈ o 0o755 | Permisos UNIX/Linux |
| **Hexadecimal** | 16 | 0-9, A-F | 2AF₁₆ o 0x2AF | Direcciones, colores |

### ¿Por qué diferentes sistemas?

- **Binario:** Es el lenguaje natural del ordenador (electricidad on/off)
- **Octal:** Agrupa bits de 3 en 3, más compacto que binario
- **Hexadecimal:** Agrupa bits de 4 en 4, muy compacto y legible
- **Decimal:** Es el que usamos los humanos habitualmente

---

## 2. SISTEMA DECIMAL (BASE 10)

### Características

- **Base:** 10
- **Dígitos:** 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
- **Sistema posicional:** Cada posición vale 10 veces más que la anterior
- **Sistema más común:** Es el que utilizamos en la vida diaria

### Valor posicional

En el número **3.527₁₀**:

```
Posiciones:    3      5      2      7
               ↓      ↓      ↓      ↓
Potencias:    10³    10²    10¹    10⁰
               ↓      ↓      ↓      ↓
Valores:     1000    100     10      1
               ↓      ↓      ↓      ↓
Resultado:   3000  + 500  +  20  +  7  = 3.527
```

### Fórmula general

Para cualquier número decimal:

**N = dₙ × 10ⁿ + dₙ₋₁ × 10ⁿ⁻¹ + ... + d₁ × 10¹ + d₀ × 10⁰**

Donde dₙ, dₙ₋₁, ..., d₁, d₀ son los dígitos del número.

### Ejemplo detallado

**4.806₁₀** = 4×10³ + 8×10² + 0×10¹ + 6×10⁰
           = 4×1000 + 8×100 + 0×10 + 6×1
           = 4000 + 800 + 0 + 6
           = **4.806**

---

## 3. SISTEMA BINARIO (BASE 2)

### Características

- **Base:** 2
- **Dígitos:** 0, 1 (llamados bits)
- **Sistema fundamental** en informática
- **Notación:** Se añade subíndice ₂ o prefijo 0b

### Valor posicional

En el número binario **1101₂**:

```
Posiciones:    1      1      0      1
               ↓      ↓      ↓      ↓
Potencias:    2³     2²     2¹     2⁰
               ↓      ↓      ↓      ↓
Valores:       8      4      2      1
               ↓      ↓      ↓      ↓
Resultado:     8  +   4  +   0  +   1  = 13₁₀
```

### Tabla de potencias de 2 (memorizar)

| Posición | 2⁰ | 2¹ | 2² | 2³ | 2⁴ | 2⁵ | 2⁶ | 2⁷ | 2⁸ | 2⁹ | 2¹⁰ |
|----------|----|----|----|----|----|----|----|----|----|----|-----|
| **Valor** | 1 | 2 | 4 | 8 | 16 | 32 | 64 | 128 | 256 | 512 | 1024 |

### Tabla de equivalencias (4 bits)

| Binario | Decimal | Binario | Decimal |
|---------|---------|---------|---------|
| 0000 | 0 | 1000 | 8 |
| 0001 | 1 | 1001 | 9 |
| 0010 | 2 | 1010 | 10 |
| 0011 | 3 | 1011 | 11 |
| 0100 | 4 | 1100 | 12 |
| 0101 | 5 | 1101 | 13 |
| 0110 | 6 | 1110 | 14 |
| 0111 | 7 | 1111 | 15 |

### Ejemplos de números binarios

- **10₂** = 2₁₀
- **100₂** = 4₁₀
- **1000₂** = 8₁₀
- **10000₂** = 16₁₀
- **11111111₂** = 255₁₀ (valor máximo con 8 bits)
- **10000000₂** = 128₁₀ (bit más significativo de un byte)

### Terminología importante

- **Bit más significativo (MSB):** El bit de la izquierda, con mayor valor
- **Bit menos significativo (LSB):** El bit de la derecha, con menor valor
- **Byte:** Conjunto de 8 bits (puede representar valores de 0 a 255)

---

## 4. SISTEMA OCTAL (BASE 8)

### Características

- **Base:** 8
- **Dígitos:** 0, 1, 2, 3, 4, 5, 6, 7
- **Notación:** Subíndice ₈ o prefijo 0o
- **Uso principal:** Permisos de archivos en sistemas UNIX/Linux

### Valor posicional

En el número octal **753₈**:

```
Posiciones:    7      5      3
               ↓      ↓      ↓
Potencias:    8²     8¹     8⁰
               ↓      ↓      ↓
Valores:      64      8      1
               ↓      ↓      ↓
Resultado:   448  +  40  +   3  = 491₁₀
```

### Relación con el sistema binario

**Cada dígito octal equivale exactamente a 3 bits:**

| Octal | Binario (3 bits) | Decimal |
|-------|------------------|---------|
| 0 | 000 | 0 |
| 1 | 001 | 1 |
| 2 | 010 | 2 |
| 3 | 011 | 3 |
| 4 | 100 | 4 |
| 5 | 101 | 5 |
| 6 | 110 | 6 |
| 7 | 111 | 7 |

Esta relación hace que sea muy fácil convertir entre binario y octal.

### Aplicación práctica: Permisos en Linux

En sistemas UNIX/Linux, los permisos de archivos se expresan en octal:

```
chmod 755 archivo.txt
```

Cada dígito representa permisos para:
- **Primer dígito (7):** Propietario
- **Segundo dígito (5):** Grupo
- **Tercer dígito (5):** Otros usuarios

Donde cada dígito es la suma de:
- **4** = Lectura (r)
- **2** = Escritura (w)
- **1** = Ejecución (x)

Ejemplos:
- **7** = 4+2+1 = rwx (todos los permisos)
- **6** = 4+2 = rw- (lectura y escritura)
- **5** = 4+1 = r-x (lectura y ejecución)
- **4** = r-- (solo lectura)

---

## 5. SISTEMA HEXADECIMAL (BASE 16)

### Características

- **Base:** 16
- **Dígitos:** 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F
- **Notación:** Subíndice ₁₆, prefijo 0x o #
- **Muy utilizado** por su compacidad y legibilidad

### Tabla de equivalencias completa

| Hex | Decimal | Binario (4 bits) | Hex | Decimal | Binario (4 bits) |
|-----|---------|------------------|-----|---------|------------------|
| 0 | 0 | 0000 | 8 | 8 | 1000 |
| 1 | 1 | 0001 | 9 | 9 | 1001 |
| 2 | 2 | 0010 | A | 10 | 1010 |
| 3 | 3 | 0011 | B | 11 | 1011 |
| 4 | 4 | 0100 | C | 12 | 1100 |
| 5 | 5 | 0101 | D | 13 | 1101 |
| 6 | 6 | 0110 | E | 14 | 1110 |
| 7 | 7 | 0111 | F | 15 | 1111 |

### Valor posicional

En el número hexadecimal **2A3F₁₆**:

```
Posiciones:     2       A       3       F
                ↓       ↓       ↓       ↓
Potencias:    16³     16²     16¹     16⁰
                ↓       ↓       ↓       ↓
Valores:     4096     256      16       1
                ↓       ↓       ↓       ↓
Cálculo:     8192 + 2560 +   48  +   15  = 10.815₁₀
             (2×4096) (10×256) (3×16) (15×1)
```

### Relación con el sistema binario

**Cada dígito hexadecimal equivale exactamente a 4 bits:**

Esto hace que 2 dígitos hexadecimales = 1 byte (8 bits).

**Ejemplo:**
```
Hexadecimal:    A       F       3       9
                ↓       ↓       ↓       ↓
Binario:      1010    1111    0011    1001
                ↓       ↓       ↓       ↓
Completo:     1010111100111001₂
```

### Notaciones comunes

- **Lenguajes de programación (C, C++, Java, Python):** 0x2A
- **Colores HTML/CSS:** #FF5733
- **Ensamblador:** 2Ah o $2A
- **Direcciones de memoria:** 0x7FFF5FBFF8A0

---

## 6. CONVERSIONES ENTRE SISTEMAS DE NUMERACIÓN

### 6.1 De Binario a Decimal

**Método:** Multiplicar cada bit por su peso (potencia de 2) y sumar todos los resultados.

**Ejemplo 1:** Convertir **10110₂** a decimal

```
Paso 1: Identificar posiciones y potencias de 2
Binario:     1      0      1      1      0
Posición:    4      3      2      1      0
Potencia:   2⁴     2³     2²     2¹     2⁰
Valor:      16      8      4      2      1

Paso 2: Multiplicar cada bit por su peso
           1×16 + 0×8 + 1×4 + 1×2 + 0×1

Paso 3: Sumar los resultados
            16  +  0  +  4  +  2  +  0  = 22₁₀
```

**Ejemplo 2:** Convertir **11111111₂** a decimal

```
128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255₁₀
```

---

### 6.2 De Decimal a Binario

**Método:** Divisiones sucesivas entre 2, anotando los restos. El resultado se lee de abajo hacia arriba.

**Ejemplo 1:** Convertir **45₁₀** a binario

```
División    Cociente    Resto
45 ÷ 2  =      22         1    ← LSB (bit menos significativo)
22 ÷ 2  =      11         0
11 ÷ 2  =       5         1
 5 ÷ 2  =       2         1
 2 ÷ 2  =       1         0
 1 ÷ 2  =       0         1    ← MSB (bit más significativo)

Resultado (leer de abajo hacia arriba): 101101₂
```

**Verificación:** 32 + 8 + 4 + 1 = 45 ✓

**Ejemplo 2:** Convertir **100₁₀** a binario

```
100 ÷ 2 = 50    resto 0
 50 ÷ 2 = 25    resto 0
 25 ÷ 2 = 12    resto 1
 12 ÷ 2 = 6     resto 0
  6 ÷ 2 = 3     resto 0
  3 ÷ 2 = 1     resto 1
  1 ÷ 2 = 0     resto 1

Resultado: 1100100₂
```

---

### 6.3 De Binario a Octal

**Método:** Agrupar de 3 en 3 bits (de derecha a izquierda) y convertir cada grupo.

**Ejemplo 1:** Convertir **101110011₂** a octal

```
Paso 1: Agrupar de 3 en 3 desde la derecha
        101  110  011

Paso 2: Convertir cada grupo
         5    6    3

Resultado: 563₈
```

**Ejemplo 2:** Convertir **11010101₂** a octal

```
Agrupar:     011  010  101
Convertir:    3    2    5

Resultado: 325₈
```

---

### 6.4 De Octal a Binario

**Método:** Convertir cada dígito octal a su equivalente de 3 bits.

**Ejemplo 1:** Convertir **726₈** a binario

```
Octal:        7         2         6
              ↓         ↓         ↓
Binario:     111       010       110

Resultado: 111010110₂
```

**Ejemplo 2:** Convertir **345₈** a binario

```
3 = 011
4 = 100
5 = 101

Resultado: 011100101₂ = 11100101₂
```

---


### 6.5 De Binario a Hexadecimal

**Método:** Agrupar de 4 en 4 bits (de derecha a izquierda) y convertir cada grupo a su equivalente hexadecimal.

**Ejemplo 1:** Convertir **10110101111₂** a hexadecimal

```
Paso 1: Agrupar de 4 en 4 desde la derecha
        (rellenar con ceros a la izquierda si es necesario)
        0101  1010  1111

Paso 2: Convertir cada grupo
         5     A     F

Resultado: 5AF₁₆
```

**Ejemplo 2:** Convertir **11011010₂** a hexadecimal

```
Agrupar:    1101  1010
Convertir:    D     A

Resultado: DA₁₆
```

---

### 6.6 De Hexadecimal a Binario

**Método:** Convertir cada dígito hexadecimal a su equivalente de 4 bits.

**Ejemplo 1:** Convertir **3C9₁₆** a binario

```
Hexadecimal:    3         C         9
                ↓         ↓         ↓
Binario:      0011      1100      1001

Resultado: 001111001001₂ 
Simplificado: 1111001001₂
```

**Ejemplo 2:** Convertir **BEAD₁₆** a binario

```
B = 1011
E = 1110
A = 1010
D = 1101

Resultado: 1011111010101101₂
```

---

### 6.7 De Octal a Decimal

**Método 1:** Multiplicar cada dígito por su peso (potencia de 8) y sumar.
**Método 2:** Convertir primero a binario y luego a decimal.

**Ejemplo 1:** Convertir **345₈** a decimal

```
Octal:        3        4        5
              ↓        ↓        ↓
Potencias:   8²       8¹       8⁰
              ↓        ↓        ↓
Valores:     64        8        1
              ↓        ↓        ↓
Cálculo:   3×64  +  4×8  +  5×1
            192  +   32  +   5   = 229₁₀
```

**Ejemplo 2:** Convertir **777₈** a decimal

```
Binario: 111111111₂
Decimal: 256 + 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 511₁₀
```

---

### 6.8 De Decimal a Octal

**Método 1:** Divisiones sucesivas entre 8, anotando los restos.
**Método 2:** Convertir primero a binario y luego a octal.

**Ejemplo 1:** Convertir **253₁₀** a octal

```
División    Cociente    Resto
253 ÷ 8  =     31         5    ← Dígito menos significativo
 31 ÷ 8  =      3         7
  3 ÷ 8  =      0         3    ← Dígito más significativo

Resultado (leer de abajo hacia arriba): 375₈
```

**Verificación:** 3×64 + 7×8 + 5×1 = 192 + 56 + 5 = 253 ✓

**Ejemplo 2:** Convertir **100₁₀** a octal

```
Binario: 1100100₂
Resultado: 144₈
```

---

### 6.9 De Hexadecimal a Decimal

**Método 1:** Multiplicar cada dígito por su peso (potencia de 16) y sumar.
**Método 2:** Convertir primero a binario y luego a decimal.

**Ejemplo 1:** Convertir **1F4₁₆** a decimal

```
Hexadecimal:    1        F        4
                ↓        ↓        ↓
Potencias:    16²      16¹      16⁰
                ↓        ↓        ↓
Valores:      256       16        1
                ↓        ↓        ↓
Cálculo:    1×256 + 15×16 + 4×1
              256  +  240  +  4   = 500₁₀
```

**Ejemplo 2:** Convertir **A0B₁₆** a decimal

```
Binario: 101000001011₂
Decimal: 2048 + 512 + 8 + 2 + 1 = 2571₁₀
```

---

### 6.10 De Decimal a Hexadecimal

**Método 1:** Divisiones sucesivas entre 16, anotando los restos.
**Método 2:** Convertir primero a binario y luego a hexadecimal.

**Ejemplo 1:** Convertir **2748₁₀** a hexadecimal

```
División      Cociente    Resto (Hex)
2748 ÷ 16  =    171         12 (C)    ← Dígito menos significativo
 171 ÷ 16  =     10         11 (B)
  10 ÷ 16  =      0         10 (A)    ← Dígito más significativo

Resultado (leer de abajo hacia arriba): ABC₁₆
```

**Verificación:** A×256 + B×16 + C×1 = 10×256 + 11×16 + 12 = 2560 + 176 + 12 = 2748 ✓

**Ejemplo 2:** Convertir **255₁₀** a hexadecimal

```
Binario: 11111111₂
Hexadecimal: FF₁₆
```

---

### 6.11 De Octal a Hexadecimal (vía binario)

**Método:** Convertir primero a binario y luego a hexadecimal.

**Ejemplo:** Convertir **765₈** a hexadecimal

```
Paso 1: Octal a binario
7 = 111
6 = 110
5 = 101
Binario: 111110101₂

Paso 2: Agrupar en 4 bits y convertir a hex
0001  1111  0101
  1     F     5

Resultado: 1F5₁₆
```

---

### 6.12 De Hexadecimal a Octal (vía binario)

**Método:** Convertir primero a binario y luego a octal.

**Ejemplo:** Convertir **3D₁₆** a octal

```
Paso 1: Hexadecimal a binario
3 = 0011
D = 1101
Binario: 00111101₂

Paso 2: Agrupar en 3 bits y convertir a octal
000  111  101
 0    7    5

Resultado: 075₈ = 75₈
```

---

### 6.13 Tabla resumen de conversiones

| Origen → Destino | Método |
|------------------|--------|
| **Binario → Decimal** | Multiplicar cada bit por potencia de 2 y sumar |
| **Decimal → Binario** | Divisiones sucesivas entre 2 |
| **Binario → Octal** | Agrupar de 3 en 3 bits |
| **Octal → Binario** | Cada dígito octal = 3 bits |
| **Binario → Hexadecimal** | Agrupar de 4 en 4 bits |
| **Hexadecimal → Binario** | Cada dígito hex = 4 bits |
| **Decimal → Octal** | Divisiones sucesivas entre 8 / Convertir vía binario |
| **Octal → Decimal** | Multiplicar cada dígito por potencia de 8 y sumar / Convertir vía binario |
| **Decimal → Hexadecimal** | Divisiones sucesivas entre 16 / Convertir vía binario |
| **Hexadecimal → Decimal** | Multiplicar cada dígito por potencia de 16 y sumar / Convertir vía binario |
| **Octal ↔ Hexadecimal** | Convertir vía binario |
| **Hexadecimal ↔ Octal** | Convertir vía binario |

---

## 7. APLICACIONES PRÁCTICAS EN INFORMÁTICA

### 7.1 Colores en diseño web (HTML/CSS)

Los colores se representan en hexadecimal con el formato **#RRGGBB**:
- **RR:** Componente rojo (00 a FF)
- **GG:** Componente verde (00 a FF)
- **BB:** Componente azul (00 a FF)

**Ejemplos:**
- **#FFFFFF** = Blanco (R:255, G:255, B:255)
- **#000000** = Negro (R:0, G:0, B:0)
- **#FF0000** = Rojo puro (R:255, G:0, B:0)
- **#00FF00** = Verde puro (R:0, G:255, B:0)
- **#0000FF** = Azul puro (R:0, G:0, B:255)
- **#FFA500** = Naranja (R:255, G:165, B:0)

**Desglose del color #3498DB:**
```
#3498DB
 ││││││
 ││││└└─ BB = DB₁₆ = 219₁₀ (Componente azul)
 ││└└─── GG = 98₁₆ = 152₁₀ (Componente verde)
 └└───── RR = 34₁₆ = 52₁₀  (Componente rojo)
```

### 7.2 Direcciones IP (IPv4)

Una dirección IP está formada por 4 octetos (bytes) en notación decimal separados por puntos.

**Ejemplo:** **192.168.1.254**

Conversión a binario:
```
192₁₀ = 11000000₂
168₁₀ = 10101000₂
  1₁₀ = 00000001₂
254₁₀ = 11111110₂

Dirección IP completa en binario:
11000000.10101000.00000001.11111110
```

En hexadecimal:
```
C0.A8.01.FE  (o en forma compacta: C0A801FE)
```

**Máscaras de subred:**
- **255.255.255.0** = 11111111.11111111.11111111.00000000 (24 bits activos)
- **255.255.0.0** = 11111111.11111111.00000000.00000000 (16 bits activos)

### 7.3 Direcciones MAC

Las direcciones MAC identifican de forma única cada tarjeta de red y se expresan en hexadecimal.

**Formato:** 6 bytes (48 bits) separados por ":" o "-"

**Ejemplo:** **A4:5E:60:E7:3B:2F**

Conversión a binario:
```
A4 = 10100100
5E = 01011110
60 = 01100000
E7 = 11100111
3B = 00111011
2F = 00101111

Completo: 101001000101111001100000111001110011101100101111
```

Conversión a decimal (cada octeto):
```
A4₁₆ = 164₁₀
5E₁₆ = 94₁₀
60₁₆ = 96₁₀
E7₁₆ = 231₁₀
3B₁₆ = 59₁₀
2F₁₆ = 47₁₀
```

### 7.4 Permisos de archivos en Linux/UNIX

Los permisos se expresan en octal con 3 dígitos:

**Formato:** **[Propietario][Grupo][Otros]**

Cada dígito es la suma de:
- **4** = Lectura (r)
- **2** = Escritura (w)
- **1** = Ejecución (x)

**Ejemplos comunes:**

| Octal | Binario | Permisos | Significado |
|-------|---------|----------|-------------|
| 777 | 111 111 111 | rwxrwxrwx | Todos los permisos para todos |
| 755 | 111 101 101 | rwxr-xr-x | Propietario todo, demás lectura/ejecución |
| 644 | 110 100 100 | rw-r--r-- | Propietario lee/escribe, demás solo leen |
| 600 | 110 000 000 | rw------- | Solo propietario lee/escribe |
| 666 | 110 110 110 | rw-rw-rw- | Todos leen/escriben, nadie ejecuta |

**Ejemplo detallado de chmod 755:**
```
7 = 4+2+1 = 111₂ = rwx (Propietario: lectura, escritura, ejecución)
5 = 4+1   = 101₂ = r-x (Grupo: lectura y ejecución)
5 = 4+1   = 101₂ = r-x (Otros: lectura y ejecución)
```

### 7.5 Direcciones de memoria

Las direcciones de memoria en sistemas de 32 o 64 bits se expresan en hexadecimal.

**Ejemplos:**
- **Dirección de 32 bits:** 0x7FFF5A3C
- **Dirección de 64 bits:** 0x00007FFF5FBFF8A0

**Ventajas del hexadecimal para memoria:**
- 1 byte = exactamente 2 dígitos hexadecimales
- Mucho más compacto que binario
- Más legible que decimal para este propósito

### 7.6 Códigos de caracteres

**ASCII (American Standard Code for Information Interchange):**

Los caracteres se codifican con números que pueden expresarse en diferentes bases:

| Carácter | Decimal | Hexadecimal | Binario |
|----------|---------|-------------|---------|
| A | 65 | 0x41 | 01000001 |
| a | 97 | 0x61 | 01100001 |
| 0 | 48 | 0x30 | 00110000 |
| Espacio | 32 | 0x20 | 00100000 |
| Enter | 10 | 0x0A | 00001010 |

### 7.7 Puertos de red

Los puertos de red se numeran de 0 a 65535 (16 bits = 2¹⁶ - 1):

| Puerto | Decimal | Hexadecimal | Servicio |
|--------|---------|-------------|----------|
| HTTP | 80 | 0x0050 | Web |
| HTTPS | 443 | 0x01BB | Web segura |
| FTP | 21 | 0x0015 | Transferencia archivos |
| SSH | 22 | 0x0016 | Terminal remoto seguro |
| DNS | 53 | 0x0035 | Resolución nombres |

### 7.8 Códigos de error

Muchos sistemas muestran códigos de error en hexadecimal:

**Ejemplo de Windows:**
- **0x80004005:** Error no especificado
- **0x80070002:** No se encuentra el archivo

**En binario:** 0x80004005 = 10000000000000000100000000000101₂

---

## 8. EJERCICIOS RESUELTOS

### Ejercicio 1: Binario → Decimal

**Enunciado:** Convertir **11010110₂** a decimal

**Solución:**
```
Posiciones:  7   6   5   4   3   2   1   0
Binario:     1   1   0   1   0   1   1   0
Potencias:  2⁷  2⁶  2⁵  2⁴  2³  2²  2¹  2⁰
Valores:   128  64  32  16   8   4   2   1

Cálculo:
1×128 + 1×64 + 0×32 + 1×16 + 0×8 + 1×4 + 1×2 + 0×1
= 128 + 64 + 16 + 4 + 2
= 214₁₀
```

**Respuesta:** 214₁₀

---

### Ejercicio 2: Decimal → Binario

**Enunciado:** Convertir **156₁₀** a binario

**Solución:**
```
156 ÷ 2 = 78   resto 0  ← LSB
 78 ÷ 2 = 39   resto 0
 39 ÷ 2 = 19   resto 1
 19 ÷ 2 = 9    resto 1
  9 ÷ 2 = 4    resto 1
  4 ÷ 2 = 2    resto 0
  2 ÷ 2 = 1    resto 0
  1 ÷ 2 = 0    resto 1  ← MSB

Leyendo de abajo hacia arriba: 10011100₂
```

**Verificación:** 128 + 16 + 8 + 4 = 156 ✓

**Respuesta:** 10011100₂

---

### Ejercicio 3: Hexadecimal → Binario

**Enunciado:** Convertir **B7₁₆** a binario

**Solución:**
```
B = 11₁₀ = 1011₂
7 = 7₁₀  = 0111₂

Uniendo ambos grupos:
B7₁₆ = 1011 0111₂ = 10110111₂
```

**Respuesta:** 10110111₂

---

### Ejercicio 4: Binario → Hexadecimal

**Enunciado:** Convertir **11111010101₂** a hexadecimal

**Solución:**
```
Paso 1: Agrupar de 4 en 4 desde la derecha
        0111  1101  0101

Paso 2: Convertir cada grupo
         7     D     5

Resultado: 7D5₁₆
```

**Respuesta:** 7D5₁₆

---

### Ejercicio 5: Decimal → Hexadecimal

**Enunciado:** Convertir **1000₁₀** a hexadecimal

**Solución:**
```
1000 ÷ 16 = 62   resto 8
  62 ÷ 16 = 3    resto 14 (E)
   3 ÷ 16 = 0    resto 3

Leyendo de abajo hacia arriba: 3E8₁₆
```

**Verificación:** 3×256 + 14×16 + 8 = 768 + 224 + 8 = 1000 ✓

**Respuesta:** 3E8₁₆

---

### Ejercicio 6: Hexadecimal → Decimal

**Enunciado:** Convertir **2AF₁₆** a decimal

**Solución:**
```
Posiciones:    2        A        F
               ↓        ↓        ↓
Potencias:   16²      16¹      16⁰
               ↓        ↓        ↓
Valores:     256       16        1

Cálculo:
2×256 + 10×16 + 15×1 = 512 + 160 + 15 = 687₁₀
```

**Respuesta:** 687₁₀

---

### Ejercicio 7: Octal → Decimal

**Enunciado:** Convertir **756₈** a decimal

**Solución:**
```
Posiciones:    7        5        6
               ↓        ↓        ↓
Potencias:    8²       8¹       8⁰
               ↓        ↓        ↓
Valores:      64        8        1

Cálculo:
7×64 + 5×8 + 6×1 = 448 + 40 + 6 = 494₁₀
```

**Respuesta:** 494₁₀

---

### Ejercicio 8: Binario → Octal

**Enunciado:** Convertir **11010110₂** a octal

**Solución:**
```
Paso 1: Agrupar de 3 en 3 desde la derecha
        011  010  110

Paso 2: Convertir cada grupo
         3    2    6

Resultado: 326₈
```

**Respuesta:** 326₈

---

### Ejercicio 9: Color HTML

**Enunciado:** El color naranja en HTML se representa como #FFA500. ¿Cuántos niveles de rojo, verde y azul tiene?

**Solución:**
```
#FFA500 se divide en:
  FF      A5      00
  ↓       ↓       ↓
 Rojo   Verde   Azul

Conversiones a decimal:
FF₁₆ = 15×16 + 15 = 255₁₀ (Rojo al máximo)
A5₁₆ = 10×16 + 5 = 165₁₀ (Verde medio)
00₁₆ = 0₁₀ (Sin azul)
```

**Respuesta:** Rojo: 255, Verde: 165, Azul: 0

---

### Ejercicio 10: Permisos Linux

**Enunciado:** Un archivo tiene permisos **644₈**. ¿Qué puede hacer cada tipo de usuario?

**Solución:**
```
6 = 110₂ = 4+2 = rw- (Propietario: lectura y escritura)
4 = 100₂ = 4   = r-- (Grupo: solo lectura)
4 = 100₂ = 4   = r-- (Otros: solo lectura)
```

**Respuesta:**
- **Propietario:** Puede leer y modificar el archivo
- **Grupo:** Puede solo leer el archivo
- **Otros:** Pueden solo leer el archivo
- **Nadie** puede ejecutar el archivo

---

### Ejercicio 11: Dirección IP

**Enunciado:** Convierte la IP **192.168.1.100** a binario y hexadecimal

**Solución:**

**A binario:**
```
192₁₀ = 11000000₂
168₁₀ = 10101000₂
  1₁₀ = 00000001₂
100₁₀ = 01100100₂

IP en binario: 11000000.10101000.00000001.01100100
```

**A hexadecimal:**
```
192₁₀ = C0₁₆
168₁₀ = A8₁₆
  1₁₀ = 01₁₆
100₁₀ = 64₁₆

IP en hexadecimal: C0.A8.01.64
```

**Respuesta:**
- Binario: 11000000.10101000.00000001.01100100
- Hexadecimal: C0.A8.01.64

---

## 9. EJERCICIOS PROPUESTOS

### Nivel Básico

**Ejercicio 1:** Convierte los siguientes números binarios a decimal:
- a) 1010₂
- b) 11001₂
- c) 101010₂
- d) 11111111₂

**Ejercicio 2:** Convierte los siguientes números decimales a binario:
- a) 25₁₀
- b) 64₁₀
- c) 100₁₀
- d) 200₁₀

**Ejercicio 3:** Convierte los siguientes números hexadecimales a decimal:
- a) 1A₁₆
- b) FF₁₆
- c) A0₁₆
- d) 3C₁₆

**Ejercicio 4:** Convierte los siguientes números decimales a hexadecimal:
- a) 32₁₀
- b) 255₁₀
- c) 512₁₀
- d) 1024₁₀

**Ejercicio 5:** Convierte los siguientes números octales a decimal:
- a) 17₈
- b) 777₈
- c) 100₈
- d) 456₈

**Ejercicio 6:** Convierte los siguientes números binarios a hexadecimal:
- a) 10101010₂
- b) 11110000₂
- c) 10011110011₂
- d) 11111111₂

**Ejercicio 7:** Convierte los siguientes números hexadecimales a binario:
- a) CA₁₆
- b) F0F₁₆
- c) DEAD₁₆
- d) CAFE₁₆

**Ejercicio 8:** Convierte los siguientes números binarios a octal:
- a) 11010110₂
- b) 101101₂
- c) 11111000₂
- d) 10001001₂

**Ejercicio 9:** Convierte los siguientes números octales a binario:
- a) 347₈
- b) 777₈
- c) 125₈
- d) 666₈

**Ejercicio 10:** Convierte los siguientes números decimales a octal:
- a) 64₁₀
- b) 128₁₀
- c) 255₁₀
- d) 500₁₀

---

### Nivel Avanzado: Aplicaciones Prácticas

**Ejercicio 11:** Análisis de colores HTML
- a) Descompón el color #3498DB en sus componentes RGB (en decimal)
- b) Crea el código hexadecimal para un color con R:200, G:100, B:50
- c) ¿Qué color representa #808080?

**Ejercicio 12:** Direcciones IP
- a) Convierte la IP 10.0.0.1 a binario completo
- b) Convierte la IP 255.255.255.0 (máscara común) a binario
- c) Convierte la IP en binario 11000000.10101000.00000001.00000001 a decimal

**Ejercicio 13:** Dirección MAC
- La dirección MAC A4:C3:F0:2E:7B:19:
- a) Convierte cada octeto a decimal
- b) Convierte cada octeto a binario
- c) ¿Cuántos bits tiene una dirección MAC completa?

**Ejercicio 14:** Conversiones encadenadas
- a) Convierte 237₁₀ a binario, luego a hexadecimal
- b) Convierte 1AF₁₆ a binario, luego a octal
- c) Convierte 456₈ a binario, luego a decimal
