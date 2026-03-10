# Práctica: Inventario y auditoría de software con WinAudit

---

## 1. Introducción

En cualquier entorno profesional, conocer con exactitud qué software está instalado en los equipos es una tarea esencial para el técnico de sistemas. Esta información permite gestionar licencias, detectar software no autorizado, planificar actualizaciones y garantizar el cumplimiento legal de la organización.

WinAudit es una herramienta gratuita, de código abierto y portable que genera un informe exhaustivo del sistema: hardware, software instalado, cuentas de usuario, configuración de red, políticas de seguridad, parches aplicados y mucho más. En esta práctica la utilizarás para auditar el equipo del aula y construir un inventario de software estructurado.

> **Nota:** WinAudit no requiere instalación. Es una aplicación portable que puedes copiar en un USB y ejecutar en cualquier equipo Windows sin dejar rastro en el sistema.

---

## 2. Parte A — Auditoría individual del equipo

### 2.1. Ejecución de WinAudit

**Paso 1 — Descarga y ejecuta WinAudit**

1. Descarga WinAudit desde la [web oficial](https://parmavex.co.uk/winaudit.html), descomprime y cópialo en el escritorio o en una carpeta de trabajo.
2. Ejecuta `WinAudit.exe` haciendo doble clic. No requiere instalación ni permisos de administrador.
3. La herramienta comenzará automáticamente a recopilar información del sistema. Espera a que se complete el análisis (hay una barra de progreso en la parte inferior).

**Paso 2 — Explora el informe generado**

1. Una vez completado el análisis, navega por las categorías del panel izquierdo.
2. Localiza y revisa al menos estas secciones: `Software instalado → Installed Programs`, `Software instalado → Software Updates`, `Grupos y Usuarios → Users`, `Red TCP/IP → Network Adapters`.
3. Dedica unos minutos a explorar libremente el informe antes de continuar.

> **Nota:** Fíjate especialmente en la sección *Installed Programs*. WinAudit muestra información más completa que la lista de aplicaciones de Windows, incluyendo la ruta de instalación, la fecha y en algunos casos la clave de licencia.

**Paso 3 — Exporta el informe**

1. Ve al menú `Archivo → Guardar`.
2. Selecciona el formato **CSV** para la tabla resumen y también **HTML** para conservar el informe completo con toda la información.
3. Guarda ambos archivos con tu nombre como prefijo, por ejemplo: `alumno01_winaudit.csv` y `alumno01_winaudit.html`.

---

### 2.2. Construcción de la tabla de inventario

A partir del informe exportado, elabora una tabla de inventario de software con la siguiente estructura. Incluye un mínimo de **10 aplicaciones**, priorizando las que no sean componentes internos del sistema operativo (evita entradas como *Microsoft Visual C++ Redistributable* o *Windows SDK*).

| Nombre de la aplicación | Versión | Desarrollador | Tipo de licencia | ¿Necesaria en este equipo? |
|---|---|---|---|---|
| Ejemplo: LibreOffice | 7.6.4 | The Document Foundation | Software libre (MPL 2.0) | Sí — ofimática general |
| Ejemplo: VLC media player | 3.0.20 | VideoLAN | Software libre (GPL v2) | Sí — reproducción multimedia |
| … | … | … | … | … |

> **Nota:** Para identificar el tipo de licencia de cada aplicación, consulta la web oficial del desarrollador o la sección *About* de la propia aplicación. Apunta la fuente donde has encontrado la información.

---

### 2.3. Preguntas de análisis individual

Responde brevemente a estas preguntas en el mismo documento de la tabla:

1. ¿Cuántas aplicaciones instaladas tienen licencia de software libre? ¿Y propietaria?
2. ¿Hay alguna aplicación instalada cuya licencia no hayas podido identificar?
3. ¿Detectas alguna aplicación que no tenga una utilidad clara en este equipo de aula? ¿Qué harías con ella?

---

## 3. Parte B — Comparativa por parejas

Una vez completada la parte individual, intercambia los archivos de informe con el equipo de tu compañero y realizaréis una comparativa entre los dos equipos.

### 3.1. Tabla comparativa

Elabora una tabla comparativa con los siguientes puntos. Añádela al mismo documento de la parte A:

| Aspecto comparado | Tu equipo | Equipo del compañero/a |
|---|---|---|
| Número total de aplicaciones instaladas | | |
| Aplicaciones presentes en ambos equipos | (lista) | (lista) |
| Aplicaciones solo en tu equipo | (lista) | — |
| Aplicaciones solo en el equipo del compañero/a | — | (lista) |

---

### 3.2. Preguntas de análisis comparativo

Responde brevemente a estas preguntas en el documento:

1. ¿Qué diferencias relevantes has encontrado entre los dos equipos? ¿A qué crees que se deben?
2. ¿Qué ventajas tiene disponer de una herramienta como WinAudit frente a revisar manualmente el panel de aplicaciones de Windows?
3. ¿En qué situaciones profesionales crees que sería útil ejecutar WinAudit de forma periódica en todos los equipos de una red?

---

## 4. Entrega

Cada alumno entrega individualmente los siguientes archivos a través de Aules:

1. `tunombre_winaudit.html` — informe completo en HTML generado por WinAudit
2. `tunombre_winaudit.csv` — datos en formato CSV
3. `tunombre_inventario.pdf` o `.docx` — documento con tabla de inventario, tabla comparativa y respuestas a las preguntas
