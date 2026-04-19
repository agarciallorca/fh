## Sistemas de alimentación ininterrumpida - Actividades

### Actividad 1 – Topologías de SAI

Une cada topología con su característica principal:

| Topología | Tiempo de transferencia | Protección que ofrece |
|---|---|---|
| Off-line (standby) | | |
| Line-interactive | | |
| On-line doble conversión | | |

---

### Actividad 2 – Dimensionamiento de SAI

Una sala de servidores tiene el siguiente equipamiento:

| Equipo | Cantidad | Consumo unitario |
|---|---|---|
| Servidor rack 2U | 8 | 500 W |
| Switch core 48p 10G | 2 | 350 W |
| NAS empresarial | 1 | 250 W |
| Firewall HA | 2 | 150 W |

**a)** Calcula la potencia total de la carga.

**b)** Teniendo en cuenta que se dimensiona el SAI al 80% de capacidad, ¿qué potencia mínima en kVA necesitas? (Considera FP del SAI = 0,9).

**c)** ¿Qué topología de SAI es la adecuada para este entorno? Justifica.

**d)** Se quiere una autonomía de **15 minutos** con la carga anterior. ¿Cuánta capacidad de batería en Wh se necesita?

**e)** Propón **dos** modelos de SAI adecuados para este caso.

**f)** ¿Para qué sirve el grupo electrógeno en combinación con el SAI? ¿Cuándo arrancaría?

---

### Actividad 3 – Análisis de incidentes eléctrico

Durante una revisión de los logs del SAI (topología on-line doble conversión, autonomía nominal de 10 minutos) se detectan los siguientes eventos en la última semana:

```
Lun 09:14 – Interrupción de suministro de 8 ms. Batería activada. Red restaurada.
Mar 14:30 – Tensión de entrada: 198 V (nominal: 230 V). Modo batería activado.
Jue 03:22 – Fallo de red. Batería activada. Duración: 4 min 12 s. Red restaurada.
Vie 11:05 – Temperatura de batería: 38 °C (umbral: 40 °C). Alerta.
```

**a)** Clasifica los eventos del lunes, martes y jueves según el tipo de problema del suministro eléctrico que representa cada uno.

**b)** ¿Qué medida correctiva tomarías ante el evento del martes?

**c)** ¿Qué implicación tiene la alerta de temperatura de las baterías del viernes? Investiga qué tipos de baterías usan generalmente los SAI y cuál es su rango de temperaturas de funcionamiento óptimo.

**d)** ¿Habría sido suficiente un SAI line-interactive con la misma autonomía nominal para proteger la carga ante el evento del jueves? ¿Y ante el del martes? Razona ambas respuestas.
