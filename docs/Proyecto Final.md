# DistanciaCero · Memoria del proyecto final

**Reposabrazos Centinela** · Proyectos 4 · Ingeniería Mecatrónica · IBERO Puebla
**Versión de la página:** v9.1 · 24/11/2026 · *se actualiza cada semana; historial en el Anexo B*

> **Leyenda de evidencia:** **MEDIDO** (dato propio con archivo) · **VERIFICADO** (fuente externa con fecha) · **ESTIMADO** (cálculo con supuestos declarados) · **SUPUESTO** (sin fuente) · **HIPÓTESIS** (afirmación sobre usuarios o mercado sin evidencia) · **POR VERIFICAR** (falta confirmar con autoridad o fabricante) · `[MEDIR: …]` (campo que se llena al correr la prueba) · `[URL_PENDIENTE: …]` (enlace que todavía no existe).
>
> **Plantilla de cada sección:** *Versión y fecha* · *Decisión* · *Evidencia* · *Qué cambió* · *Qué falta*. El detalle largo va en los Anexos A–F.

## Cómo evaluar esta página

**Ruta rápida de 10 minutos:** [§0 Resumen](#0-resumen-ejecutivo) → [§5 Propuesta de valor](#5-propuesta-de-valor-y-oferta) → [§13 Business Blueprint](#13-business-blueprint) → [§17 Integración y pruebas](#17-integracion-y-pruebas-del-sistema) → [§18 Pruebas con usuarios](#18-pruebas-con-usuarios) → [§21 Uso de IA](#21-uso-de-ia-en-el-proyecto) → [§20 Pitch y demo](#20-pitch-y-demo)

| Criterio de la rúbrica | Peso | Se muestra en | Secciones que lo respaldan |
|---|---|---|---|
| Producto físico funcionando con IA | **30 %** | Demo de 7 min | 7, 8, 9, 10, 11, 17, 21 |
| App conectada al producto | **25 %** | Demo de 7 min | 8, 12, 17, 18 |
| Landing de lanzamiento | **15 %** | Demo, tramo de compra | 19 |
| Pitch | **15 %** | Pitch de 3 min y retroalimentación | 0, 2, 5, 13, 15, 20 |
| Documentación técnica y BOM | **10 %** | Esta página | 3, 4, 6, 7, 8, 11, 13–16, 18 |
| Entregables semanales y proceso | **5 %** | Página y repositorio | 1, 10, 21, 22, Anexo B |

**Mapa para inversionistas:**

| Busca | Sección |
|---|---|
| Resumen | §0 |
| Problema | §2 y §3 |
| Solución | §5 y §9 |
| Mercado | §4 |
| Modelo de negocio | §13 |
| Operación | §11 |
| Finanzas | §14 y §15 |
| Legal | §16 |
| Tracción | §18 y §19 |
| Equipo | §1 |
| Riesgos | §22 |

---

## 0. Resumen ejecutivo

*Se redacta al final con lo que esté demostrado en §1–§22. Esta es la versión borrador de la Semana 9.*

- **Versión y fecha:** v9.1 · 24/11/2026 (borrador; la versión final se cierra en la Semana B)
- **Decisión:** presentar DistanciaCero como un **servicio de tranquilidad por excepción** para hijos e hijas de personas mayores que viven solas: hardware de $4,490 más suscripción de $449 al mes, validado primero con un piloto de 10 familias.
- **Evidencia:** 3 entrevistas con disposición de pago entre $450 y $700 al mes (§3); economía unitaria ESTIMADA (§15); pruebas T1–T6 `[PENDIENTES]` (§17).
- **Qué cambió:** el módulo pasa a SIM7600SA-H (bandas de México), el reporte pasa a cada 30 min (autonomía) y el consentimiento queda como un acto único (Semana 9).
- **Qué falta:** sistema integrado medido, 5 sesiones con usuarios, landing publicada y video del pitch.

| Campo | Contenido |
|---|---|
| Nombre y logo | **DistanciaCero** `[IMAGEN: logo]` |
| Propuesta de valor (≤ 25 palabras) | *"Para hijos lejos de su padre o madre mayor: la certeza diaria de que todo está bien, sin preguntar y sin que ella haga nada."* (25 palabras) |
| Imagen del producto | `[IMAGEN: render del sillón con la placa]` |
| Mercado alcanzable | SOM: **850 familias** en los años 1–2 (**SUPUESTO**, §4) |
| Precio | **$4,490** el equipo + **$449/mes** (IVA por confirmar, §16 R8) |
| Economía unitaria | Contribución de **$342.70/mes**; LTV ÷ inversión de **13.8** (paga el hardware) o **3.72** (comodato con DFM), **ESTIMADO** (§15) |
| Enlaces | Landing `[URL_PENDIENTE: landing]` · Video del pitch `[URL_PENDIENTE: video]` · Repositorio `[URL_PENDIENTE: GitHub]` · Demo de respaldo `[URL_PENDIENTE: video demo]` |
| Estado honesto (1 línea) | **Diseño completo y documentado. Integración y pruebas con usuarios en curso: todavía no hay mediciones del sistema completo ni clientes.** `[ACTUALIZAR al cierre]` |

---

# Parte I · Oportunidad y mercado

## 1. Equipo

- **Versión y fecha:** v1 · Semana 1 → v9.1 · 24/11/2026
- **Decisión:** el equipo se organiza en 4 roles de cierre: **H** hardware y firmware · **A** app y nube · **N** negocio, usuarios y landing · **D** documentación, pitch y demo.
- **Evidencia:** perfil de equipo de la Semana 1 `[ENLACE]`; bitácora de commits (Anexo B).
- **Qué cambió:** en la Semana 9 se pasó de roles generales a roles con entregables por semana.
- **Qué falta:** nombres en cada rol y la tabla "quién hizo qué" con enlaces a commits.

| Integrante | Rol | Aportaciones verificables (enlaces a commits o entregables) |
|---|---|---|
| Mauro David Sánchez Arenas | `[ROL]` | `[ ]` |
| Jesús Hernández | `[ROL]` | `[ ]` |
| `[NOMBRE]` | `[ROL]` | `[ ]` |
| `[NOMBRE]` | `[ROL]` | `[ ]` |

**Acuerdo de colaboración:** `[ENLACE: acuerdo firmado]` (horarios, canal de comunicación y regla de un commit por sesión).

## 2. Problema y oportunidad

- **Versión y fecha:** v2 · Semana 2 → v9.1 · 24/11/2026
- **Decisión:** atacar el miedo de los hijos e hijas a "la llamada", más que el riesgo médico de la persona mayor; el valor es la **certeza sin fricción**.
- **Evidencia:** mapa de dolores y ganancias de la Semana 2 `[ENLACE]`; 3 entrevistas (§3).
- **Qué cambió:** el problema se reformuló: no es la **distancia**, sino la **ausencia de una red humana local** (Semana 4).
- **Qué falta:** cuantificar la frecuencia del dolor (¿cuántas llamadas al día, cuánto tiempo?) en las sesiones de la §18.

| Elemento | Contenido |
|---|---|
| Enunciado de oportunidad | Los hijos e hijas que no tienen a alguien cerca de su padre o madre mayor hoy dependen de llamadas diarias que generan culpa y ansiedad; no existe una forma pasiva, sin wifi y sin pedirle nada a la persona mayor, de saber que su rutina sigue normal. |
| Criterios de selección | Dolor emocional fuerte, pago recurrente plausible y un hardware que el equipo puede construir |
| Alternativas descartadas | Bastón Centinela y Posavasos Guardián (§9); concepto deportivo para adultos mayores (Semana 2) |
| Evidencia de deseabilidad | Las 3 personas entrevistadas aceptan una suscripción (§3) |

## 3. Usuario y evidencia de campo

- **Versión y fecha:** v3 · Semanas 3–4 → v9.1 · 24/11/2026
- **Decisión:** el comprador es el **hijo o hija de 35 a 55 años sin red local de cuidado**; el usuario pasivo es su padre o madre de 65 años o más que vive solo.
- **Evidencia:** 3 entrevistas (Mariana, Lupita y Ricardo) en el Anexo D.
- **Qué cambió:** la capa psicográfica pasó de HIPÓTESIS a **CONFIRMADA CON MATIZ**: la preocupación depende de la red local, no de los kilómetros.
- **Qué falta:** las citas textuales de cada entrevista (hoy solo están los precios), entrevistar a personas mayores sobre su aceptación (brecha B2) y llegar a ≥ 5 entrevistas.

| Entrevista | Perfil | Precio "sin pensarlo" | Cita textual |
|---|---|---|---|
| Mariana | Hija, `[PERFIL]` | $450/mes | "`[CITA PENDIENTE]`" |
| Lupita | Hija, `[PERFIL]` | US$30–35/mes (≈ $550–650) | "`[CITA PENDIENTE]`" |
| Ricardo | Hijo con red local fuerte | $600–700/mes; a partir de $1,000 lo consulta con su hermana | "`[CITA PENDIENTE]`" |

| Capa del segmento | Definición | Estatus |
|---|---|---|
| Demográfica | Personas de 60 años o más que viven solas (INEGI) | **VERIFICADO**, solo para la persona mayor |
| Conductual | Existen el mercado y las comunidades de cuidadores | **VERIFICADO** (existencia) |
| Psicográfica | La angustia depende de no tener una red local | **CONFIRMADA CON MATIZ** (n = 3) |
| Comprador | Hijo o hija de 35 a 55 años que paga | **CONFIRMADA CON MATIZ** (n = 3) |

**Hipótesis críticas pendientes:** S1, alguien paga $4,490 por el hardware · S2, la persona mayor acepta la placa · S3, la rutina del sillón basta para detectar un cambio relevante.

## 4. Mercado y competencia

- **Versión y fecha:** v4 · Semana 4 → v9.1 · 24/11/2026
- **Decisión:** posicionarse como el único **pasivo, sin wifi y con objeto cotidiano**, frente a botones de pánico, cámaras y la llamada diaria.
- **Evidencia:** TAM, SAM y SOM sobre ENIGH 2024 (38.8 M hogares) y lista de competidores con precios (Anexo F).
- **Qué cambió:** se identificó a la **llamada diaria** (costo cero) como el sustituto más peligroso.
- **Qué falta:** reemplazar los filtros que propuso la IA (10.9 %, 17.5 %, 85 %, 60 % y 25 %) por fuentes; la disposición de pago (25 %) es el filtro más frágil.

| Nivel | Universo | Valor anual | Estatus |
|---|---|---|---|
| TAM | 94,350 personas | $509.5 M | **SUPUESTO** (filtros sin fuente) |
| SAM | 17,832 personas | $96.3 M | **SUPUESTO** |
| SOM (años 1–2) | 850 familias | $4.59 M | **SUPUESTO** |

| Tipo | Competidor | Precio | Fuente o estatus |
|---|---|---|---|
| Directo | Estoy Bien | $299/mes | Semana 4 `[ENLACE]` |
| Directo | Cuida Más | $800–928/mes, con call center | Semana 4 `[ENLACE]` |
| Directo | Care 60+ | Desde $6,588/año | Semana 4 `[ENLACE]` |
| Indirecto | Life360, Family Link, sensores wifi DIY | — | Sin precio |
| Sustituto | Llamada diaria y red informal | $0 | **El más peligroso** |
| Sustituto | Cuidador por horas | $9,000–27,000/mes | Semana 4 |

**Lienzo estratégico (4 acciones):**
- **Eliminar:** la interacción de la persona mayor.
- **Reducir:** el call center.
- **Incrementar:** el silencio cuando todo está bien.
- **Crear:** rutina aprendida en un objeto cotidiano, sin wifi.

`[IMAGEN: mapa de posicionamiento]`

## 5. Propuesta de valor y oferta

- **Versión y fecha:** v3 · Semana 4 → v9.1 · 24/11/2026
- **Decisión:** *"Para hijos que viven lejos de su padre o madre mayor, DistanciaCero reemplaza el miedo a 'la llamada' por la certeza diaria de que todo está bien, sin preguntar y sin culpa."*
- **Evidencia:** 3 entrevistas (§3); evaluación IDEO: Insightful ✅, Unique ✅, Targeted ✅ con matiz.
- **Qué cambió:** de la v1 (segmento definido por la distancia) a la v3 (red local), con variantes por perfil.
- **Qué falta:** probar el mensaje en la landing (§19): ¿lo explican con sus palabras en < 30 s?

| Elemento | Contenido |
|---|---|
| Oferta técnica | Placa de ~114 × 62 × 15 mm bajo el cojín, LTE sin wifi, avisos por excepción por app y WhatsApp, resumen semanal |
| Nivel de la pirámide de Bain | **Funcional** hoy (reduce ansiedad, ahorra tiempo); la meta es **Emocional** (tranquilidad). El nivel Transformador se descartó por prematuro |
| Error principal de la v1 | Definir el segmento por la distancia y no por la red humana local |

## 6. Propiedad intelectual, marca y vigilancia

- **Versión y fecha:** v1 · Semana 3 → v9.1 · 24/11/2026
- **Decisión:** usar la marca **DistanciaCero** (ganó frente a SilencioActivo) con registro en las clases 9 y 42, y el dominio distanciacero.mx.
- **Evidencia:** análisis de la patente MX 351729 B (detección de caídas en piso): veredicto **"fuera"**, solo con la reivindicación 1.
- **Qué cambió:** se agregó una variante de handle por la colisión con una banda argentina llamada "Distancia Cero".
- **Qué falta:** la búsqueda fonética en MARCANET, porque **no se ha corrido**. La libertad de operación es "alta", pero sobre una búsqueda parcial: falta la ruta IMPI → LATIPAT → Lens.org con 3 a 5 patentes y los códigos IPC G08B21/04xx y A61B5/1118.

| Tema | Estatus |
|---|---|
| Búsqueda fonética IMPI, clases 9 y 42 | **POR VERIFICAR** |
| Libertad de operación | Alta, con **búsqueda parcial** |
| Dominio | `[POR VERIFICAR: disponibilidad y compra]` |
| Estrategia de protección | Marca y secreto industrial (parámetros del modelo); patente no prioritaria por ahora |

---

# Parte II · Producto

## 7. Especificación de producto (PDS)

- **Versión y fecha:** v1 · Semana 5 → v9.1 · 24/11/2026
- **Decisión:** 16 requisitos en 4 categorías, cada uno con su prueba. En la Semana 9 se ajustan RD-01 (batería), RR-02 (consentimiento) y la interpretación de RF-02.
- **Evidencia:** tabla del PDS (Semana 5); pruebas en la §17.
- **Qué cambió:**
  - RD-01: la batería pasa de una 18650 a una LiPo plana de 1.92 Ah.
  - RR-02: dice "sin acciones **recurrentes**"; el consentimiento único está permitido.
  - RF-02: se mide desde que el backend decide; con ventanas de 30 min, la latencia de evento a aviso puede llegar a ~40 min.
- **Qué falta:** ningún requisito está **MEDIDO** todavía.

| ID | Requisito | Meta | Verificación | Estatus |
|---|---|---|---|---|
| RF-01 | Detectar desviaciones de la rutina individual | Alerta solo ante desviación propia | Dataset de 14 días | `[PENDIENTE]` |
| RF-02 | Silencio si todo es normal y aviso tras la decisión | ≤ 10 min | T4, 10 corridas | `[PENDIENTE]` |
| RF-03 | Baseline sin alertas | 10–14 días | Logs | `[PENDIENTE]`; en la demo es precargado |
| RF-04 | Historial de 30 días sin conexión | 30 días en caché | Modo avión | `[PENDIENTE]` |
| RD-01 | Autonomía | ≥ 15 días | T5 | ESTIMADO en 24.2 días (escenario C) · `[MEDIR]` |
| RD-02 | Error del algoritmo | FP < 5 %, FN < 2 % | 50 eventos | `[MEDIR]` |
| RD-03 | Transmisión | ≤ 30 s | T4, 20 envíos | `[MEDIR]` |
| RD-04 | Disponibilidad del backend | ≥ 99 % | Uptime (T6) | `[MEDIR]` |
| RI-01 | Estado entendible | < 10 s | §18, tarea 2 | `[MEDIR]` |
| RI-02 | Solo red celular, con TLS | TLS | Inspección | `[PENDIENTE]` |
| RI-03 | Onboarding sin la persona mayor | ≤ 10 min | T3 y §18 | `[MEDIR]` |
| RI-04 | Dos canales de aviso | ≥ 2 | T1 | `[MEDIR]` |
| RR-01 | Costo recurrente | $300–600/mes | Modelo | Cumple ($449) |
| RR-02 | Sin acciones **recurrentes** de la persona mayor | 0 | Revisión de diseño | Cumple en diseño; consentimiento único en la instalación |
| RR-03 | Sin audio ni video | 0 campos | Auditoría del esquema | Cumple en diseño (A1) |
| RR-04 | PCB fabricable en JLCPCB | Sin BGA ni pitch < 0.5 mm | DRC | **POR VERIFICAR** con el módulo LCC |

## 8. Arquitectura del sistema

- **Versión y fecha:** v1 · Semana 5 → v9.1 · 24/11/2026
- **Decisión:** arquitectura **híbrida**. El edge agrega los datos y los guarda si no hay señal; la nube aprende la rutina y decide; HTTPS en lugar de MQTT para ahorrar batería.
- **Evidencia:** diagrama anotado `[IMAGEN: diagrama v9]`; justificación de la Semana 5.
- **Qué cambió respecto a la Semana 5:** se eliminó el PIR (no cabía y no detecta a través del cojín), el módulo pasa del E-H al SA-H, la batería de la 18650 a la LiPo de 1.92 Ah, y el periodo de reporte de 15–30 min a 30 min.
- **Qué falta:** confirmar la detección solo con el acelerómetro (HIPÓTESIS S3, prueba F1).

| Tramo | Protocolo | Decisión |
|---|---|---|
| MPU6050 → ESP32-S3 | I²C e interrupción de movimiento | El ESP32 duerme y despierta con cada movimiento |
| ESP32-S3 → SIM7600SA-H | UART y comandos AT | Módem apagado entre reportes |
| Dispositivo → Firebase | HTTPS POST con JSON sobre TLS, cada 30 min | Ingesta idempotente con buffer en flash |
| Firestore → Cloud Function | Trigger al escribir | z-score por hora; un hueco es "sin reporte" |
| Nube → app | Listener de Firestore, FCM y WhatsApp | Dos canales |
| Nube → Claude Haiku | HTTPS | Solo el resumen semanal; hay plantilla si falla |

## 9. Diseño del producto

- **Versión y fecha:** v1 · Semana 6 → v9.1 · 24/11/2026
- **Decisión:** se eligió el **Reposabrazos Centinela**: una placa bajo el cojín, sin LED ni botones.
- **Evidencia:** matriz de Pugh con deseabilidad 50 % y factibilidad 50 %, con el bastón como referencia: **Sillón +80**, Posavasos +50.
- **Qué cambió:** de 90 × 60 × 15 mm en ABS con silicona (Semana 6) a carcasa de PETG en 2 piezas con snap-fit, en dos variantes (Semana 8).
- **Qué falta:** prototipo impreso y prueba de cierre de 20 ciclos; confirmar si el producto supone un solo sillón de uso constante (HIPÓTESIS).

| Elemento | Contenido |
|---|---|
| Principio rector | "Silencio = tranquilidad". Además: affordances, contour bias, constraints y consistencia |
| Tabla morfológica | 7 parámetros × 3 variantes (Semana 6) `[ENLACE]` |
| Tres conceptos | Bastón Centinela · **Reposabrazos Centinela** · Posavasos Guardián |
| Render y boceto con cotas | `[IMAGEN: render]` · `[IMAGEN: boceto con cotas]` |

## 10. Prototipos y evidencia

- **Versión y fecha:** v1 · Semana 8 → v9.1 · 24/11/2026
- **Decisión:** cada prototipo responde **una** pregunta; el prototipo de función (sensado) tiene la prioridad más alta.
- **Evidencia:** landing estática, carcasa en 3D con 4 archivos STL, prototipo de la app en Figma Make (Semana 6).
- **Qué cambió:** el primer acomodo de la carcasa chocaba (el USB-C quedaba sobre el ESP32); se reacomodaron los componentes.
- **Qué falta:** el prototipo de función, el impreso de la carcasa y la hoja de observación de la landing (está vacía).

| Prototipo | Pregunta | Tipo | Qué se construyó | Evidencia | Aprendizaje → cambio |
|---|---|---|---|---|---|
| Landing estática | ¿El hijo o hija explica el producto y decide con el precio? | Negocio, baja | HTML de un archivo | **PENDIENTE** (hoja vacía) | — |
| Carcasa en 2 variantes | ¿Caben el PCB, el módulo y la batería en una placa que cierra sin herramientas? | Forma, alta (digital) | Blender, planos y 4 STL | Modelo 3D | Se reacomodaron componentes; el JST se movió 1 mm |
| App en Figma Make | ¿Los estados se entienden? | Interfaz, media | Pantallas con datos de ejemplo | `[URL_PENDIENTE: Figma]` | — |
| **Función (sensado)** | ¿El acelerómetro bajo el cojín distingue sentarse de un golpe? | Función, alta | `[POR CONSTRUIR]` | `[MEDIR: F1]` | — |

`[IMAGEN: línea de tiempo con fotos]`

## 11. Manufactura, DFM y circularidad

- **Versión y fecha:** v1 · Semana 5 → v3 · Semana 8 → v9.1 · 24/11/2026
- **Decisión:** módulo celular en formato **LCC soldado al PCB propio** y carcasa PETG de 2 piezas; volumen de **10 unidades** para el piloto.
- **Evidencia:** costo unitario de $4,158 → **$2,072** con DFM (BOM × 1.40); el módulo explica el 87 % del ahorro.
- **Qué cambió:** el **E-H se reemplaza por el SA-H** (Semana 9), así que la línea del módulo y el ahorro DFM quedan **POR RECOTIZAR**.
- **Qué falta:** cotizar el SA-H en LCC; cotizar las 5 líneas que siguen estimadas; tiempo de ensamble medido.

| Componente | Especificación | Precio unitario | Proveedor | Lead time | Estatus |
|---|---|---|---|---|---|
| Módulo celular | Antes SIM7600E-H LCC ($805) → ahora **SIM7600SA-H LCC** | `[COTIZAR]` | `[ ]` | `[ ]` | **POR VERIFICAR** |
| ESP32-S3 | Módulo, 8 MB flash | ~$120 | `[ ]` | `[ ]` | ESTIMADO |
| MPU6050 (GY-521) | Acelerómetro y giroscopio | ~$60 | `[ ]` | `[ ]` | ESTIMADO |
| LiPo 1.92 Ah | 52 × 34.5 × 10.8 mm, con documentos UN 38.3 | `[ ]` | `[ ]` | `[ ]` | ESTIMADO |
| PCB + PCBA | 2 capas | ~$250 | JLCPCB | `[ ]` | ESTIMADO |
| Carcasa | PETG, 2 piezas, FDM | ~$70 | Propia | — | ESTIMADO |

**Proceso de manufactura:** PCB y PCBA en JLCPCB → carcasa impresa en FDM → ensamble manual (~9 min por unidad, ESTIMADO) → prueba de humo con reporte al backend.

**Circularidad (4 preguntas):**

| Pregunta | Respuesta | Estatus |
|---|---|---|
| ¿Los componentes son accesibles? | Snap-fit sin pegamento ni tornillos | Cumple |
| ¿Los módulos se reemplazan? | Batería con JST y sensor en header; ESP32 y módem soldados | Parcial |
| ¿Los materiales se identifican? | PETG con marcado en relieve; falta el código de reciclaje | Parcial |
| ¿Se actualiza sin reemplazarse? | Por USB-C; falta la actualización remota (partición OTA) | Parcial |

**Cómo reproducir una unidad:** `[ENLACE: Anexo C, paso a paso]`.

## 12. App conectada

- **Versión y fecha:** v1 · Semana 6 (wireframes) → v9.1 · 24/11/2026
- **Decisión:** app en React Native con Expo, con 3 pantallas (Estado, Historial y Onboarding) y 5 estados; nunca muestra un dato viejo como actual.
- **Evidencia:** wireframes y Figma Make (Semana 6); prompts A1–A6 de construcción (Actividad 9, §6.1).
- **Qué cambió:** se agregó el estado **"Sin reportar desde HH:MM"**, que es distinto de "Alerta" (frontera F3).
- **Qué falta:** la app construida y conectada, las capturas, el README y el enlace al repositorio.

| Elemento | Contenido |
|---|---|
| Flujo de usuario | Onboarding (cuenta → QR → alias → aviso de prueba) → Estado → Historial → Alerta → acción (llamar) |
| Estados | Cargando · Todo bien · Alerta · Sin reportar · Error |
| Protocolo y datos | Listener de Firestore; ventana JSON `{device_id, window_start, sit_events, stand_events, active_seconds, vbat_mv, rssi, seq}` |
| Capturas | `[IMAGEN ×5]` |
| Cómo correrla | `[README: npx expo start …]` |
| Repositorio | `[URL_PENDIENTE: GitHub]` · commits: `[ ]` |
| Limitaciones conocidas | `[ ]` |

---

# Parte III · Negocio

## 13. Business Blueprint

- **Versión y fecha:** v1 · Semana 7 → v9.1 · 24/11/2026
- **Decisión:** **hardware de venta única más suscripción mensual**; comodato como plan B si el precio del hardware no se acepta.
- **Evidencia:** benchmarks de Medical Guardian, Ring y CarePredict (Semana 7).
- **Qué cambió:** se agregó el escenario de comodato con DFM (Semana 9).
- **Qué falta:** las 8 cajas no quedaron documentadas en la Semana 7; la tabla siguiente es el borrador que hay que validar.

| Caja | Contenido | Sección |
|---|---|---|
| Cliente | Hijo o hija de 35 a 55 años sin red local | §3 |
| Propuesta de valor | Certeza diaria sin preguntar | §5 |
| Canales | Landing, referidos y comunidades de cuidadores | §15 |
| Relación | Aviso por excepción y resumen semanal | §12 |
| Ingresos | $4,490 + $449/mes | §14 |
| Recursos clave | Hardware, modelo de rutina y datos | §8, §11 |
| Actividades clave | Fabricación, instalación guiada y soporte | §11 |
| Costos | BOM, SIM, nube, soporte y CAC | §14 |

| Benchmark | Modelo | Precio | Fuente |
|---|---|---|---|
| Medical Guardian | Equipo + cuota (mínimo 3 meses) | US$149.95–199.95 + US$31.95–49.95/mes | seniorliving.org, 25/08/2026 |
| Ring | Hardware + planes en capas | US$4.99, 9.99 y 19.99/mes | security.org, 28/09/2026 |
| CarePredict | Hardware + servicio (B2B) | Sin precio público | Comunicado del 30/03/2022 |

## 14. Costos, precio y viabilidad financiera

- **Versión y fecha:** v1 · Semana 7 → v9.1 · 24/11/2026
- **Decisión:** $4,490 + $449/mes; desarrollo estimado en **5 ciclos ($71,540)**; tasa de descuento del 15 % anual.
- **Evidencia:** modelo financiero en el Anexo E (fórmulas visibles).
- **Qué cambió:** el costo unitario estimado bajó de $4,158 a $2,072 (DFM); el costo de la IA bajó a ~$0.03 por usuario al mes (Haiku 5.5, ESTIMADO).
- **Qué falta:** el precio basado en valor; el costo **medido** de la IA; si los precios incluyen IVA (§16, R8); el VPN con el módulo SA-H.

| Concepto | Valor | Estatus |
|---|---|---|
| Costo de desarrollo (mínimo / promedio / máximo) | $42,924 / **$71,540** / $114,464 (3, 5 y 8 ciclos de $14,308) | ESTIMADO |
| Cost-plus del 40 % | $5,821 por el hardware | ESTIMADO |
| Precio basado en valor | `[PENDIENTE]`; las entrevistas sugieren $450–700/mes | HIPÓTESIS |
| Equilibrio del desarrollo | 9.7 unidades (24 meses, sin cancelación) · ≈ 15 unidades (24 meses, 3 % de cancelación) | ESTIMADO |
| Flujo a 12 meses | −$67,499; pico de −$73,001 en el mes 6; recuperación en el mes 21 | ESTIMADO |
| VPN (15 % anual) | 12 meses: −$68,041 · **24 meses: +$46,404** · con tipo de cambio FIX y 3 % de cancelación: −$15,459 | ESTIMADO |
| Costo de la IA por usuario al mes | ~$0.03 (cota usada en el modelo: $0.14) | ESTIMADO · `[MEDIR]` |

**Tablas CREAR y DISTRIBUIR:** 17 costos clasificados, 5 de ellos determinantes (D) → Anexo E.

## 15. Go-to-market y economía unitaria

- **Versión y fecha:** v1 · Semana 9 · 24/11/2026
- **Decisión:** cliente #1 = hijo o hija sin red local, en Puebla y CDMX. Canal: landing + referidos. Primer paso: **piloto de 10 familias en comodato**.
- **Evidencia:** Actividad 9, §3 (aritmética completa).
- **Qué cambió:** se agregaron el análisis de sensibilidad, el efecto del IVA y la meta de clientes para recuperar el desarrollo.
- **Qué falta:** el CAC y la cancelación reales (son SUPUESTOS); medir la conversión de la landing.

| Métrica | Valor | Estatus |
|---|---|---|
| CAC | $1,000 | SUPUESTO |
| Contribución mensual | $342.70 | ESTIMADO |
| Cancelación / vida media | 3 % / 33.3 meses | SUPUESTO |
| LTV | $11,423 | ESTIMADO |
| LTV ÷ inversión · payback | **13.8 · 2.4 meses** (paga el HW) · 2.21 · 15.1 (comodato) · **3.72 · 9.0** (comodato con DFM) | ESTIMADO |
| Lo que más mueve el resultado (±25 %) | **Precio de la suscripción** y, en segundo lugar, la cancelación | ESTIMADO |
| Clientes para recuperar los $71,540 | ≈ 15 (costo actual) · ≈ 10 (DFM) | ESTIMADO |

**Plan del piloto:** 10 familias · 4 semanas · comodato · consentimiento firmado. **Éxito si:** ≥ 6 de 10 aceptan pagar $449/mes al terminar, o ≥ 3 aceptan comprar el equipo. `[FECHAS]`

## 16. Regulación y legal

- **Versión y fecha:** v1 · Semana 9 · 24/11/2026
- **Decisión:** piloto de ≤ 10 unidades **sin venta** mientras se resuelven la homologación, la privacidad y las NOM. El producto se comunica como "**no es un dispositivo médico**".
- **Evidencia:** checklist de 14 temas con fuentes (Actividad 9, §4).
- **Qué cambió:** se descubrió que el **E-H no cubre las bandas de México** y que la rutina podría contar como un **dato sensible**.
- **Qué falta:** todos los puntos **POR VERIFICAR**, en particular R1 (CRT), R3 (consentimiento por escrito), R7 (UN 38.3) y R8 (precio con IVA).

| Tema | Estatus | Tema | Estatus |
|---|---|---|---|
| R1 Homologación (CRT) | POR VERIFICAR | R8 Precio con IVA (LFPC) | POR VERIFICAR |
| R2 Bandas (SA-H) | **VERIFICADO** en la hoja de datos | R9 Términos de la suscripción | POR VERIFICAR |
| R3 Datos personales (LFPDPPP 2025) | Ley VERIFICADA; alcance POR VERIFICAR | R10 Licencias de software | POR VERIFICAR |
| R4 Transferencia internacional | POR VERIFICAR | R11 Términos de Anthropic y WhatsApp | POR VERIFICAR |
| R5 No es dispositivo médico (COFEPRIS) | POR VERIFICAR | R12 Economía circular | Ley VERIFICADA; obligación POR VERIFICAR |
| R6 NOM-001-SCFI | POR VERIFICAR | R13 Marca IMPI | POR VERIFICAR |
| R7 Batería (IEC 62133-2, UN 38.3) | POR VERIFICAR | R14 Exportación | No aplica |

**Aviso de privacidad y consentimiento:** `[ENLACE: aviso de privacidad]` · `[ENLACE: formato de consentimiento de la persona mayor]`.

---

# Parte IV · Validación y lanzamiento

## 17. Integración y pruebas del sistema

- **Versión y fecha:** v1 · Semana 9 · 24/11/2026
- **Decisión:** 4 fronteras con registros y 6 pruebas ordenadas de la más barata a la más cara; RD-02 se prueba aparte con un dataset.
- **Evidencia:** `[PENDIENTE: CSV y videos de T1–T6 en el Anexo D]`.
- **Qué cambió:** se agregaron la degradación sin red y sin IA y la regla "hueco ≠ anomalía".
- **Qué falta:** **todas las mediciones**. La frontera más frágil es la **F2** (módem, batería y red).

| Prueba | Criterio | Resultado | Evidencia |
|---|---|---|---|
| T1 Falla de canal y de IA | Aviso por el otro canal en ≤ 10 min; plantilla si falla Haiku | `[MEDIR]` | `[ ]` |
| T2 Desconexión de 10 min | 0 reportes perdidos; recuperación en ≤ 60 s | `[MEDIR]` | `[ ]` |
| T3 Instalación sin ayuda | ≤ 10 min | `[MEDIR]` | `[ ]` |
| T4 Latencia | ≤ 30 s (20/20) · ≤ 10 min (10/10) | `[MEDIR]` | `[ ]` |
| T5 Autonomía | ≤ 4.27 mA, que da ≥ 15 días | `[MEDIR]` (ESTIMADO: 2.64 mA, 24.2 días) | `[ ]` |
| T6 Operación de 48 h | 0 reinicios, 0 reportes perdidos, ≥ 99 % de disponibilidad | `[MEDIR]` | `[ ]` |
| RD-02 (dataset) | FP < 5 %, FN = 0 de 25 | `[MEDIR]` | `[ ]` |

**Bugs y diagnóstico:** `[tabla: síntoma → hipótesis → prueba → causa → corrección → commit]`
**Problemas conocidos:** `[ ]`
**Lista "listo para la demo":** ☐ T1–T6 aprobadas · ☐ firmware congelado (`demo-freeze`) · ☐ 3 ensayos · ☐ video de respaldo · ☐ hotspot de reserva · ☐ baseline precargado documentado

## 18. Pruebas con usuarios

- **Versión y fecha:** v1 · Semana 9 · 24/11/2026
- **Decisión:** 5 sesiones de 30 min (3 del segmento y 2 de otros equipos) con 3 tareas: instalar, interpretar estados y encontrar el precio. A las personas mayores solo se les consulta la aceptación.
- **Evidencia:** protocolo y hoja de observación (Actividad 9, §2); datos crudos en el Anexo D.
- **Qué cambió:** la señal de negocio se separa en opinión y compromiso (pre-registro < referido < fecha de piloto < anticipo).
- **Qué falta:** **correr las 5 sesiones**.

| Tarea | Éxito sin ayuda (n/5) | Tiempo mediano | SEQ promedio |
|---|---|---|---|
| Instalar y vincular | `[ ]` | `[ ]` | `[ ]` |
| Interpretar estados | `[ ]` | `[ ]` | `[ ]` |
| Encontrar el precio y apartar | `[ ]` | `[ ]` | `[ ]` |

**Hallazgos** (crítico, mayor y menor, con n y cita): `[ ]`
**Cambios realizados:** `[ ]`
**Señal de negocio:** `[ ] pre-registros · [ ] referidos · [ ] fechas de piloto · [ ] anticipos`

## 19. Landing de lanzamiento

- **Versión y fecha:** v1 · Semana 8 (HTML estático) → v9.1 · 24/11/2026
- **Decisión:** una sola página primero para celular, con **un solo CTA** ("Aparta tu lugar en el piloto"), el precio visible y el aviso "producto en validación".
- **Evidencia:** prompt de construcción (Actividad 9, §6.2).
- **Qué cambió:** se agregaron el aviso de privacidad, la leyenda "no es un dispositivo médico" y la nota sobre el IVA.
- **Qué falta:** publicarla y medir.

| Elemento obligatorio | Estado |
|---|---|
| URL publicada | `[URL_PENDIENTE: landing]` |
| Headline | "Saber que tu mamá está bien, sin tener que llamarle." |
| Imagen | `[render]` |
| Beneficios (3) | Sin botones · Sin wifi · Silencio cuando todo está bien |
| Precio visible | $4,490 + $449/mes `[IVA]` |
| CTA único | "Aparta tu lugar en el piloto" |
| Metadatos y Open Graph | `<title>`, description ≤ 155 caracteres, og:title, og:description, og:image de 1200×630, og:url |
| Métricas | Visitas `[ ]` · clics en el CTA `[ ]` · pre-registros `[ ]` · conversión `[ ] %` |
| Prompt utilizado | Actividad 9, §6.2 |

## 20. Pitch y demo

- **Versión y fecha:** v1 · Semana 9 · 24/11/2026
- **Decisión:** pitch de **337 palabras (~2:36)** que abre con Mariana y cierra con "el silencio significa tranquilidad"; demo en 6 tramos con Plan B, declarando el **baseline precargado**.
- **Evidencia:** guiones completos (Actividad 9, §5).
- **Qué cambió:** las afirmaciones sin evidencia se marcaron P1–P9; el tramo de tracción dice con honestidad "todavía no tenemos clientes".
- **Qué falta:** el video del pitch, 3 ensayos de la demo y el video de respaldo.

| Entregable | Enlace |
|---|---|
| Video del pitch (3 min) | `[URL_PENDIENTE]` |
| Guion del pitch | Actividad 9, §5.1 |
| Guion de la demo (7 min) con Plan B | Actividad 9, §5.2 |
| Video de respaldo de la demo | `[URL_PENDIENTE]` |
| Preguntas difíciles (Q1–Q10) | Actividad 9, §5.3 |

---

# Parte V · Cierre

## 21. Uso de IA en el proyecto

- **Versión y fecha:** v1 · Semana 9 · 24/11/2026
- **Decisión:** en el producto, la IA estadística (z-score por persona y por hora) **decide**, y Claude Haiku **solo redacta** el resumen semanal. Si la IA falla, hay plantilla y las alertas no dependen de ella.
- **Evidencia:** costo ESTIMADO de ~$0.03 por usuario al mes; `[MEDIR: tokens promedio de 10 resúmenes]`.
- **Qué cambió:** se registran los tokens de cada llamada en `model_runs`.
- **Qué falta:** medir FP y FN, medir los tokens y documentar el error de la IA en el proceso.

**IA en el proceso: 5 prompts que cambiaron el proyecto**

| # | Qué se pidió | Qué respondió la IA | Qué corrigió el equipo |
|---|---|---|---|
| 1 | Llenar el checklist regulatorio (Semana 9) | Comparó bandas: el **E-H no cubre las de México** | Se cambió el módulo al SA-H |
| 2 | Calcular la autonomía (Semana 9) | 13.8 días si se reporta cada 15 min | Reporte cada 30 min con el módem apagado |
| 3 | Estimar el TAM (Semana 4) | Propuso filtros sin fuente | **Error de la IA:** los filtros se marcaron como SUPUESTO; falta reemplazarlos con fuentes |
| 4 | Revisar DFM (Semana 8) | Propuso el módulo en LCC | Ahorro estimado de $1,295 en el módulo |
| 5 | Matriz de Pugh (Semana 6) | Eligió el concepto del sillón | Se detectó que la 18650 no cabe y se cambió a LiPo plana |

**IA en el producto**

| Qué hace | Dónde corre | Entrada | Salida | Costo por usuario | Si falla | ¿Por qué sería peor sin IA? |
|---|---|---|---|---|---|---|
| z-score por hora contra la rutina propia | Cloud Function | Ventanas de 30 min | anomalía / normal / sin reporte | ≈ $0 | Si hay hueco, sale "sin reporte" y no alerta | Un umbral fijo daría falsas alarmas a quien es menos activo y no vería cambios en quien es muy activo |
| Resumen semanal (Claude Haiku) | API de Anthropic | Estadísticas sin datos personales | 3 frases en JSON | ~$0.03/mes (ESTIMADO) | Plantilla | La plantilla funciona, pero se lee fría; es un valor emocional, no crítico |

## 22. Reflexión y siguientes pasos

- **Versión y fecha:** v1 · Semana 9 · 24/11/2026
- **Decisión:** el siguiente paso es un **piloto de 90 días con 10 familias**, que solo arranca con el módulo SA-H y el consentimiento firmado.
- **Evidencia:** §15–§17.
- **Qué cambió:** se pasó de "construir el sistema completo" a "probar primero las tres hipótesis que deciden el negocio".
- **Qué falta:** el aprendizaje firmado por cada integrante.

| Integrante | Aprendizaje clave (un párrafo) | Firma |
|---|---|---|
| Andrea Solano López | `[ ]` | `[ ]` |
| Jesús Hernández | `[ ]` | `[ ]` |


**Qué haríamos diferente:** `[ ]`

| Hipótesis sin verificar | Cómo se prueba |
|---|---|
| S1: alguien paga $4,490 | Anticipo reembolsable en la landing o en el piloto |
| S2: la persona mayor acepta la placa | Consentimiento en las instalaciones del piloto (tasa de aceptación) |
| S3: el sillón basta para detectar el cambio | RD-02 con datos reales del piloto |

| Plan de 90 días | Acción |
|---|---|
| Días 1–30 | SA-H, 10 unidades, aviso de privacidad, CRT |
| Días 31–60 | Piloto en comodato |
| Días 61–90 | Conversión a pago, decisión de precio y búsqueda de fondos (convocatoria `[ ]`) |

| Riesgo principal | Mitigación |
|---|---|
| Nadie paga el precio | Comodato con DFM |
| Homologación del producto | Módulo certificado y consulta a la CRT |
| Rechazo de la persona mayor | Consentimiento y opción de pausa |
| Autonomía | Reporte cada 30 min o cada 60 min |

---

## Anexos

| Anexo | Contenido | Enlace |
|---|---|---|
| **A** | BOM completa con cotizaciones (proveedor, fecha y captura) | `[URL_PENDIENTE: hoja BOM]` |
| **B** | Repositorio, README, bitácora de commits y entregables por semana; tabla de licencias (R10) | `[URL_PENDIENTE: GitHub]` |
| **C** | Archivos de diseño: CAD y STL de la carcasa, esquemático y PCB, firmware | `[URL_PENDIENTE: carpeta]` |
| **D** | Datos crudos de entrevistas, sesiones y pruebas T1–T6 (con consentimiento; anonimizados) | `[URL_PENDIENTE: carpeta]` |
| **E** | Modelo financiero con fórmulas visibles (CREAR/DISTRIBUIR, flujo, VPN, economía unitaria y sensibilidad) | `[URL_PENDIENTE: hoja]` |
| **F** | Bibliografía y fuentes (INEGI, ENIGH 2024, hojas de datos de SIMCom y Espressif, LFPDPPP 2025, LFPC, Ley General de Economía Circular, precios de Anthropic y benchmarks) | `[URL_PENDIENTE]` |

**Historial de versiones:**

| Versión | Semana | Fecha | Secciones actualizadas |
|---|---|---|---|
| v1–v8 | 1–8 | `[ ]` | 1–14 (por entregable semanal) |
| v9.1 | 9 | 24/11/2026 | 15–20 y ajustes a 7, 8, 11, 14 y 21 |
| v10 | Final | `[ ]` | 0, 12, 17, 18, 19, 21, 22 y Anexos |