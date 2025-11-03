# TARJETAS DE EXPANSIÓN - APUNTES FUNDAMENTALES

## 1. INTRODUCCIÓN A LAS TARJETAS DE EXPANSIÓN

### 1.1 ¿Qué son las tarjetas de expansión?

Las tarjetas de expansión son componentes hardware que se instalan en los slots (ranuras) de la placa base para añadir o mejorar funcionalidades del sistema. Son una de las características más importantes de la arquitectura PC, ya que permiten personalizar y ampliar las capacidades del ordenador sin necesidad de sustituir componentes principales.

A lo largo de la historia de la informática personal, las tarjetas de expansión han evolucionado desde simples añadidos para funciones básicas hasta complejos sistemas que pueden transformar completamente las capacidades de un ordenador. Hoy en día, aunque muchas funciones que antes requerían tarjetas dedicadas están integradas en las placas base modernas (como audio, red Ethernet, USB, etc.), las tarjetas de expansión siguen siendo fundamentales para aplicaciones especializadas y para obtener rendimiento superior al que ofrecen los componentes integrados.

### 1.2 Filosofía de la arquitectura abierta

El concepto de tarjetas de expansión es inherente a la filosofía de "arquitectura abierta" que IBM estableció con el PC original en 1981. A diferencia de los sistemas cerrados donde el fabricante controla todas las capacidades del equipo, un PC con slots de expansión permite que terceros desarrollen hardware adicional. Esta apertura ha sido clave para el éxito y la evolución del PC.

Imagina que tu placa base es como una ciudad con diferentes tipos de carreteras (buses). Las tarjetas de expansión son como edificios que construyes conectándose a estas carreteras para añadir nuevos servicios a la ciudad. Algunos edificios necesitan autopistas de alta velocidad (PCIe x16 para gráficas), otros pueden funcionar con carreteras más modestas (PCIe x1 para tarjetas de red).

### 1.3 Evolución histórica de los buses de expansión

Para entender las tarjetas de expansión actuales, es útil conocer su evolución. Los primeros PCs utilizaban el **bus ISA (Industry Standard Architecture)**, que operaba a velocidades de 8 MHz con 8 o 16 bits de ancho de datos. Aunque revolucionario en su momento, ISA era extremadamente lento para los estándares actuales, con un ancho de banda máximo de apenas 16 MB/s.

Le siguió **PCI (Peripheral Component Interconnect)**, introducido en 1992, que aumentó significativamente el rendimiento con 33 MHz y 32 bits, proporcionando 133 MB/s de ancho de banda. PCI se convirtió en el estándar durante más de una década y aún hoy podemos encontrar algunos slots PCI en placas base antiguas.

**AGP (Accelerated Graphics Port)** fue un bus diseñado específicamente para tarjetas gráficas, apareciendo en 1997. Ofrecía un canal dedicado entre la GPU y la CPU, evitando el cuello de botella del bus PCI compartido. AGP evolucionó hasta AGP 8x con 2.1 GB/s de ancho de banda, pero fue completamente sustituido por PCIe.

Finalmente, **PCI Express (PCIe)**, introducido en 2003, revolucionó completamente el panorama. A diferencia de sus predecesores, PCIe utiliza enlaces serie punto a punto en lugar de un bus compartido, lo que permite velocidades mucho mayores y eliminando problemas de contención. Cada slot PCIe tiene un ancho de banda dedicado que no se comparte con otros dispositivos.

---

## 2. BUS PCI EXPRESS (PCIe)

### 2.1 Arquitectura y funcionamiento

PCI Express es el estándar actual y futuro previsible para tarjetas de expansión. Su arquitectura es radicalmente diferente a la de los buses anteriores. En lugar de un bus paralelo compartido donde todos los dispositivos compiten por el ancho de banda, PCIe utiliza **enlaces serie dedicados** llamados "lanes" (carriles).

Cada lane de PCIe consiste en dos pares de cables: uno para transmisión y otro para recepción. Esto permite comunicación **full-duplex**, es decir, datos pueden fluir simultáneamente en ambas direcciones a máxima velocidad. Es como tener una carretera de doble sentido donde el tráfico en cada dirección no interfiere con el otro.

Los slots PCIe pueden tener diferentes números de lanes, designados como x1, x4, x8 o x16 (pronunciado "por uno", "por cuatro", etc.). Un slot x16 tiene 16 lanes, proporcionando 16 veces el ancho de banda de un slot x1. Visualmente, los slots x16 son los más largos (aproximadamente 89 mm), mientras que los x1 son los más cortos (aproximadamente 25 mm).

Una característica interesante de PCIe es que las tarjetas más pequeñas pueden instalarse en slots más grandes. Por ejemplo, puedes instalar una tarjeta PCIe x1 en un slot x16, aunque solo utilizará un lane. Sin embargo, una tarjeta x16 no puede instalarse físicamente en un slot x4 debido a su mayor longitud (aunque existen adaptadores y algunas placas tienen slots x16 "abiertos" que permiten esto).

### 2.2 Generaciones de PCIe y ancho de banda

PCIe ha evolucionado a través de varias generaciones, duplicando aproximadamente el ancho de banda en cada una:

**PCIe 1.0 (2003):** La primera generación ofrecía 250 MB/s por lane (2.5 GT/s), lo que significaba 4 GB/s para un slot x16. Aunque esto era impresionante comparado con AGP 8x (2.1 GB/s), rápidamente quedó obsoleto.

**PCIe 2.0 (2007):** Duplicó la velocidad a 500 MB/s por lane (5 GT/s), proporcionando 8 GB/s en x16. Esta generación fue suficiente para las tarjetas gráficas de su época y todavía es funcional para muchas aplicaciones actuales, aunque limitada.

**PCIe 3.0 (2010):** Volvió a duplicar el ancho de banda a 984.6 MB/s por lane (8 GT/s), alcanzando aproximadamente 16 GB/s en x16. Esta generación dominó durante muchos años y sigue siendo perfectamente válida para la mayoría de tarjetas gráficas actuales de gama media-alta.

**PCIe 4.0 (2017):** Introdujo 1.969 GB/s por lane (16 GT/s), con 32 GB/s en x16. Esta generación es especialmente importante para SSDs NVMe de alto rendimiento, que pueden saturar completamente PCIe 3.0 x4. Las tarjetas gráficas de alta gama también se benefician, aunque menos dramáticamente que los SSDs.

**PCIe 5.0 (2019):** Ofrece 3.938 GB/s por lane (32 GT/s), llegando a 64 GB/s en x16. Los primeros SSDs PCIe 5.0 empezaron a aparecer en 2022-2023, alcanzando velocidades de lectura/escritura de 12-14 GB/s. Sin embargo, estos SSDs generan mucho calor y requieren refrigeración activa.

**PCIe 6.0 (2022):** La especificación fue finalizada con 7.877 GB/s por lane (64 GT/s), alcanzando teóricamente 128 GB/s en x16. Esta generación utiliza codificación PAM4 (Pulse Amplitude Modulation con 4 niveles) en lugar de NRZ (Non-Return-to-Zero), lo que permite duplicar la tasa de transferencia sin aumentar la frecuencia. Los primeros productos están empezando a aparecer en 2024-2025.

**PCIe 7.0 (2025+):** Ya está en desarrollo con la especificación esperada para 2025, ofreciendo 15.754 GB/s por lane (128 GT/s), lo que significaría 256 GB/s en x16. Esto es orientado principalmente a aplicaciones de computación de alto rendimiento, inteligencia artificial y centros de datos.

### 2.3 Compatibilidad entre generaciones

Una de las grandes ventajas de PCIe es su **retrocompatibilidad completa**. Puedes instalar una tarjeta PCIe de cualquier generación en un slot de cualquier otra generación, y funcionará. Sin embargo, la comunicación se realizará a la velocidad del componente más lento.

Por ejemplo, si instalas una tarjeta gráfica PCIe 4.0 en un slot PCIe 3.0, funcionará perfectamente pero a velocidades PCIe 3.0. En la práctica, esto raramente es un problema significativo para la mayoría de aplicaciones. Incluso tarjetas gráficas de alta gama actuales solo pierden un 0-5% de rendimiento funcionando en PCIe 3.0 x16 en lugar de PCIe 4.0 x16, porque la mayoría del trabajo se realiza en la memoria de la propia tarjeta, no transfiriendo datos constantemente al sistema.

Sin embargo, hay una situación donde las diferencias de generación sí importan: cuando una tarjeta diseñada para funcionar en x16 se ve forzada a funcionar en x8 o menos lanes. Por ejemplo, una GPU de alta gama en PCIe 3.0 x8 tendrá un cuello de botella más notable que la misma GPU en PCIe 4.0 x8, porque PCIe 4.0 x8 proporciona el mismo ancho de banda que PCIe 3.0 x16.

### 2.4 Distribución de lanes PCIe

Un aspecto crucial que muchos usuarios desconocen es que el número total de lanes PCIe disponibles en un sistema es limitado y debe distribuirse entre todos los dispositivos. Los procesadores modernos de consumo típicamente ofrecen:

**Intel (generaciones recientes):**
- Procesadores mainstream (i5, i7, i9): 16-20 lanes PCIe desde la CPU
- Procesadores HEDT (i9 Extreme, antiguos Core X): 44-48 lanes

**AMD (generaciones recientes):**
- Ryzen mainstream: 24 lanes PCIe (20 usables, 4 reservados para el chipset)
- Ryzen Threadripper: 64-128 lanes según el modelo

Estos lanes se distribuyen típicamente así: 16 lanes para la tarjeta gráfica principal, 4 lanes para el primer SSD M.2, y el resto para el chipset. El chipset, a su vez, proporciona lanes adicionales que se comparten entre los dispositivos conectados a él (SSDs M.2 adicionales, slots PCIe x1, SATA, USB, etc.).

Esto significa que si instalas múltiples tarjetas de expansión y SSDs M.2, podrías estar reduciendo el ancho de banda disponible para cada uno. Las placas base modernas suelen incluir tablas en sus manuales mostrando cómo se distribuyen los lanes según la configuración de dispositivos instalados. Por ejemplo, instalar un SSD en el segundo slot M.2 podría desactivar dos puertos SATA, o hacer que el segundo slot PCIe x16 funcione solo en modo x4.

### 2.5 PCIe Bifurcation (Bifurcación)

Algunas placas base y sistemas avanzados soportan **bifurcation**, que permite dividir un slot PCIe x16 en múltiples slots más pequeños. Por ejemplo, dividir un x16 en cuatro x4, o dos x8. Esto es útil para instalar múltiples SSDs NVMe en un solo slot mediante tarjetas adaptadoras, o para configuraciones con múltiples GPUs donde no se necesita el ancho de banda completo para cada una.

La bifurcation debe estar soportada tanto por la placa base como habilitada en la BIOS. No todas las placas la soportan, especialmente las de gama baja y media, por lo que es importante verificar las especificaciones antes de comprar hardware que dependa de esta función.

---

## 3. TARJETAS GRÁFICAS (GPU)

### 3.1 La tarjeta de expansión más importante

Las tarjetas gráficas son, sin duda, las tarjetas de expansión más comunes, importantes y potentes en los sistemas actuales. Aunque técnicamente muchos procesadores incluyen gráficos integrados suficientes para tareas básicas, cualquier uso que involucre gaming, edición de vídeo, diseño 3D, renderizado, o inteligencia artificial requiere una GPU dedicada.

Una tarjeta gráfica moderna es, esencialmente, un ordenador completo dentro de tu ordenador. Contiene su propio procesador (la GPU), su propia memoria RAM (VRAM), su propio sistema de refrigeración, su propia placa de circuito impreso (PCB), e incluso su propio firmware y controladores de software. En muchos casos, una tarjeta gráfica de alta gama es más potente y cara que el resto del ordenador completo.

### 3.2 Arquitectura de una tarjeta gráfica

La **GPU (Graphics Processing Unit)** es el chip principal de la tarjeta. A diferencia de una CPU que tiene pocos núcleos muy potentes y versátiles, una GPU tiene miles de núcleos más simples diseñados para realizar operaciones matemáticas en paralelo. Esta arquitectura es perfecta para gráficos, donde millones de píxeles deben procesarse simultáneamente, pero también para otras aplicaciones paralelizables como criptominería, inteligencia artificial, o simulaciones científicas.

Las GPUs modernas contienen diferentes tipos de núcleos especializados:
- **CUDA Cores (NVIDIA) / Stream Processors (AMD):** Los núcleos de procesamiento general
- **Tensor Cores (NVIDIA) / Matrix Cores (AMD):** Aceleradores para operaciones de inteligencia artificial y deep learning
- **RT Cores (NVIDIA) / Ray Accelerators (AMD):** Unidades dedicadas para ray tracing (trazado de rayos) en tiempo real
- **Unidades de texturizado:** Especializadas en aplicar texturas a superficies 3D
- **ROPs (Render Output Units):** Finalizan los píxeles y los escriben en memoria

La **VRAM (Video RAM)** es la memoria dedicada de la tarjeta gráfica. Almacena texturas, modelos 3D, framebuffers, y otros datos necesarios para el renderizado. La cantidad y tipo de VRAM son cruciales para el rendimiento:

**Cantidad de VRAM necesaria:**
- Gaming 1080p: 6-8 GB suficiente
- Gaming 1440p: 8-12 GB recomendado
- Gaming 4K / Edición vídeo 4K: 12-16 GB mínimo
- Workstation profesional / IA: 24 GB o más

**Tipos de VRAM:**
- **GDDR6:** Estándar actual, velocidades de 14-16 Gbps por pin
- **GDDR6X:** Versión mejorada usada por NVIDIA en gamas altas, hasta 21 Gbps
- **GDDR7:** Nueva generación empezando a aparecer en 2024-2025, hasta 32 Gbps
- **HBM (High Bandwidth Memory):** Memoria apilada verticalmente usada en GPUs profesionales y de gama extremadamente alta, ofrece anchos de banda de varios TB/s pero es muy cara

El **ancho de bus de memoria** (128-bit, 192-bit, 256-bit, 384-bit) determina cuántos datos pueden transferirse simultáneamente entre la GPU y la VRAM. Un bus más ancho generalmente significa mejor rendimiento, especialmente a resoluciones altas.

### 3.3 Sistemas de refrigeración en GPUs

Las tarjetas gráficas modernas de alto rendimiento pueden consumir entre 200 y 600 vatios, generando cantidades enormes de calor que deben disiparse eficientemente. Existen varios diseños de refrigeración:

**Diseño de referencia (Founders Edition en NVIDIA, Reference en AMD):**
- Diseño oficial del fabricante del chip
- Suele priorizar estética y tamaño compacto
- Rendimiento térmico y acústico generalmente aceptable pero no excepcional
- A veces más económicas

**Diseños custom de terceros (ASUS, MSI, Gigabyte, etc.):**
- Disipadores más grandes y elaborados
- Típicamente 2-3 ventiladores de 80-100mm
- Mejor refrigeración y menor ruido
- Frecuencias ligeramente superiores (factory overclocked)
- Suelen ser más caras que las de referencia

**Refrigeración líquida híbrida:**
- AIO integrado en la tarjeta
- Excelente refrigeración para modelos de consumo extremo (450W+)
- Más cara y compleja de instalar
- Ejemplos: EVGA Hybrid, MSI Sea Hawk

**Bloques de agua para custom loop:**
- Para entusiastas del watercooling personalizado
- Máximo rendimiento térmico
- Muy caros (200-400€ solo el bloque)
- Requieren circuito de refrigeración líquida completo

### 3.4 Conectores de alimentación

Las tarjetas gráficas modernas requieren alimentación adicional más allá de los 75W que puede proporcionar el slot PCIe x16. Esta alimentación extra se suministra mediante conectores dedicados:

**Conectores tradicionales:**
- **6-pin PCIe:** Proporciona hasta 75W adicionales
- **8-pin (6+2) PCIe:** Proporciona hasta 150W adicionales
- Las tarjetas de gama alta pueden requerir múltiples conectores: 2x 8-pin (300W + 75W slot = 375W total), o incluso 3x 8-pin para modelos extremos

**Conector 12VHPWR (PCIe 5.0):**
- Nuevo estándar introducido con GPUs NVIDIA RTX 40-series
- 16 pines (12 para alimentación, 4 para señalización)
- Puede proporcionar hasta 600W en un solo conector
- Inicialmente tuvo problemas de derretimiento de conectores debido a conexiones incorrectas o mal diseño de algunos cables
- Versión mejorada **12V-2x6** corrige estos problemas

Es absolutamente crítico que tu fuente de alimentación tenga los conectores y la potencia suficiente para la tarjeta gráfica. Una regla general: la fuente debe tener al menos 150-200W más de capacidad que el consumo total estimado del sistema para tener margen de seguridad y eficiencia óptima.

### 3.5 Tecnologías y características modernas

**Ray Tracing (Trazado de Rayos):**
- Técnica de renderizado que simula el comportamiento físico real de la luz
- Produce reflejos, sombras e iluminación global mucho más realistas
- Muy demandante computacionalmente
- Acelerado por hardware en GPUs modernas (RTX 20-series en adelante para NVIDIA, RX 6000 en adelante para AMD)

**DLSS (Deep Learning Super Sampling - NVIDIA) / FSR (FidelityFX Super Resolution - AMD):**
- Técnicas de upscaling impulsadas por IA que renderizan el juego a resolución más baja y luego lo escalan inteligentemente
- Permiten jugar a 4K con rendimiento cercano al de 1440p
- DLSS generalmente considerado superior pero exclusivo de NVIDIA RTX
- FSR funciona en más hardware (incluso GPUs antiguas) pero con resultados variables

**VRAM unificada vs dedicada:**
- Gráficos integrados usan parte de la RAM del sistema (unificada)
- GPUs dedicadas tienen su propia VRAM (dedicada)
- VRAM dedicada es mucho más rápida pero limitada en cantidad
- Algunos sistemas (como Apple Silicon) usan VRAM unificada de alta velocidad con resultados excelentes

### 3.6 Consideraciones de instalación

**Espacio físico:**
- Las GPUs modernas son enormes: 270-340mm de largo, ocupando 2-3 slots de altura
- Verificar que la caja tiene espacio suficiente
- Distancia mínima desde el final del slot PCIe hasta la jaula de discos/panel frontal

**Sag (combadura):**
- Las tarjetas pesadas (1-2 kg) pueden combarse por su propio peso
- Solución: Soportes anti-sag, brackets verticales, o montaje vertical con riser

**Montaje vertical:**
- Requiere riser cable (cable PCIe que extiende la conexión)
- Mejora estética mostrando la cara de la GPU
- Puede empeorar refrigeración si la GPU queda muy cerca del panel lateral
- Asegurar que el riser es de calidad (PCIe 3.0/4.0 certificado)

**Clearance con componentes:**
- Verificar que no interfiere con VRM heatsinks de la placa
- Algunos disipadores CPU grandes pueden interferir con GPUs en el primer slot

---

## 4. TARJETAS DE SONIDO

### 4.1 ¿Sigue siendo relevante una tarjeta de sonido dedicada?

Esta es una pregunta válida en 2025. Las placas base modernas incluyen audio integrado basado en codecs de alta calidad (Realtek ALC1220, ALC4080, etc.) que para la mayoría de usuarios proporcionan calidad más que suficiente. Entonces, ¿por qué comprar una tarjeta de sonido dedicada?

La respuesta corta es: para la mayoría de usuarios, no es necesaria. Pero hay casos específicos donde sí tiene sentido:

**Audiófilos y músicos:**
Si utilizas auriculares de alta impedancia (250-600 ohmios), el amplificador integrado en la placa base probablemente no podrá alimentarlos adecuadamente, resultando en volumen bajo y calidad comprometida. Una tarjeta de sonido dedicada o, mejor aún, un DAC/amplificador externo, es necesaria para aprovechar completamente estos auriculares.

**Productores y creadores de contenido audio:**
Para grabación y producción musical profesional, se necesita una tarjeta con entradas XLR/TRS balanceadas, conversores AD/DA (analógico-digital/digital-analógico) de alta calidad, drivers ASIO de baja latencia, y monitorización sin latencia. Esto requiere interfaces de audio profesionales, no tarjetas de sonido consumer.

**Gaming competitivo:**
Algunos jugadores profesionales aprecian el audio posicional mejorado que ofrecen tarjetas con procesamiento dedicado como las Sound BlasterX AE-5 Plus o ASUS Essence STX II. Sin embargo, esto es cada vez más controversial, ya que el audio espacial basado en software (Windows Sonic, Dolby Atmos for Headphones, DTS:X) es muy competente.

### 4.2 Tipos de tarjetas y tecnologías

**Tarjetas de sonido consumer (gaming):**
- Enfocadas en gaming con audio posicional mejorado
- Amplificador para auriculares de hasta 150-300 ohmios
- Iluminación RGB (porque por qué no)
- Ejemplos: Creative Sound BlasterX AE-5 Plus, ASUS Strix Soar
- Precio: 80-200€

**Tarjetas de sonido audiófilo:**
- SNR (Signal-to-Noise Ratio) de 120+ dB
- THD (Total Harmonic Distortion) <0.001%
- Componentes de audio de gama alta (op-amps intercambiables, condensadores de calidad)
- Ejemplos: ASUS Essence STX II, EVGA Nu Audio Card
- Precio: 150-300€

**Interfaces de audio profesionales:**
- Realmente no son "tarjetas de sonido" sino interfaces externas
- Conectividad profesional: XLR, TRS, ADAT, S/PDIF
- Conversores de alta calidad, preamplificadores de micrófono
- Drivers ASIO con latencias de 2-5ms
- Ejemplos: Focusrite Scarlett, Universal Audio Apollo, RME Babyface
- Precio: 100-3000€+

### 4.3 Audio integrado vs dedicado: La realidad actual

La verdad incómoda para los fabricantes de tarjetas de sonido es que el audio integrado ha mejorado dramáticamente. Un codec Realtek ALC1220 bien implementado con:
- Condensadores de audio de calidad
- PCB con separación física de componentes digitales ruidosos
- Blindaje EMI adecuado
- Fuente de alimentación limpia

...puede rivalizar con tarjetas de sonido de 100€ de hace unos años. Marcas como MSI, ASUS y Gigabyte ponen considerable esfuerzo en sus implementaciones de audio, con esquemas como "Audio Boost", "SupremeFX", o "AMP-UP Audio".

El verdadero diferenciador de una tarjeta dedicada moderna es el **amplificador de auriculares**. Si tienes auriculares de 32-80 ohmios (la mayoría de gaming y consumo), el audio integrado es suficiente. Si tienes auriculares de 250-600 ohmios (Sennheiser HD 600, Beyerdynamic DT 990 Pro), necesitas amplificación dedicada.

### 4.4 DACs y amplificadores externos: La alternativa moderna

Muchos audiófilos y profesionales han abandonado las tarjetas de sonido internas en favor de **DACs/amplificadores externos** conectados por USB. Las ventajas son significativas:

**Aislamiento eléctrico:**
Fuera de la caja, lejos del ruido electromagnético de la GPU, fuente de alimentación, y otros componentes. Esto resulta en un ruido de fondo (floor noise) mucho más bajo.

**Portabilidad:**
Puedes usar el mismo DAC con tu ordenador, portátil, tablet, o incluso smartphone.

**Mejor soporte:**
Los drivers USB Audio Class 2.0 están integrados en los sistemas operativos modernos, sin necesidad de drivers propietarios problemáticos.

**Upgradability:**
Puedes mejorar tu cadena de audio sin abrir el PC ni preocuparte por compatibilidad de slots.

Marcas populares incluyen Schiit (Modi/Magni stack), FiiO, Topping, JDS Labs, y en gamas altas, Chord, Benchmark, o RME. Los precios van desde 50€ (FiiO E10K) hasta varios miles de euros para equipos de referencia.

---

## 5. TARJETAS DE RED

### 5.1 Tarjetas Ethernet (Cable)

Aunque prácticamente todas las placas base modernas incluyen Ethernet Gigabit (1 Gbps) integrado, existen razones válidas para añadir una tarjeta de red dedicada:

**Velocidades superiores:**
Si tienes una red doméstica o empresarial con infraestructura de 2.5 Gbps, 5 Gbps, 10 Gbps o incluso 25 Gbps, necesitarás una tarjeta que soporte estas velocidades. El Gigabit integrado se convierte en un cuello de botella severo cuando trabajas con almacenamiento en red de alto rendimiento.

**Características profesionales:**
- Soporte para VLAN (Virtual LAN) con hardware
- Wake-on-LAN más robusto
- Priorización de tráfico (QoS por hardware)
- Teaming/Bonding para redundancia o mayor ancho de banda
- Virtualización con SR-IOV (Single Root I/O Virtualization)

**Servidores y NAS:**
Los sistemas que actúan como servidores de archivos se benefician enormemente de NICs (Network Interface Cards) de mayor rendimiento. Una NIC de 10 Gbps puede parecer excesiva, pero cuando múltiples clientes acceden simultáneamente, marca una diferencia enorme.

### 5.2 Controladores y chipsets Ethernet

Los chipsets de red varían significativamente en calidad y características:

**Intel (i210, i225, i226, X520, X550, E810):**
- Considerados el estándar de oro en confiabilidad
- Excelentes drivers para Windows, Linux y BSD
- Menor uso de CPU gracias a offloading eficiente
- Precios más altos pero justificados
- i225/i226: 2.5 Gbps común en placas base de gama media-alta
- X520/X550: 10 Gbps para servidores y NAS
- E810: 25/100 Gbps para datacenters

**Realtek (RTL8111, RTL8125, RTL8156):**
- Dominan el mercado de bajo coste
- RTL8111: Gigabit, extremadamente común en placas base económicas
- RTL8125: 2.5 Gbps, cada vez más común
- Funcionan bien para uso doméstico, pero drivers menos pulidos que Intel
- Mayor uso de CPU en cargas pesadas de red

**Aquantia (ahora Marvel, AQC107, AQC113):**
- 2.5/5/10 Gbps
- Buena calidad, se encuentran en placas de gama alta
- Drivers han mejorado mucho pero históricamente problemáticos

**Mellanox (ahora NVIDIA, ConnectX series):**
- 10/25/40/100 Gbps
- Estándar en datacenters y HPC (High Performance Computing)
- Extremadamente caros pero rendimiento excepcional
- Soporte excelente para RDMA (Remote Direct Memory Access)

### 5.3 Velocidades de red modernas

El panorama de velocidades de red para consumo ha evolucionado significativamente:

**1 Gbps (Gigabit Ethernet):**
- Estándar universal desde hace más de una década
- ~125 MB/s teóricos, ~110-115 MB/s reales
- Suficiente para streaming 4K, gaming online, uso doméstico general
- Limitado para transferencias grandes de NAS o edición colaborativa

**2.5 Gbps (2.5GBASE-T):**
- El "sweet spot" actual para hogar/pequeña oficina
- ~300 MB/s reales
- Funciona con cableado Cat5e existente (hasta 100m)
- No requiere switches caros como 10 Gbps
- Cada vez más común en placas base de gama media-alta

**5 Gbps (5GBASE-T):**
- Menos común, un paso intermedio raro
- ~600 MB/s reales
- Mismo cableado que 2.5 Gbps
- Pocos productos en el mercado

**10 Gbps (10GBASE-T):**
- Estándar profesional/prosumer
- ~1200 MB/s reales
- Requiere Cat6a o Cat7 para distancias completas (100m)
- Switches y tarjetas significativamente más caros
- Consumo energético mayor (6-10W por puerto vs 1-2W de Gigabit)
- Ideal para NAS de alto rendimiento, edición de vídeo en red

**25/40/100 Gbps:**
- Datacenter y HPC
- Requieren switches extremadamente caros
- Típicamente usan SFP+ o QSFP+ (fibra óptica o DAC copper)
- Fuera del alcance del hogar/pequeña empresa

### 5.4 Tarjetas WiFi y Bluetooth

Aunque muchas placas base modernas incluyen WiFi, las tarjetas PCIe WiFi siguen siendo populares para:

**Actualizar a estándares más nuevos:**
- WiFi 6 (802.11ax): Hasta 9.6 Gbps teóricos, mejor eficiencia en entornos congestionados
- WiFi 6E: Añade banda de 6 GHz con más canales disponibles
- WiFi 7 (802.11be): Comenzando a aparecer en 2024, hasta 46 Gbps teóricos

**PCs de sobremesa sin WiFi integrado:**
- Alternativa a adaptadores USB que ocupan puertos y pueden interferir con otros dispositivos
- Mejor rendimiento y estabilidad que adaptadores USB económicos
- Antenas externas reposicionables para mejor señal

**Bluetooth:**
- Muchas tarjetas WiFi incluyen Bluetooth 5.0/5.1/5.2/5.3
- Útil para periféricos inalámbricos, auriculares, transferencia de archivos

### 5.5 Chipsets WiFi populares

**Intel (AX200, AX201, AX210, AX211, BE200):**
- Excelente soporte en Windows y Linux
- Drivers estables y actualizados regularmente
- AX200/AX201: WiFi 6 (2.4 Gbps máximo)
- AX210/AX211: WiFi 6E con banda de 6 GHz
- BE200: WiFi 7
- Muy recomendados, relación calidad-precio excepcional

**MediaTek (MT7921, MT7922):**
- WiFi 6/6E económicos
- Soporte en Linux ha mejorado significativamente
- Buen rendimiento, algo inferior a Intel en estabilidad

**Qualcomm (Atheros) (QCA6174, QCA9377):**
- Históricamente populares en portátiles
- Soporte variable, algunos modelos problemáticos en Linux

**Broadcom:**
- Comunes en portátiles y productos Apple
- Soporte en Linux históricamente pobre, ha mejorado
- No recomendados para construcción de PC custom

---

## 6. TARJETAS CONTROLADORAS

### 6.1 Controladoras SATA/SAS

Aunque las placas base modernas incluyen 4-8 puertos SATA, hay situaciones donde necesitas más:

**NAS y servidores de archivos:**
Un NAS de 8-12 bahías requiere al menos ese número de puertos SATA. Las placas base mainstream raramente ofrecen más de 6 puertos, y algunos pueden deshabilitarse al usar ciertos slots M.2.

**Solución:**
Tarjetas controladoras SATA/SAS PCIe. Estas tarjetas añaden puertos adicionales conectándose a un slot PCIe. Opciones comunes:

**Controladoras SATA básicas:**
- Chipsets Marvel, ASMedia
- 4-8 puertos SATA adicionales
- PCIe 2.0 x1 o x2 (suficiente para 4-6 HDDs)
- Económicas (25-60€)
- Ejemplos: IO Crest 4-Port SATA III, StarTech 4-Port SATA

**Controladoras SAS empresariales (IT mode):**
La solución preferida por entusiastas de NAS/homelab. Tarjetas empresariales reacondicionadas flasheadas a "IT mode" (modo passthrough sin RAID):

- **LSI 9211-8i / IBM M1015:** El clásico, 8 puertos internos SAS/SATA
- **LSI 9300-8i:** Versión más moderna, PCIe 3.0
- **LSI 9305-16i:** 16 puertos, para arrays grandes
- Soporte excelente en Linux (ZFS, UnRAID)
- Muy fiables, procedentes de servidores retirados
- Precio: 40-150€ en mercado de segunda mano

**Importante:** Los puertos SAS pueden usar discos SATA (con cables apropiados), pero puertos SATA no pueden usar discos SAS.

### 6.2 Controladoras RAID por hardware

Aunque RAID por software (mdadm en Linux, Storage Spaces en Windows, ZFS) es muy capaz, el RAID por hardware tiene ventajas en ciertos escenarios:

**Ventajas:**
- Procesamiento dedicado (no usa CPU del sistema)
- Caché con batería de respaldo (protege escrituras ante cortes de luz)
- Mejor rendimiento en RAID 5/6 (cálculos de paridad en hardware)
- Booteable (puedes arrancar el SO desde el array RAID)

**Desventajas:**
- Muy caras (200-2000€+)
- Dependencia del controlador (si falla, necesitas uno idéntico o compatible)
- Menos flexibles que soluciones software modernas

**Ejemplos:**
- Adaptec SmartRAID 3154-8i
- Broadcom/LSI MegaRAID 9361-8i
- HighPoint RocketRAID series

**Realidad actual:** Para la mayoría de usuarios, incluso profesionales, RAID por software con SSDs de calidad es superior. RAID por hardware tiene sentido principalmente en entornos empresariales específicos con requisitos de compatibilidad o soporte.

### 6.3 Controladoras USB/Thunderbolt

**Tarjetas USB adicionales:**
Útiles cuando necesitas más puertos USB que los disponibles en la placa base, o para añadir puertos USB de última generación:

- USB 3.2 Gen 2 (10 Gbps)
- USB 3.2 Gen 2x2 (20 Gbps)
- USB4 (40 Gbps, compatible con Thunderbolt 3/4)

**Controladoras Thunderbolt:**
Añadir puertos Thunderbolt 3 o 4 a sistemas que no los tienen. Requieren:
- Header Thunderbolt en placa base (no todas lo tienen)
- Certificación de Intel para Thunderbolt
- Relativamente caras (100-200€)

Ejemplos: ASUS ThunderboltEX 4, Gigabyte GC-Maple Ridge

**Consideración:** Verificar que la placa base tiene el header necesario antes de comprar.

---

## 7. TARJETAS DE CAPTURA DE VÍDEO

### 7.1 ¿Para qué sirven?

Las tarjetas de captura permiten grabar o hacer streaming de contenido desde fuentes externas: consolas de videojuegos, cámaras, otros ordenadores, equipos médicos, o cualquier dispositivo con salida de vídeo.

### 7.2 Tipos de tarjetas de captura

**Captura básica (streaming/gaming):**
- Capturan señal HDMI desde consolas o PC secundario
- Encoders por hardware (H.264/H.265)
- Passthrough de baja latencia para jugar sin retraso
- Resoluciones 1080p60 o 4K30/4K60
- Ejemplos: Elgato HD60 Pro, AVerMedia Live Gamer 4K
- Precio: 100-250€
- Uso: Streamers, creadores de contenido gaming

**Captura profesional:**
- SDI (Serial Digital Interface) además de HDMI
- 4K60 10-bit, HDR
- Múltiples entradas simultáneas
- Menor latencia, mayor calidad
- Ejemplos: Blackmagic DeckLink 4K Extreme, Magewell Pro Capture
- Precio: 300-2000€+
- Uso: Producción profesional, broadcast, edición

**Captura para TV analógica:**
- Prácticamente obsoletas
- Capturaban señales VHS, TV analógica, cámaras antiguas
- Aún útiles para digitalizar material antiguo

### 7.3 Consideraciones importantes

**Passthrough:**
Esencial para gaming. Permite ver el juego en tu monitor sin latencia mientras capturas. Sin passthrough, tendrías que ver el juego en el software de captura con retraso.

**Encoding:**
- **Hardware encoding:** La tarjeta codifica el vídeo (H.264/HEVC), descargando la CPU
- **Software encoding:** Envía vídeo sin comprimir al PC, que debe encoderlo
- Hardware encoding es preferible para streaming/grabación

**Resolución y framerate:**
- 1080p60: Estándar para streaming
- 4K30: Para contenido cinemático
- 4K60: Gaming nueva generación, requiere tarjetas de gama alta

**HDCP:**
Si la fuente tiene HDCP (protección de copia), no podrás capturar. Esto afecta a streaming de Netflix, Blu-rays, etc. desde consolas.

---

## 8. OTRAS TARJETAS ESPECIALIZADAS

### 8.1 Aceleradoras de Inteligencia Artificial

Con el boom de la IA, han aparecido tarjetas dedicadas a acelerar inferencia y entrenamiento de modelos:

**NVIDIA (Tensor Cores):**
- Las GPUs GeForce RTX tienen Tensor Cores para IA
- GPUs profesionales: A100, H100, L40 (datacenters)
- CUDA domina el ecosistema de IA

**Google TPU (Tensor Processing Unit):**
- ASICs diseñados específicamente para TensorFlow
- Principalmente en Google Cloud, pero existen Edge TPUs para dispositivos

**Intel (Habana Gaudi, Movidius):**
- Gaudi para training en datacenters
- Movidius para inferencia edge (dispositivos)

**AMD (Instinct MI300):**
- Competidores de las A100/H100 de NVIDIA
- Ecosistema ROCm creciendo pero aún menor que CUDA

Para la mayoría de usuarios, una GPU NVIDIA RTX de gama media-alta es suficiente para experimentar con modelos de IA (Stable Diffusion, LLMs locales, etc.).

### 8.2 Tarjetas aceleradoras de vídeo

**QuickSync (Intel integrado):**
Procesadores Intel con gráficos integrados incluyen QuickSync, un encoder/decoder de vídeo por hardware muy eficiente. Útil para servidores de medios (Plex, Jellyfin) que transcodifican muchos streams simultáneos.

**NVIDIA NVENC/NVDEC:**
Encoders/decoders por hardware en GPUs NVIDIA. Excelentes para streaming (NVENC produce calidad similar a x264 medium con mínimo uso de CPU) y edición de vídeo.

**Tarjetas dedicadas de transcodificación:**
En entornos donde se necesita transcodificar muchos streams pero no renderizar gráficos (servidores de medios grandes), existen tarjetas PCIe dedicadas o se usan GPUs Quadro/Tesla sin salidas de vídeo exclusivamente para trancodificación.

### 8.3 Tarjetas de adquisición de datos (DAQ)

Para aplicaciones científicas, industriales o de laboratorio:
- Adquisición de señales analógicas (termopares, sensores, etc.)
- Generación de señales (control de instrumentos)
- I/O digital de alta velocidad

Marcas: National Instruments, Measurement Computing, Advantech

Uso: Laboratorios, automatización industrial, investigación científica

### 8.4 Tarjetas FPGAs

**FPGA (Field-Programmable Gate Array):**
Chips programables que pueden configurarse para realizar funciones específicas a nivel de hardware.

Usos:
- Prototipado de ASICs
- Procesamiento de señales de alta velocidad
- Criptominería especializada (Monero, antes de que cambiara el algoritmo)
- Aceleración de algoritmos específicos (trading de alta frecuencia, compresión)
- Investigación y desarrollo

Ejemplos: Xilinx, Intel (Altera), Lattice

Muy especializadas, requieren conocimientos de HDL (Hardware Description Language) como VHDL o Verilog.

### 8.5 Tarjetas de TV (prácticamente obsoletas)

Antes populares para ver y grabar TV en el PC, han sido mayormente sustituidas por:
- Streaming (Netflix, Prime Video, etc.)
- TDT con dispositivos dedicados o Smart TVs
- Dispositivos USB de TDT (más convenientes que tarjetas PCIe)

Aún existen modelos para aplicaciones específicas (HTPC - Home Theater PC, grabación multi-canal), pero es un mercado en declive.

---

## 9. COMPATIBILIDAD Y CONSIDERACIONES

### 9.1 Slots disponibles y distribución de lanes

Antes de comprar tarjetas de expansión, es crucial entender la configuración de slots de tu placa base:

**Distribución típica en placa ATX:**
- 1× PCIe x16 (generalmente x16 eléctrico, para GPU principal)
- 1× PCIe x16 (a menudo x4 eléctrico, compartido con slots M.2)
- 2-4× PCIe x1
- A veces: 1-2 slots PCI legacy (cada vez más raros)

**Importante:** El segundo slot x16 en muchas placas base solo tiene 4 lanes eléctricamente (x4), aunque físicamente sea x16. Esto es suficiente para la mayoría de tarjetas (captura, red, sonido) pero limitante para GPUs secundarias.

### 9.2 Conflictos de recursos

Instalar múltiples tarjetas puede causar conflictos:

**Compartición de lanes:**
Como mencionamos en la sección PCIe, los lanes son limitados. Consultar el manual de la placa para entender qué configuraciones son posibles. Ejemplos comunes:
- "Si el slot M.2_2 está ocupado, PCIe_3 se deshabilita"
- "El segundo slot PCIe x16 funciona en modo x16 si no hay GPU en el primero, x4 si hay GPU en el primero"

**IRQ (Interrupt Request):**
Aunque los sistemas modernos tienen muchos IRQs disponibles y gestionan bien el compartirlos, en sistemas muy cargados de dispositivos pueden surgir conflictos. Raramente es problema hoy en día.

**Espacio físico:**
- GPUs de 2-3 slots bloquean slots adyacentes
- Tarjetas con backplates voluminosos pueden interferir
- Cables y conectores pueden dificultar el acceso

### 9.3 Alimentación y presupuesto térmico

**Consumo eléctrico:**
Cada slot PCIe puede proporcionar hasta 75W. Dispositivos de alto consumo (GPUs) requieren alimentación adicional. Calcular el consumo total:
- GPU de alta gama: 200-450W
- GPU de gama media: 150-250W
- Tarjeta de captura: 15-30W
- Tarjeta de red 10Gbit: 6-10W
- Otras tarjetas: 3-15W generalmente

Asegurar que la fuente de alimentación tiene capacidad suficiente con margen (mínimo 20-30% de headroom).

**Calor:**
Múltiples dispositivos generando calor en un espacio cerrado pueden crear problemas:
- Asegurar flujo de aire adecuado
- Considerar espaciado entre tarjetas de alto consumo
- Monitorizar temperaturas (GPU, chipset PCH, VRM)

### 9.4 Compatibilidad de drivers

**Windows:**
Generalmente excelente soporte. La mayoría de dispositivos tienen drivers oficiales. Windows Update suele instalar drivers funcionales automáticamente.

**Linux:**
Variable según el hardware:
- Intel (NICs, WiFi, GPU integradas): Excelente, drivers en kernel
- NVIDIA (GPUs): Buenos drivers propietarios, pero requieren instalación manual
- AMD (GPUs): Drivers open-source en kernel, buenos pero algo detrás de Windows en rendimiento gaming
- Dispositivos exóticos: Puede requerir compilar drivers o no tener soporte

**macOS:**
Muy restrictivo. Solo hardware específico es compatible. Hackintosh requiere selección cuidadosa de componentes.

---

## 10. INSTALACIÓN Y MEJORES PRÁCTICAS

### 10.1 Procedimiento de instalación física

**Preparación:**
1. Apagar completamente el equipo y desconectar de la corriente
2. Tocar metal del chasis para descargar electricidad estática
3. Consultar manual de la placa base para identificar slots óptimos
4. Verificar que el/los slot(s) están libres de polvo

**Instalación:**
1. Remover la(s) chapas metálicas correspondientes en la parte trasera del chasis
2. Alinear la tarjeta con el slot, asegurando que los contactos dorados quedan alineados
3. Presionar firmemente pero con cuidado hasta que el pestillo de seguridad haga clic
4. Fijar la tarjeta al chasis con tornillo(s)
5. Conectar alimentación adicional si es necesario (GPUs, tarjetas especializadas)
6. Conectar cables externos (HDMI, DisplayPort, Ethernet, antenas WiFi, etc.)

**Precauciones:**
- No forzar nunca. Si no entra suavemente, está mal alineada
- Sostener la tarjeta por los bordes, evitar tocar componentes o contactos
- Asegurar que no hay cables o componentes en el camino
- Verificar que la tarjeta queda completamente asentada y nivelada

### 10.2 Instalación de drivers y software

**Orden recomendado:**
1. Instalar sistema operativo si es nuevo PC
2. Instalar chipset drivers de la placa base primero
3. Instalar drivers de tarjetas de expansión (priorizar GPU si hay)
4. Actualizar firmware si el fabricante lo recomienda
5. Instalar software de gestión (RGB, overclocking, monitorización)

**Fuentes de drivers:**
- **Preferible:** Sitio web oficial del fabricante (sección soporte/downloads)
- **Aceptable:** Windows Update (a menudo drivers genéricos funcionales pero no optimizados)
- **Evitar:** Sitios de descarga de drivers de terceros (pueden contener malware o drivers incorrectos/obsoletos)

### 10.3 Verificación post-instalación

**En Windows:**
- Administrador de dispositivos: Verificar que no hay signos de exclamación amarillos
- Herramientas de diagnóstico específicas (GPU-Z para GPUs, CrystalDiskInfo para controladoras de almacenamiento, etc.)
- Benchmarks básicos para confirmar rendimiento esperado

**En Linux:**
- `lspci -v` para listar dispositivos PCIe y verificar drivers cargados
- `dmesg` para revisar mensajes del kernel sobre la detección del dispositivo
- Herramientas específicas según el dispositivo

### 10.4 Cable management

Las tarjetas de expansión, especialmente GPUs grandes, pueden complicar el cable management:

**Consejos:**
- Routear cables de alimentación PCIe desde la PSU por detrás, emergiendo cerca de la GPU
- Usar bridas o velcro para agrupar cables
- Evitar que cables bloqueen el flujo de aire hacia/desde la GPU
- Considerar cables custom o extensions si la estética es importante
- Verificar que cables no están tensos ni forzando conectores

---

## 11. TROUBLESHOOTING Y PROBLEMAS COMUNES

### 11.1 La tarjeta no es detectada

**Posibles causas:**
- No está completamente insertada en el slot → Verificar que el pestillo hizo clic
- Slot defectuoso → Probar en otro slot
- Tarjeta defectuosa → Probar en otro ordenador si es posible
- Incompatibilidad física (tarjeta PCIe 4.0 en placa muy antigua que no soporta 4.0)
- BIOS desactualizada → Actualizar BIOS puede añadir soporte para hardware nuevo
- Alimentación insuficiente → Verificar que todos los conectores de alimentación están conectados
- Conflicto de recursos → Desactivar temporalmente otros dispositivos para aislar el problema

**Pasos de diagnóstico:**
1. Verificar en BIOS si el slot PCIe está habilitado
2. Verificar en BIOS si la tarjeta aparece listada
3. Comprobar con otra tarjeta conocida funcional en el mismo slot
4. Resetear BIOS a valores por defecto

### 11.2 Rendimiento inferior al esperado

**GPU no rinde como debería:**
- Verificar que está en el slot correcto (primer slot x16, no uno secundario x4/x8)
- Drivers desactualizados o incorrectos
- Throttling térmico (verificar temperaturas con GPU-Z o HWiNFO)
- CPU bottleneck (procesador no puede alimentar suficientes datos a la GPU)
- Resolución/settings demasiado altos
- Malware/procesos en background consumiendo recursos
- Conexión a monitor equivocado (monitor conectado a GPU integrada en lugar de discreta)

**Tarjeta de red no alcanza velocidad esperada:**
- Cable Ethernet de categoría insuficiente (Cat5 en lugar de Cat5e/Cat6)
- Router/switch no soporta la velocidad de la tarjeta
- Drivers desactualizados
- Configuración de velocidad/dúplex incorrecta (forzada a 100Mbps en lugar de negociación automática)

### 11.3 Problemas de estabilidad

**System crashes, pantallazos azules, reinicios:**
- Alimentación insuficiente → Upgrade de PSU
- Overclocking inestable → Volver a configuración stock
- Drivers conflictivos → Desinstalar con DDU (Display Driver Uninstaller) y reinstalar
- Sobrecalentamiento → Mejorar refrigeración, limpiar polvo
- Memoria defectuosa → Probar con MemTest86+
- Tarjeta defectuosa → RMA si está en garantía

**Artifacts visuales en GPU:**
- VRAM defectuosa → RMA
- Overclocking VRAM demasiado agresivo → Reducir OC
- Drivers corruptos → Reinstalación limpia
- Temperaturas excesivas de VRAM → Mejorar refrigeración (pads térmicos, undervolting)

### 11.4 Problemas de ruido

**Coil whine:**
Zumbido de alta frecuencia proveniente de inductores bajo carga:
- Normal en cierto grado, especialmente a framerates muy altos
- Limitar FPS puede reducirlo (V-Sync, FPS cap)
- PSU de calidad inferior puede agravarlo
- RMA si es excesivamente molesto (algunos fabricantes lo cubren, otros no)

**Ventiladores ruidosos:**
- Acumulación de polvo → Limpieza
- Rodamientos desgastados → Reemplazo de ventiladores (en GPUs customizables)
- Curva de ventiladores demasiado agresiva → Ajustar con MSI Afterburner u otra utilidad
- Configuración de placa base (algunos establecen ventiladores al 100% por defecto hasta detectar sensor)

### 11.5 Problemas de compatibilidad con múltiples GPUs

**SLI (NVIDIA) / CrossFire (AMD):**
Estas tecnologías que permitían usar múltiples GPUs para gaming están prácticamente muertas:
- NVIDIA ha discontinuado SLI en GPUs consumer (RTX 30/40-series no lo soportan)
- AMD mantiene mGPU limitadamente pero pocos juegos lo aprovechan
- Soporte de juegos es pésimo (mayoría no escalan bien o directamente no funcionan)
- Microstuttering (variación en frametime) es común

**Múltiples GPUs para computación:**
Funciona bien para:
- Renderizado 3D (Blender, V-Ray puede usar múltiples GPUs independientemente)
- Entrenamiento de IA (distribución de modelos o data parallelism)
- Minería de criptomonedas (cada GPU trabaja independientemente)
- Computación científica con CUDA/OpenCL

**Configuración:**
- Verificar que la placa base soporta múltiples GPUs (slots x16/x8 suficientes)
- Calcular distribución de lanes (típicamente x8/x8 para 2 GPUs)
- PSU con potencia suficiente y conectores PCIe necesarios
- Refrigeración crítica (GPUs muy juntas se calientan mutuamente)

---

## 12. OPTIMIZACIÓN Y AJUSTES

### 12.1 BIOS/UEFI settings para tarjetas de expansión

**PCIe configuration:**
- **PCIe speed:** Auto (recomendado) vs Force Gen3/Gen4
  - Forzar puede resolver incompatibilidades raras pero limita rendimiento
- **Above 4G Decoding:** Necesario para múltiples GPUs o resizable BAR
- **Resizable BAR / Smart Access Memory:** Permite a la CPU acceder a toda la VRAM de la GPU, mejorando rendimiento 0-15% según juego
  - Requiere CPU compatible, GPU compatible, BIOS actualizada
- **Link Speed:** Auto deja que negocie la velocidad óptima

**Bifurcation settings:**
- Si usas tarjetas adaptadoras M.2 quad en slots PCIe x16
- Dividir x16 en 4×x4 o 2×x8
- No todas las placas lo soportan

### 12.2 Overclocking de GPUs

Aunque técnicamente no es instalación de hardware, es una optimización común:

**Herramientas:**
- MSI Afterburner (universal, funciona con todas las marcas)
- EVGA Precision X1 (NVIDIA)
- AMD Radeon Software (integrado)

**Parámetros ajustables:**
- **Core Clock:** Frecuencia de la GPU (+50-150 MHz típico, varía por chip)
- **Memory Clock:** Frecuencia de VRAM (+500-1000 MHz en GDDR6/6X)
- **Power Limit:** % de TDP máximo que la GPU puede consumir (aumentar permite mayor boost)
- **Voltage:** Generalmente bloqueado en GPUs consumer modernas
- **Fan Curve:** Ajustar velocidad de ventiladores según temperatura

**Undervolting:**
Reducir voltaje manteniendo frecuencias puede reducir temperaturas y ruido sin perder rendimiento:
- Especialmente efectivo en Ampere (RTX 30) y RDNA2/3 (RX 6000/7000)
- Requiere prueba y error para encontrar el punto óptimo
- Puede mejorar longevidad al reducir estrés térmico

**Importante:** Overclocking anula garantía en algunos fabricantes. Nunca es necesario para operación normal.

### 12.3 Monitorización de rendimiento

**Software recomendado:**
- **HWiNFO64:** El más completo, monitoriza todo
- **GPU-Z:** Específico para GPUs, muestra especificaciones detalladas
- **MSI Afterburner + RivaTuner:** Overlay en juegos mostrando FPS, temperaturas, uso
- **CPU-Z:** Para CPU y RAM, también muestra info de PCIe slots

**Métricas importantes a vigilar:**
- Temperaturas (GPU, Hotspot, VRAM si está disponible)
- Utilización GPU (debería estar cerca del 100% en gaming para aprovechar al máximo)
- Utilización VRAM (si alcanza el máximo, necesitas más VRAM o reducir settings)
- Power consumption (W)
- Clock speeds (actual vs rated)

---

## 13. CASOS DE USO Y CONFIGURACIONES TÍPICAS

### 13.1 Gaming mainstream

**Configuración típica:**
- 1× GPU de gama media (RTX 4060 Ti, RX 7600 XT)
- Audio integrado de la placa base (suficiente)
- Ethernet Gigabit integrado
- Sin tarjetas adicionales necesarias

**Presupuesto:** 300-500€ en GPU, 0€ en otras tarjetas

**Resultado:** Capaz de jugar a 1080p-1440p en settings altos con framerates suaves.

### 13.2 Gaming enthusiast / Alta gama

**Configuración:**
- 1× GPU de gama alta (RTX 4080/4090, RX 7900 XTX)
- Tarjeta de red 2.5Gbit o 10Gbit si hay infraestructura que lo aproveche
- Opcionalmente: Tarjeta de sonido o DAC externo para audio de alta calidad
- Tarjeta de captura si hace streaming desde consolas

**Presupuesto:** 1000-2000€ en GPU, 100-400€ en tarjetas adicionales

**Resultado:** Gaming a 4K 60+ FPS o 1440p 144+ FPS con ray tracing, streaming, multitarea pesada.

### 13.3 Workstation de edición de vídeo

**Configuración:**
- 1× GPU profesional (NVIDIA RTX 4000/5000 Ada, o consumer de alta gama)
- Controladora SATA/SAS para múltiples HDDs de almacenamiento
- Tarjeta de red 10Gbit para transferencias rápidas a/desde NAS
- Tarjeta de captura profesional si ingesta vídeo desde cámaras

**Presupuesto:** 800-3000€ en GPU, 200-600€ en tarjetas adicionales

**Resultado:** Edición fluida de 4K/8K, renderizado acelerado, flujos de trabajo profesionales.

### 13.4 Servidor doméstico / NAS

**Configuración:**
- Sin GPU o GPU básica (iGPU suficiente, o GT 1030 para transcoding si necesario)
- Controladora SAS para 8-16 HDDs
- Tarjeta de red dual 10Gbit o quad Gigabit para redundancia y ancho de banda
- Opcionalmente: Tarjeta controladora RAID por hardware con BBU

**Presupuesto:** 100-150€ en controladora storage, 200-400€ en red, 0-500€ en RAID

**Resultado:** Sistema de almacenamiento centralizado de alto rendimiento y capacidad.

### 13.5 Estación de Machine Learning / Deep Learning

**Configuración:**
- 1-4× GPUs de alta gama (RTX 4090, A6000, H100)
- Sin tarjetas adicionales generalmente necesarias (los datos entrenan localmente)
- Red 10Gbit+ si trabaja con datasets en servidores remotos

**Presupuesto:** 2000-40000€ en GPUs según escala

**Resultado:** Capacidad para entrenar modelos grandes localmente, experimentación rápida.

### 13.6 HTPC (Home Theater PC)

**Configuración:**
- GPU básica con buena decodificación de vídeo (o iGPU con QuickSync)
- Tarjeta de sonido con salida digital (S/PDIF) para conectar a receiver AV
- Tarjeta de TV si aún se usa (raro)
- Opcionalmente: Tarjeta WiFi para conectividad inalámbrica

**Presupuesto:** 0-200€ (muchos usan solo componentes integrados)

**Resultado:** Centro de entretenimiento silencioso capaz de reproducir contenido 4K HDR.

---

## 14. MANTENIMIENTO Y CICLO DE VIDA

### 14.1 Mantenimiento preventivo

**Limpieza regular (cada 3-6 meses):**
- Apagar y desconectar el equipo
- Usar aire comprimido para remover polvo de ventiladores y heatsinks
- No soplar directamente sobre PCBs (humedad)
- Limpiar filtros de aire de la caja con agua (secar completamente antes de reinstalar)
- Verificar que ventiladores giran libremente

**Actualización de firmware y drivers:**
- Drivers de GPU: Cada 1-3 meses o cuando salen juegos importantes
- Firmware de tarjetas: Solo si el fabricante recomienda actualizar por bugs críticos o nuevas features
- BIOS de la placa base: Con precaución, solo si es necesario

**Monitorización térmica:**
- Verificar temperaturas periódicamente
- Si incrementan significativamente desde baseline, investigar (polvo, pasta térmica degradada, ventiladores fallando)

### 14.2 ¿Cuándo actualizar?

**GPU:**
La actualización más común. Considera upgrade cuando:
- No alcanzas framerates deseados en juegos actuales
- No tienes suficiente VRAM (stuttering, texturas de baja resolución forzadas)
- Nuevas tecnologías que quieres usar (ray tracing, DLSS/FSR, AV1 encoding)
- Tu GPU tiene 3-5 años (ciclo típico para gamers)

**Regla del doble de rendimiento:** No vale la pena actualizar si la nueva GPU no ofrece al menos el doble de rendimiento.

**Otras tarjetas:**
- Tarjeta de red: Cuando actualizas infraestructura (de Gigabit a 2.5/10 Gbit)
- Tarjeta de sonido: Cuando compras auriculares de alta impedancia o mejoras setup de audio
- Controladoras: Cuando necesitas más puertos o tecnologías más nuevas (SATA → SAS, USB 3.0 → USB 3.2/4)

### 14.3 Reventa y reciclaje

**Mercado de segunda mano:**
Las GPUs retienen valor razonablemente bien, especialmente modelos de gama alta. Una RTX 3080 de 2020 aún puede venderse por 50-60% de su precio original en 2025.

**Dónde vender:**
- eBay, Wallapop, Vibbo (locales)
- r/hardwareswap en Reddit
- Foros especializados (Forobeta, Overclocking.net)

**Preparación para venta:**
- Limpiar completamente
- Probar que funciona correctamente (benchmarks, stress tests)
- Incluir accesorios originales si es posible (caja, manuales, cables)
- Ser honesto sobre condiciones (overclocking, reparaciones, defectos)

**Reciclaje responsable:**
Hardware que no se puede vender o está roto debe reciclarse apropiadamente:
- Puntos limpios municipales
- Programas de reciclaje de fabricantes (Dell, HP tienen programas de devolución)
- Tiendas de electrónica a menudo aceptan hardware antiguo
- **Nunca tirar a basura normal:** Contienen materiales peligrosos (plomo, mercurio) y valiosos (oro, cobre, metales raros)

---

## 15. TENDENCIAS FUTURAS

### 15.1 PCIe 6.0 y 7.0: Ancho de banda infinito

PCIe 6.0 (2024-2025) y 7.0 (2025+) ofrecerán anchos de banda estratosféricos: 128 GB/s y 256 GB/s respectivamente en x16. Esto es mucho más de lo que cualquier GPU actual puede aprovechar. Las aplicaciones que se beneficiarán:

- SSDs: PCIe 6.0 x4 permitirá velocidades de 24+ GB/s
- Aceleradores de IA comunicándose con memoria del sistema a velocidades extremas
- GPUs con memoria unificada o compartiendo datasets masivos con CPU
- Almacenamiento en red sobre PCIe (NVMe-oF)

### 15.2 CXL (Compute Express Link)

CXL es un estándar que permite coherencia de caché entre CPU, GPUs, y otros aceleradores. Usa PHY (capa física) de PCIe pero añade protocolos adicionales para compartir memoria eficientemente.

**Beneficios:**
- GPUs pueden acceder directamente a RAM del sistema sin copiar datos
- Múltiples aceleradores pueden colaborar en mismo dataset
- Simplifica programación de sistemas heterogéneos

**Versiones:**
- CXL 1.0/1.1: Sobre PCIe 5.0
- CXL 2.0: Switching, pooling de memoria
- CXL 3.0: Sobre PCIe 6.0, latencias ultra-bajas

Principalmente relevante en datacenters y HPC inicialmente, pero eventualmente llegará a workstations.

### 15.3 Integración creciente vs especialización

Dos tendencias opuestas están ocurriendo simultáneamente:

**Mayor integración:**
- Placas base con WiFi 6E/7, Bluetooth, 2.5GbE, audio de alta calidad, múltiples M.2
- SoCs (System-on-Chip) como Apple M-series integrando CPU, GPU, Neural Engine, controladores I/O
- Menos necesidad de tarjetas de expansión para funcionalidad básica

**Mayor especialización:**
- GPUs más potentes y especializadas (gaming vs AI vs rendering)
- Aceleradores de IA dedicados
- FPGAs y ASICs para cargas de trabajo específicas
- Hardware de red ultra-rápido (25/100 GbE)

El resultado: El usuario promedio necesita menos tarjetas de expansión que nunca, pero usuarios especializados (profesionales, entusiastas) las necesitan más potentes y especializadas.

### 15.4 Refrigeración y densidad de potencia

Las GPUs modernas consumen 300-600W en espacios cada vez más compactos. Futuras generaciones seguirán esta tendencia:

**Desafíos:**
- Disipación de calor de 600-800W en una tarjeta
- Ruido de ventiladores a altas velocidades
- Complejidad y coste de refrigeración líquida

**Soluciones emergentes:**
- Refrigeración líquida como estándar en gamas altas
- Vapor chambers más grandes y eficientes
- Materiales de interfaz térmica avanzados (metal líquido de fábrica)
- Diseños multi-chip con heat spreaders mejorados
- Undervolting de fábrica más agresivo

### 15.5 Modularidad y reparabilidad

La tendencia actual es hacia dispositivos menos reparables (GPUs con componentes soldados, firmware bloqueado), pero hay contracorrientes:

**Right to repair:**
Movimientos legislativos en EU y algunos estados de USA están empujando por mayor reparabilidad. Esto podría significar:
- Disponibilidad de repuestos y esquemas de circuitos
- Firmware menos restrictivo
- Diseños más modulares

**Framework y similares:**
Algunas compañías están experimentando con PCs y laptops completamente modulares donde casi todo es reemplazable y actualizable, incluyendo tarjetas de expansión propietarias modulares.

---

## 16. SEGURIDAD Y CONSIDERACIONES ESPECIALES

### 16.1 Ataques basados en hardware

**DMA (Direct Memory Access) attacks:**
Dispositivos PCIe tienen acceso directo a la memoria del sistema. Un dispositivo malicioso (o firmware comprometido) podría:
- Leer contraseñas y datos sensibles de RAM
- Modificar código del sistema operativo
- Bypassear seguridad del SO

**Mitigaciones:**
- IOMMU (Intel VT-d, AMD-Vi): Virtualización de memoria para dispositivos I/O
- Kernel DMA Protection en Windows 10/11 (requiere soporte de placa base)
- Thunderbolt Security Levels
- No instalar hardware de fuentes no confiables

### 16.2 Firmware de tarjetas

Las tarjetas modernas tienen firmware actualizable:

**Beneficios:**
- Corrección de bugs
- Nuevas funcionalidades
- Mejoras de compatibilidad

**Riesgos:**
- Firmware malicioso podría instalar rootkits persistentes
- Actualizaciones fallidas pueden "brickear" la tarjeta
- Firmware modificado (BIOS mods en GPUs para minería) puede causar inestabilidad

**Mejores prácticas:**
- Solo actualizar firmware de fuentes oficiales
- Leer notas de la versión para entender qué cambios incluye
- No actualizar si no hay problemas o features específicas necesarias
- Backup del firmware original cuando sea posible
- UPS para evitar cortes de luz durante actualización

### 16.3 Criptominería y GPUs de segunda mano

El mercado de GPUs usadas está inundado de tarjetas que se usaron para minería 24/7. Consideraciones:

**Desgaste:**
- Minería es carga constante al 100%, similar a gaming intensivo pero continuo
- Si la refrigeración era adecuada y la tarjeta no se overclockó agresivamente, puede estar en buen estado
- Los ventiladores son el componente más desgastado (reemplazables)
- Silicon degradation es mínimo si temperaturas fueron controladas

**BIOS modificadas:**
- Algunas GPUs de minería tienen BIOS modificadas para optimizar hashrate
- Pueden causar inestabilidad en gaming
- Flashear BIOS original suele solucionar (arriesgado, puede brickear)

**Verificación:**
- Probar exhaustivamente con benchmarks y stress tests
- Verificar temperaturas (repasting puede ser necesario)
- Confirmar que todas las salidas de vídeo funcionan (algunas de minería las tenían deshabilitadas)

---

## RESUMEN DE CONCEPTOS CLAVE

1. **PCIe es el estándar actual y futuro** - Arquitectura superior a buses antiguos con lanes dedicados y comunicación full-duplex

2. **Las generaciones PCIe son retrocompatibles** - Pero funcionan a la velocidad del componente más lento

3. **Los lanes PCIe son limitados** - Distribuidos entre GPU, SSDs M.2, y slots de expansión. Consultar manual de placa base.

4. **Las GPUs son las tarjetas más importantes** - Ordenadores completos dentro del ordenador, críticas para gaming, rendering, IA

5. **Alimentación es crítica** - GPUs de alta gama necesitan 300-600W. Asegurar PSU adecuada.

6. **Audio integrado es suficiente para mayoría** - Tarjetas de sonido solo para casos específicos (alta impedancia, producción profesional)

7. **Networking está evolucionando rápido** - 2.5GbE es el nuevo estándar emergente para hogar, 10GbE para profesional

8. **Compatibilidad física y lógica importan** - Verificar slots, lanes, drivers, BIOS antes de comprar

9. **Mantenimiento preventivo prolonga vida** - Limpieza regular, monitorización térmica, actualización de drivers

10. **No todas las tarjetas son necesarias** - Evaluar si la funcionalidad integrada es suficiente antes de comprar expansión

---

## EJERCICIOS PROPUESTOS

1. **Análisis de distribución de lanes:** Dada una placa base con 20 lanes PCIe de la CPU (16 GPU + 4 chipset) y un chipset con 16 lanes adicionales, diseña la configuración óptima para: 1 GPU, 2 SSDs M.2, 1 tarjeta de red 10GbE, 1 tarjeta de captura.

2. **Cálculo de ancho de banda:** Una GPU en PCIe 4.0 x8 vs la misma GPU en PCIe 3.0 x16. ¿Cuál tiene más ancho de banda? Calcula la diferencia en GB/s.

3. **Dimensionamiento de PSU:** Sistema con: CPU 125W, GPU 350W, Placa base + RAM + Storage 80W, Tarjeta de captura 25W, Tarjeta de red 10W. ¿Qué potencia mínima de PSU recomiendas con margen de seguridad?

4. **Diagnóstico de problema:** Una GPU nueva no es detectada. La GPU anterior funcionaba en el mismo slot. LED de alimentación PCIe en GPU encendido. BIOS actualizada. ¿Pasos de troubleshooting?

5. **Investigación de compatibilidad:** Para un proyecto de NAS con 12 HDDs, investiga 3 controladoras SATA/SAS diferentes (nuevas o usadas) y compara: número de puertos, tipo de interfaz, precio, soporte Linux.

6. **Planificación de upgrade:** Tienes un sistema con RTX 3060 Ti. ¿Qué GPU upgrade considerarías basándote en la regla del doble de rendimiento? Consulta benchmarks reales.

7. **Diseño de sistema de streaming:** Especifica todas las tarjetas de expansión necesarias para un PC dedicado a streaming de gaming desde consolas en 4K60, con edición básica.

8. **Optimización térmica:** Una GPU alcanza 85°C bajo carga en una caja con 2 ventiladores frontales y 1 trasero. Propón mejoras sin cambiar la GPU o caja.

9. **Comparativa de tecnologías:** Compara WiFi 6E (PCIe) vs Ethernet 2.5GbE para gaming: latencia, estabilidad, throughput, coste, interferencias.

10. **Proyecto de integración:** Diseña la configuración completa de tarjetas de expansión para una workstation de edición de vídeo 8K con presupuesto de 3000€ (solo tarjetas de expansión, no CPU/RAM/placa/caja/PSU).