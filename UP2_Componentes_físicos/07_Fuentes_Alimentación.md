# FUENTES DE ALIMENTACIÓN

## 1. INTRODUCCIÓN

La fuente de alimentación (PSU - Power Supply Unit) es el componente responsable de convertir la corriente alterna (AC) de la red eléctrica doméstica (230V en Europa, 120V en América) en corriente continua (DC) a los voltajes que necesitan los componentes del ordenador: +12V, +5V, +3.3V y -12V.

Aunque a menudo es un componente olvidado o menospreciado en las configuraciones de PC, la PSU es absolutamente crítica. Una fuente de mala calidad puede causar inestabilidad del sistema, dañar componentes caros, o incluso suponer un riesgo de incendio. Por el contrario, una buena fuente puede durar más de una década y sobrevivir múltiples actualizaciones del resto del sistema.

---

## 2. POTENCIA Y DIMENSIONAMIENTO

### ¿Cuántos vatios necesito?

Esta es la pregunta más común y, frecuentemente, la peor respondida. Muchos usuarios sobredimensionan significativamente sus PSUs, gastando dinero innecesariamente.

**Cálculo básico:**
1. CPU: Consultar TDP (65W, 125W, 150W típico)
2. GPU: Consultar TDP (150-450W según modelo)
3. Placa base + RAM + almacenamiento: ~80-100W
4. Periféricos y tarjetas adicionales: +25-50W

**Ejemplo práctico:**
- CPU Ryzen 7 7800X3D: 120W
- GPU RTX 4070: 200W
- Resto del sistema: 100W
- **Total: 420W**
- **Recomendación: PSU de 650-750W**

**¿Por qué no 500W?** Tres razones:
1. **Picos de consumo:** Los componentes pueden tener picos breves muy superiores al TDP
2. **Eficiencia óptima:** Las PSUs funcionan más eficientemente al 50-80% de carga
3. **Margen para upgrades:** Futuras GPU más potentes
4. **Degradación:** La capacidad disminuye ligeramente con los años

---

## 3. CERTIFICACIÓN DE EFICIENCIA 80 PLUS

### 3.1 ¿Qué significa 80 PLUS?

La certificación 80 PLUS garantiza que la fuente convierte al menos el 80% de la energía AC de entrada en DC útil, con el resto perdiéndose como calor. Existen varios niveles:

| Certificación | Eficiencia 20% carga | Eficiencia 50% carga | Eficiencia 100% carga |
|---------------|----------------------|----------------------|-----------------------|
| **80 PLUS** | 80% | 80% | 80% |
| **80 PLUS Bronze** | 82% | 85% | 82% |
| **80 PLUS Silver** | 85% | 88% | 85% |
| **80 PLUS Gold** | 87% | 90% | 87% |
| **80 PLUS Platinum** | 90% | 92% | 89% |
| **80 PLUS Titanium** | 92% | 94% | 90% |

### 3.2 ¿Vale la pena pagar más por mayor eficiencia?

**Ventajas de mayor eficiencia:**
- Menor factura eléctrica a largo plazo
- Menos calor generado (sistema más fresco y silencioso)
- Generalmente indica mejor calidad de componentes internos

**Análisis coste-beneficio:**
- Diferencia Bronze vs Gold: ~30-50€
- Ahorro anual en electricidad: ~5-15€ (dependiendo uso)
- Break-even: 3-6 años

**Recomendación práctica:**
- **Gaming/home:** 80+ Bronze o Gold (mejor relación precio/rendimiento)
- **Workstation uso intensivo:** 80+ Gold o Platinum
- **Servidor 24/7:** 80+ Platinum o Titanium (ROI más rápido)

---

## 4. MODULARIDAD

### 4.1 Tipos de fuentes según cableado

**No modular:**
- Todos los cables permanentemente conectados
- Más económica
- Cable management complicado (cables sobrantes ocupan espacio)
- Solo recomendable en presupuestos muy ajustados

**Semi-modular:**
- Cables principales (24-pin ATX, 8-pin CPU) fijos
- Cables PCIe, SATA, Molex desmontables
- Buen balance precio/funcionalidad
- **Opción más popular**

**Completamente modular:**
- Todos los cables desmontables
- Cable management óptimo
- Más cara (20-40€ extra)
- Ideal para cajas con ventana lateral o builds premium

### 4.2 Ventajas del cableado modular

- Mejor flujo de aire (menos obstrucciones)
- Estética más limpia
- Facilita instalación y mantenimiento
- Permite usar cables custom (sleeved)

---

## 5. CONECTORES PRINCIPALES

### 5.1 Conectores esenciales

**ATX 24-pin (20+4):**
- Alimentación principal de la placa base
- Suministra +12V, +5V, +3.3V
- El +4 es desmontable para compatibilidad con placas antiguas

**EPS 8-pin CPU (4+4):**
- Alimentación dedicada para el procesador
- CPUs de alta gama pueden necesitar 8+4 o 8+8 pines
- Crítico: NO confundir con PCIe 8-pin (pin-out diferente)

**PCIe 6+2 pin:**
- Alimentación para tarjetas gráficas
- 6-pin: hasta 75W
- 8-pin (6+2): hasta 150W
- GPUs de alta gama requieren 2×8-pin o 3×8-pin

**12VHPWR (PCIe 5.0):**
- Nuevo conector de 16 pines para GPUs RTX 40-series
- Hasta 600W en un solo conector
- ⚠️ Importante: Insertar completamente hasta oír click (problemas de derretimiento si mal conectado)
- Versión mejorada: 12V-2×6 (estándar definitivo)

**SATA:**
- Alimentación para HDDs, SSDs 2.5", periféricos
- 3.3V, 5V, 12V en un conector plano
- Máximo 4-5 dispositivos por cable

**Molex 4-pin:**
- Conector antiguo pero aún presente
- Ventiladores, bombas de watercooling, iluminación RGB
- Menos común en builds modernos

---

## 6. CALIDAD Y FIABILIDAD

### 6.1 OEM (Fabricantes reales)

La mayoría de marcas de PSUs NO fabrican sus propias fuentes. Contratan a OEMs especializados:

**OEMs de calidad premium:**
- **Seasonic:** Fabrican sus propias PSUs y para otras marcas (Corsair RMx, EVGA G-series)
- **Super Flower:** High-end, usados por EVGA y otras
- **CWT (Channel Well Technology):** Calidad variable según modelo
- **Flextronics:** Corsair AX series

**OEMs de calidad media:**
- FSP, Great Wall, Enhance

**OEMs problemáticos:**
- Algunos modelos chinos genéricos sin certificación

**Conclusión:** El OEM importa más que la marca en la caja. Una Corsair VS (CWT básico) es inferior a una Seasonic Focus (Seasonic interno).

### 6.2 ¿Cómo identificar una buena PSU?

**Indicadores positivos:**
- Certificación 80+ Gold o superior
- Garantía de 5-10 años (indica confianza del fabricante)
- Reviews profesionales positivas (JonnyGURU, Tom's Hardware, Aris' PSU reviews)
- OEM conocido de calidad
- Protecciones completas (OVP, UVP, OCP, OTP, SCP)
- PFC activo
- Single-rail o multi-rail inteligente

**Red flags:**
- Sin certificación 80+ o solo 80+ básico
- Garantía <3 años
- Marca desconocida a precio sospechosamente bajo
- Especificaciones no disponibles o vagas
- "Max output" vs "continuous output" (la continua es la real)

### 6.3 Marcas recomendadas por gama

**Premium (150-300€):**
- Seasonic Prime TX/PX
- Corsair RMx/HX/AX
- be quiet! Dark Power Pro 12/13
- EVGA SuperNOVA G6/P6/T2

**Calidad-Precio (80-150€):**
- Seasonic Focus/Core
- Corsair RM (no RMx)
- EVGA SuperNOVA G7/G+
- MSI MPG A-GF
- Thermaltake Toughpower GF1/GF3

**Presupuesto ajustado (50-80€):**
- Seasonic S12III/Core
- Corsair CX/CXM (no CV)
- be quiet! System Power 10
- EVGA BQ

**Evitar:**
- Marcas genéricas sin reviews
- "Gaming PSU" sin especificaciones claras
- Cualquier cosa con "Max" o "Peak" watts sin especificar continuous

---

## 7. PROTECCIONES Y SEGURIDAD

### 7.1 Protecciones esenciales

Una PSU de calidad debe incluir:

**OVP (Over Voltage Protection):** Apaga la PSU si el voltaje supera umbrales seguros. Previene daño a componentes por sobrevoltaje.

**UVP (Under Voltage Protection):** Apaga si el voltaje cae demasiado. Previene inestabilidad y corrupción de datos.

**OCP (Over Current Protection):** Limita corriente por raíl. Previene sobrecalentamiento y daños.

**OPP (Over Power Protection):** Apaga si la potencia total excede capacidad. Previene sobrecarga.

**SCP (Short Circuit Protection):** Detecta cortocircuitos y desconecta inmediatamente.

**OTP (Over Temperature Protection):** Apaga si temperatura interna es excesiva.

### 7.2 Ripple y voltaje regulation

**Ripple (Rizado):**
Fluctuaciones residuales de AC en la salida DC. Debe ser <50mV en el raíl +12V para considerarse excelente. PSUs de calidad tienen <30mV.

**Voltage regulation:**
Estabilidad del voltaje bajo diferentes cargas. Una buena PSU mantiene voltajes dentro de ±3% (ATX spec es ±5%).

Ejemplo: Raíl +12V debe mantenerse entre 11.64V y 12.36V bajo cualquier carga.

---

## 8. FACTORES DE FORMA

### 8.1 ATX (estándar)

- Tamaño: 150mm ancho × 86mm alto × 140-180mm profundidad
- El más común en torres ATX y muchas microATX
- Mayor variedad de modelos y potencias (300-1600W)

### 8.2 SFX y SFX-L

- **SFX:** 125mm × 63.5mm × 100mm
- **SFX-L:** 125mm × 63.5mm × 125mm (más profundo)
- Para cajas pequeñas (Mini-ITX, SFF)
- Potencias típicas: 450-850W
- Ventilador más pequeño (92mm) → Puede ser más ruidoso
- Adaptador incluido para instalar en caja ATX

### 8.3 TFX y FlexATX

- Formatos especializados para cajas slim y servidores
- Menos comunes en builds custom
- Potencias limitadas (250-500W típico)

---

## 9. CÁLCULO DE CONSUMO Y EJEMPLOS

### 9.1 Ejemplos de configuraciones reales

**Build Gaming Económico:**
- CPU: Ryzen 5 7600 (65W)
- GPU: RTX 4060 (115W)
- Resto: 80W
- **Total: 260W → PSU recomendada: 550W 80+ Bronze**

**Build Gaming Alto Rendimiento:**
- CPU: i7-14700K (125W base, 253W boost)
- GPU: RTX 4080 (320W)
- Resto: 100W
- **Total: ~570W → PSU recomendada: 850W 80+ Gold**

**Build Workstation/Rendering:**
- CPU: Threadripper 7970X (350W)
- GPU: RTX 4090 (450W)
- Resto: 120W
- **Total: ~920W → PSU recomendada: 1200W 80+ Platinum**

**Build SFF/Mini-ITX:**
- CPU: i5-13600K (125W)
- GPU: RTX 4070 (200W)
- Resto: 80W
- **Total: ~405W → PSU recomendada: 650W SFX 80+ Gold**

### 9.2 Herramientas de cálculo

**Calculadoras online confiables:**
- [be quiet! PSU Calculator](https://www.bequiet.com/en/psucalculator)
- [Seasonic Wattage Calculator](https://seasonic.com/wattage-calculator/)
- [Cooler Master PSU Calculator](https://www.coolermaster.com/en-global/power-supply-calculator/)

**Importante:** Estas calculadoras suelen sobreestimar ligeramente (por seguridad), lo cual está bien.

---

## 10. MANTENIMIENTO Y VIDA ÚTIL

### 10.1 Vida útil esperada

- PSU de calidad: 7-10 años (garantía típica: 5-10 años)
- PSU económica: 3-5 años (garantía típica: 2-3 años)

Los condensadores son el componente que más se degrada con el tiempo. PSUs de calidad usan condensadores japoneses (Nippon Chemi-Con, Rubycon) que duran más.

### 10.2 Mantenimiento

**Limpieza (cada 6-12 meses):**
- Aire comprimido en la rejilla del ventilador
- NO abrir la PSU (riesgo de electrocución por condensadores cargados)
- Verificar que el ventilador gira libremente

**Señales de que la PSU está fallando:**
- Ruidos extraños (zumbidos, chasquidos)
- Apagados aleatorios
- Inestabilidad del sistema (pantallazos azules frecuentes)
- Ventilador constantemente a máxima velocidad
- Olor a quemado

**Si la PSU falla:** NO repararla tú mismo. Reemplazarla. Los condensadores pueden mantener carga letal incluso desconectada.

---

## EJERCICIOS PROPUESTOS

1. Calcula la PSU necesaria para: Ryzen 9 7950X (170W), RTX 4070 Ti (285W), 64GB RAM, 3 SSDs, 2 HDDs

2. Compara el coste de electricidad anual entre 80+ Bronze (85%) y 80+ Gold (90%) para un sistema que consume 400W durante 6 horas diarias (precio kWh: 0.15€)

3. Investiga el OEM de 3 PSUs diferentes de marcas conocidas y compara especificaciones

4. Explica por qué una PSU de 500W real es mejor que una de "700W max" sin certificación

5. Diseña la especificación de PSU óptima para un build Mini-ITX gaming de alta gama
