# Estación de desarrollo — Raspberry Pi 16 GB + HAT 40 TOPS

- **Equipo:** Raspberry Pi, 16 GB de RAM, HAT de IA de 40 TOPS.
  _(pendiente: modelo exacto del HAT, sistema operativo y nombre en la red)_
- **Uso:** desarrollo. Aquí se programa, se calcula, se caracterizan
  componentes con Python y se guardan las mediciones.
- **No es** la Raspberry del remolque: aquella controla en producción
  (panel Django, MQTT, serial ESP32 y RS485). Lo probado aquí se migra allá.
- **Carpeta de trabajo en la Raspberry (propuesta):** `~/desarrollo/yollot-desarrollo`
- **GitHub:** repositorio (público, creado por Aurelio el 2026-11-20) `AurelioGuarneros/yollot-desarrollomuse`.
  Aurelio lo hizo público para facilitar el acceso. Ojo: al ser público,
  cualquiera con el enlace puede verlo — no subir credenciales, datos
  personales ni nada que deba mantenerse reservado.
- **HAT de 40 TOPS:** su uso natural en nuestros temas es visión/inferencia
  (lectora de placas) y apoyo a modelos con datos de mediciones. No interviene
  en el lazo de control de potencia.
