# PLACA BASE

---

## Índice

1. [Qué es la placa base](#1-qué-es-la-placa-base)
2. [Factores de forma](#2-factores-de-forma)
3. [Componentes principales](#3-componentes-principales)
4. [El socket del procesador](#4-el-socket-del-procesador)
5. [El chipset](#5-el-chipset)
6. [Memoria RAM: ranuras y canales](#6-memoria-ram-ranuras-y-canales)
7. [Buses y ranuras de expansión](#7-buses-y-ranuras-de-expansión)
8. [Almacenamiento: SATA y M.2](#8-almacenamiento-sata-y-m2)
9. [Alimentación y VRM](#9-alimentación-y-vrm)
10. [BIOS y UEFI](#10-bios-y-uefi)
11. [Conectores del panel frontal y cabeceras internas](#11-conectores-del-panel-frontal-y-cabeceras-internas)
12. [Conectores del panel trasero (I/O)](#12-conectores-del-panel-trasero-io)
13. [Placas base para servidores y estaciones de trabajo](#13-placas-base-para-servidores-y-estaciones-de-trabajo)
14. [Compatibilidad entre componentes](#14-compatibilidad-entre-componentes)
15. [Cómo elegir una placa base](#16-cómo-elegir-una-placa-base)
16. [Comandos útiles para identificar la placa](#18-comandos-útiles-para-identificar-la-placa)

---

## 1. Qué es la placa base

La **placa base** (*motherboard*, *mainboard*) es la placa de circuito impreso (PCB) sobre la que se conectan y comunican todos los componentes del equipo: procesador, memoria, almacenamiento, tarjetas de expansión y periféricos.

Sus funciones principales son:

- **Alojar** físicamente los componentes principales.
- **Interconectarlos** mediante pistas, buses y controladores.
- **Suministrar energía** a los componentes a partir de la fuente de alimentación.
- **Gestionar la comunicación** entre CPU, memoria y dispositivos de entrada/salida.
- **Almacenar la configuración básica** del sistema (firmware BIOS/UEFI).

> **Idea clave:** la placa base determina qué procesador, qué tipo de memoria y cuántos dispositivos podrán usarse. Es la pieza que marca la **compatibilidad y la capacidad de ampliación** de todo el equipo.

---

## 2. Factores de forma

El **factor de forma** define las dimensiones de la placa, la posición de los orificios de anclaje y la disposición de conectores. Debe coincidir con la caja (torre) y la fuente de alimentación.

| Factor de forma | Dimensiones aprox. (mm) | Ranuras PCIe típicas | Uso habitual |
|-----------------|-------------------------|----------------------|--------------|
| **ATX** | 305 × 244 | Hasta 7 | Equipos de sobremesa estándar |
| **Micro-ATX (mATX)** | 244 × 244 | Hasta 4 | Equipos compactos y de oficina |
| **Mini-ITX** | 170 × 170 | 1 | Equipos muy pequeños, HTPC |
| **E-ATX (Extended ATX)** | 305 × 330 | Hasta 7 o más | Estaciones de trabajo y entusiastas |
| **EEB / SSI CEB** | Variable, mayores | Variable | Servidores y estaciones de trabajo |

**Reglas de compatibilidad:**

- Una caja admite normalmente su factor de forma y los **más pequeños** (una caja ATX admite mATX y Mini-ITX).
- Los orificios de anclaje estándar permiten atornillar placas más pequeñas en cajas grandes.
- Conviene verificar también la conexión de la **fuente** (ATX de 24 pines + alimentación de CPU).

---

## 3. Componentes principales

```text
┌──────────────────────────────────────────────────────────┐
│  [Panel trasero I/O]   [VRM + disipadores]  [Conector    │
│                         ▓▓▓▓▓▓▓▓▓▓▓▓       CPU EPS]      │
│                        ┌────────────┐                    │
│                        │   SOCKET   │    ┌─┬─┬─┬─┐       │
│                        │    CPU     │    │ │ │ │ │ RAM   │
│                        └────────────┘    └─┴─┴─┴─┘ DIMM  │
│                                                ATX 24p   │
│  ┌──────────────────┐     ┌────────┐                     │
│  │ PCIe x16 (GPU)   │     │ M.2    │   ┌─────────┐       │
│  ├──────────────────┤     └────────┘   │ CHIPSET │       │
│  │ PCIe x1 / x4     │                  └─────────┘       │
│  ├──────────────────┤   [SATA] [SATA]   [Panel frontal]  │
│  │ PCIe x1 / x4     │   [Batería CMOS]  [Cabeceras USB]  │
│  └──────────────────┘                                    │
└──────────────────────────────────────────────────────────┘
```
*(Esquema orientativo: la distribución real varía según el modelo.)*

| Componente | Función |
|------------|---------|
| **Socket de CPU** | Conector donde se instala el procesador |
| **Chipset** | Coordina la comunicación con periféricos y buses |
| **Ranuras DIMM** | Alojan los módulos de memoria RAM |
| **Ranuras PCIe** | Tarjetas gráficas, de red, controladoras, etc. |
| **Ranuras M.2 / puertos SATA** | Unidades de almacenamiento |
| **VRM** | Regula el voltaje que recibe la CPU |
| **Chip de firmware (BIOS/UEFI)** | Inicializa el hardware y arranca el sistema |
| **Pila CMOS** | Mantiene la hora y la configuración del firmware |
| **Conectores de alimentación** | ATX 24 pines, EPS 4/8 pines para CPU |
| **Cabeceras y conectores** | Panel frontal, USB, audio, ventiladores, RGB… |
| **Códec de audio y controlador de red** | Audio y Ethernet integrados |

---

## 4. El socket del procesador

El **socket** es el zócalo físico donde se inserta la CPU. Cada socket es compatible **solo** con determinadas familias de procesadores.

| Tipo de contacto | Descripción | Ejemplos |
|------------------|-------------|----------|
| **LGA** (*Land Grid Array*) | Pines en la placa; la CPU tiene contactos planos | Intel de consumo y servidor; AMD AM5 y servidor |
| **PGA** (*Pin Grid Array*) | Pines en la CPU | AMD AM4 (generaciones anteriores) |
| **BGA** (*Ball Grid Array*) | CPU soldada a la placa | Portátiles y equipos compactos |

**Puntos importantes:**

- El socket **por sí solo no garantiza** compatibilidad: también influyen el chipset y la versión de **BIOS/UEFI**.
- En sockets LGA, los pines de la placa son muy delicados: **nunca** introduzcas la CPU con fuerza.
- El disipador debe ser compatible con el sistema de anclaje del socket.

> **Consejo:** antes de comprar una CPU para una placa ya existente, consulta la **lista de CPU compatibles** (CPU Support List) en la web del fabricante de la placa y comprueba la versión mínima de BIOS.

---

## 5. El chipset

El **chipset** es el conjunto de circuitos que gestiona la comunicación entre el procesador y el resto de componentes. En las plataformas actuales, buena parte de las funciones antes repartidas (antiguo *northbridge*) se ha integrado en la CPU: controlador de memoria y líneas PCIe principales. El chipset de la placa actúa como **concentrador** de las conexiones adicionales.

### Qué gestiona el chipset

- Puertos USB y SATA adicionales.
- Líneas PCIe secundarias (para M.2, tarjetas de expansión).
- Audio, red y otros controladores integrados.
- Opciones de RAID por hardware/firmware (según modelo).
- Posibilidades de **overclocking** (según gama).

### Gamas de chipset

Cada fabricante ofrece varias gamas, de las más básicas a las más completas:

| Gama | Características típicas |
|------|-------------------------|
| **Básica / entrada** | Menos puertos USB y PCIe, sin overclock de CPU |
| **Media** | Más conectividad, posibilidad de ajustar memoria |
| **Alta / entusiasta** | Máxima conectividad, overclock, más líneas PCIe y M.2 |
| **Workstation / servidor** | ECC, más canales, gestión remota |

> Los nombres de chipsets y las generaciones cambian con frecuencia. Consulta la **documentación del fabricante** (Intel, AMD) para cada plataforma.

### Conexión CPU ↔ chipset

El chipset se comunica con la CPU mediante un **enlace dedicado** (DMI en Intel, enlace PCIe equivalente en AMD). Su ancho de banda es **compartido** por todos los dispositivos colgados del chipset, por lo que conviene repartir bien las unidades de alta velocidad.

---

## 6. Memoria RAM: ranuras y canales

### Tipos de módulo

| Tipo | Formato | Uso |
|------|---------|-----|
| **DIMM** | Módulo de 288 pines (DDR4/DDR5) | Sobremesa y servidores |
| **SO-DIMM** | Formato reducido | Portátiles, mini-PC |
| **UDIMM** | Sin búfer | Equipos de consumo |
| **RDIMM / LRDIMM** | Con registro / carga reducida | Servidores |

### Generaciones DDR

| Generación | Notas |
|------------|-------|
| **DDR4** | Muy extendida; tensión ~1,2 V |
| **DDR5** | Mayor ancho de banda y capacidad por módulo; tensión ~1,1 V; ECC en el propio chip (*on-die*) |

**Las generaciones DDR no son intercambiables:** la muesca del módulo está en una posición distinta y no encaja físicamente en ranuras de otra generación. La placa admite **una** generación, no ambas.

### Canales de memoria

- **Canal único (*single channel*):** un único camino hacia la memoria.
- **Doble canal (*dual channel*):** dos caminos en paralelo, duplicando el ancho de banda teórico.
- **Cuatro u ocho canales:** en plataformas de estación de trabajo y servidor.

> **Buena práctica:** instala los módulos en las ranuras indicadas en el manual (habitualmente alternadas, por ejemplo A2 y B2) para activar el doble canal. Usa módulos **idénticos** siempre que sea posible.

### Parámetros que conviene conocer

- **Capacidad** (GiB) y **máxima admitida** por la placa.
- **Velocidad** (MT/s) y **latencias** (CL).
- **Perfiles XMP / EXPO:** perfiles de overclock de memoria activables desde la BIOS/UEFI.
- **ECC:** corrección de errores; requiere soporte de CPU, placa y módulos.

---

## 7. Buses y ranuras de expansión

### PCI Express (PCIe)

Es el bus de expansión actual, basado en **líneas (lanes)** punto a punto. Cada generación duplica aproximadamente el ancho de banda por línea.

| Generación | Velocidad aprox. por línea (por sentido) | x1 | x4 | x16 |
|------------|------------------------------------------|----|----|-----|
| **PCIe 3.0** | ~1 GB/s | ~1 GB/s | ~4 GB/s | ~16 GB/s |
| **PCIe 4.0** | ~2 GB/s | ~2 GB/s | ~8 GB/s | ~32 GB/s |
| **PCIe 5.0** | ~4 GB/s | ~4 GB/s | ~16 GB/s | ~64 GB/s |

**Notas importantes:**

- El tamaño físico de la ranura (x1, x4, x8, x16) **no siempre coincide** con las líneas eléctricas conectadas. Una ranura x16 puede funcionar eléctricamente a x4 o x8.
- Las tarjetas son **retrocompatibles**: una tarjeta PCIe 4.0 funciona en una ranura 3.0, a la velocidad menor.
- Una tarjeta x16 puede insertarse en una ranura más larga o, si la ranura está abierta, en una más corta.
- El número total de líneas disponibles depende de la **CPU y el chipset**; instalar muchos dispositivos puede **repartir o reducir** líneas.

### Otros buses

| Bus | Situación actual |
|-----|------------------|
| **PCI** (clásico) | Obsoleto, presente en equipos antiguos o industriales |
| **AGP** | Obsoleto (antigua ranura de gráficos) |
| **USB / Thunderbolt** | Conexión externa; controladoras integradas en CPU o chipset |

---

## 8. Almacenamiento: SATA y M.2

### SATA

- Conector para discos duros y SSD de 2,5" y 3,5".
- **SATA III:** hasta 6 Gbit/s (~550 MB/s reales).
- Usa cable de datos y conector de alimentación independiente (desde la fuente).

### M.2

Formato de ranura pequeña para SSD y otros módulos. **Ojo:** el formato físico no determina el protocolo.

| Interfaz | Protocolo | Velocidad aprox. |
|----------|-----------|------------------|
| **M.2 SATA** | SATA | ~550 MB/s |
| **M.2 NVMe (PCIe 3.0 x4)** | NVMe | ~3.500 MB/s |
| **M.2 NVMe (PCIe 4.0 x4)** | NVMe | ~7.000 MB/s |
| **M.2 NVMe (PCIe 5.0 x4)** | NVMe | ~12.000+ MB/s |

**Tamaños habituales** (se indican con un código de longitud): `2242`, `2260`, `2280`, `22110`. El más común en sobremesa es el **2280** (22 mm de ancho × 80 mm de largo).

**Aspectos a comprobar en el manual:**

- Qué ranuras M.2 admiten **NVMe**, **SATA** o ambos.
- Si usar una ranura M.2 **deshabilita algún puerto SATA** (comparten líneas).
- Si la ranura dispone de **disipador**.

### RAID

Permite combinar varias unidades para mejorar rendimiento y/o tolerancia a fallos (RAID 0, 1, 5, 10…). Puede implementarse por **hardware** (controladora dedicada), por **firmware del chipset** ("fake RAID") o por **software** del sistema operativo.

---

## 9. Alimentación y VRM

### Conectores de alimentación

| Conector | Pines | Función |
|----------|-------|---------|
| **ATX principal** | 24 (20+4) | Alimenta la placa |
| **EPS / CPU** | 4, 8 o 4+4 (a veces dos) | Alimenta el procesador |
| **PCIe auxiliar** | 6, 8 o conector 12VHPWR / 12V-2x6 | Alimenta gráficas potentes (conectado desde la fuente a la tarjeta) |
| **SATA / Molex** | — | Unidades de almacenamiento y accesorios |

> **Error frecuente:** olvidar conectar el **EPS de CPU**. El equipo no arranca o se queda sin vida aunque el ATX de 24 pines esté conectado.

### VRM (*Voltage Regulator Module*)

La CPU necesita tensiones bajas y muy estables (en torno a 1 V), mientras que la fuente suministra **+12 V**. El **VRM** convierte y regula esa tensión.

Se compone de:

- **Fases de alimentación** (*power phases*): cuantas más, mejor reparto de carga y menor calor por fase.
- **MOSFET**: conmutan la corriente.
- **Inductancias (chokes)** y **condensadores**: filtran y estabilizan.
- **Controlador PWM**: gestiona las fases.
- **Disipadores de VRM**: evacuan calor.

> Una CPU potente en una placa con VRM justo puede sufrir **limitación de rendimiento** (*throttling*) o inestabilidad. Al elegir placa, valora que su VRM esté a la altura del consumo (TDP/PL2) del procesador.

---

## 10. BIOS y UEFI

El **firmware** de la placa base es el primer software que se ejecuta al encender. Inicializa el hardware, realiza el **POST** y cede el control al gestor de arranque del sistema operativo.

### BIOS (Basic Input/Output System) vs UEFI

| Característica | BIOS clásica (*Legacy*) | UEFI |
|----------------|-------------------------|------|
| Modo de ejecución | 16 bits | 32/64 bits |
| Esquema de particiones | **MBR** (discos hasta 2 TiB, 4 particiones primarias) | **GPT** (discos muy grandes, muchas particiones) |
| Interfaz | Texto, solo teclado | Gráfica, admite ratón |
| Arranque seguro | No | **Secure Boot** |
| Arranque | Lento, basado en MBR | Más rápido, basado en la partición **ESP** |
| Extensibilidad | Limitada | Modular, admite controladores y aplicaciones |

> Hoy en día, casi todas las placas usan **UEFI**, aunque es habitual seguir llamándolo "BIOS". Muchas ofrecen **CSM** (modo de compatibilidad con arranque *legacy*).

### Proceso de arranque

1. **Encendido:** la fuente da la señal *Power Good* y arranca la CPU.
2. **POST** (*Power-On Self-Test*): comprueba CPU, RAM, gráficos y dispositivos básicos.
3. **Inicialización del hardware** y aplicación de la configuración guardada.
4. **Búsqueda del dispositivo de arranque** según el orden configurado.
5. **Carga del gestor de arranque** y del sistema operativo.

### Opciones habituales a conocer

- **Orden de arranque** (*Boot Order*).
- **Virtualización:** Intel VT-x / AMD-V (SVM).
- **Secure Boot** y **TPM** (necesarios para algunos sistemas operativos).
- **Perfiles de memoria** XMP/EXPO.
- **Modo SATA:** AHCI, RAID.
- **Curvas de ventiladores** y monitorización de temperaturas.
- **Contraseñas** de supervisor y usuario.
- **Restablecer valores por defecto** (*Load Optimized Defaults*).

### Actualización del firmware

- Se realiza desde la propia UEFI o desde el sistema, con el archivo oficial del fabricante.
- Es necesaria a veces para **soportar nuevas CPU** o corregir fallos de seguridad.
- **Precaución:** no apagues ni interrumpas el equipo durante la actualización, ya que puede dejar la placa inservible. Muchas placas incluyen **BIOS dual** o función de recuperación (*BIOS Flashback*).

### Pila CMOS y reinicio de la configuración

- La pila de botón (normalmente **CR2032**, 3 V) conserva hora y ajustes.
- Si se agota: fecha y hora incorrectas y pérdida de configuración.
- Para **restablecer** la configuración: retirar la pila unos minutos con el equipo desenchufado, o usar el **jumper CLR_CMOS** / botón de reset CMOS.

---

## 11. Conectores del panel frontal y cabeceras internas

### Panel frontal de la caja (*F_PANEL*)

Agrupa los cables de botones y LED de la caja:

| Señal | Función |
|-------|---------|
| **PWR_SW** | Botón de encendido |
| **RESET_SW** | Botón de reinicio |
| **PWR_LED** | LED de encendido |
| **HDD_LED** | LED de actividad del disco |
| **Speaker** | Altavoz interno (códigos de pitidos) |

> Los LED tienen **polaridad** (+/−); los botones no. La serigrafía de la placa y el manual indican la posición de cada pin.

### Otras cabeceras internas

| Cabecera | Uso |
|----------|-----|
| **USB 2.0** (9 pines) | Puertos USB frontales |
| **USB 3.x** (19/20 pines) | Puertos USB 3 frontales |
| **USB-C frontal** (conector tipo clave) | Puerto USB-C de la caja |
| **HD Audio** (AAFP) | Audio frontal |
| **CPU_FAN / SYS_FAN / AIO_PUMP** | Ventiladores y bomba de refrigeración líquida |
| **RGB / ARGB** (12 V / 5 V) | Iluminación (conectores **no compatibles** entre sí) |
| **TPM** | Módulo de plataforma segura (si no está integrado) |
| **COM / LPT** | Puertos serie/paralelo (algunas placas) |
| **Jumpers** | Configuración (p. ej. CLR_CMOS) |

---

## 12. Conectores del panel trasero (I/O)

| Conector | Descripción |
|----------|-------------|
| **USB-A / USB-C** | Periféricos y almacenamiento (USB 2.0, 3.x, USB4 en algunas placas) |
| **Ethernet (RJ-45)** | Red cableada (1 GbE, 2,5 GbE, 10 GbE según modelo) |
| **HDMI / DisplayPort** | Salida de vídeo de la gráfica integrada de la CPU |
| **Audio (jack 3,5 mm / S/PDIF)** | Entradas y salidas de audio |
| **Wi-Fi / Bluetooth (antenas)** | En modelos con tarjeta inalámbrica integrada |
| **PS/2** | Teclado y ratón clásicos (en algunas placas) |
| **Botones BIOS Flashback / Clear CMOS** | Utilidades de recuperación |

> **Importante:** las salidas de vídeo de la placa **solo funcionan si la CPU tiene gráficos integrados**. Si se instala una gráfica dedicada, el monitor debe conectarse a ella.

---

## 13. Placas base para servidores y estaciones de trabajo

Las placas de servidor están diseñadas para funcionar de forma continua, con mayor fiabilidad y capacidad de gestión remota.

### Diferencias respecto a las placas de consumo

| Aspecto | Consumo | Servidor / workstation |
|---------|---------|------------------------|
| Procesadores | 1 CPU | 1, 2, 4 u 8 CPU (multi-socket) |
| Memoria | Sin ECC (normalmente), 2–4 ranuras | **ECC**, RDIMM, 8–32 ranuras, varios canales |
| Factor de forma | ATX, mATX, Mini-ITX | E-ATX, SSI, propietarios para rack |
| Gestión remota | No | **BMC** (IPMI, iDRAC, iLO, Redfish) |
| Red | 1 puerto, a menudo 1–2,5 GbE | Varios puertos, 10/25/100 GbE |
| Expansión | Pocas líneas PCIe | Muchas líneas PCIe, OCuLink, backplanes SAS/NVMe |
| Almacenamiento | SATA, M.2 | SAS, NVMe U.2/U.3, controladoras RAID |
| Vídeo | GPU integrada de CPU | Chip gráfico básico en el BMC |
| Diseño | Estética, RGB | Robustez, redundancia, ventilación en flujo de aire |

### Gestión remota (BMC)

- Controlador independiente con **su propia red** y alimentación.
- Permite **encender, apagar, reiniciar, ver consola y montar ISO** de forma remota, aunque el sistema operativo no esté funcionando.
- Monitoriza temperaturas, ventiladores, tensiones y registra eventos de hardware.

### Redundancia y fiabilidad

- **Fuentes de alimentación redundantes** (N+1).
- **Módulos de memoria con ECC** y modos de espejo/*sparing*.
- **Discos intercambiables en caliente** (*hot-swap*) y controladoras RAID.
- Componentes de larga duración y **ciclos de soporte** prolongados.

---

## 14. Compatibilidad entre componentes

Antes de montar o ampliar un equipo, comprueba esta cadena de compatibilidad:

| Elemento | Qué verificar |
|----------|---------------|
| **CPU ↔ placa** | Socket, chipset y **versión de BIOS** compatible |
| **RAM ↔ placa/CPU** | Generación (DDR4/DDR5), tipo (UDIMM/RDIMM), velocidad y capacidad máxima, ECC |
| **Caja ↔ placa** | Factor de forma, altura de disipador, longitud de gráfica |
| **Fuente ↔ placa** | Conectores ATX 24 pines, EPS de CPU, conectores PCIe y potencia total |
| **Disipador ↔ socket** | Sistema de anclaje y **TDP** soportado |
| **Gráfica ↔ placa** | Ranura PCIe disponible, alimentación auxiliar, espacio físico |
| **Almacenamiento ↔ placa** | Ranuras M.2 (formato y protocolo), puertos SATA disponibles |
| **Sistema operativo ↔ firmware** | UEFI/GPT, Secure Boot, TPM si se requieren |

### Fuentes de información fiables

- **Manual de la placa base** (PDF del fabricante): ranuras, conectores, tabla de compatibilidad.
- **Listas QVL** (*Qualified Vendor List*): memorias y dispositivos probados por el fabricante.
- **Lista de CPU compatibles** con la versión mínima de BIOS.

---

## 15. Cómo elegir una placa base

| Criterio | Preguntas que hay que hacerse |
|----------|-------------------------------|
| **Socket y chipset** | ¿Soporta la CPU elegida y deja margen de ampliación futura? |
| **Factor de forma** | ¿Cabe en la caja prevista y ofrece las ranuras necesarias? |
| **Memoria** | ¿DDR4 o DDR5? ¿Cuántas ranuras y qué capacidad máxima? ¿ECC? |
| **Almacenamiento** | ¿Cuántas ranuras M.2 y puertos SATA? ¿Soporta NVMe PCIe 4.0/5.0? |
| **Expansión** | ¿Hay ranuras PCIe suficientes y con las líneas necesarias? |
| **Conectividad** | ¿Red 1/2,5/10 GbE? ¿Wi-Fi? ¿USB-C, USB 3.2, Thunderbolt? |
| **VRM y refrigeración** | ¿Es adecuado para el consumo de la CPU? |
| **Firmware** | ¿Buen soporte de actualizaciones? ¿Función BIOS Flashback? |
| **Uso previsto** | Oficina, virtualización, servidor, juegos, edición… |
| **Presupuesto** | Equilibrar prestaciones reales frente a funciones que no se usarán |

### Orientación por perfil de uso

| Uso | Enfoque recomendado |
|-----|---------------------|
| **Oficina / aula** | Chipset básico, mATX, gráficos integrados, bajo consumo |
| **Desarrollo y virtualización** | Muchas ranuras de RAM y capacidad alta, varios M.2, buena red |
| **Servidor de ficheros / NAS** | Muchos puertos SATA o controladora RAID, ECC, red fiable |
| **Servidor profesional** | Placa de servidor, ECC, BMC, redundancia |
| **Edición / renderizado** | VRM robusto, mucha RAM, varios NVMe |
| **Equipo compacto** | Mini-ITX, atención a refrigeración y ranuras limitadas |

---

## 16. Comandos útiles para identificar la placa

### Linux

```bash
# Modelo y fabricante de la placa base
sudo dmidecode -t baseboard

# Versión y fecha de la BIOS/UEFI
sudo dmidecode -t bios

# Información del sistema completa
sudo dmidecode -t system

# Comprobar si el sistema arrancó en modo UEFI
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "BIOS Legacy"

# Dispositivos PCI (incluye chipset, tarjetas y controladoras)
lspci

# Dispositivos USB
lsusb

# Módulos de memoria: tipo, velocidad, ranuras ocupadas
sudo dmidecode -t memory

# Resumen de hardware
sudo lshw -short
```

### Windows (CMD / PowerShell)

```powershell
# Fabricante, modelo y versión de la placa
wmic baseboard get manufacturer,product,version,serialnumber

# Versión de BIOS
wmic bios get smbiosbiosversion,manufacturer,releasedate

# Equivalente con PowerShell
Get-CimInstance Win32_BaseBoard | Select-Object Manufacturer, Product, Version
Get-CimInstance Win32_BIOS | Select-Object SMBIOSBIOSVersion, Manufacturer, ReleaseDate

# Información general del sistema (incluye modo de BIOS)
msinfo32
```

> En **msinfo32** aparecen el modelo de la placa, la versión de BIOS y el **Modo de BIOS** (UEFI o Heredado), además de si el arranque seguro está activado.

### Herramientas gráficas útiles

- **CPU-Z** (pestañas *Mainboard* y *Memory*).
- **HWiNFO**: información y monitorización detallada de sensores.
- **Speccy** o **AIDA64**: inventario de hardware.

---

### Bibliografía y recursos recomendados

- **Manual de la placa base** del fabricante (ASUS, Gigabyte, MSI, ASRock, Supermicro, etc.).
- Web de **Intel** y **AMD**: especificaciones de chipsets y sockets.
- Especificación **UEFI** (uefi.org) y documentación de **PCI-SIG** (PCI Express).
- Documentación de **Linux** (`man dmidecode`, `man lspci`) y de **Microsoft Learn** (CIM/WMI).

> **Aviso:** nombres de chipsets, generaciones y velocidades cambian con rapidez. Los conceptos de este documento son estables, pero contrasta siempre los datos de un modelo concreto con la documentación oficial del fabricante.
