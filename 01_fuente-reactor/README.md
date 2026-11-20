# Fuente del reactor — convertidor CD-CD

## Objetivo

Mejorar la fuente del reactor, principalmente el convertidor CD-CD que
trabaja sobre la bobina. Esta es la línea principal de desarrollo.

## Punto de partida (estado actual, 2026-11-20)

- Ya se quitaron las resistencias que limitaban la corriente.
- Hoy se está usando **una bobina**, que todavía no está caracterizada.
- La ferrita actual es muy grande y **no es comercial**: no sirve como
  referencia reproducible. Hay que pasar a ferritas comerciales.
- Circuito actual que maneja la bobina: un IGBT con el colector a bus-.

## La línea (en este orden, sin saltar pasos)

### 1. Bobina — `02_bobina/`
Caracterizar adecuadamente la bobina actual y diseñar la nueva:
- inductancia (henrios) en función de vueltas, corriente y frecuencia;
- núcleo: ferritas comerciales, su AL, saturación y pérdidas;
- número de vueltas, henrios objetivo, frecuencia de trabajo.
Sin esta caracterización no se diseña el convertidor: la bobina manda.

### 2. Medio puente — `03_medio-puente/`
Pasar del IGBT único (colector a bus-) a un medio puente H para controlar
el convertidor CD-CD sobre esa bobina ya caracterizada.
Base existente: el firmware de medio puente de la ESP32 en `yollot-reactor`
(`firmware/esp32/ESP32_version5_2.ino`, dos pulsos MCPWM desfasados 180°).

### 3. Puente H completo — `04_puente-h-completo/`
Misma bobina y mismo control, ahora con puente completo: más rango y
posibilidad de invertir el sentido / trabajar como inversor.

### 4. Decisión — `05_decision-transformador-o-cdcd/`
Con el puente H completo medido, decidir con datos:
- poner un transformador y trabajar como inversor, o
- dejarlo como convertidor CD-CD.
La decisión se documenta ahí, con las mediciones que la sostienen.

## Seguridad

Esto es electrónica de potencia. Cada etapa se prueba primero sin tensión
en el bus, con límite de corriente de laboratorio, verificando paro,
tiempos muertos y saturación de la bobina antes de subir potencia.
