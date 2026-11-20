# La bobina

Tú y yo trabajaremos en la bobina. Lleva su propia línea dentro de la fuente.

## Qué tenemos que cerrar

1. **Caracterizar la bobina actual** (la que ya estás usando, sin las
   resistencias que limitaban la corriente):
   - resistencia DC del devanado;
   - inductancia a baja señal y con corriente DC (sesgo): L cae al acercarse
     a saturación, y ese punto manda;
   - corriente de saturación práctica;
   - comportamiento con la frecuencia de trabajo prevista (1–20 kHz hoy en
     el firmware de la ESP32; a confirmar para el nuevo convertidor).
2. **Pasar a ferrita comercial**: fichar candidatas (forma, material,
   AL, Ae, le, Bsat, proveedor y precio en México) y compararlas contra la
   ferrita grande no comercial actual.
3. **Diseñar la bobina nueva**: número de vueltas ↔ henrios ↔ corriente,
   con el cálculo hecho en Python en `calculos/` y verificado midiendo.

## Relaciones que usaremos siempre (y verificaremos midiendo)

- L = AL · N²  →  N = √(L / AL)
- Energía: E = ½ · L · I²
- Densidad de flujo: B ≈ L · I / (N · Ae) — debe quedar con margen bajo Bsat
  a la corriente y temperatura de trabajo.
- Rizo de corriente en el convertidor: ΔI ≈ V · D / (L · f)
  → con V, duty y frecuencia conocidos, L fija el rizo.

## Dónde va cada cosa

- `caracterizacion/` — protocolo y resultados de medición de cada bobina.
- `ferritas-comerciales/` — una ficha por ferrita, con su fuente.
- `calculos/` — scripts Python (vueltas, henrios, saturación, rizo).
- `mediciones/crudas/` — archivos tal cual salen del instrumento.
- `mediciones/procesadas/` — tablas y gráficas ya limpias.
- `disenos/` — cada versión de bobina: vueltas, alambre, núcleo, foto.
