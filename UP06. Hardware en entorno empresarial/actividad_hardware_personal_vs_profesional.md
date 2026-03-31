# Actividad: Auditoría Técnica de Hardware Empresarial
---

## 1. Escenario 
La empresa de logística **"Rápido & Seguro S.A."** necesita renovar su servidor principal de base de datos y virtualización. El Director Financiero ha visto una oferta de un **PC Gaming Extreme** en una gran superficie por unos **3.000€** que incluye un procesador Intel Core i9 de última generación, 128GB de RAM y refrigeración líquida. 

Argumenta que *"es mucho más rápido en GHz que los servidores de 5.000€ que propone el departamento técnico"*. Como futuro administrador de sistemas, debes realizar un **informe técnico individual** que compare ambas plataformas y justifique la inversión correcta basándote en la arquitectura real del hardware.

---

## 2. Fase de Investigación
Utiliza configuradores oficiales (Dell, HPE, Lenovo) y webs de componentes de consumo para completar la siguiente comparativa técnica entre un **PC de Alta Gama (Consumo)** y un **Servidor en Rack de entrada (Enterprise)**.

### Tabla Comparativa de Arquitectura

| Característica | PC Gaming / Workstation (i9/Ryzen 9) | Servidor Rack (Xeon Silver / EPYC) |
| :--- | :--- | :--- |
| **Modelo de Procesador** | | |
| **Frecuencia Máxima (GHz)** | | |
| **Canales de Memoria (RAM)** | | |
| **Soporte Memoria ECC** | | |
| **Carriles (Lanes) PCIe totales** | | |
| **Tipo de Almacenamiento** | | |
| **Gestión Remota** | | |
| **Fuentes de Alimentación** | | |

---

## 3. Análisis Técnico (Cuestiones Críticas)
Responde de forma razonada a las siguientes preguntas basándote en tu investigación:

1. **Rendimiento vs. Paralelismo:** Si el PC tiene más GHz pero solo 2 canales de memoria, y el servidor tiene menos GHz pero 8 canales de memoria, ¿cuál de los dos gestionará mejor 15 Máquinas Virtuales (VMs) accediendo a RAM simultáneamente? Justifica por qué.
2. **El cuello de botella (PCIe):** Investiga cuántos carriles PCIe consume una tarjeta de red de 25GbE y una controladora RAID profesional. ¿Podría el bus de un PC de consumo mantener el mismo flujo de datos masivo que el de un servidor sin saturarse?
3. **Disponibilidad y "Hot-Swap":** Define el concepto *Hot-Swap*. Identifica qué componentes del servidor permiten ser sustituidos sin apagar el equipo y explica cómo afecta esto al **SLA** (Acuerdo de Nivel de Servicio) de la empresa.
4. **Integridad de datos:** Explica brevemente qué es un "error de bit" (bit flip) en la memoria RAM y por qué la ausencia de tecnología **ECC** en el hardware de consumo es un riesgo inaceptable para una base de datos crítica.

---

## 4. Conclusión 
Redacta una breve conclusión técnica (máximo 150 palabras) dirigida a la dirección de la empresa. 

> Busca qué significa **TCO** (*Total Cost of Ownership*). Justifica si el coste de un servidor es menor a largo plazo, a pesar de que el precio de compra sea más elevado, centrándote en los conceptos de **redundancia, mantenibilidad y estabilidad**.
