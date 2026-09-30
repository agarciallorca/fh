# MICROPROCESADORES

---

## Índice

1. [Qué es un microprocesador](#1-qué-es-un-microprocesador)
2. [Breve historia y evolución](#2-breve-historia-y-evolución)
3. [Arquitectura interna](#3-arquitectura-interna)
4. [Características principales](#4-características-principales)
5. [Jerarquía de memoria caché](#5-jerarquía-de-memoria-caché)
6. [Núcleos, hilos y paralelismo](#6-núcleos-hilos-y-paralelismo)
7. [Arquitecturas: CISC vs RISC y x86 vs ARM](#7-arquitecturas-cisc-vs-risc-y-x86-vs-arm)
8. [Zócalos (sockets) y compatibilidad](#8-zócalos-sockets-y-compatibilidad)
9. [Refrigeración y disipación térmica](#9-refrigeración-y-disipación-térmica)
10. [Fabricantes y familias actuales](#10-fabricantes-y-familias-actuales)
11. [Procesadores para servidores](#11-procesadores-para-servidores)
12. [Cómo elegir un procesador](#12-cómo-elegir-un-procesador)
13. [Comandos útiles para identificar la CPU](#13-comandos-útiles-para-identificar-la-cpu)
14. [Averías y diagnóstico habituales](#14-averías-y-diagnóstico-habituales)

---

## 1. Qué es un microprocesador

El **microprocesador** (CPU, *Central Processing Unit*) es un circuito integrado que interpreta y ejecuta las instrucciones de los programas. Es el "cerebro" del equipo: realiza operaciones aritmético-lógicas, controla el flujo de datos y coordina al resto de componentes.

- Está fabricado en **silicio** mediante procesos de litografía, con miles de millones de **transistores**.
- Trabaja con **señales digitales** (0 y 1) sincronizadas por una señal de reloj.
- Se comunica con la memoria RAM, el chipset y los periféricos mediante **buses** y controladores.

> **Nota:** hoy en día muchos procesadores integran también controlador de memoria, gráficos (iGPU), controlador PCIe y aceleradores de IA, por lo que se habla de **SoC** (*System on Chip*) en dispositivos móviles y de CPU con múltiples funciones en PC.

---

## 2. Breve historia y evolución

| Año | Hito | Detalle |
|-----|------|---------|
| 1971 | Intel 4004 | Primer microprocesador comercial, 4 bits, ~2.300 transistores |
| 1978 | Intel 8086 | Origen de la arquitectura **x86**, 16 bits |
| 1985 | Intel 80386 | Primer x86 de 32 bits |
| 1993 | Intel Pentium | Superescalar, dos tuberías de ejecución |
| 2003 | AMD Opteron / Athlon 64 | Introducen la extensión de 64 bits **x86-64** |
| 2005 | Primeros dual-core | Comienza la era multinúcleo |
| 2011+ | Gráficos integrados generalizados | CPU + GPU en el mismo encapsulado |
| 2017+ | Diseños con *chiplets* (AMD Zen) | Varios dados de silicio en un mismo encapsulado |
| 2021+ | Arquitecturas híbridas (núcleos P y E) | Núcleos de alto rendimiento y de eficiencia |

La **Ley de Moore** (1965) observó que el número de transistores en un chip se duplicaba aproximadamente cada dos años. Hoy ese ritmo se ha ralentizado, y la mejora de rendimiento se consigue más con **más núcleos, mejor arquitectura y especialización** que con subir la frecuencia.

---

## 3. Arquitectura interna

### 3.1 Componentes principales

- **Unidad de control (UC):** decodifica las instrucciones y genera las señales que gobiernan al resto de la CPU.
- **Unidad aritmético-lógica (ALU):** realiza operaciones aritméticas (suma, resta…) y lógicas (AND, OR, NOT…).
- **Unidad de coma flotante (FPU):** operaciones con números reales.
- **Registros:** memoria muy pequeña y ultrarrápida dentro de la CPU.
- **Memoria caché:** memoria intermedia entre CPU y RAM (ver apartado 6).
- **Unidad de gestión de memoria (MMU):** traduce direcciones virtuales en físicas.
- **Controlador de memoria integrado:** gestiona el acceso a la RAM.

### 3.2 Registros más habituales

| Registro | Función |
|----------|---------|
| **PC / IP** (*Program Counter / Instruction Pointer*) | Dirección de la siguiente instrucción a ejecutar |
| **IR** (*Instruction Register*) | Instrucción que se está ejecutando |
| **Acumulador / registros de propósito general** | Almacenan operandos y resultados |
| **SP** (*Stack Pointer*) | Apunta a la cima de la pila |
| **Registro de estado / FLAGS** | Indicadores del resultado (cero, acarreo, desbordamiento…) |
| **MAR / MDR** | Dirección y dato en accesos a memoria |

### 3.3 Buses

- **Bus de datos:** transporta los datos. Su anchura condiciona cuántos bits se mueven a la vez.
- **Bus de direcciones:** indica la posición de memoria a la que se accede. Con *n* líneas se pueden direccionar **2ⁿ** posiciones.
- **Bus de control:** señales de lectura/escritura, interrupciones, reloj, etc.

> **Ejemplo:** un bus de direcciones de 32 bits direcciona 2³² = 4 GiB. Por eso los sistemas de 32 bits están limitados a unos 4 GiB de RAM.

---

## 4. Características principales

### 4.1 Frecuencia de reloj

Se mide en **GHz** (miles de millones de ciclos por segundo). Indica la velocidad del reloj, **pero no es el único factor de rendimiento**.

- **Frecuencia base:** la garantizada en condiciones normales.
- **Frecuencia turbo / boost:** frecuencia máxima alcanzable temporalmente si hay margen térmico y de consumo.

### 4.2 IPC (instrucciones por ciclo)

Mide cuántas instrucciones ejecuta la CPU en cada ciclo. Un procesador a menor frecuencia pero con mayor IPC puede ser más rápido.

```text
Rendimiento ≈ IPC × Frecuencia × Nº de núcleos aprovechados
```

### 4.3 Anchura de palabra

Bits que la CPU procesa a la vez: 32 bits o 64 bits (actualmente estándar en PC y servidores).

### 4.4 Proceso de fabricación

Se expresa en **nanómetros (nm)** (p. ej. 7 nm, 5 nm, 3 nm). Un proceso más pequeño permite más transistores, menor consumo y menos calor. Los nombres comerciales de los nodos ya no equivalen exactamente a medidas físicas reales.

### 4.5 TDP (*Thermal Design Power*)

Potencia térmica de referencia que el sistema de refrigeración debe poder disipar. Se mide en **vatios (W)**. Es una referencia de diseño, no el consumo máximo exacto (los procesadores pueden superar su TDP temporalmente).

### 4.6 Resumen de especificaciones típicas

| Característica | Qué indica | Unidad |
|----------------|-----------|--------|
| Núcleos / hilos | Capacidad de ejecución paralela | nº |
| Frecuencia base / turbo | Velocidad del reloj | GHz |
| Caché L1/L2/L3 | Memoria rápida integrada | KiB / MiB |
| TDP | Calor a disipar | W |
| Socket | Conector físico | (nombre) |
| Memoria soportada | Tipo y velocidad de RAM | DDR4/DDR5, MT/s |
| Líneas PCIe | Conectividad con GPU, NVMe… | nº y versión |
| Proceso | Tecnología de fabricación | nm |

---

## 5. Jerarquía de memoria caché

La caché reduce el **cuello de botella** entre la CPU (muy rápida) y la RAM (más lenta).

```text
        Más rápida, más pequeña, más cara
   ┌───────────────────────────────────────┐
   │  Registros                            │
   │  Caché L1  (por núcleo, KiB)          │
   │  Caché L2  (por núcleo, MiB)          │
   │  Caché L3  (compartida, decenas MiB)  │
   │  Memoria RAM  (GiB)                   │
   │  Almacenamiento SSD/HDD  (TiB)        │
   └───────────────────────────────────────┘
        Más lenta, más grande, más barata
```

| Nivel | Ubicación | Tamaño típico | Latencia aproximada |
|-------|-----------|---------------|---------------------|
| L1 | Dentro de cada núcleo | 32–64 KiB (datos) + instrucciones | ~1 ns |
| L2 | Por núcleo (o compartida por grupo) | 256 KiB – 2 MiB | ~3–5 ns |
| L3 | Compartida entre núcleos | 8 – 128+ MiB | ~10–20 ns |
| RAM | Módulos DIMM | 8 – 512+ GiB | ~60–100 ns |

**Conceptos clave:**

- **Acierto (*hit*):** el dato buscado está en la caché.
- **Fallo (*miss*):** el dato no está y hay que pedirlo al siguiente nivel.
- **Localidad temporal y espacial:** principios que justifican el uso de caché (lo usado recientemente y lo cercano se volverá a usar).

---

## 6. Núcleos, hilos y paralelismo

- **Núcleo (*core*):** unidad de procesamiento independiente dentro de la CPU.
- **Hilo (*thread*):** flujo de ejecución. Un núcleo puede gestionar uno o varios hilos.
- **SMT / Hyper-Threading:** tecnología que permite que un núcleo físico ejecute **dos hilos** simultáneamente, presentándose al sistema operativo como dos procesadores lógicos.

> **Ejemplo:** una CPU de 8 núcleos con SMT ofrece **16 hilos** (procesadores lógicos).

### Arquitecturas híbridas (núcleos P y E)

- **Núcleos P (*Performance*):** alto rendimiento, para tareas exigentes.
- **Núcleos E (*Efficiency*):** bajo consumo, para tareas en segundo plano.
- El planificador del sistema operativo reparte las tareas entre ambos tipos.

### Ley de Amdahl (idea básica)

Añadir núcleos no acelera proporcionalmente cualquier programa: la parte del código que no se puede paralelizar limita la mejora total.

---

## 7. Arquitecturas: CISC vs RISC y x86 vs ARM

| | **CISC** | **RISC** |
|---|----------|----------|
| Juego de instrucciones | Amplio y complejo | Reducido y simple |
| Longitud de instrucción | Variable | Normalmente fija |
| Instrucciones por tarea | Menos, más complejas | Más, más simples |
| Consumo energético | Tradicionalmente mayor | Tradicionalmente menor |
| Ejemplo | **x86 / x86-64** (Intel, AMD) | **ARM**, RISC-V |

En la práctica, las CPU x86 modernas traducen internamente las instrucciones CISC a microoperaciones de tipo RISC.

### x86-64 vs ARM

| Aspecto | x86-64 | ARM |
|---------|--------|-----|
| Uso típico | PC, portátiles, servidores | Móviles, tabletas, portátiles, servidores y nube |
| Fabricantes | Intel, AMD | Licencias a Apple, Qualcomm, Ampere, AWS (Graviton)… |
| Compatibilidad de software | Muy amplia en escritorio | Creciente; puede requerir versiones nativas o emulación |
| Eficiencia energética | Buena y en mejora | Muy alta |

> **Atención al instalar software:** el binario debe coincidir con la arquitectura (p. ej. `amd64`/`x86_64` vs `arm64`/`aarch64`). Es un detalle habitual al trabajar con imágenes de máquinas virtuales y contenedores.

---

## 8. Zócalos (sockets) y compatibilidad

El **socket** es el conector físico entre CPU y placa base. Para que una CPU funcione deben coincidir:

1. **Socket** físico (forma y número de contactos).
2. **Chipset** y **BIOS/UEFI** de la placa compatibles con esa generación.
3. **Tipo de memoria** soportada (DDR4 o DDR5, según plataforma).
4. **Capacidad del VRM** (alimentación) de la placa para el consumo de la CPU.

### Tipos de encapsulado

| Tipo | Descripción | Ejemplos |
|------|-------------|----------|
| **LGA** (*Land Grid Array*) | Los pines están en el **socket**; la CPU tiene contactos planos | Intel (LGA1700, LGA1851…) |
| **PGA** (*Pin Grid Array*) | Los pines están en la **CPU** | AMD clásicos (AM4) |
| **LGA en AMD moderno** | AMD pasó a LGA en su plataforma actual | AM5 |
| **BGA** (*Ball Grid Array*) | Soldado a la placa, no reemplazable | Portátiles, equipos compactos |

> **Consejo de montaje:** nunca fuerces una CPU. Alinea la marca del triángulo dorado o las muescas con las del socket, y aplica la **pasta térmica** en cantidad moderada (tamaño de un guisante) antes de colocar el disipador.

---

## 9. Refrigeración y disipación térmica

Toda la energía eléctrica que consume la CPU acaba convertida en **calor**, que debe evacuarse para evitar daños y pérdida de rendimiento.

### Elementos

- **Pasta térmica:** mejora el contacto entre el IHS (tapa metálica de la CPU) y el disipador.
- **Disipador (*heatsink*):** masa metálica con aletas (cobre/aluminio) que aumenta la superficie de intercambio.
- **Ventilador:** fuerza el flujo de aire.
- **Heat pipes:** tubos que transportan calor mediante cambio de fase de un fluido.
- **Refrigeración líquida (AIO o custom):** bomba, radiador y bloque sobre la CPU.

### Conceptos importantes

- **Thermal throttling:** la CPU reduce su frecuencia automáticamente al alcanzar temperaturas elevadas.
- **Temperatura máxima de unión (Tjunction/Tjmax):** límite térmico del fabricante (suele rondar los 90–100 °C).
- **Flujo de aire de la caja:** entrada frontal/inferior y salida trasera/superior.

| Síntoma | Posible causa |
|---------|---------------|
| Apagados repentinos | Sobrecalentamiento, protección térmica |
| Rendimiento que cae con el tiempo | *Throttling* por mala refrigeración |
| Ruido excesivo de ventiladores | Polvo, rodamientos desgastados, temperaturas altas |
| Temperaturas altas en reposo | Pasta seca, disipador mal anclado |

---

## 10. Fabricantes y familias actuales

| Fabricante | Familias de consumo | Notas |
|------------|---------------------|-------|
| **Intel** | Core (i3/i5/i7/i9, Core Ultra), Pentium/Celeron | Plataforma x86; arquitecturas híbridas P+E |
| **AMD** | Ryzen 3/5/7/9, Ryzen PRO | Diseño con chiplets; sockets de larga vida |
| **Apple** | Serie M (M1, M2, M3…) | ARM propio, integrado en SoC |
| **Qualcomm** | Snapdragon (incl. líneas para portátil) | ARM |

> Los nombres comerciales y las generaciones cambian con frecuencia. Consulta siempre la **ficha oficial del fabricante** (Intel ARK, AMD Product Specifications) para datos exactos de un modelo.

### Cómo leer un nombre de modelo (ejemplo genérico Intel)

```text
Core i7 - 13700 K
   │       │    │
   │       │    └── Sufijo: K = desbloqueado para overclock, F = sin gráficos, T = bajo consumo…
   │       └─────── Generación (13ª) + número de SKU
   └─────────────── Gama (i3 < i5 < i7 < i9)
```

En AMD Ryzen los sufijos también informan del tipo de modelo (por ejemplo **X** = mayor frecuencia, **G** = con gráficos integrados, **X3D** = con caché 3D apilada).

---

## 11. Procesadores para servidores

En entornos profesionales (objetivo principal de un técnico ASIR) se usan procesadores pensados para **fiabilidad, escalabilidad y funcionamiento 24/7**.

| Familia | Fabricante | Características destacadas |
|---------|------------|----------------------------|
| **Xeon** | Intel | Muchos núcleos, soporte multi-socket, memoria ECC |
| **EPYC** | AMD | Muy alto número de núcleos, muchas líneas PCIe |
| **Ampere Altra / Graviton** | Ampere / AWS | ARM para nube, alta eficiencia |

### Diferencias respecto a los procesadores de escritorio

- **Memoria ECC:** detecta y corrige errores de bit en RAM.
- **Más canales de memoria** y mayor capacidad máxima.
- **Más líneas PCIe** para tarjetas de red, almacenamiento NVMe y aceleradores.
- **Configuraciones multi-socket** (2, 4 u 8 CPU en una placa).
- **Funciones de gestión remota** (BMC/iLO/iDRAC en el servidor).
- **Ciclos de vida y soporte** más largos.

### NUMA

En sistemas multi-socket, cada CPU tiene su memoria "local". Acceder a la memoria de otra CPU es más lento. Esto se denomina **NUMA** (*Non-Uniform Memory Access*) y afecta al rendimiento de máquinas virtuales y bases de datos.

---

## 12. Cómo elegir un procesador

Antes de elegir, hay que definir **para qué se va a usar el equipo**.

| Uso | Prioridades |
|-----|-------------|
| Ofimática / equipo de oficina | Bajo consumo, gráficos integrados, coste ajustado |
| Desarrollo y virtualización | Muchos núcleos/hilos, mucha RAM, VT-x/AMD-V |
| Servidor de ficheros / red | Fiabilidad, ECC, eficiencia |
| Servidor de virtualización | Núcleos, canales de memoria, PCIe, NUMA |
| Edición de vídeo / renderizado | Núcleos, frecuencia, buena refrigeración |
| Juegos | Alto rendimiento por núcleo, caché, buena GPU |
| Equipos compactos / IoT | Consumo y tamaño mínimos (ARM, SoC) |

### Lista de comprobación

- [ ] ¿Es compatible con el **socket** y el **chipset** de la placa?
- [ ] ¿La placa necesita **actualizar la BIOS** para reconocer la CPU?
- [ ] ¿El **tipo de memoria** coincide (DDR4/DDR5)?
- [ ] ¿La **fuente de alimentación** soporta el consumo total?
- [ ] ¿El **disipador** cubre el TDP y es compatible con el socket?
- [ ] ¿Tiene **gráficos integrados** o se necesita tarjeta gráfica dedicada?
- [ ] ¿Incluye las **funciones** necesarias (virtualización, ECC, etc.)?
- [ ] ¿Relación **rendimiento / precio / consumo** adecuada?

---

## 13. Comandos útiles para identificar la CPU

### Linux

```bash
# Información detallada de la CPU
lscpu

# Datos en bruto del kernel
cat /proc/cpuinfo

# Número de procesadores lógicos disponibles
nproc

# Comprobar si hay virtualización por hardware (vmx = Intel, svm = AMD)
grep -E -o 'vmx|svm' /proc/cpuinfo | sort -u

# Temperaturas y sensores (paquete lm-sensors)
sensors

# Resumen de hardware
sudo dmidecode -t processor
```

### Windows (CMD / PowerShell)

```powershell
# Información básica
wmic cpu get name,numberofcores,numberoflogicalprocessors,maxclockspeed

# Información completa del sistema
systeminfo

# Con PowerShell (recomendado en versiones actuales)
Get-CimInstance Win32_Processor | Select-Object Name, NumberOfCores, NumberOfLogicalProcessors, MaxClockSpeed
```

> También se puede consultar desde el **Administrador de tareas → Rendimiento → CPU**, y con herramientas como **CPU-Z**, **HWiNFO** o **Core Temp**.

### macOS

```bash
sysctl -n machdep.cpu.brand_string
sysctl hw.ncpu
```

---

## 14. Averías y diagnóstico habituales

| Síntoma | Causas probables | Qué comprobar |
|---------|------------------|---------------|
| El equipo no enciende | Fuente, placa, conexión de alimentación de CPU (EPS 4/8 pines) | Cable de alimentación de CPU conectado |
| Enciende pero no da imagen | CPU mal colocada, BIOS incompatible, RAM | Reasentar CPU y RAM, revisar versión de BIOS |
| Pitidos al arrancar | Error POST (código según fabricante) | Manual de la placa, códigos de pitidos/LED |
| Reinicios o pantallazos azules | Sobrecalentamiento, RAM defectuosa, overclock inestable | Temperaturas, prueba de memoria, valores por defecto |
| Rendimiento bajo | *Throttling*, plan de energía restrictivo, procesos en segundo plano | Temperaturas, plan de energía, Administrador de tareas |
| CPU con pines doblados | Instalación incorrecta | Inspección visual; no forzar |

### Método de diagnóstico recomendado

1. **Observar e identificar** el síntoma con precisión.
2. **Comprobar lo básico:** alimentación, conexiones, refrigeración.
3. **Aislar:** probar con configuración mínima (CPU, una RAM, sin periféricos).
4. **Sustituir componentes** sospechosos por otros que funcionen.
5. **Documentar** el problema y la solución.

### Pruebas de estrés y monitorización

- **Linux:** `stress-ng`, `s-tui`, `htop`.
- **Windows:** Prime95, OCCT, Cinebench, HWMonitor.
- Durante la prueba, vigila **temperatura**, **frecuencia** y **estabilidad**.

### Bibliografía y recursos recomendados

- Fichas oficiales de producto: **Intel ARK** (ark.intel.com) y **AMD Product Specifications** (amd.com).
- Documentación de **Linux** (`man lscpu`, `man proc`) y de **Microsoft Learn** (WMI / CIM).
- Herramientas de diagnóstico: CPU-Z, HWiNFO, lm-sensors, stress-ng.
- Manuales de placa base del fabricante (listas de CPU compatibles y versiones de BIOS).

> **Aviso:** las cifras, modelos y generaciones concretas evolucionan rápidamente. Los conceptos de este documento son estables, pero contrasta siempre los datos de productos con la fuente oficial del fabricante.
