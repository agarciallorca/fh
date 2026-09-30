# UNIDADES DE ALMACENAMIENTO

## 1. INTRODUCCIÓN AL ALMACENAMIENTO

### 1.1 ¿Qué es el almacenamiento?

El almacenamiento es la capacidad de guardar datos de forma **persistente** (no volátil), es decir, que se mantienen aunque se apague el equipo, a diferencia de la RAM.

### 1.2 Clasificación general

**Por volatilidad:**
- **Volátil:** Pierde datos sin alimentación (RAM)
- **No volátil:** Mantiene datos sin alimentación (HDD, SSD, USB)

**Por acceso:**
- **Primario:** Directamente accesible por CPU (RAM)
- **Secundario:** Almacenamiento masivo (HDD, SSD)
- **Terciario:** Backup y archivo (cintas, discos ópticos)

**Por tecnología:**
- **Magnético:** HDD, cintas
- **Óptico:** CD, DVD, Blu-ray
- **Estado sólido:** SSD, memoria flash

---

## 2. DISCOS DUROS MECÁNICOS (HDD)

### 2.1 Funcionamiento

Los **HDD (Hard Disk Drive)** utilizan **tecnología magnética** para almacenar datos en **platos giratorios** recubiertos de material magnético.

**Componentes principales:**

**Platos (platters):**
- Discos de aluminio o vidrio recubiertos de material magnético
- Giran constantemente a velocidad fija
- Varios platos apilados en el eje

**Cabezales de lectura/escritura:**
- Uno por cada superficie de plato
- Flotan sobre el plato sin tocarlo (distancia microscópica)
- Campo magnético para escribir, detectan magnetismo para leer

**Brazo actuador:**
- Mueve los cabezales radialmente
- Acceso a diferentes pistas

**Motor del eje (spindle motor):**
- Hace girar los platos
- Velocidades típicas: 5400, 7200, 10000, 15000 RPM

**Controlador:**
- Chip que gestiona operaciones
- Interfaz con el sistema
- Caché incorporada

### 2.2 Organización de datos

**Pista (track):** Círculo concéntrico en la superficie del plato

**Sector:** Subdivisión de una pista (tradicionalmente 512 bytes, ahora 4 KB)

**Cilindro:** Conjunto de pistas en la misma posición de todos los platos

**Clúster:** Unidad mínima de asignación del sistema de archivos (múltiples sectores)

### 2.3 Especificaciones técnicas

**Capacidad:**
- Actual: 500 GB - 22 TB (consumo)
- Servidores/empresas: hasta 24 TB+
- Medida en bytes (1 TB = 1000 GB en marketing, 1024 GiB real)

**Velocidad de rotación (RPM):**
- **5400 RPM:** Bajo consumo, portátiles, almacenamiento masivo
- **7200 RPM:** Estándar para desktop
- **10000 RPM:** Alto rendimiento (raro actualmente)
- **15000 RPM:** Enterprise (casi obsoleto, sustituido por SSD)

Mayor RPM = Menor latencia + Mayor velocidad de transferencia

**Velocidad de transferencia:**
- **Sostenida:** 80-160 MB/s (5400 RPM), 120-200 MB/s (7200 RPM)
- **Pico (burst):** Desde la caché, mucho mayor pero breve
- Depende de: RPM, densidad de datos, posición en el plato

**Tiempo de acceso:**
- **Seek time (tiempo de búsqueda):** 8-15 ms
- **Latencia rotacional:** Depende de RPM
  - 7200 RPM → 4.16 ms promedio
  - 5400 RPM → 5.55 ms promedio
- **Total:** 10-20 ms (muy superior a SSD)

**Caché/Buffer:**
- 8 MB (básico), 64-256 MB (actual), hasta 512 MB (high-end)
- Acelera operaciones frecuentes
- Importante para multitarea

**Formato:**
- **3.5":** Desktop, servidores (mayor capacidad)
- **2.5":** Portátiles, externos (menor consumo)

### 2.4 Interfaces de conexión

**SATA (Serial ATA):**
- **SATA I:** 1.5 Gb/s (150 MB/s)
- **SATA II:** 3 Gb/s (300 MB/s)
- **SATA III:** 6 Gb/s (600 MB/s) - **Actual estándar**
- Retrocompatibles entre sí

**SAS (Serial Attached SCSI):**
- Entorno empresarial/servidor
- Mayor fiabilidad y rendimiento
- SAS-2: 6 Gb/s, SAS-3: 12 Gb/s, SAS-4: 22.5 Gb/s
- Compatibilidad: Controladoras SAS pueden usar discos SATA, NO al revés

**IDE/PATA (Parallel ATA):**
- Obsoleto
- Cable ancho de 40/80 pines
- Máximo 133 MB/s

### 2.5 Ventajas e inconvenientes

**Ventajas:**\
✓ **Precio por GB muy bajo** (5-10 veces más barato que SSD)\
✓ Gran capacidad disponible (hasta 24 TB)\
✓ Larga vida útil para almacenamiento de archivos\
✓ Tecnología madura y confiable\
✓ Mejor para escrituras constantes (vs SSD con escrituras limitadas)

**Inconvenientes:**\
✗ **Muy lento comparado con SSD** (100-150× más lento en acceso aleatorio)\
✗ Sensible a golpes y vibraciones (partes móviles)\
✗ Ruido audible\
✗ Mayor consumo energético\
✗ Genera calor\
✗ Tiempo de arranque del sistema lento\
✗ Latencia alta (ms vs μs del SSD)

### 2.6 Casos de uso recomendados

✓ Almacenamiento masivo de archivos (fotos, vídeos, documentos)\
✓ Backups y copias de seguridad\
✓ Servidores de archivos (NAS)\
✓ Almacenamiento secundario (complemento a SSD)\
✓ Presupuestos ajustados con necesidad de mucha capacidad

---

## 3. UNIDADES DE ESTADO SÓLIDO (SSD)

### 3.1 Funcionamiento

Los **SSD (Solid State Drive)** utilizan **memoria flash NAND** para almacenar datos de forma electrónica, **sin partes móviles**.

**Componentes principales:**

**Chips de memoria NAND:**
- Múltiples chips en la PCB
- Almacenan los datos en celdas de memoria

**Controlador:**
- Cerebro del SSD
- Gestiona lectura/escritura
- Algoritmos de corrección de errores (ECC)
- Wear leveling (distribución del desgaste)
- Garbage collection
- TRIM support

**Caché DRAM (opcional):**
- SSD de gama alta incluyen RAM dedicada
- Acelera operaciones
- Mejora rendimiento en escrituras aleatorias
- SSD DRAM-less: Usan parte de memoria NAND o RAM del sistema

**Firmware:**
- Software embebido en el controlador
- Optimizaciones y gestión

### 3.2 Tipos de memoria NAND

Las celdas NAND almacenan bits mediante niveles de carga eléctrica:

**SLC (Single-Level Cell):**
- **1 bit por celda**
- Más rápido y duradero
- Muy caro
- Ciclos de escritura: 50,000-100,000
- Uso: Enterprise, industrial

**MLC (Multi-Level Cell):**
- **2 bits por celda**
- Balance rendimiento/precio/durabilidad
- Ciclos: 3,000-10,000
- Menos común hoy (sustituido por TLC)

**TLC (Triple-Level Cell):**
- **3 bits por celda**
- Estándar actual para consumo
- Buen balance precio/rendimiento
- Ciclos: 1,000-3,000
- Uso: SSD de consumo, gaming

**QLC (Quad-Level Cell):**
- **4 bits por celda**
- Más barato, mayor capacidad
- Menor durabilidad y rendimiento
- Ciclos: 100-1,000
- Uso: Almacenamiento masivo, presupuesto ajustado

**PLC (Penta-Level Cell):**
- **5 bits por celda**
- Emergente, aún en desarrollo
- Muy alta densidad pero menor fiabilidad

**Comparación:**

| Tipo | Bits/celda | Velocidad | Durabilidad | Precio | Uso |
|------|------------|-----------|-------------|--------|-----|
| SLC | 1 | ★★★★★ | ★★★★★ | ★★★★★ | Enterprise |
| MLC | 2 | ★★★★☆ | ★★★★☆ | ★★★★☆ | Pro/Legacy |
| TLC | 3 | ★★★☆☆ | ★★★☆☆ | ★★★☆☆ | Consumo |
| QLC | 4 | ★★☆☆☆ | ★★☆☆☆ | ★★☆☆☆ | Masivo |

**Importante:** Más bits por celda = Más capacidad y menor precio, pero también menor velocidad y durabilidad

### 3.3 Interfaces y formatos

**Interfaces:**

**SATA III (6 Gb/s):**
- Límite teórico: 600 MB/s
- Real: ~550 MB/s lectura/escritura
- Compatible con HDDs
- Más económico
- Suficiente para muchos usos

**NVMe (Non-Volatile Memory Express):**
- Protocolo diseñado específicamente para SSD
- Usa líneas PCIe directamente
- Muchísimo más rápido que SATA
- Menor latencia
- Paralelismo masivo

**PCIe (Peripheral Component Interconnect Express):**
- Diferentes generaciones y anchos de banda:
  - **PCIe 3.0 x4:** ~3,500 MB/s
  - **PCIe 4.0 x4:** ~7,000 MB/s
  - **PCIe 5.0 x4:** ~14,000 MB/s (actual)
  - **PCIe 6.0 x4:** ~28,000 MB/s (futuro cercano)

**Formatos físicos:**

**2.5" SATA:**
- Factor de forma de HDD 2.5"
- Interfaz SATA
- Compatible con cualquier equipo con SATA
- Velocidad limitada a ~550 MB/s

**M.2:**
- Formato compacto tipo tarjeta
- Tamaños: 2230, 2242, 2260, **2280** (más común), 22110
- Puede usar interfaz SATA o NVMe (verificar compatibilidad)
- Directamente en placa base
- Sin cables

**M.2 SATA:**
- Factor M.2 pero protocolo SATA
- Limitado a ~550 MB/s
- Key B+M (muesca en ambos lados)

**M.2 NVMe:**
- Factor M.2 con protocolo NVMe
- PCIe 3.0/4.0/5.0
- Key M (una muesca)
- Hasta 14,000 MB/s (PCIe 5.0)

**PCIe Add-in Card (AIC):**
- Tarjeta PCIe estándar
- SSD integrado o adaptador para M.2
- Uso enterprise o entusiastas
- Máximo rendimiento

**U.2 / U.3:**
- Enterprise
- Similar a 2.5" pero protocolo NVMe
- Hot-swappable en servidores

### 3.4 Especificaciones técnicas

**Capacidad:**
- Consumo: 128 GB - 8 TB
- Enterprise: hasta 30 TB+
- Precio por GB disminuye con capacidad

**Velocidad de lectura secuencial:**
- SATA: ~550 MB/s
- NVMe PCIe 3.0: 2,000-3,500 MB/s
- NVMe PCIe 4.0: 5,000-7,400 MB/s
- NVMe PCIe 5.0: 10,000-14,000 MB/s

**Velocidad de escritura secuencial:**
- Similar a lectura en gama alta
- Puede ser menor en modelos económicos
- SATA: ~500-520 MB/s

**IOPS (Input/Output Operations Per Second):**
- Medida de operaciones aleatorias (más importante que velocidad secuencial para SO)
- Lectura aleatoria 4K: 100,000-1,000,000+ IOPS
- Escritura aleatoria 4K: 80,000-1,000,000+ IOPS
- HDD: ~100-200 IOPS (¡diferencia abismal!)

**Latencia:**
- 10-100 microsegundos (μs)
- HDD: 10-20 milisegundos (ms)
- **SSD es 100-1000× más rápido**

**TBW (Total Bytes Written):**
- Cantidad total de datos que se pueden escribir durante la vida útil
- 150-600 TBW (consumo 500GB)
- 300-1200 TBW (consumo 1TB)
- En la práctica: Duran muchos años de uso normal

**DWPD (Drive Writes Per Day):**
- Cuántas veces se puede escribir la capacidad completa del disco diariamente durante la garantía
- Consumo: 0.3-1 DWPD (5 años)
- Enterprise: 1-10+ DWPD

### 3.5 Ventajas e inconvenientes

**Ventajas:**\
✓ **Velocidad extremadamente superior** a HDD\
✓ Latencia mínima (μs vs ms)\
✓ Sin partes móviles → Resistente a golpes\
✓ Silencioso (sin ruido mecánico)\
✓ Menor consumo energético\
✓ Menor generación de calor\
✓ Factor de forma compacto (M.2)\
✓ IOPS altísimos (operaciones aleatorias)\
✓ Arranque de sistema casi instantáneo

**Inconvenientes:**\
✗ **Precio por GB mayor** que HDD (5-10×)\
✗ Capacidades menores (limitado por precio)\
✗ Escrituras limitadas (TBW)\
✗ Recuperación de datos más difícil en caso de fallo\
✗ Degradación de rendimiento al llenarse\
✗ Requiere refrigeración en modelos de alto rendimiento (M.2 NVMe)

### 3.7 Casos de uso recomendados

✓ **Sistema operativo (imprescindible)**\
✓ Aplicaciones y programas\
✓ Gaming (tiempos de carga)\
✓ Edición de vídeo/foto (archivos de trabajo)\
✓ Bases de datos\
✓ Máquinas virtuales\
✓ Cualquier uso que requiera velocidad

**Configuración ideal:** SSD para SO + programas, HDD para almacenamiento masivo

---

## 4. COMPARATIVA HDD vs SSD

| Característica | HDD | SSD SATA | SSD NVMe |
|----------------|-----|----------|----------|
| **Velocidad secuencial** | 80-200 MB/s | ~550 MB/s | 2,000-14,000 MB/s |
| **IOPS (4K random)** | 100-200 | 50,000-100,000 | 200,000-1,000,000+ |
| **Latencia** | 10-20 ms | 0.1 ms | 0.01-0.1 ms |
| **Precio por GB** | €0.015-0.025/GB | €0.08-0.12/GB | €0.10-0.20/GB |
| **Capacidad máxima** | 24 TB | 4 TB | 8 TB |
| **Durabilidad física** | Frágil (golpes) | Resistente | Resistente |
| **Ruido** | Audible | Silencioso | Silencioso |
| **Consumo** | 6-10W | 2-4W | 3-8W |
| **Vida útil escrituras** | Ilimitado práct. | Limitado (TBW) | Limitado (TBW) |
| **Recuperación datos** | Más fácil | Difícil | Difícil |

---

## 5. RENDIMIENTO Y BENCHMARKING

### 5.1 Métricas importantes

**Velocidad secuencial:**
- Lectura/escritura de archivos grandes contiguos
- Importante para: Vídeo 4K, transferencia de archivos grandes
- Medida: MB/s o GB/s

**Velocidad aleatoria (4K):**
- Lectura/escritura de archivos pequeños en ubicaciones aleatorias
- **Más importante para uso real del SO**
- Medida: IOPS (operaciones por segundo)
- Windows hace ~90% operaciones 4K

**Latencia:**
- Tiempo de respuesta de una operación
- Crítico para sensación de "rapidez"
- HDD: ms, SSD: μs

**Queue Depth (QD):**
- Número de operaciones simultáneas
- QD1: Una operación a la vez (uso típico)
- QD32: 32 operaciones simultáneas (servidores, benchmarks)
- Rendimiento real del usuario ≈ QD1-QD4

### 5.2 Herramientas de benchmark

**CrystalDiskMark:**
- Windows
- Pruebas secuenciales y aleatorias
- Diferentes tamaños de bloque y QD
- Más usado y popular

**AS SSD Benchmark:**
- Windows
- Similar a CrystalDiskMark
- Incluye compression benchmark

**ATTO Disk Benchmark:**
- Windows/macOS
- Diferentes tamaños de transferencia
- Usado por fabricantes

**Blackmagic Disk Speed Test:**
- macOS
- Enfocado en vídeo
- Simple y visual

**fio (Flexible I/O Tester):**
- Linux/Windows/macOS
- Línea de comandos
- Muy configurable
- Profesional

**hdparm:**
- Linux
- Información y tests básicos
- Línea de comandos

### 5.3 Interpretando benchmarks

**Importante:**
- Benchmarks sintéticos ≠ Rendimiento real
- Operaciones 4K QD1 más relevantes que secuencial QD32
- SSD de 3000 MB/s vs 7000 MB/s: Diferencia real mínima en uso diario
- IOPS 4K más importante que velocidad secuencial para SO

**Factores que afectan rendimiento real:**
- Nivel de llenado del SSD (>80% = más lento)
- Temperatura (throttling térmico)
- Tamaño del caché SLC
- Firmware del SSD
- Trimming y garbage collection

---

## 6. TEMPERATURA Y REFRIGERACIÓN DE ALMACENAMIENTO

### 6.1 Temperaturas de operación

**HDD:**
- Operación normal: 30-45°C
- Máxima: 60°C
- Crítica: >65°C
- Importante: Temperatura constante (evitar cambios bruscos)

**SSD SATA:**
- Operación normal: 30-50°C
- Máxima: 70°C
- Throttling: >75°C
- Menos crítico que HDD

**SSD NVMe:**
- Operación normal: 40-70°C
- Máxima: 80-85°C
- Throttling: >80°C (depende del modelo)
- **Más crítico:** PCIe 4.0/5.0 pueden superar 80°C fácilmente

### 6.2 Refrigeración de almacenamiento

**HDD:**
- Flujo de aire general suficiente
- Evitar cajas sin ventilación
- En NAS: Ventiladores dedicados

**SSD 2.5" SATA:**
- No suele necesitar refrigeración adicional
- Disipadores opcionales (estética)

**SSD M.2 NVMe:**
- **PCIe 3.0:** Disipador placa base suficiente
- **PCIe 4.0:** Disipador recomendado
- **PCIe 5.0:** Disipador + ventilación activa necesarios

**Soluciones de refrigeración M.2:**
- Disipador pasivo (incluido en placa base)
- Disipador aftermarket de aluminio/cobre
- Disipadores con heatpipes
- Ventiladores dedicados (raro)
- Backplate térmico (parte trasera)

**Importante:** Algunos SSD NVMe incluyen etiqueta térmica. NO quitarla si no se añade disipador.

---

## 7. FIABILIDAD Y VIDA ÚTIL

### 7.1 Modos de fallo

**HDD:**
- Fallo mecánico (motor, actuador, cabezales)
- Bad sectors (sectores defectuosos)
- Fallo electrónico (controladora)
- "Click of death" (cabezales golpeando)

**SSD:**
- Desgaste de celdas (TBW agotado)
- Fallo de controladora
- Corrupción de firmware
- Pérdida de datos por tiempo sin alimentación (años)

### 7.2 Prolongar vida útil

**Para HDD:**\
✓ Mantener temperatura estable 30-40°C\
✓ Evitar vibraciones y golpes\
✓ No mover mientras está en uso\
✓ Ventilación adecuada en NAS

**Para SSD:**\
✓ No llenar más del 80%\
✓ Mantener TRIM habilitado\
✓ Actualizar firmware\
✓ Evitar temperaturas >75°C\
✓ No escribir constantemente (logs, torrents)

---

## RESUMEN DE CONCEPTOS CLAVE

1. **HDD usa tecnología magnética con partes móviles** - Lento pero económico y alta capacidad
2. **SSD usa memoria flash sin partes móviles** - Rápido, duradero físicamente, más caro
3. **Diferencia abismal de rendimiento** - SSD 100-1000× más rápido en acceso aleatorio
4. **Más bits por celda = Más capacidad pero menos durabilidad** - SLC>MLC>TLC>QLC
5. **NVMe supera ampliamente a SATA** - Pero diferencia real menor de lo que indican benchmarks
10. **SSD necesita espacio libre y TRIM** - Mantener <80% lleno para rendimiento óptimo

---

## EJERCICIOS PROPUESTOS

1. Compara el coste por GB de un HDD de 4 TB vs un SSD de 1 TB.

2. Diseña una configuración de almacenamiento para un equipo gaming con presupuesto de 250€.

3. Explica por qué un SSD NVMe PCIe 4.0 de 7000 MB/s no se nota más rápido que uno SATA de 550 MB/s para uso ofimático.

4. Calcula cuántos años durará un SSD de 500 GB con 300 TBW si escribes 20 GB diarios.
