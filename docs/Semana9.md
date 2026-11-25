# Semana 9 
## Integración, Go-to-Market y Pitch

**Proyecto:** DistanciaCero, "Reposabrazos Centinela" · **Materia:** Proyectos 4 · IBERO Puebla
**Versión:** v9.1 · 24/11/2026 · **Base:** Actividad 9 del equipo (06/11/2026) y guía de la Semana 9 del profesor

> **Cómo leer esta página.** Cada número lleva una etiqueta de evidencia:
>
> | Etiqueta | Significado |
> |---|---|
> | **MEDIDO** | Dato tomado por el equipo en laboratorio o campo, con su archivo de evidencia |
> | **VERIFICADO** | Dato con fuente externa consultada (enlace y fecha) |
> | **ESTIMADO** | Cálculo propio a partir de supuestos declarados |
> | **SUPUESTO** | Valor elegido sin fuente; se debe medir o confirmar |
> | **HIPÓTESIS** | Afirmación sobre usuarios o mercado que aún no tiene evidencia |
> | **POR VERIFICAR** | Requisito legal o técnico que falta confirmar con la autoridad o el fabricante |
> | **PENDIENTE** | Campo que el equipo llena cuando corra la prueba: `[MEDIR: …]` |
>
> **Estado real al 24/11/2026:** todavía no hay ninguna medición integrada. Toda la tabla de resultados está lista para llenarse; no hay ningún valor de laboratorio inventado.

---

## 0. Las seis brechas de la Semana 9 y la decisión que tomamos con cada una

| # | Brecha | Decisión del equipo | Dónde se cierra |
|---|---|---|---|
| B1 | El SIM7600**E-H** es la variante para Europa: no tiene las bandas **B2, B4 ni B28** que usan Telcel, AT&T y Movistar | Cambiar a **SIM7600SA-H** (variante para Latinoamérica) y repetir el DFM y el costo | §4, fila R2; Memoria §11 y §16 |
| B2 | "No pedirle nada a la persona mayor" choca con su consentimiento para tratar sus datos | RR-02 se redefine como "sin acciones **recurrentes**". El consentimiento es **un solo acto, en la instalación**, firmado por la persona mayor, y ella puede pausar o retirar la placa cuando quiera | §4, fila R3; Memoria §7 y §16 |
| B3 | Con la batería de 1.92 Ah, los 15 días de autonomía quedan en el límite (13.8 días si se reporta cada 15 min) | Reportar **cada 30 min y apagar el módem entre reportes** (escenario C: 24.2 días ESTIMADOS). La prueba T5 confirma o rechaza | §1.4 y T5 |
| B4 | Un buen payback por cliente no cubre los $71,540 de desarrollo | Se declara la meta de recuperar el desarrollo: **≈ 14 clientes** con el costo actual o **≈ 10** con DFM, con 24 meses de vida y 3 % de cancelación | §3.4 |
| B5 | El baseline de 10 a 14 días no cabe en las 2 semanas de cierre | La demo usa un **baseline precargado de 14 días simulados**, y el narrador **lo dice en voz alta**. RF-03 se prueba aparte con logs | §5.2, tramo 3 |
| B6 | No hay evidencia real: pruebas integradas, consumo, tokens, sesiones con usuarios ni métricas de la landing | Cada vacío es una prueba con dueño y fecha (§7). En la memoria se marca como **PENDIENTE** hasta que exista el archivo | §1, §2, §3, §7 |

---

## 1. Plan de integración y pruebas por fronteras

### 1.1 Mapa de fronteras (F1 a F4)

```
[MPU6050] --I²C--> [ESP32-S3: ventanas de 30 min + buffer en flash] --UART / AT--> [SIM7600SA-H]
                                                                                     |
                                                                   HTTPS POST (JSON, TLS)
                                                                                     v
   [Cloud Function] <--trigger-- [Firestore] <------------------------------------ (F2)
         |  z-score por hora + Claude Haiku (resumen semanal)            (F3)
         v
   [FCM push] + [WhatsApp]  -->  [App React Native: Estado · Historial · Onboarding]   (F4)
```

| Frontera | De → a | Protocolo | Qué tiene que cumplir | Registro que la vigila |
|---|---|---|---|---|
| **F1** Sensado | MPU6050 → ESP32-S3 | I²C a 400 kHz e interrupción de movimiento | Distinguir sentarse y levantarse de golpes y vibraciones | Log serie con `ts, evento, ax, ay, az, umbral` |
| **F2** Conectividad | ESP32-S3 → SIM7600 → red celular → Cloud Function | UART con comandos AT y HTTPS/TLS 1.2 | Reporte de extremo a extremo en ≤ 30 s (RD-03) y 0 reportes perdidos | Log de firmware con `AT+CREG?`, `AT+CSQ`, código HTTP, `VBAT` mínima y duración de la transmisión |
| **F3** Modelo e IA | Firestore → z-score → API de Haiku | Llamada interna y HTTPS | Un hueco de señal **no** se lee como inactividad; el resumen siempre es válido | Colección `model_runs` con `inputs_hash, z, decision, latency_ms, tokens_in, tokens_out` |
| **F4** Notificación | Backend → FCM, WhatsApp y app | FCM, WhatsApp Business y listener de Firestore | Estado correcto en la app en ≤ 10 min (RF-02) por ≥ 2 canales (RI-04) | Colección `notifications` con `t_decision, t_sent, t_delivered, canal, estado` |

### 1.2 Dos fallos probables por frontera y la primera prueba para aislarlos

| Frontera | Fallo probable | Síntoma | Primera prueba de diagnóstico (la más barata) |
|---|---|---|---|
| F1 | 1. El umbral no distingue sentarse de un golpe o de una mascota | Eventos falsos o eventos perdidos | En banco: 20 sentadas, 20 levantadas y 20 golpes con la mano sobre el cojín. Graficar \|a\| y contar aciertos |
| F1 | 2. El ruido de la alimentación mientras el módem transmite crea lecturas falsas | Eventos fantasma que coinciden con cada transmisión | Comparar el log de eventos con las marcas de transmisión; repetir con el módem apagado |
| F2 | 1. Caída de VBAT en la LiPo durante los picos del módem (hasta ~2 A según la hoja de datos, POR VERIFICAR para LTE) | Reinicio del ESP32 o del módem a la mitad del POST | Osciloscopio en VBAT durante el registro y la transmisión. Si baja de 3.4 V, agregar capacitores de baja ESR cerca del módulo |
| F2 | 2. El módem no se registra en la red: banda equivocada (E-H) o antena | `+CREG: 0,2` o `0,3` permanentes y `AT+CSQ` = 99 | `AT+CPSI?` para ver banda y operador, en el mismo lugar con un teléfono de referencia |
| F3 | 1. Un hueco de 3 o más reportes se interpreta como "no se sentó" y genera una **falsa alerta** | Alerta sin causa real | Simulación: borrar 3 ventanas de un día normal del dataset y revisar que el sistema dé "Sin reportar" y no "Alerta" |
| F3 | 2. Haiku tarda, falla o devuelve un resumen con formato roto | Resumen vacío o JSON inválido | Validar la salida contra el esquema; forzar un timeout de 1 ms y comprobar que entra la plantilla de respaldo |
| F4 | 1. La notificación FCM llega tarde o no llega (ahorro de batería de Android o token caducado) | `t_delivered − t_decision` > 10 min | Comparar las marcas de tiempo de `notifications` en 10 corridas; repetir con optimización de batería desactivada |
| F4 | 2. La app muestra un dato viejo como si fuera actual (caché) | El estado dice "Todo bien" con el dispositivo apagado | Apagar el dispositivo y verificar que la app pase a **"Sin reportar desde HH:MM"** en ≤ 2 ventanas |

### 1.3 Seis pruebas de sistema, de la más barata a la más cara

| # | Prueba | Procedimiento | Métrica | Criterio de aprobación (PDS) | Evidencia que se guarda | Resultado |
|---|---|---|---|---|---|---|
| **T1** | Falla de canal y de la API de IA | a) Revocar el token FCM y provocar una alerta. b) Bloquear WhatsApp. c) Poner una API key inválida de Haiku | Canal que entrega; resumen que se genera | La alerta llega por el canal que queda **en ≤ 10 min** (RI-04, RF-02); con Haiku caído llega el **resumen de plantilla**; cero pantallas en blanco | Capturas de los dos canales y export de `notifications` | `[MEDIR]` |
| **T2** | Desconexión y recuperación | Cortar la red celular 10 min (jaula de Faraday o antena desconectada) y restablecerla | Reportes perdidos; tiempo de recuperación | **0 reportes perdidos** (el buffer en flash los reenvía); primer reporte **≤ 60 s** después de volver la red; la app muestra "Sin reportar" y **no** una alerta | Log de firmware y conteo de documentos en Firestore | `[MEDIR]` |
| **T3** | Instalación sin ayuda | Una persona sin experiencia instala la placa y vincula la app solo con el instructivo | Tiempo; ayudas necesarias | **≤ 10 min**, sin ayuda (RI-03) | Video cronometrado y hoja de observación | `[MEDIR]` |
| **T4** | Latencia de extremo a extremo | 20 transmisiones normales y 10 anomalías inyectadas (ventana marcada como inactiva) | Tiempo de transmisión; tiempo de decisión a notificación | Transmisión **≤ 30 s en 20/20** (RD-03); decisión a notificación **≤ 10 min en 10/10** (RF-02) | CSV de marcas de tiempo; mediana y máximo | `[MEDIR]` |
| **T5** | Autonomía | Medir la corriente de cada fase (shunt de 1 Ω y osciloscopio, o un medidor de µA), integrar un ciclo de 30 min y extrapolar; descarga real de 72 h | Corriente promedio (mA); días proyectados | **≤ 4.27 mA promedio**, que da **≥ 15 días** con 80 % útil de 1,920 mAh (RD-01) | Capturas del osciloscopio y hoja de cálculo | `[MEDIR]` |
| **T6** | Operación continua de 48 h | Placa en un sillón real con baseline precargado y uso normal, con 2 cortes de red programados | Reinicios; reportes perdidos; disponibilidad del backend | **0 reinicios**, **0 reportes perdidos** y disponibilidad **≥ 99 %**, que equivale a ≤ 29 min sin servicio en 48 h (RD-04, solo indicativo) | Log completo y export del monitor de uptime | `[MEDIR]` |

**Prueba aparte, sin hardware (RD-02):** dataset simulado de 14 días con **50 eventos: 25 normales y 25 anómalos**. El criterio es **falsos positivos < 5 % y falsos negativos < 2 %**. Resultado: `[MEDIR: FP = __ %, FN = __ %]`. Con 25 anómalos, un solo falso negativo ya es 4 %; por eso el criterio exige **0 FN** en este set. Esto se declara como límite de la muestra.

**Por qué este orden.** T1 y T2 se corren en el escritorio en minutos y ya descartan los fallos de arquitectura, que son los más caros de corregir. T5 y T6 necesitan el sistema completo y días de reloj, así que van al final, pero **T6 debe arrancar a más tardar el día 7** de la ruta de cierre (§7).

### 1.4 Autonomía: cálculo previo a la medición (ESTIMADO)

Capacidad útil: 1,920 mAh × 80 % = **1,536 mAh**. Para durar 15 días (360 h): 1,536 ÷ 360 = **4.27 mA promedio máximo**.

| Fase | Corriente | Duración por reporte | Origen |
|---|---|---|---|
| ESP32-S3 en sueño profundo | 0.007 mA | Continuo | Hoja de datos de Espressif (VERIFICADO por el equipo en la Semana 9) |
| ESP32-S3 activo | ≈ 30 mA | 12 s | **SUPUESTO** |
| Módem registrado en reposo | 2.3 mA | Continuo | **SUPUESTO** (con DRX) |
| Módem transmitiendo | 150 mA | 10 s | **SUPUESTO** |
| Módem apagado entre reportes | 0.05 mA, más 15 s de registro a 150 mA | Por reporte | **SUPUESTO** |
| MPU6050 | 0.3 mA | Continuo | **SUPUESTO** (en modo de ciclo de bajo consumo puede ser menor) |

| Escenario | Promedio | Días con 80 % útil | ¿Cumple RD-01? |
|---|---|---|---|
| A: reporte cada 15 min, módem en reposo | 4.65 mA | 13.8 | **No** |
| B: reporte cada 30 min, módem en reposo | 3.63 mA | 17.6 | Sí, con poco margen |
| **C: reporte cada 30 min, módem apagado** | **2.64 mA** | **24.2** | **Sí (decisión)** |
| D: reporte cada 60 min, módem apagado | 1.50 mA | 42.7 | Sí |

**Lo que este cálculo no incluye:** las veces que el ESP32 despierta por la interrupción del MPU6050 en cada movimiento, la autodescarga, la temperatura ni el envejecimiento de la celda. Por eso el escenario C es la **decisión de diseño** y T5 es la **evidencia**.

**Efecto del escenario C en RF-02:** con ventanas de 30 min, la anomalía se puede **decidir** hasta 30 min después de que ocurre. RF-02 ("≤ 10 min") se mide desde que el backend tiene los datos que la confirman hasta que llega la notificación. La latencia total, de evento a aviso, puede llegar a ~40 min. Así se declara en la memoria, para no prometer "en tiempo real".

### 1.5 Degradación ante fallas (cómo falla "con gracia")

| Falla | Qué hace el sistema | Qué ve el hijo o hija |
|---|---|---|
| Sin red celular | El firmware guarda cada ventana en un buffer circular en flash: 7 días × 48 ventanas × ~64 B ≈ 21 KB. Reintenta con espera creciente (30 s, 2 min, 10 min) y reenvía todo al volver | "Sin reportar desde HH:MM. No es una alerta: la placa no tiene señal." Nunca dice "Todo bien" con datos viejos |
| Sin internet en la nube o Cloud Function caída | Los documentos se acumulan en Firestore y la función reprocesa en orden al volver (idempotente por `device_id + window_start`) | Igual que la fila anterior, después de 2 ventanas sin datos procesados |
| Falla FCM | Se reintenta por WhatsApp; si falla también, se marca `pendiente` y se reintenta cada 5 min | Llega por el canal que funcione (RI-04) |
| Falla de Haiku (timeout de 10 s, error o JSON inválido) | Se usa un **resumen de plantilla** con los mismos números ("Esta semana: 6 de 7 días con rutina normal…") | El resumen semanal llega igual, sin redacción natural. **La detección de alertas no depende de la IA** |
| Batería baja (< 3.5 V) | Reporta cada 60 min y manda el aviso "Batería baja" | Un aviso con días estimados restantes. `[MEDIR: umbral real en T5]` |

---

## 2. Protocolo y plantilla de pruebas con usuarios (30 min)

### 2.1 Participantes y ética

| Sesión | Perfil | Origen | Consentimiento |
|---|---|---|---|
| S1, S2, S3 | Hija o hijo adulto (35 a 55 años) con un padre o madre de 65 o más que vive solo. **Segmento objetivo** | Referidos de las 3 entrevistas de la Semana 4 y red del equipo | Consentimiento verbal grabado o por escrito (Anexo D) |
| S4, S5 | Estudiantes de otros equipos de Proyectos 4 | Intercambio de sesiones | Consentimiento verbal |

**Personas mayores:** no se hacen pruebas de uso con ellas, porque el producto no les pide nada. Si alguna participa, solo es para **explicarle el concepto y preguntarle si aceptaría la placa en su sillón**, con su consentimiento y sin recolectar datos de rutina. Esa respuesta es evidencia directa para la brecha B2.

### 2.2 Guion de 30 minutos

| Tiempo | Bloque | Qué hace el facilitador | Qué se registra |
|---|---|---|---|
| 0:00–3:00 | Introducción | Lee el guion fijo: "Probamos el producto, no a ti. Piensa en voz alta. No podemos ayudarte durante las tareas." Pide consentimiento para grabar | Hora, consentimiento sí o no |
| 3:00–10:00 | **Tarea 1:** instalar y vincular | Le da la placa, el instructivo de una hoja y el teléfono con la app | Éxito sin ayuda, tiempo, errores, SEQ, cita |
| 10:00–17:00 | **Tarea 2:** interpretar estados | Le muestra 3 pantallas en orden aleatorio: "Todo bien", "Alerta" y "Sin reportar" y le pregunta: "¿Qué harías ahora?" | ¿Distingue "Alerta" de "Sin reportar" en < 10 s (RI-01)? |
| 17:00–23:00 | **Tarea 3:** encontrar el precio y apartar | Abre la landing: "¿Cuánto cuesta en el primer año? Si te interesa, apártalo." | Tiempo hasta el precio, si deja sus datos, cita |
| 23:00–30:00 | Entrevista de cierre | Pregunta por comportamiento, no por opinión: "¿Qué usas hoy para saber cómo está tu mamá? ¿Cuánto te cuesta? ¿A quién más se lo recomendarías **ahora mismo**?" | Compromisos (§2.4) y citas |

**SEQ** (Single Ease Question): al terminar cada tarea se pregunta "¿Qué tan fácil o difícil fue?" en una escala de 1 a 7, donde 7 es "muy fácil".

### 2.3 Hoja de observación (una por sesión)

| Sesión | Tarea | ¿Éxito sin ayuda? (S/N) | Tiempo (mm:ss) | Errores | SEQ (1–7) | Cita textual |
|---|---|---|---|---|---|---|
| S1 | T1 instalar | `[ ]` | `[ ]` | `[ ]` | `[ ]` | "`[ ]`" |
| S1 | T2 estados | `[ ]` | `[ ]` | `[ ]` | `[ ]` | "`[ ]`" |
| S1 | T3 precio | `[ ]` | `[ ]` | `[ ]` | `[ ]` | "`[ ]`" |

**Síntesis por tarea** (se llena con las 5 sesiones):

| Tarea | Éxito sin ayuda (n/5) | Tiempo mediano | SEQ promedio | Meta |
|---|---|---|---|---|
| T1 instalar | `[ ]` | `[ ]` | `[ ]` | ≥ 4/5 en ≤ 10 min (RI-03) |
| T2 estados | `[ ]` | `[ ]` | `[ ]` | 5/5 distinguen "Alerta" de "Sin reportar" |
| T3 precio | `[ ]` | `[ ]` | `[ ]` | ≥ 4/5 encuentran el precio en < 30 s |

**Hallazgos por severidad:**

| Severidad | Definición | Hallazgo | Usuarios (n/5) | Cita | Cambio propuesto | Hipótesis del cambio |
|---|---|---|---|---|---|---|
| **Crítico** | Impide terminar la tarea | `[ ]` | `[ ]` | "`[ ]`" | `[ ]` | `[ ]` |
| **Mayor** | Termina con ayuda o con un error recuperable | `[ ]` | `[ ]` | "`[ ]`" | `[ ]` | `[ ]` |
| **Menor** | Molestia sin consecuencia | `[ ]` | `[ ]` | "`[ ]`" | `[ ]` | `[ ]` |

**Tres cambios de alto impacto y bajo esfuerzo:** `[ ]` · `[ ]` · `[ ]`
**Límites de la muestra:** son 5 sesiones, 3 del segmento, en una sola ciudad, con un prototipo y no con el producto final. Sirven para encontrar problemas de uso, **no** para estimar la demanda.

### 2.4 Señal de negocio: compromiso real o cortesía

| Señal | Tipo | Cuenta como evidencia |
|---|---|---|
| "Me encanta", "yo lo compraría", "está muy padre" | Opinión o cortesía | **No** |
| Deja su nombre, correo y ciudad en el pre-registro de la landing | Compromiso de tiempo y datos | Sí, débil |
| Nos presenta **en ese momento** a otro hijo o hija del segmento | Compromiso social | Sí, media |
| Acepta una fecha para instalar la placa en casa de su papá o mamá (piloto) | Compromiso de acceso | **Sí, fuerte** |
| Deja un anticipo reembolsable o firma una carta de intención con precio | Compromiso económico | **Sí, la más fuerte** |

Resultado: `[ ] pre-registros · [ ] referidos · [ ] fechas de piloto · [ ] anticipos`, de 5 sesiones.

---

## 3. Economía unitaria de lanzamiento y sensibilidad

### 3.1 Insumos

| Insumo | Valor | Estatus | Fuente o nota |
|---|---|---|---|
| Precio del hardware | $4,490 | **SUPUESTO**, decisión de precio | Semana 7. El rango tolerado según las entrevistas de la Semana 4 es **$2,000–$4,000 (HIPÓTESIS)** |
| Suscripción | $449/mes | **SUPUESTO**; respaldo parcial en entrevistas | Mariana $450, Lupita ≈ $550–650 y Ricardo $600–700 "sin pensarlo" (Semana 4, n = 3) |
| Costo operativo por suscriptor | $90.14/mes | **ESTIMADO** | SIM $50, nube $18, soporte $12, notificaciones $10, IA $0.14 |
| Comisión de la pasarela de pago | 3.6 % = $16.16/mes | **SUPUESTO** | Tarifa típica de pasarela, POR VERIFICAR |
| Costo del hardware | $4,158 actual / **$2,072 con DFM** | **ESTIMADO** | BOM × 1.40 (Semanas 7 y 8). Solo el módulo celular está cotizado |
| CAC | $1,000 | **SUPUESTO** | 5 demos × 1.5 h × $80/h = $600, más $400 en anuncios |
| Cancelación (churn) | 3 % mensual | **SUPUESTO** | Sin benchmark nacional |
| Costo de desarrollo | $71,540 | **ESTIMADO** | 5 ciclos × $14,308 (Semana 7) |
| Tokens de Haiku | `[MEDIR]` | **ESTIMADO** en §3.5 | `usage.input_tokens` y `output_tokens` de la API |

### 3.2 Cálculo (aritmética visible)

```
Contribución mensual   = 449 − 90.14 − 16.16                     = $342.70
Vida media             = 1 ÷ 0.03                                = 33.3 meses
LTV                    = 342.70 × 33.3                           = $11,423
Ingreso neto de HW     = 4,490 × (1 − 0.036)                     = $4,328.36

Caso (a) el cliente paga el hardware a $4,490:
  Inversión por cliente = CAC + costo HW − ingreso neto HW = 1,000 + 4,158 − 4,328.36 = $830
  LTV ÷ inversión       = 11,423 ÷ 830                             = 13.8
  Payback               = 830 ÷ 342.70                             = 2.4 meses

Caso (b) hardware subsidiado (comodato):
  Inversión             = 1,000 + 4,158                            = $5,158
  LTV ÷ inversión       = 2.21      Payback = 15.1 meses

Caso (b) con DFM:
  Inversión             = 1,000 + 2,072                            = $3,072
  LTV ÷ inversión       = 3.72      Payback = 9.0 meses
```

| Caso | Inversión por cliente | LTV ÷ inversión | Payback | ¿Pasa la regla práctica (≥ 3 y < 12 meses)? |
|---|---|---|---|---|
| (a) HW a $4,490, costo actual | $830 | **13.8** | **2.4 meses** | Sí, **pero depende de que alguien pague $4,490**, arriba del rango tolerado (HIPÓTESIS S1) |
| (b) HW subsidiado, costo actual | $5,158 | 2.21 | 15.1 meses | **No** |
| (b) HW subsidiado, con DFM | $3,072 | 3.72 | 9.0 meses | Sí |

### 3.3 Sensibilidad (±25 % por insumo, caso b con costo actual)

| Insumo movido | Valor | LTV ÷ inversión | Payback |
|---|---|---|---|
| Suscripción +25 % | $561 | 2.91 | 11.4 meses |
| Suscripción −25 % | $337 | 1.52 | 22.0 meses |
| Cancelación −25 % | 2.25 % | 2.95 | 15.1 meses |
| Cancelación +25 % | 3.75 % | 1.77 | 15.1 meses |
| CAC −25 % | $750 | 2.33 | 14.3 meses |
| CAC +25 % | $1,250 | 2.11 | 15.8 meses |
| Tokens de IA ×10 | IA = $1.40/mes | 2.21 (sin cambio apreciable) | 15.1 meses |
| **Precios con IVA incluido** (ver §4, fila R8) | $449 → $387.07 neto | **1.81** | **18.4 meses** |

**Lectura (máximo 8 líneas):**
1. **Lo que más mueve el resultado es el precio de la suscripción**, y después la cancelación. El CAC y la IA casi no lo mueven.
2. El caso (a) solo cumple porque el margen del hardware es casi cero. La pregunta que decide el negocio es **si alguien paga $4,490**, y hoy no hay evidencia de eso.
3. **El IVA es un riesgo escondido.** Si $449 incluye IVA, la contribución baja a $280.77 y el caso (b) DFM queda en 3.05 y 10.9 meses: en el límite.
4. El costo de la IA es irrelevante para la economía (< 0.1 % de la contribución). Se reporta para cumplir con la rúbrica, no porque sea una palanca.

### 3.4 Palancas con efecto numérico (caso b)

| Palanca | Inversión | LTV ÷ inversión | Payback |
|---|---|---|---|
| 1. **DFM** (módulo LCC, carcasa PETG) | $3,072 | 3.72 | 9.0 meses |
| 2. **Programa de referidos** (CAC $600) | $4,758 | 2.40 | 13.9 meses |
| 3. **DFM + referidos + cancelación 2 %** | $2,672 | **6.41** | **7.8 meses** |
| Alternativa: HW a $2,000 con costo DFM | $1,144 | 9.99 | 3.3 meses |

**Recuperar el desarrollo ($71,540)** con 24 meses de vida y 3 % de cancelación:

```
Contribución esperada en 24 meses = 342.70 × (1 − 0.97²⁴) ÷ 0.03 = 342.70 × 17.29 = $5,924 por cliente
Caso (a), costo actual: 5,924 − 830 = $5,094 por cliente  → 71,540 ÷ 5,094 = 14.0 → 15 clientes para cubrirlo completo
Caso (a), con DFM:      5,924 + 1,256 = $7,180 por cliente → 71,540 ÷ 7,180 = 9.96 → 10 clientes
```

Con la meta de SOM de 850 familias, 15 clientes son el **1.8 %**. La meta es alcanzable si se cumple S1 (que alguien pague el precio).

### 3.5 Costo real de la IA (Claude Haiku): ESTIMADO, por medir

| Concepto | Valor | Estatus |
|---|---|---|
| Uso | 1 resumen semanal por usuario. La detección **no** usa IA | Decisión de diseño |
| Tokens por resumen | ~2,000 de entrada (instrucciones + 7 días de estadísticas agregadas) y ~300 de salida | **SUPUESTO** |
| Precio de Haiku 5.5 | US$0.10 por millón de tokens de entrada y US$0.50 por millón de salida, para prompts < 100 K tokens | **VERIFICADO** con fuentes secundarias (nov 2026). Confirmar en la página oficial de precios de Anthropic |
| Costo por resumen | 2,000 × 0.10/10⁶ + 300 × 0.50/10⁶ = **US$0.00035** | ESTIMADO |
| Costo por usuario al mes | 0.00035 × 4.35 semanas = US$0.0015 ≈ **$0.03 MXN** (con 18.42 MXN/USD) | ESTIMADO. El modelo usa **$0.14 como cota alta** |
| Cómo se mide | Registrar `usage.input_tokens` y `usage.output_tokens` de cada respuesta en `model_runs`, y reportar el promedio de 10 resúmenes | `[MEDIR]` |

---

## 4. Checklist regulatorio y legal (México)

> No somos abogados. Esta tabla organiza lo que hay que confirmar. El estatus **VERIFICADO** solo se usa cuando hay una fuente consultada con fecha.

| # | Tema | ¿Aplica? | Qué exige | Trámite y emisor | Costo y tiempo | Estatus |
|---|---|---|---|---|---|---|
| R1 | **Homologación** de equipos con radio (módulo celular, y wifi/BLE del ESP32-S3 aunque no se use) | Sí | El equipo que se conecta a redes públicas debe estar homologado | Hasta 2025 era el IFT. Con la ley de telecomunicaciones de 2025 lo atiende la **CRT** (Comisión Reguladora de Telecomunicaciones) | Derechos en el art. 174-J de la Ley Federal de Derechos; monto y plazo sin confirmar | Alcance **VERIFICADO** (Semana 9). Trámite **POR VERIFICAR**: ¿basta un módulo certificado o se homologa el producto final? |
| R2 | **Bandas LTE** del módulo | Sí | Operar en las bandas de Telcel y AT&T (B2, B4, B28) y de Movistar (B2) | Hoja de datos de SIMCom y operador | — | E-H **VERIFICADO incompatible**: B1/B3/B5/B7/B8/B20/B38/B40/B41. SA-H **VERIFICADO compatible** en la hoja de datos: B1/B2/B3/B4/B5/B7/B8/B28/B66. Precio y disponibilidad en LCC **POR VERIFICAR** |
| R3 | **Datos personales** | Sí | Aviso de privacidad, consentimiento, derechos ARCO y medidas de seguridad. Si los datos revelan **salud**, son **sensibles** y piden consentimiento **expreso y por escrito** | LFPDPPP (publicada el 20/03/2025). La autoridad es la Secretaría Anticorrupción y Buen Gobierno (antes INAI) | Sin costo de trámite; requiere redactar el aviso | Ley **VERIFICADO** (fuente secundaria). **POR VERIFICAR**: si la rutina de uso del sillón cuenta como dato de salud. **Decisión:** tratarla como sensible por precaución |
| R4 | **Transferencia internacional** (Firebase y la API de Anthropic, con servidores fuera de México) | Sí | Informarla en el aviso de privacidad | LFPDPPP | — | **POR VERIFICAR**. Minimizar: a Haiku solo se mandan estadísticas, sin nombres ni ubicación |
| R5 | **No es un dispositivo médico** | Sí, como límite | Si se anuncia para monitorear la salud, podría caer en la regulación de dispositivos médicos | COFEPRIS | Un registro sanitario sería prohibitivo en esta etapa | **POR VERIFICAR**. Regla de mensaje: sin "detecta caídas", "salud" ni "emergencia médica"; decir "avisa si cambia la rutina" |
| R6 | **Seguridad eléctrica** | Probable si se vende con cargador | Cumplir la NOM aplicable a equipo electrónico (NOM-001-SCFI-2018) | Laboratorio acreditado (p. ej. NYCE) | Sin cotizar | **POR VERIFICAR**. Opción: vender sin cargador y usar uno USB-C ya certificado |
| R7 | **Baterías LiPo** | Sí | Celda con pruebas de seguridad (IEC 62133-2) y resumen de pruebas UN 38.3 para enviarla por paquetería | Proveedor de la celda y paquetería | Pedir los documentos al proveedor | **POR VERIFICAR**. Sin estos documentos, la paquetería puede rechazar el envío |
| R8 | **Información comercial y precio** | Sí | Instructivo y garantía en español (NOM-024-SCFI aplicable a electrónicos) y **precio total con impuestos visible** | PROFECO, Ley Federal de Protección al Consumidor (LFPC) | — | **POR VERIFICAR**. Hoy el modelo usa precios **sin IVA**: la landing debe mostrar el total |
| R9 | **Suscripción y cancelación** | Sí | Contrato o términos claros, forma de cancelar y garantía del hardware | PROFECO (contratos de adhesión, si aplica) | — | **POR VERIFICAR** |
| R10 | **Licencias de software** | Sí | Revisar las de firmware (ESP-IDF o Arduino core, librería del módem), React Native, Expo y los SDK de Firebase | Repositorio de cada proyecto | $0 | **POR VERIFICAR**. Tabla de licencias en el Anexo B. Ojo con las LGPL del firmware si se distribuye el binario |
| R11 | **Términos de la API de IA y de WhatsApp** | Sí | Términos comerciales de Anthropic; WhatsApp Business exige plantillas aprobadas para mensajes iniciados por la empresa | Anthropic y Meta (o Twilio) | Por mensaje en WhatsApp: **POR VERIFICAR** | **POR VERIFICAR** |
| R12 | **Economía circular y residuos electrónicos** | Probable | Plan de manejo de residuos electrónicos y de baterías | Ley General de Economía Circular (publicada el 19/01/2026) y SEMARNAT | — | Ley **VERIFICADO** (fuente secundaria, 05/11/2026). Obligación concreta **POR VERIFICAR** |
| R13 | **Marca** "DistanciaCero" | Sí | Búsqueda fonética y registro en las clases 9 y 42 | IMPI | Tarifa vigente del IMPI | **POR VERIFICAR** (la búsqueda no se ha corrido) |
| R14 | Exportación | No en esta etapa | — | — | — | No aplica |

**Lo que sí se puede hacer en un piloto de 5 a 10 unidades (sin venta):**
- Unidades en comodato con familias conocidas, con **consentimiento firmado por la persona mayor y por el hijo o hija** y un aviso de privacidad simple.
- Usar módulos que ya traigan certificación de origen y celdas con documentos UN 38.3, sin cobrar.
- Datos mínimos: sin nombre de la persona mayor en el backend (se usa un alias), borrado al terminar el piloto.

**Lo que se resuelve antes de vender a terceros:**
- R1 (homologación ante la CRT), R2 (módulo SA-H), R3 y R4 (aviso de privacidad final y consentimiento por escrito), R5 (confirmar que no es dispositivo médico), R6 a R9 (NOM, precio con IVA, términos y garantía) y R13 (marca).

---

## 5. Pitch de 3 minutos, demo de 7 minutos y preguntas del jurado

### 5.1 Guion del pitch (337 palabras, unas 2:36 a 130 palabras por minuto)

| Parte | Tiempo | Tope | Palabras | Guion |
|---|---|---|---|---|
| 1. Persona y problema | 35 s | 76 | 63 | Mariana vive lejos de su mamá. En nuestra entrevista nos dijo que pagaría 450 pesos al mes, sin pensarlo, por algo que le quite el miedo a «la llamada». Su mamá vive sola. Hoy la única forma que tiene Mariana de saber si está bien es llamarle todos los días, y cuando su mamá no contesta, el miedo llega antes que la explicación. |
| 2. Solución e IA con propósito | 35 s | 76 | 67 | DistanciaCero es una placa delgada que va debajo del cojín del sillón favorito de su mamá. No tiene botones, no usa wifi y ella no tiene que hacer nada en su día. Un acelerómetro registra cuándo se sienta y se levanta, la nube aprende su rutina hora por hora y, solo si algo se sale de lo normal, Mariana recibe un aviso. Si todo está bien: silencio. |
| 3. Mercado y modelo | 35 s | 76 | 67 | Estimamos unas 94 mil personas mayores que viven solas y tienen un hijo o hija que podría pagar este servicio; nuestra meta para los dos primeros años es llegar a 850 familias. Cobramos 4,490 pesos por el equipo y 449 al mes. Cada suscripción deja 343 pesos de contribución mensual y, si el cliente paga el equipo, recuperamos lo que cuesta conseguirlo en menos de tres meses. |
| 4. Tracción y validación | 35 s | 76 | 63 | ¿Qué tenemos hoy? Tres entrevistas con hijos e hijas: los tres aceptaron pagar una suscripción y pusieron precios entre 450 y 700 pesos al mes. Tenemos la placa, la app y el modelo de detección, y probamos el sistema completo con seis pruebas ligadas a nuestras especificaciones. Lo que todavía no tenemos son clientes: hoy publicamos la landing y medimos los primeros pre-registros. |
| 5. Equipo | 15 s | 32 | 28 | Somos cuatro estudiantes de Ingeniería Mecatrónica de la IBERO Puebla. Diseñamos nosotros mismos el hardware, el firmware, la nube, la app y el modelo que aprende la rutina. |
| 6. Petición y cierre | 25 s | 54 | 49 | Buscamos diez familias para un piloto de un mes en Puebla. Si tu mamá o tu papá vive solo, escanea el código y aparta tu lugar hoy. Porque saber que alguien que amas está bien no debería depender de que conteste el teléfono. Con DistanciaCero, el silencio significa tranquilidad. |

**Respaldo de cada afirmación y lo que sigue PENDIENTE:**

| # | Afirmación | Evidencia | Estatus |
|---|---|---|---|
| P1 | "Mariana vive lejos… pagaría 450 sin pensarlo" | Entrevista de la Semana 4 (precio "sin pensarlo": $450) | El precio está **VERIFICADO** (n = 1). "Vive lejos" y "le quite el miedo a la llamada" quedan **PENDIENTES**: confirmarlos con las notas de la entrevista o cambiarlos por su frase real |
| P2 | "Ella no tiene que hacer nada en su día" | RR-02 redefinido (B2) | Cierto en la operación diaria; el consentimiento es un acto único en la instalación |
| P3 | "La nube aprende su rutina" | Modelo z-score (RF-01) | **PENDIENTE** hasta que se mida RD-02 (FP y FN) |
| P4 | "94 mil… 850 familias" | TAM y SOM de la Semana 4 | **SUPUESTO**: los filtros los propuso la IA; la disposición de pago (25 %) es el más frágil |
| P5 | "343 pesos… menos de tres meses" | §3.2, caso (a) | **ESTIMADO**: depende de que paguen $4,490 |
| P6 | "Probamos el sistema completo con seis pruebas" | T1–T6 | **PENDIENTE**: solo se dice si T1–T6 están corridas el día del pitch. Si no, se dice "estamos probando" |
| P7 | "Hoy publicamos la landing y medimos pre-registros" | §6.2 | **PENDIENTE**: la landing aún no está publicada |
| P8 | Equipo de cuatro | — | **PENDIENTE**: nombres y roles |
| P9 | "Diez familias para un piloto" | — | Es la petición; nadie ha aceptado todavía |

**Las 5 preguntas más difíciles del jurado** están en la §5.3: Q1, Q3, Q4, Q5 y Q7.

### 5.2 Guion de la demo de 7 minutos, con Plan B por tramo

**Atajos que se declaran en voz alta al empezar:** (1) intervalo de reporte comprimido a **10 s** en lugar de 30 min; (2) **baseline precargado** de 14 días simulados; (3) si no hay señal celular en el salón, se usa el **hotspot del teléfono** y se dice. El firmware de la demo se congela después del último ensayo; tiene que haber 3 ensayos completos y un video de respaldo grabado.

| Tramo | Tiempo | Quién | Qué pasa | Lo que se dice | Plan B si falla |
|---|---|---|---|---|---|
| 1. Contexto | 0:00–0:45 | Narrador | Sillón real con la placa y el teléfono proyectado | "Esto es lo que vería Mariana. La placa ya está debajo del cojín." | Render del sillón y fotos del prototipo |
| 2. Camino principal | 0:45–3:15 | Operador | Vincular la placa con la app (onboarding) → sentarse y levantarse 3 veces → llega "Todo bien" con el historial del día | "Reportamos cada 10 segundos solo para la demo; el producto reporta cada 30 minutos para durar más de 15 días con una carga." | Video de 90 s del mismo flujo (T3) y capturas |
| 3. Evento provocado | 3:15–4:45 | Operador | Se simula "una mañana sin actividad": la ventana esperada no tiene eventos → z-score fuera de rango → push y WhatsApp en dos teléfonos | "**Aclaración honesta:** el sistema necesita de 10 a 14 días para aprender la rutina. Para hoy cargamos 14 días simulados. En el piloto aprende la rutina real." | Disparar la alerta desde el dataset precargado con un script; si tampoco funciona, video |
| 4. Fallo manejado | 4:45–5:45 | Operador | Se desconecta la antena 20 s → la app dice "Sin reportar", **no** "Alerta" → se reconecta → llegan los reportes guardados | "Un hueco de señal no es una emergencia. No queremos que Mariana llame asustada por un problema de cobertura." | Video de T2 |
| 5. Compra | 5:45–6:30 | Narrador | Código QR a la landing → precio visible → pre-registro en vivo de alguien del público | "El precio está a la vista y hay un solo botón." | Captura de la landing y del contador de pre-registros |
| 6. Cierre | 6:30–7:00 | Narrador | Tabla de estado: qué funciona, qué falta, siguiente paso | "Funciona X y está medido Y. Falta Z. El siguiente paso es el piloto con diez familias." | — |

### 5.3 Preguntas difíciles de evaluadores e inversionistas

| # | Pregunta | Respuesta directa | Respaldo en la memoria |
|---|---|---|---|
| Q1 | ¿Por qué alguien pagaría $4,490 si en las entrevistas toleraban entre $2,000 y $4,000? | No lo sabemos todavía; es nuestra hipótesis más débil. Por eso tenemos un plan B: comodato, con 3.72 y 9 meses de payback si se aplica el DFM. El piloto mide cuál de los dos acepta la gente | §15, §14 |
| Q2 | ¿Cuánto cuesta fabricar una unidad? | $4,158 con la BOM actual y $2,072 con DFM, los dos ESTIMADOS. Solo el módulo celular está cotizado | §11, Anexo A |
| Q3 | ¿Funciona con las redes de México? | Con el módulo que teníamos no: el E-H es europeo. Cambiamos al SA-H, que en su hoja de datos sí tiene B2, B4 y B28. Falta probarlo con un SIM de Telcel | §16, R2; §17, F2 |
| Q4 | ¿Quién autorizó medir la rutina de la persona mayor? | Ella misma, una sola vez, al instalarla, con un consentimiento escrito y simple. Puede pausarla o quitarla. No pedimos nada todos los días, pero sí su permiso | §16, R3; §7, RR-02 |
| Q5 | ¿Cuántos clientes necesitan para no perder dinero? | Unos 15 para recuperar los $71,540 de desarrollo con el costo actual y unos 10 con DFM, con 24 meses de vida y 3 % de cancelación | §15 |
| Q6 | ¿Por qué no usar un reloj con botón de pánico o una cámara? | El botón requiere que ella lo use y lo cargue, y la cámara invade. Nosotros eliminamos la interacción y no tomamos audio ni imagen (RR-03) | §4, §5 |
| Q7 | ¿Dónde está la IA y por qué no basta un `if`? | La detección es estadística: un z-score contra la rutina de **cada persona** por hora, que un umbral fijo no capta. Claude Haiku solo redacta el resumen semanal y cuesta centavos. Si se cae, hay una plantilla | §21, §17 T1 |
| Q8 | ¿Cuántas falsas alarmas da? | La meta es < 5 % de falsos positivos y < 2 % de falsos negativos. `[MEDIR en el dataset de 50 eventos]`. Un hueco de señal nunca se convierte en alerta | §7, RD-02; §17 |
| Q9 | ¿Qué pasa si se acaba la batería? | La app avisa días antes. La meta es ≥ 15 días con una carga, y la estimación da 24 con reportes cada 30 min. `[MEDIR en T5]` | §17 T5 |
| Q10 | ¿Quién es su competencia más peligrosa? | La llamada diaria, que cuesta cero. Competimos contra la culpa y el miedo, no contra otra app | §4 |

---

## 6. Prompts maestros de construcción

### 6.1 App conectada: 6 prompts en orden, cada uno con criterio de aprobación

> **Contexto común para pegar al inicio de cada prompt:**
> "Proyecto DistanciaCero. Una placa bajo el cojín de un sillón (ESP32-S3 + MPU6050 + SIM7600SA-H) manda cada 30 min un JSON por HTTPS a una Cloud Function de Firebase. Firestore guarda los datos. Un modelo z-score por hora decide si hay anomalía. Una app React Native (Expo) para el hijo o hija muestra el estado y recibe avisos por FCM y WhatsApp. Reglas: sin lenguaje médico; un dato viejo **nunca** se muestra como actual; ninguna clave va en el código de la app; todo en español de México."

**Prompt A1. Esquema de datos y contrato del dispositivo**
"Define el esquema de Firestore para `devices`, `windows` (una por cada 30 min: `device_id`, `window_start` ISO, `sit_events`, `stand_events`, `active_seconds`, `vbat_mv`, `rssi`, `fw_version`, `seq`), `model_runs`, `alerts` y `notifications`. Escribe las reglas de seguridad de Firestore: el hijo o hija solo lee sus dispositivos y nadie escribe desde la app. Incluye un ejemplo del JSON que manda el ESP32 y la validación del lado del servidor."
**Aprobado si:** un JSON válido se guarda y uno con campos faltantes recibe un 400; el emulador de reglas rechaza la lectura de un dispositivo ajeno.

**Prompt A2. Cloud Function de ingesta, idempotente**
"Escribe una Cloud Function HTTPS en Python que reciba el lote de ventanas del dispositivo (puede traer varias si estuvo sin señal), autentique con un token por dispositivo guardado en Secret Manager, inserte cada ventana con id `device_id + window_start` (idempotente) y responda con el último `seq` recibido."
**Aprobado si:** mandar el mismo lote dos veces no duplica documentos, y un lote con 20 ventanas atrasadas se guarda completo en < 5 s.

**Prompt A3. Detección z-score con hueco ≠ anomalía**
"Escribe la función que corre al guardar una ventana: calcula el z-score de `active_seconds` contra el baseline de la misma hora (media y desviación de los últimos 14 días). Marca **anomalía** solo si hay datos y z < −2.5 en 2 ventanas seguidas de la franja habitual. Si **faltan** ventanas, marca **sin_reporte**, nunca anomalía. Durante los primeros 10 días (RF-03) no genera alertas. Incluye un script para cargar un baseline simulado de 14 días y pruebas unitarias."
**Aprobado si:** en el dataset de 50 eventos, FP < 5 % y FN = 0 (RD-02), y borrar 3 ventanas da `sin_reporte`.

**Prompt A4. Notificaciones con respaldo**
"Al crear una `alert`, manda un push FCM y un mensaje de WhatsApp con plantilla aprobada (Twilio o Meta). Registra `t_decision`, `t_sent` y `t_delivered` por canal. Si FCM falla, reintenta por WhatsApp; si los dos fallan, reintenta cada 5 min durante una hora."
**Aprobado si:** con el token FCM revocado, el aviso llega por WhatsApp en ≤ 10 min (T1, RI-04).

**Prompt A5. App Expo: Estado, Historial y Onboarding**
"Crea la app en React Native con Expo y tres pantallas. **Estado**, con 5 estados visuales: cargando, todo bien, alerta, sin reportar desde HH:MM y error, cada uno con un texto distinto y sin lenguaje médico. **Historial** de 30 días en caché con AsyncStorage, que se ve sin conexión y con la marca 'Actualizado hace X'. **Onboarding** en 4 pasos: crear cuenta, escanear el QR de la placa, nombrar a la persona con un alias y probar el aviso. Usa listeners de Firestore, no polling."
**Aprobado si:** en modo avión se ve el historial con la marca de antigüedad; con el dispositivo apagado, el estado pasa a 'Sin reportar' y no a 'Todo bien'; una persona nueva completa el onboarding en ≤ 10 min (RI-03).

**Prompt A6. Resumen semanal con Haiku y plantilla de respaldo**
"Escribe una función programada (domingo a las 19:00, hora de CDMX) que arme las estadísticas de la semana, sin nombres ni ubicación, y llame a la API de Claude Haiku para redactar un resumen cálido de 3 frases en español, sin diagnósticos. Valida la salida contra un esquema JSON `{titulo, resumen, dias_normales}`. Si hay timeout (10 s), error o JSON inválido, usa una plantilla. Guarda `usage.input_tokens` y `usage.output_tokens` en `model_runs`."
**Aprobado si:** con una API key inválida llega el resumen de plantilla, y el promedio de tokens de 10 corridas queda registrado (§3.5).

### 6.2 Landing de lanzamiento (prompt para v0 o Framer)

```
Crea una landing de una sola página, primero para celular, en español de México, para "DistanciaCero".

Secciones, en este orden:
1. Headline: "Saber que tu mamá está bien, sin tener que llamarle."
   Subheadline: "Una placa bajo el cojín de su sillón aprende su rutina y te avisa solo si algo cambia. Ella no tiene que hacer nada."
2. Imagen principal: render del sillón con la placa (usa un placeholder con texto alternativo descriptivo).
3. Tres beneficios con ícono: "Sin botones ni cargadores diarios para ella" · "Sin wifi: funciona con red celular" · "Silencio cuando todo está bien; aviso por app y WhatsApp cuando no".
4. Cómo funciona en 3 pasos: la colocas · aprende 2 semanas · te avisa por excepción.
5. Evidencia: bloque "Lo que nos dijeron 3 hijas e hijos" con un placeholder [CITA REAL PENDIENTE]. No inventes testimonios.
6. Precio visible: "$4,490 equipo + $449/mes" con la leyenda [IVA: CONFIRMAR SI INCLUIDO] y "Cancela cuando quieras".
7. Aviso fijo: "Producto en validación. El pre-registro no cobra nada."
8. CTA ÚNICO, repetido arriba y abajo con el mismo texto: "Aparta tu lugar en el piloto". Abre un formulario con nombre, correo, ciudad y "¿quién vive solo?" (mamá, papá u otro), con una casilla de consentimiento que enlaza al aviso de privacidad.
9. Pie de página: aviso de privacidad, contacto, "No es un dispositivo médico".

Restricciones: no prometas duración de batería, detección de caídas ni uso médico. Contraste AA y botones de al menos 44 px.
Metadatos: <title>DistanciaCero · Tranquilidad sin llamar</title>; meta description de ≤ 155 caracteres; Open Graph og:title, og:description, og:type=website, og:image de 1200×630 y og:url; Twitter card summary_large_image; favicon.
Analítica: eventos "view", "click_cta" y "submit_preregistro", sin cookies de terceros.
```

**Métricas de la landing** (se llenan en la Memoria §19): visitas `[ ]` · clics en el CTA `[ ]` · pre-registros `[ ]` · conversión `[ ] %` · periodo `[ ]`.

### 6.3 Cinco errores comunes del vibe coding con hardware y cómo evitarlos

| # | Error | Cómo se evita |
|---|---|---|
| 1 | Pedirle a la IA "el firmware completo" y que invente pines, librerías o comandos AT que el módulo no tiene | Darle la hoja de datos y el pinout reales; probar cada comando AT a mano por serial antes de automatizarlo |
| 2 | Probar la app solo con datos simulados y descubrir el formato real el día de la demo | Fijar el contrato JSON (A1) primero y usar el mismo JSON en el simulador y en el ESP32 |
| 3 | Dejar claves de API en el código de la app o del firmware | Secret Manager en la nube; token por dispositivo; rotarlo si se filtra |
| 4 | No contemplar la falta de señal: el código asume que siempre hay red | Buffer en flash, reintentos con espera creciente e idempotencia (A2), con la prueba T2 obligatoria |
| 5 | Cambiar el firmware la noche anterior a la demo | Congelar el firmware después del último ensayo; solo correcciones críticas, con un commit etiquetado `demo-freeze` |

---

## 7. Ruta de cierre: dos semanas con responsables

| Rol | Responsable | Semana A | Semana B |
|---|---|---|---|
| **H**: hardware y firmware | `[NOMBRE]` | Pedir el SIM7600SA-H o un módulo equivalente con bandas de México; firmware con buffer en flash; T1, T2 y T3 | T4, T5 y arranque de T6 (día 7 a más tardar); correcciones críticas; congelar el firmware |
| **A**: app y nube | `[NOMBRE]` | Prompts A1 a A4 corriendo con datos simulados; dataset de RD-02 | A5 y A6; app conectada al dispositivo real; métricas de `notifications` |
| **N**: negocio, usuarios y landing | `[NOMBRE]` | Landing publicada (§6.2); aviso de privacidad y consentimiento (R3); cotizaciones de R2, R7 y R11 | 5 sesiones con usuarios (§2) y su síntesis; métricas de la landing |
| **D**: documentación, pitch y demo | `[NOMBRE]` | Memoria §1–§16 al día | Memoria §17–§22 y §0; 3 ensayos de la demo; video del pitch y video de respaldo; README y manual de usuario |

---

## 8. Preguntas de salida de la Semana 9

| Pregunta | Respuesta |
|---|---|
| ¿Cuál es la frontera más frágil y qué registro la vigila? | **F2** (módem, batería y red): por el cambio de módulo y la caída de VBAT. La vigila el log `VBAT_min, CREG, CSQ, http_code, tx_ms` en cada reporte |
| ¿Cuánto valen el CAC, el LTV y la relación LTV ÷ inversión? | CAC $1,000 (SUPUESTO), LTV $11,423 (ESTIMADO); 13.8 si paga el hardware, 2.21 en comodato y 3.72 en comodato con DFM |
| ¿Qué tema regulatorio puede impedir vender y qué fuente lo confirma? | La **homologación y las bandas (R1 y R2)**: la hoja de datos de SIMCom confirma que el E-H no cubre las bandas de México. Le sigue el **consentimiento (R3)**, por la LFPDPPP de 2025 |
| ¿Qué evidencia respalda cada parte del pitch? | Tabla P1–P9 de la §5.1. Hoy solo el precio de P1 está VERIFICADO; P4 y P5 son SUPUESTO o ESTIMADO; P3, P6, P7 y P8 siguen PENDIENTES |
| ¿Cuál es el camino principal de la demo y su Plan B? | Instalar → "Todo bien" → alerta provocada → corte de señal manejado → pre-registro. Cada tramo tiene un video de respaldo (§5.2) |