# Hardware específico de Centros de Proceso de Datos (CPD)

## 1. Hardware personal vs. empresarial

### 1.1 El hardware personal

El hardware personal está diseñado para un único usuario y un uso cotidiano: navegación web, ofimática, multimedia o gaming. Sus características principales son:

- **Coste reducido:** componentes de gama de consumo.
- **Facilidad de uso:** interfaces sencillas, configuración mínima.
- **Rendimiento suficiente** para tareas de un solo usuario.
- **Escalabilidad limitada:** pocas ranuras de expansión, RAM máxima reducida.
- **Tolerancia a fallos casi nula:** un fallo implica parada total.

### 1.2 El hardware empresarial

El hardware empresarial está concebido para dar servicio a múltiples usuarios de forma continua y fiable. Sus características principales son:

- **Alta disponibilidad:** diseñado para funcionar 24×7×365.
- **Redundancia:** fuentes de alimentación duales, discos RAID, NICs en *teaming*.
- **Escalabilidad:** capacidad de añadir CPUs, RAM, almacenamiento sin parar el sistema.
- **Gestión remota:** tarjetas IPMI / iDRAC / iLO para administrar sin presencia física.
- **Soporte extendido:** garantías de 3 a 5 años con sustitución en pocas horas (NBD, 4h, etc.).
- **Coste elevado:** justificado por la criticidad de los servicios que aloja.

### 1.3 Tabla comparativa

| Característica | Personal | Empresarial |
|---|---|---|
| Disponibilidad | La mejor posible | 99,99 % o superior |
| Redundancia | No | Fuentes, discos, NICs, CPU |
| Gestión remota | No | IPMI / iDRAC / iLO |
| Factor de forma | Desktop / laptop | Rack / Blade / Tower server |
| Ciclo de vida | 3-4 años | 5-7 años |
| Memoria ECC | No | Sí (detecta y corrige errores) |
| Soporte | Garantía básica | Contrato con proveedor |
| Precio medio | 500 – 2.000 € | 3.000 – 100.000 € |

### 1.4 Memoria ECC (*Error Correcting Code*)

La RAM ECC es una de las diferencias más importantes. Utiliza bits adicionales para detectar y corregir errores de un solo bit de forma transparente. En un servidor que procesa millones de operaciones por segundo, un error de memoria no corregido puede provocar la corrupción de datos o el cuelgue del sistema.

---

## 2. Entornos que requieren hardware específico

### 2.1 Criterios para identificar entornos críticos

Un entorno requiere hardware empresarial o específico cuando se da al menos uno de estos factores:

- **Alta concurrencia:** muchos usuarios simultáneos (bases de datos, aplicaciones web, ERP).
- **Procesamiento intensivo:** renderizado, big data, machine learning, simulación científica.
- **Almacenamiento masivo:** sistemas de archivos corporativos, copias de seguridad, archivado.
- **Comunicaciones críticas:** centralitas IP, firewalls, sistemas de videovigilancia.
- **Regulación:** entornos sujetos a normativa (RGPD, PCI-DSS, ISO 27001) que impone requisitos de seguridad y trazabilidad.

### 2.2 Principales entornos empresariales

#### Data Center / CPD propio
Instalación dedicada donde la empresa aloja todos sus sistemas. Requiere infraestructura completa: clima, alimentación, seguridad física y conectividad redundante.

#### Hosting y Housing
- **Hosting:** el proveedor gestiona el hardware; el cliente contrata recursos (VPS, cloud, servidores dedicados).
- **Housing / Colocation:** el cliente lleva su propio hardware al CPD del proveedor, que le ofrece espacio, energía y conectividad.

#### Edge Computing
Procesamiento cercano a la fuente de datos (fábrica, tienda, vehículo). Requiere hardware compacto y robusto capaz de operar en condiciones adversas (temperatura, vibración, polvo).

#### Entornos HPC (*High Performance Computing*)
Clústeres de computación para simulación científica, predicción meteorológica o IA. Se caracterizan por interconexiones de muy baja latencia (InfiniBand) y aceleradores GPU/TPU.

#### Entornos de virtualización y nube privada
Infraestructuras hiperconvergentes (HCI) donde cómputo, almacenamiento y red se integran en un solo nodo escalable (VMware vSAN, Nutanix, Microsoft Azure Stack HCI).

---

## 3. Componentes hardware empresariales

### 3.1 Servidores

#### Factor de forma
- **Tower:** formato torre, para pequeñas empresas o ubicaciones sin rack.
- **Rack:** se monta en armario de 19". La altura se mide en unidades rack (U; 1U = 44,45 mm). Los más comunes: 1U, 2U, 4U.
- **Blade:** cuchillas que se insertan en un chasis compartido. Compactos y con gestión centralizada. Ideales para grandes CPD.
- **Micro-servidor:** nodos de bajo consumo (ARM o Intel Atom) para cargas de trabajo ligeras y densas.

#### CPU de servidor
- Diseñadas para múltiples núcleos (16, 32, 64+) y soporte de más RAM que los procesadores de consumo.
- Ejemplos: Intel Xeon Scalable, AMD EPYC.
- Soporte de multiprocesamiento simétrico (SMP): 2, 4 u 8 sockets físicos en un mismo servidor.

#### RAM de servidor
- **Tipo:** DDR5 / DDR4 Registered (RDIMM) o Load-Reduced (LRDIMM).
- **ECC obligatorio** para garantizar integridad de datos.
- Capacidades de 16 GB a 256 GB por módulo; servidores con hasta 6 TB de RAM.

#### Almacenamiento interno
- Discos SAS (Serial Attached SCSI): mayor fiabilidad y velocidad que SATA, pensados para uso 24×7.
- SSD NVMe U.2 / U.3: altísimo rendimiento para cargas IOPS-intensivas.
- Controladora RAID hardware con caché protegida por batería (BBU).

### 3.2 Almacenamiento en red

#### NAS (*Network Attached Storage*)
- Dispositivo con varios bahías de disco, accesible por red mediante protocolos de ficheros: NFS, SMB/CIFS, AFP.
- Ideal para compartir ficheros entre usuarios y para copias de seguridad.

#### SAN (*Storage Area Network*)
- Red dedicada de alta velocidad (Fibre Channel, iSCSI, FCoE) que conecta servidores con unidades de almacenamiento.
- Los servidores ven los LUNs como discos locales → mayor rendimiento y flexibilidad.
- Protocolos: Fibre Channel (FC), iSCSI (FC sobre IP), NVMe-oF (NVMe sobre red).

#### Comparativa NAS vs. SAN

| | NAS | SAN |
|---|---|---|
| Protocolo | Ficheros (NFS, SMB) | Bloques (FC, iSCSI) |
| Rendimiento | Medio | Alto |
| Complejidad | Baja | Alta |
| Coste | Bajo | Alto |
| Caso de uso | Compartición de ficheros | Bases de datos, VMs |

### 3.3 Networking empresarial

- **Switches de acceso:** conectan dispositivos finales (1G / 10G por puerto).
- **Switches de distribución/core:** interconectan switches de acceso (10G / 25G / 40G / 100G).
- **Switches ToR (*Top of Rack*):** ubicados en la parte superior del rack, conectan todos los servidores del armario.
- **Balanceadores de carga:** distribuyen tráfico entrante entre varios servidores (hardware: F5 BIG-IP, Citrix ADC; software: HAProxy, Nginx).
- **Firewalls de nueva generación (NGFW):** inspeccionan tráfico en capa 7, con IPS, DLP y control de aplicaciones.

### 3.4 Tarjetas y aceleradores

- **HBA (*Host Bus Adapter*):** conexión FC o SAS para SAN/almacenamiento.
- **NIC (*Network Interface Card*) de alta velocidad:** 10G, 25G, 100G; con funciones de *offload* (TOE, RDMA/RoCE).
- **GPU / FPGA / TPU:** aceleración de IA, renderizado, criptografía, procesamiento de señales.
- **Tarjeta IPMI / iDRAC / iLO:** gestión *out-of-band* del servidor (encendido/apagado remoto, consola KVM, actualizaciones de firmware).

---

## 4. Requerimientos físicos y ambientales de un CPD

### 4.1 Ubicación y construcción

- **Planta baja o sótano superior** para facilitar el tendido de cableado y evitar inundaciones.
- **Estructura resistente al fuego** (mínimo RF-120).
- **Aislamiento acústico y térmico.**
- **Sin ventanas** o con ventanas protegidas.
- **Doble acceso** en edificios de gran tamaño (evacuación y seguridad).
- **Suelo técnico elevado** (falso suelo) para distribución de cableado y refrigeración por suelo.

### 4.2 Control de acceso y seguridad física

- **Perímetros de seguridad en capas:** recinto exterior → sala de servidores → racks individuales.
- **Autenticación multifactor:** tarjeta + PIN, biometría (huella, iris).
- **CCTV** con grabación continua y almacenamiento de al menos 30 días.
- **Registro de accesos:** log de entradas y salidas con identidad, fecha y hora.
- **Política de acompañamiento:** las visitas siempre deben ir escoltadas por personal autorizado.
- **Control de dispositivos extraíbles:** prohibición o registro de pendrives, discos externos, etc.

### 4.3 Condiciones ambientales

Las condiciones recomendadas por ASHRAE y la norma EN 50600 son:

| Parámetro | Rango recomendado (clase A1) |
|---|---|
| Temperatura | 15 °C – 27 °C |
| Humedad relativa | 20 % – 80 % (sin condensación) |
| Punto de rocío | 5,5 °C – 15 °C |

- **Sensores de temperatura y humedad** distribuidos en la sala (entrada y salida de aire de los racks).
- **Alarmas automáticas** cuando se superan los umbrales.

### 4.4 Sistema de climatización

- **CRAC (*Computer Room Air Conditioning*):** unidades de precisión que controlan temperatura y humedad con alta exactitud.
- **Pasillo frío / pasillo caliente:** organización de los racks en filas alternas para separar el aire frío (entra por la parte delantera) del aire caliente (expulsado por la trasera).
- **Contención de pasillos:** paneles y puertas que aíslan el pasillo frío o caliente para mayor eficiencia.
- **Free cooling:** aprovechamiento del aire exterior cuando la temperatura exterior lo permite.
- **Liquid cooling:** refrigeración líquida directa al procesador para densidades de potencia muy elevadas.

#### PUE (*Power Usage Effectiveness*)

$$PUE = \frac{\text{Potencia total del CPD}}{\text{Potencia de los equipos TI}}$$

Un CPD eficiente debe tener PUE < 1,5. Los mejores hyperscalers alcanzan PUE ≈ 1,1.

### 4.5 Protección contra incendios

- **Detectores de humo de aspiración (VESDA):** detectan partículas de humo antes de que haya fuego visible.
- **Detección por temperatura y llama.**
- **Extinción automática con gas limpio** (FM-200, Novec 1230, CO₂ inertizante): no daña los equipos ni deja residuos.
- **Prohibición de extinción con agua** en la sala de servidores.
- **Extintor portátil de CO₂** como medida complementaria.

### 4.6 Organización del cableado

- **Patch panels** para terminación ordenada de cables de red.
- **Bandejas y canaletas** separadas para cableado eléctrico y de datos.
- **Etiquetado** en ambos extremos de cada cable.
- **Gestión del cableado vertical y horizontal** dentro del rack (organizadores de cable).
- **Documentación del cableado** actualizada (planos, inventario).

---

## 5. Sistemas de alimentación ininterrumpida

### 5.1 Problemas en el suministro eléctrico

| Problema | Descripción |
|---|---|
| Microcorte | Interrupción < 20 ms |
| Corte de suministro | Interrupción prolongada |
| Pico de tensión (*spike*) | Sobretensión breve y muy elevada |
| Sobretensión (*swell*) | Tensión superior a la nominal durante ciclos completos |
| Bajada de tensión (*sag*) | Tensión inferior a la nominal |
| Ruido eléctrico | Interferencias en la onda sinusoidal |
| Distorsión armónica | Deformación de la onda causada por cargas no lineales |

### 5.2 Estabilizadores de tensión y acondicionadores de línea

- **Reguladores / estabilizadores:** mantienen la tensión de salida constante ante variaciones de entrada (±20 %).
- **Acondicionadores de línea:** filtran ruido eléctrico y estabilizan tensión. Solución básica para pequeñas instalaciones.
- **Transformadores de aislamiento:** separan galvánicamente la carga de la red, eliminando interferencias de modo común.

### 5.3 SAI / UPS (*Uninterruptible Power Supply*)

El SAI combina un rectificador, baterías y un inversor para proporcionar alimentación continua y limpia.

#### Topologías

| Topología | Descripción | Tiempo de transferencia | Uso |
|---|---|---|---|
| **Off-line (standby)** | La carga va por red; el inversor sólo actúa si hay fallo | 4 – 10 ms | Equipos de bajo coste |
| **Line-interactive** | Regulador AVR en línea; inversor actúa en fallo | 2 – 4 ms | Workstations, pequeños servidores |
| **On-line doble conversión** | La carga siempre va por el inversor; red → baterías → carga | 0 ms | Servidores críticos, CPD |

#### SAI on-line doble conversión (detalle)

Es el estándar en entornos de CPD. La corriente alterna de red se rectifica a continua, carga las baterías y alimenta el inversor, que genera una onda sinusoidal limpia. Si falla la red, las baterías toman el relevo de forma instantánea (0 ms).

#### Parámetros clave del SAI

- **Potencia aparente (VA):** capacidad total del SAI.
- **Potencia activa (W):** potencia real que puede suministrar (VA × factor de potencia, típicamente 0,8 – 0,9).
- **Autonomía:** tiempo en minutos que puede alimentar la carga con las baterías.
- **Factor de potencia de la carga:** cargas de servidores modernos tienen FP ≈ 0,9 – 1.
- **Tiempo de recarga:** tiempo para recuperar la carga completa de las baterías tras un fallo.

#### Cálculo de la potencia necesaria

```
Potencia total carga (W) = Σ consumos de todos los equipos
Potencia SAI (VA) = Potencia total (W) / Factor de potencia del SAI
Autonomía = Capacidad batería (Wh) / Potencia carga (W)
```

**Regla práctica:** se dimensiona el SAI al 70-80% de su capacidad para dejar margen de crecimiento.

### 5.4 Grupos electrógenos

Para autonomías largas (>30 min), el SAI se complementa con un generador diésel:

1. Fallo de red → SAI toma la carga inmediatamente.
2. A los 10-30 segundos → arranca el generador.
3. El generador alimenta la carga; el SAI recarga sus baterías.
4. Cuando se restaura la red → transición ordenada de vuelta a la red.

Los generadores se prueban periódicamente bajo carga real.

### 5.5 PDU (*Power Distribution Unit*)

La PDU distribuye la alimentación del SAI a los equipos del rack:

- **PDU básica:** regleta de enchufes sin gestión.
- **PDU metered:** mide el consumo total.
- **PDU switched:** permite apagar/encender enchufes individuales de forma remota.
- **PDU monitored con salidas inteligentes:** control y monitorización por enchufe.

En entornos críticos se instalan **dos PDUs por rack** (alimentadas desde dos SAIs independientes) y los servidores con fuente dual se conectan a ambas.

---

## 6. Almacenamiento y conexión en caliente

### 6.1 ¿Qué es la conexión en caliente (*hot-swap / hot-plug*)?

La conexión en caliente permite sustituir o añadir un componente mientras el sistema está encendido y en producción, sin interrumpir el servicio. Es una característica esencial en entornos 24×7.

### 6.2 Discos con hot-swap

- Los servidores empresariales disponen de bahías hot-swap con expulsor (*ejector*).
- El disco se conecta al backplane mediante un conector SAS/SATA/NVMe que incorpora un circuito de protección.
- **Procedimiento de extracción:**
  1. Verificar en el sistema operativo o controladora RAID que el disco está marcado como *failed* o preparado para extracción.
  2. Pulsar el pestillo de la bandeja y extraer el disco lentamente.
  3. Insertar el disco de repuesto hasta que encaje.
  4. La controladora RAID inicia automáticamente la reconstrucción.
- **Indicadores LED:** cada bahía tiene un LED de actividad (verde) y un LED de fallo (ámbar). Siempre verificar el LED antes de extraer.

### 6.3 Fuentes de alimentación redundantes con hot-swap

- Los servidores empresariales incorporan 2 o más fuentes (PSU).
- Funcionan en modo **N+1** (una activa, una en standby) o **N+N** (carga compartida).
- Si una falla, la otra asume toda la carga sin interrupción.
- **Procedimiento de sustitución:**
  1. Confirmar que la fuente que se va a extraer es la que ha fallado (LED ámbar).
  2. Desconectar el cable de alimentación de esa fuente.
  3. Pulsar el pestillo y extraer la fuente defectuosa.
  4. Insertar la nueva fuente y conectar el cable.
  5. Verificar que el LED cambia a verde.

### 6.4 RAID (*Redundant Array of Independent Disks*)

El RAID protege los datos ante el fallo de uno o varios discos combinando múltiples unidades.

| Nivel | Descripción | Discos mín. | Tolerancia a fallos | Uso |
|---|---|---|---|---|
| RAID 0 | Striping (sin redundancia) | 2 | Ninguno | Rendimiento (no producción) |
| RAID 1 | Espejo (mirror) | 2 | 1 disco | Discos de sistema, logs |
| RAID 5 | Striping con paridad distribuida | 3 | 1 disco | Almacenamiento general |
| RAID 6 | Striping con doble paridad | 4 | 2 discos | Archivos críticos |
| RAID 10 | RAID 1 + RAID 0 | 4 | 1 por subespejo | BD críticas, alto rendimiento |

#### Disco de reserva (*hot spare*)
Un disco configurado como *hot spare* está conectado al sistema pero inactivo. Cuando un disco falla, la controladora RAID lo activa automáticamente e inicia la reconstrucción sin intervención humana.

### 6.5 Tarjetas y módulos hot-plug

Además de discos y fuentes, pueden sustituirse en caliente:

- **NICs** en servidores con soporte PCIe hot-plug (menos común, requiere soporte del sistema operativo y BIOS/UEFI).
- **Módulos de ventiladores** en la mayoría de servidores empresariales.
- **Módulos de memoria** en plataformas específicas que soportan *memory hot-add*.
- **Tarjetas en chasis blade:** toda la electrónica del chasis (switches de red, módulos de gestión) es hot-swappable.
