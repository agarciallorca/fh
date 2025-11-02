# 🔌 Fundamentos de Hardware: La Fuente de Alimentación (PSU)

La **Fuente de Alimentación (Power Supply Unit - PSU)** es el componente que se encarga de suministrar corriente eléctrica a todos los elementos del equipo microinformático.  
Su función esencial es **transformar** la **Corriente Alterna (CA)** de la red eléctrica (ej. 230V) en **Corriente Continua (CC)** y reducir su voltaje a los niveles específicos que necesita el PC.

---

## ⚡ Voltajes de Salida Comunes

Los voltajes de CC más habituales suministrados por una fuente ATX son:

* **$+12V$**: El carril más importante. Alimenta el **procesador (CPU)**, la **tarjeta gráfica (GPU)** y los motores de los discos duros/ventiladores.
* **$+5V$**: Usado principalmente por la placa base y algunos dispositivos USB y de almacenamiento más antiguos.
* **$+3.3V$**: Utilizado por la **memoria RAM** y la lógica de control de la placa base.
* **$+5VSB$** (Standby): Siempre activo, alimenta el circuito de encendido por *software* (función *soft-power*) de la placa base.

---

## ⚙️ Proceso de Transformación (Fuentes Conmutadas - SMPS)

Las fuentes de alimentación modernas de PC son **Fuentes Conmutadas (Switching Mode Power Supply - SMPS)**. Realizan la conversión CA $\rightarrow$ CC en las siguientes etapas:

1.  **Rectificación**: Transforma la CA de entrada en CC pulsante, utilizando un **puente rectificador** (diodos).
2.  **Filtrado Inicial**: Suaviza la señal rectificada para reducir el *ripple* (ondulación). Se realiza con **condensadores**.
3.  **Conmutación e Inversión**: Se utiliza un circuito de conmutación de alta frecuencia y un transformador más pequeño para reducir la tensión eficientemente.
4.  **Rectificación y Filtrado Final**: Convierte las señales resultantes en las tensiones de CC estables requeridas ($+12V, +5V, +3.3V$).
5.  **Estabilización y Regulación**: Circuitos internos (reguladores) mantienen las tensiones de salida constantes y dentro de los límites aceptables, independientemente de las fluctuaciones de la entrada o la carga.

---

## 📏 Tipos y Características de Fuentes de PC

### 1. Según el Factor de Forma
| Tipo | Uso principal | Características |
| :--- | :--- | :--- |
| **ATX** | PCs de escritorio estándar | Formato más común ($150mm \times 86mm$). Sucesora del estándar AT. |
| **SFX** | PCs compactos (Mini-ITX) | Dimensiones notablemente más reducidas para cajas pequeñas. |
| **TFX** | PCs de perfil bajo (*Slim*) | Formato alargado y estrecho. |

### 2. Según la Gestión del Cableado
* **No Modulares**: Todos los cables están fijos. Económicas, pero dificultan la gestión del cableado.
* **Semi-Modulares**: Los cables principales (24-pines y CPU) son fijos; los demás (SATA, PCIe) son desmontables.
* **Modulares**: Todos los cables son desmontables. Máxima flexibilidad, mejor estética y flujo de aire.

### 3. Según la Eficiencia (Certificación 80 PLUS)

La certificación **80 PLUS** indica que la fuente convierte al menos el **$80\%$** de la energía de entrada en potencia utilizable, perdiéndose el resto en calor. Cuanto más alta la certificación, mejor eficiencia.

| Certificación | **$50\%$** Carga |
| :---: | :---: |
| **80 PLUS** | $80\%$ |
| **Bronze** | $85\%$ |
| **Silver** | $88\%$ |
| **Gold** | $90\%$ |
| **Platinum** | $92\%$ |
| **Titanium** | $94\%$ |

---

## 🔌 Conectores Principales (Estándar ATX)

| Conector | Pines | Función |
| :--- | :---: | :--- |
| **ATX Principal** | $20/24$ | Suministra energía principal a la **placa base**. (El estándar actual es $24$ pines). |
| **EPS / ATX12V** | $4/8$ | Suministra energía dedicada al **procesador (CPU)**. (A menudo $4+4$ pines). |
| **PCIe** | $6/8$ | Suministra energía directa a la **tarjeta gráfica (GPU)**. (A menudo $6+2$ pines). |
| **SATA** | $15$ | Para discos duros SATA y unidades ópticas. |
| **Molex** | $4$ | Para ventiladores, bombas de agua y dispositivos IDE antiguos. |

---

## 🔢 Cálculo de la Potencia Requerida (Wattaje)

El cálculo de la potencia necesaria ($W$) es crucial para asegurar la estabilidad del sistema.

### 1. Componentes Críticos

La **CPU** y la **GPU** son los principales consumidores de energía. Su consumo máximo (TDP o TBP) se suma al consumo del resto de componentes.

$$
P_{\text{Total Estimada}} = P_{\text{CPU}} + P_{\text{GPU}} + P_{\text{Otros}}
$$

### 2. Aplicación del Margen de Seguridad

Se recomienda que la potencia nominal de la fuente seleccionada sea, al menos, un **$20\%$ a $30\%$ superior** a la potencia máxima estimada. Esto es esencial por tres motivos:

1.  **Picos de Consumo:** Cubrir los picos de potencia instantáneos (especialmente en la GPU).
2.  **Eficiencia Máxima:** Garantizar que la fuente opere cerca de su punto de máxima eficiencia (entre el $40\%$ y $60\%$ de carga).
3.  **Longevidad:** Evitar el estrés térmico y eléctrico de operar al máximo de su capacidad.

$$
\text{Potencia Fuente Requerida} \ge P_{\text{Estimada}} \times 1.25
$$

> **Ejemplo:** Si $P_{\text{Estimada}}$ es $500W$, la fuente recomendada es de al menos $500W \times 1.25 = 625W$. Se debe optar por un modelo de $650W$ o $750W$.

### 3. Foco en el Carril de $+12V$

En los PCs modernos, es más importante verificar la capacidad de entrega de corriente (Amperios, $A$) del carril de **$+12V$** que el Wattaje total. Una fuente de calidad debe ser capaz de entregar casi toda su potencia nominal en este carril (ej. una fuente de $750W$ debería soportar $\sim 62A$ en el carril de $+12V$).

---

## 🛡️ Protecciones Esenciales de la Fuente

Las fuentes de calidad incluyen circuitos de seguridad para evitar daños a los componentes del PC:

* **OCP** (Over-Current Protection): Protección contra **sobrecorriente**.
* **OVP** (Over Voltage Protection): Protección contra **sobretensión**.
* **UVP** (Under Voltage Protection): Protección contra **subtensión**.
* **OPP** (Over Power Protection): Protección contra **sobrecarga total** (superar el máximo Wattaje).
* **SCP** (Short Circuit Protection): Protección contra **cortocircuitos**.