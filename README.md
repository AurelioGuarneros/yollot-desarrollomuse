# Yollot — Desarrollo

Carpeta de trabajo exclusiva de Aurelio y Muse para desarrollo, separada del
código de producción del remolque (`yollot-reactor`).

**Regla:** aquí se experimenta y se prueba. Nada pasa a producción sin estar
medido, documentado y aprobado. Cuando una mejora se prueba, se migra a
`yollot-reactor` como versión cerrada.

## Estación de desarrollo

- Raspberry Pi con 16 GB de RAM + HAT de IA de 40 TOPS.
- Su papel: calcular, programar, caracterizar con Python, guardar mediciones
  y, en la lectora de placas, correr visión / inferencia con el HAT.
- El control en tiempo real de potencia NO corre en el HAT: sigue en la
  ESP32 (PWM) y en la Raspberry del remolque (serial + RS485).

## Líneas de trabajo

1. **Fuente del reactor — convertidor CD-CD y bobina** (`01_fuente-reactor/`)
   Línea principal. Ver su README: es la ruta
   IGBT actual → medio puente → puente H completo → decisión
   transformador (inversor) o convertidor CD-CD.
2. **Lectora de placas** (`02_lectora-de-placas/`)
3. **Otros desarrollos** (`03_otros-desarrollos/`), uno por carpeta, sin mezclar.

## Estructura

```text
00_estacion/             ficha de la Raspberry, instalación y reglas de trabajo
01_fuente-reactor/       línea principal: fuente, bobina y convertidor CD-CD
  01_estado-actual-igbt/ punto de partida: IGBT con colector a bus-, sin resistencias
  02_bobina/             LA bobina: caracterización, ferritas comerciales, cálculos
  03_medio-puente/       medio puente H para el convertidor CD-CD
  04_puente-h-completo/  puente H completo
  05_decision-transformador-o-cdcd/  decisión final de topología
02_lectora-de-placas/    visión, datos y modelo
03_otros-desarrollos/
90_plantillas/           plantilla de medición, ficha de ferrita, bitácora
99_archivo/              lo cerrado o descartado, con su motivo
```

## Cómo trabajamos en GitHub

- Repositorio (público, creado por Aurelio el 2026-11-20): `AurelioGuarneros/yollot-desarrollomuse`
  (distinto de `yollot-reactor`, que es producción del remolque).
- En la Raspberry se clona una sola vez y ahí desarrollamos; en este chat
  trabajo sobre la copia local y te muestro cada resultado antes de subirlo.
- Ramas: `main` = lo ya probado dentro de desarrollo. Cada tema en su rama,
  p. ej. `bobina/caracterizacion-ferrita-01`, `fuente/medio-puente-v1`.
- Cada medición entra con fecha, condiciones y archivo crudo. Sin eso, un
  número no cuenta como resultado.
