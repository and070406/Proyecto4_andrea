# Proyecto final: DistanciaCero

<div style="display:flex;align-items:center;gap:14px;margin:6px 0 18px">
<img src="https://jesushernandez2005.github.io/Proyecto4/DistanciaCero/logo/logo-simbolo.png" alt="Logotipo de DistanciaCero" style="height:52px;width:auto">
<div><strong style="font-size:1.3rem">DistanciaCero</strong><br><span style="color:#555">Jesús León Hernández Martínez y Andrea Solano López · Proyectos 4 · IBERO Puebla · 2026</span></div>
</div>

Esta página es la memoria del proyecto final. Cada sección sigue la misma plantilla (**versión y fecha · decisión · evidencia · qué cambió · qué falta**). Lo que no tiene evidencia dice **HIPÓTESIS**; cada número tiene fuente o dice **SUPUESTO**. El detalle vive en las [actividades semanales](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-01/) y en los [anexos](#anexos).

| Entregable | Enlace |
|---|---|
| Landing (los tres productos) | [landing/](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/landing/) |
| App de la familia (demo y dispositivo real) | [jesushernandez2005.github.io/Proyecto4/app/](https://jesushernandez2005.github.io/Proyecto4/app/) |
| Excel de costos y cálculos (fórmulas visibles) | [DistanciaCero_costos_y_calculos.xlsx](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx) |
| Repositorio | [github.com/jesushernandez2005/Proyecto4](https://github.com/jesushernandez2005/Proyecto4) |
| Guion de pitch y demo | [PDF](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/DistanciaCero_guion_pitch_y_demo.pdf) |
| Anexos A–F | [anexos.md](#anexos) |

---

## 0. Resumen ejecutivo

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (se escribe al final, regla 7) |
| **Decisión** | Lanzar un piloto de 10 familias en Puebla con los tres objetos (sillón, bastón y portavasos) y un prototipo WiFi. |
| **Evidencia** | Secciones 3, 4, 14 y 15; [Excel](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx), hojas Resumen y Landing. |
| **Qué cambió** | Hardware: sin PCB y sin módulo celular en el prototipo. Pasamos de un objeto a tres. Precio del equipo: $3,990. |
| **Qué falta** | Videos del pitch y de la demo; probar el flujo completo; sesiones con usuarios. |

<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:8px;margin:10px 0">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/render-sillon.jpg" alt="Render del sensor bajo el cojín de un sillón" style="width:100%;border-radius:6px">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/render-baston.jpg" alt="Render del bastón con sensor" style="width:100%;border-radius:6px">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/render-portavasos.jpg" alt="Render del portavasos con sensor" style="width:100%;border-radius:6px">
</div>
*Renders conceptuales de la semana 6, no fotos del prototipo.*

**Propuesta de valor (23 palabras):** DistanciaCero le da al hijo que vive lejos la certeza diaria de que su mamá o papá está bien, sin preguntar, sin culpa.

| Mercado alcanzable (SOM) | Precio | Economía unitaria |
|---|---|---|
| **850 familias** en años 1–2 · $4.59 M MXN al año ([sección 4](#4-mercado-y-competencia)) | **$3,990** el equipo + **$449** al mes | **$343** de contribución al mes; se recupera la inversión por familia ($1,312) en **3.8 meses** (CAC de $1,000: SUPUESTO) |

**Enlaces:** [repositorio](https://github.com/jesushernandez2005/Proyecto4) · [landing](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/landing/) · video del pitch: **PENDIENTE** · video de respaldo de la demo: **PENDIENTE**.

**Estado en una oración:** el sensor ya leyó movimiento real, la app está publicada y la landing está lista para publicarse, pero todavía no hemos probado el flujo completo de punta a punta ni lo ha usado ninguna familia.

---

## Parte I. Oportunidad y mercado

## 1. Equipo

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (origen: semana 1) |
| **Decisión** | Dos integrantes; el operador de la demo es Jesús (hardware) y la narradora, Andrea (sugerencia del guion). |
| **Evidencia** | [Actividad 2, matriz de selección](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-02/); [guion](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/DistanciaCero_guion_pitch_y_demo.pdf). |
| **Qué cambió** | La ruta de la semana 9 pedía cuatro roles; somos dos, así que cada quien lleva dos. |
| **Qué falta** | Acuerdo de colaboración firmado y roles confirmados. |

| Integrante | Rol | Área de interés | Quién hizo qué |
|---|---|---|---|
| Jesús León Hernández Martínez | **PENDIENTE** (el guion sugiere: operador de la demo, hardware) | Sistemas embebidos, electrónica, programación | **PENDIENTE** |
| Andrea Solano López | **PENDIENTE** (el guion sugiere: narradora) | **PENDIENTE** | **PENDIENTE** |

Lo único documentado del reparto es la frase del guion: "entre los dos hicimos el circuito, las entrevistas y el modelo financiero".

**Acuerdo de colaboración:** **PENDIENTE.** Debe decir cómo se deciden las cosas, cómo se reparte el trabajo y qué pasa si alguien no entrega. **Razón del equipo:** nuestros abuelos, que han ido perdiendo movilidad al envejecer (Actividad 2).

---

## 2. Problema y oportunidad

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (origen: semana 2) |
| **Decisión** | El dolor principal no es "la caída": es **el miedo constante a "la llamada"**. |
| **Evidencia** | [Pain-Gain Map y reporte de oportunidad (Actividad 2)](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-02/); [PDF del Pain-Gain](https://jesushernandez2005.github.io/Proyecto4/actividades/PAIN-GAIN_Chuy.pdf); [reporte](https://jesushernandez2005.github.io/Proyecto4/actividades/REPORTE_DE_OPORTUNIDAD.pdf). |
| **Qué cambió** | Al cuestionar el primer mapa con la IA, el dolor pasó de "no hay quién avise de una caída" a "no saber si está bien entre llamadas". |
| **Qué falta** | Medir con más de tres personas si el patrón se sostiene. |

**Cruce más poderoso del Pain-Gain Map:** dolor D1, el miedo a "la llamada" × ganancia G1, confirmación diaria de que está bien y activo.

**La oportunidad en una oración:** existe una oportunidad para el hijo o hija que vive lejos de un padre mayor que vive solo, que necesita una señal diaria y confiable de que está bien, sin preguntar, llamar ni sentirse culpable.

| Criterio de selección | Concepto elegido: "El Seguro que se Olvida que Existe" |
|---|---|
| Pasión | Sí: la razón son nuestros abuelos |
| Habilidad | Parcial: lo más riesgoso era la conectividad celular |
| Mercado | 5 de 5 señales de deseabilidad |

**Alternativas descartadas:** sarcopenia, osteoartrosis de rodilla y ejercicio en enfermedades crónicas (menor claridad del comprador), y el pago vía aseguradoras (inviable en el plazo de 6 meses).

**Evidencia de deseabilidad:** ya se paga por soluciones imperfectas (Estoy Bien, $299–399 al mes); el IMSS atiende más de 250,000 lesiones por caídas de adultos mayores al año; las familias ya inventan *workarounds* (mensajes diarios, vecinos que revisan, cámaras). Las fuentes están en la Actividad 2.

---

## 3. Usuario y evidencia de campo

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (origen: semanas 3 y 4) |
| **Decisión** | No es un segmento: son **tres perfiles** según si existe una red humana cerca del adulto mayor. El modo de aviso debe ser configurable. |
| **Evidencia** | [Resultados de validación, semana 3 (PDF)](https://jesushernandez2005.github.io/Proyecto4/actividades/resultados_validacion_semana3.pdf); [Actividad 4, sección 5](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-04/); [Excel, hoja Entrevistas](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx). |
| **Qué cambió** | La app pregunta "¿Alguien más lo visita seguido?" y con eso ajusta el aviso: solo excepción, o excepción más confirmación diaria. |
| **Qué falta** | Más entrevistas, separando familias con red local y sin ella. |

**Tres entrevistas (citas textuales):**

- Mariana, 42, Puebla: *"Si tarda mucho en contestar sí ya se me acelera el corazón."*
- Lupita, 37, Chicago: *"Vivir en otro país te pone en un estado de alerta constante."*
- Ricardo, 51, CDMX: *"El silencio no me pondría nervioso… ya confío en el sistema humano que tengo con Sonia."*

| Hipótesis | Resultado |
|---|---|
| H1. Se preocupan seguido, fuera de las llamadas | **Confirmada con matiz:** depende de si hay alguien cerca, no de la distancia |
| H2. Prefieren el silencio a una confirmación diaria | **Ajustada:** depende del perfil; debe ser configurable |
| H3. Pagarían $300–600 al mes | **Confirmada:** $450 a $700 al mes, sin pensarlo |

**Segmento en cuatro capas:** *Demográfica:* 1.7 millones de personas de 60+ viven solas en México (**VERIFICADO**, INEGI, ENADID 2018); hijo o hija de 35–55 años (**HIPÓTESIS**). *Conductual:* llamada casi diaria; 1 de 3 ya abandonó un botón SOS (**VERIFICADO**, n = 3). *Psicográfica:* alerta constante cuando no hay red local (**VERIFICADO**, n = 3). *Económica:* $450–700 al mes (**VERIFICADO**, n = 3); quién paga entre hermanos (**HIPÓTESIS**).

**Hipótesis críticas pendientes:** cómo avisar cuando no hay quien llegue rápido; cómo obtener el consentimiento del adulto mayor sin que se sienta vigilado; y el del cuidador local, que puede vetar la compra.

---

## 4. Mercado y competencia

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (origen: semana 4) |
| **Decisión** | Empezar con venta directa en CDMX, Guadalajara, Monterrey y Puebla. El competidor más peligroso es **llamar + la red informal**, no otra app. |
| **Evidencia** | [Actividad 4, prompts 2–5](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-04/); [Excel, hoja Mercado](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx). |
| **Qué cambió** | Las entrevistas sumaron un actor de decisión: el cuidador local, que puede bloquear la compra. |
| **Qué falta** | Validar los porcentajes de filtro, que son supuestos del equipo. |

| Paso | Valor | Fuente |
|---|--:|---|
| Hogares en México | 38.8 M | ENIGH 2024 |
| × con integrante de 65+ (10.9 %) × unipersonales (17.5 %) | 740,000 | ENIGH 2024; Coneval 2020 |
| × con hijo vivo (85 %) × hijo lejos (60 %) × dispuesto a pagar (25 %) | **94,350 (TAM)** · $509.5 M/año | **SUPUESTOS** del equipo |
| × 4 zonas metropolitanas (45 %) × canal digital (60 %) × deciles 6–10 (70 %) | **17,832 (SAM)** · $96.3 M/año | ENIGH 2024 + **SUPUESTOS** |
| Meta de años 1–2 | **850 (SOM)** · $4.59 M/año | Plan de go-to-market (Actividad 4) |

**Competencia.** *Directos:* Estoy Bien ($299/mes), Cuida Más ($800–928/mes), Care 60+ (desde $6,588/año). *Indirectos:* Life360, Google Family Link, sensores y cámaras DIY. *Sustitutos:* llamadas diarias + red informal (**el más peligroso**: cuesta $0 y ya está en la rutina), cuidador por horas.

<svg viewBox="0 0 420 250" width="100%" style="max-width:520px" role="img" aria-label="Mapa de posicionamiento">
<rect x="50" y="10" width="350" height="200" fill="#F5F6F2" stroke="#ccc"/>
<line x1="50" y1="110" x2="400" y2="110" stroke="#ddd"/><line x1="225" y1="10" x2="225" y2="210" stroke="#ddd"/>
<text x="225" y="240" font-size="11" text-anchor="middle" fill="#333">← exige que el adulto mayor haga algo · no le exige nada →</text>
<text x="18" y="110" font-size="11" fill="#333" transform="rotate(-90 18 110)" text-anchor="middle">interrumpe al hijo · silencio →</text>
<circle cx="120" cy="150" r="6" fill="#888"/><text x="128" y="154" font-size="11">Estoy Bien</text>
<circle cx="225" cy="150" r="6" fill="#888"/><text x="233" y="154" font-size="11">Cuida Más</text>
<circle cx="155" cy="168" r="6" fill="#888"/><text x="163" y="182" font-size="11">Sensores DIY</text>
<circle cx="295" cy="122" r="6" fill="#C7922F"/><text x="303" y="126" font-size="11">Llamadas + red</text>
<circle cx="380" cy="32" r="8" fill="#3E7C5B"/><text x="372" y="56" font-size="12" font-weight="bold" text-anchor="end">DistanciaCero</text>
</svg>

*Posiciones tomadas del lienzo estratégico de la Actividad 4 (puntuaciones de 1 a 5).*

**Cuatro acciones.** *Eliminar:* que el adulto mayor tenga que hacer algo. *Reducir:* el call center 24/7. *Incrementar:* el silencio cuando todo va bien. *Crear:* detección de su rutina y un sensor dentro de un objeto que ya usa.

---

## 5. Propuesta de valor y oferta

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (origen: semana 4) |
| **Decisión** | Hablar del miedo que se quita, no del aparato. |
| **Evidencia** | [Actividad 4, Prompt 6](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-04/). |
| **Qué cambió** | La versión 3 de la Actividad 4 tenía 31 palabras; se recortó a 23 para cumplir el máximo de 25. |
| **Qué falta** | Probar los tres mensajes por perfil con usuarios. |

| Propuesta de valor (≤ 25 palabras) | Oferta técnica |
|---|---|
| DistanciaCero le da al hijo que vive lejos la certeza diaria de que su mamá o papá está bien, sin preguntar, sin culpa. | Un sensor de movimiento (ESP32-S3 + MPU6050) dentro de un sillón, bastón o portavasos, más una app que avisa solo si su rutina cambia. $3,990 + $449/mes. |

**Pirámide de Bain:** hoy es *funcional* (detecta y avisa); el mensaje sube a *emocional* (quita el miedo a "la llamada"). Subir a *transformador* sería prematuro sin evidencia.

**Insightful ✅** da una señal entre llamadas que nadie más da · **Unique ✅** sensor integrado en un objeto que ya usa · **Targeted ✅ con matiz** hace falta un mensaje por perfil (con red local, sin red local, local).

**Error de la primera versión:** describía qué hace el objeto, no qué deja de sentir el hijo.

---

## 6. Propiedad intelectual, marca y vigilancia

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (origen: semana 3) |
| **Decisión** | Nombre **DistanciaCero** (sobre SilencioActivo). FTO **alta**. |
| **Evidencia** | [Actividad 3](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-03/); [presentación de nombre y FTO (PDF)](https://jesushernandez2005.github.io/Proyecto4/actividades/distanciacero_fto.pdf). |
| **Qué cambió** | El nombre que sonaba mejor (SilencioActivo) tenía más riesgo digital. |
| **Qué falta** | **La búsqueda fonética en el IMPI no se ha hecho.** Analizar 3–5 patentes más. |

- **Búsqueda fonética en IMPI:** **PENDIENTE** en marcanet.impi.gob.mx. Riesgo digital: **medio** (el .com está estacionado y hay una banda con @distancia.cero).
- **Vigilancia:** IMPI/SIGA → LATIPAT → Lens.org, con los códigos IPC G08B21/0423 (desviación de un patrón) y G08B21/0461 (sensor en un objeto no portado).
- **Patente más cercana:** MX 351729 B (piso con sensores de presión). **Fuera:** ningún elemento coincide con nuestra arquitectura.
- **Ajuste:** no hizo falta (FTO alta).
- **Estrategia de protección:** registrar la marca en el IMPI, clases 9 y 42 (Actividad 3, **pendiente**). Propuesta por decidir: proteger el firmware y la app como derechos de autor, y no buscar patente hasta tener un método de detección propio.

---

## Parte II. Producto

## 7. Especificación del producto (PDS)

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semanas 5 y 9) |
| **Decisión** | Mantener los 16 requisitos y marcar con honestidad cuáles **no cumple** el prototipo WiFi. |
| **Evidencia** | [Actividad 5, sección 12](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-05/); [firmware](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/firmware/DistanciaCero_Sensor.ino); [app](https://jesushernandez2005.github.io/Proyecto4/app/). |
| **Qué cambió** | El prototipo usa WiFi (incumple RI-02) y no tiene PCB (RR-04 no aplica). |
| **Qué falta** | Correr las pruebas T1–T6 (sección 17) para pasar de "pendiente" a "cumple" o "no cumple". |

| ID | Requisito | Verificación | Estado |
|---|---|---|---|
| RF-01 | Alertar solo ante desviación de **su** patrón | 14 días simulados + eventos inyectados | ❌ Hoy es un umbral fijo de inactividad (4 h) |
| RF-02 | Silencio en rutina normal; aviso ≤ 10 min | 10 corridas, T4 | ⏳ |
| RF-03 | 10–14 días de aprendizaje sin alertas | Registros del servidor | ❌ No implementado |
| RF-04 | Historial de 30 días sin conexión | Modo avión | ❌ La app guarda los últimos 40 eventos |
| RD-01 | ≥ 15 días sin recargar | Medición, T5 | ❌ Probable: el WiFi siempre encendido gasta mucho |
| RD-02 | Falsos positivos < 5 %, falsos negativos < 2 % | 50 eventos simulados | ⏳ |
| RD-03 | Reporte en ≤ 30 s | 20 transmisiones | ⏳ El firmware publica estado cada 30 s |
| RD-04 | Servidor disponible ≥ 99 % | Monitoreo | ⏳ Broker público, sin garantía |
| RI-01 | Estado claro en < 10 s, sin lenguaje clínico | Prueba con usuario | ⏳ |
| RI-02 | Solo celular, cifrado | Prueba sin WiFi | ❌ El prototipo usa WiFi |
| RI-03 | Instalación guiada ≤ 10 min | Cronómetro, T3 | ⏳ |
| RI-04 | Alerta por dos canales | Simular falla, T1 | ⚠️ Parcial: app + ntfy opcional; sin WhatsApp |
| RR-01 | ≤ $600 al mes | Modelo de precios | ✅ $449 |
| RR-02 | Ninguna acción del adulto mayor | Revisión de diseño | ✅ En diseño; la recarga la hace la familia |
| RR-03 | Sin audio ni video | Esquema de datos | ✅ El JSON solo lleva movimiento, batería y señal |
| RR-04 | PCB apta para JLCPCB | DRC | — No aplica al prototipo (sin PCB) |

**First-iteration product:** un objeto (sillón, bastón o portavasos) con ESP32-S3 Super Mini + MPU6050 + LiPo que publica su actividad por MQTT, y una app web que avisa a la familia si pasa más tiempo del umbral sin movimiento. Sin módulo celular y sin aprendizaje de rutina.

---

## 8. Arquitectura del sistema

| Campo | Contenido |
|---|---|
| **Versión** | v2.0 · 24/11/2026 (origen: semana 5) |
| **Decisión** | **Híbrida:** el ESP32 detecta el movimiento y cuenta la inactividad (edge); la app decide el estado y lo comparte con el círculo. |
| **Evidencia** | [Firmware](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/firmware/DistanciaCero_Sensor.ino); [protocolo MQTT en anexos](#c-archivos-de-diseno-cad-esquematicos-y-firmware); [Actividad 9, fronteras](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-09/). |
| **Qué cambió** | Ver la tabla de abajo. |
| **Qué falta** | Un servidor propio: hoy, si nadie tiene la app abierta, solo avisa el ESP32 (por ntfy). |

<svg viewBox="0 0 760 170" width="100%" role="img" aria-label="Diagrama de bloques">
<g font-size="12" font-family="sans-serif">
<rect x="5" y="40" width="150" height="80" rx="8" fill="#FFF7E6" stroke="#C7922F"/><text x="80" y="62" text-anchor="middle" font-weight="bold">Objeto</text><text x="80" y="80" text-anchor="middle">MPU6050 → ESP32-S3</text><text x="80" y="96" text-anchor="middle">LiPo 3.7 V · 50 Hz</text><text x="80" y="112" text-anchor="middle" font-size="10">I²C (GPIO 5/6)</text>
<rect x="215" y="40" width="150" height="80" rx="8" fill="#EEF3F8" stroke="#21303B"/><text x="290" y="62" text-anchor="middle" font-weight="bold">Broker MQTT</text><text x="290" y="80" text-anchor="middle">HiveMQ público</text><text x="290" y="96" text-anchor="middle" font-size="10">distanciacero/&lt;ID&gt;/…</text>
<rect x="425" y="40" width="150" height="80" rx="8" fill="#E3EDE6" stroke="#3E7C5B"/><text x="500" y="62" text-anchor="middle" font-weight="bold">App web</text><text x="500" y="80" text-anchor="middle">estado: normal /</text><text x="500" y="96" text-anchor="middle">atención / crítico</text>
<rect x="625" y="20" width="130" height="50" rx="8" fill="#fff" stroke="#999"/><text x="690" y="42" text-anchor="middle">Hijo/a</text><text x="690" y="58" text-anchor="middle" font-size="10">y cuidador local</text>
<rect x="625" y="95" width="130" height="50" rx="8" fill="#fff" stroke="#999"/><text x="690" y="117" text-anchor="middle">Adulto mayor</text><text x="690" y="133" text-anchor="middle" font-size="10">3 botones (opcional)</text>
<line x1="155" y1="80" x2="215" y2="80" stroke="#333" marker-end="url(#a)"/><text x="185" y="72" text-anchor="middle" font-size="10">WiFi · MQTT</text><text x="185" y="98" text-anchor="middle" font-size="10">cada 30 s</text>
<line x1="365" y1="80" x2="425" y2="80" stroke="#333" marker-end="url(#a)"/><text x="395" y="72" text-anchor="middle" font-size="10">WSS</text>
<line x1="575" y1="65" x2="625" y2="48" stroke="#333" marker-end="url(#a)"/><line x1="625" y1="118" x2="575" y2="98" stroke="#333" marker-end="url(#a)"/>
<path d="M80 120 C 80 165, 690 165, 690 147" fill="none" stroke="#999" stroke-dasharray="4 3"/><text x="380" y="164" text-anchor="middle" font-size="10">HTTPS → ntfy (push opcional, sin app abierta)</text>
</g>
<defs><marker id="a" markerWidth="8" markerHeight="8" refX="7" refY="4" orient="auto"><path d="M0,0 L8,4 L0,8 z" fill="#333"/></marker></defs>
</svg>

**Por qué híbrida.** (1) El movimiento se detecta a 50 Hz en el ESP32 y solo se envía un resumen, así que viaja poco dato. (2) El ESP32 puede avisar por su cuenta (ntfy) aunque nadie tenga la app abierta. (3) La app comparte el estado y las respuestas entre familiar, cuidador y adulto mayor. **Consecuencia:** sin un servidor propio no se detecta que el sensor dejó de reportar si nadie tiene la app abierta.

**Protocolos.** *I²C:* el MPU6050 lo trae y bastan dos cables. *MQTT:* mensajes chicos y "última voluntad", que avisa sola cuando el sensor se desconecta. *WebSocket seguro (wss):* el navegador no abre MQTT directo. *HTTPS a ntfy:* push gratis sin publicar una app en tiendas.

| | Semana 5 | Versión final (noviembre) |
|---|---|---|
| Red | Celular (SIM7600E-H), sin WiFi | WiFi 2.4 GHz (hotspot en la demo) |
| Sensores | MPU6050 + PIR | MPU6050 |
| Nube | HTTPS POST → Firebase + Cloud Function | Broker MQTT público |
| Detección | z-score contra su patrón por hora | Umbral de inactividad ajustable (4 h o 3 h) |
| Avisos | Push (FCM) + WhatsApp | En la app + ntfy opcional |
| Electrónica | PCB 70 × 45 mm, JLCPCB | ESP32-S3 Super Mini con jumpers, sin PCB |

---

## 9. Diseño del producto

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semana 6) |
| **Decisión** | El sillón ganó la Matriz de Pugh; hoy se ofrecen **los tres objetos**. |
| **Evidencia** | [Actividad 6: tabla morfológica, conceptos, Pugh y boceto](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-06/); [Actividad 8: planos con cotas](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-08/). |
| **Qué cambió** | El sillón ganó porque era el único donde cabían el SIM7600 y la 18650. Sin esas piezas, ese criterio (tamaño, 10 %) ya no descarta al bastón ni al portavasos. |
| **Qué falta** | Fotos del prototipo en los tres objetos; repetir la matriz con el hardware nuevo. |

**Principios aplicados y dónde se ven:** *affordances* (el portavasos invita a poner la taza) · *constraints* (el velcro solo cabe en una posición) · *contour bias* (sin aristas, radio de 4 mm) · *consistencia* (el acabado imita la tapicería) · *confirmación* (un LED solo durante la instalación) · *costo-beneficio* (sin LED permanente, para que no se note).

| Matriz de Pugh (deseabilidad 50 %, factibilidad 50 %) | Bastón (datum) | **Sillón** | Portavasos |
|---|:--:|:--:|:--:|
| Puntuación ponderada | 0 | **+80** | +50 |

<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/plano-variante-a.jpg" alt="Plano con cotas de la carcasa variante A" style="width:100%;border-radius:6px">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/carcasa-a-explosionada.jpg" alt="Carcasa variante A en vista explosionada" style="width:100%;border-radius:6px">
</div>
*Boceto técnico con cotas (variante A, 90 × 60 × 21 mm, PETG) y vista explosionada. Modelo 3D, no pieza impresa.*

**Evolución:** boceto de 90 × 60 × 15 mm (semana 6) → la 18650 no cabía → carcasa de dos piezas en PETG, variantes A y B (semana 8) → prototipo con ESP32-S3 Super Mini y jumpers dentro de los tres objetos (noviembre).

---

## 10. Prototipos y evidencia

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semana 8) |
| **Decisión** | Lo primero que se probó fue el precio (una landing), no la carcasa. |
| **Evidencia** | [Actividad 8, plan de prototipado](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-08/); [presentación final](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/DistanciaCero_presentacion_final.pptx) (diapositiva "Qué funciona hoy"). |
| **Qué cambió** | El precio de la landing bajó de $4,490 a $3,990, igual que el modelo financiero. |
| **Qué falta** | Imprimir la carcasa; sesiones con usuarios; **fotos reales** de cada prototipo. |

| Prototipo | Pregunta | Tipo · resolución | Qué se construyó | Evidencia | Aprendizaje → cambio |
|---|---|---|---|---|---|
| Landing (semana 8 → hoy) | ¿Alguien reserva viendo el precio real? | Negocio · baja | Landing de 4 páginas | **0 sesiones** | Hay que conectar el formulario para medir |
| Carcasa A/B | ¿Cabe y cierra sin herramientas? | Forma · alta (digital) | Modelo 3D, planos y 4 STL | Mallas cerradas; **sin imprimir** | La 18650 no cabía → LiPo plana |
| Circuito | ¿El MPU6050 lee movimiento real? | Funcional · media | ESP32 + MPU6050 por USB | \|a\| = 1.00 g en reposo | Sí lee; falta probar el aviso |
| App web | ¿Se entiende el estado y el aviso? | Interacción · alta | 16 pantallas, modo demo y modo real | Publicada en este sitio | Del Figma Make a una app real |
| Tres objetos | ¿Funciona en sillón, bastón y portavasos? | Integración · alta | Super Mini + MPU6050 + LiPo con jumpers | **PENDIENTE** | — |

**Línea de tiempo:** semana 6, renders y app en Figma · semana 8, landing y carcasa · semana 9, plan de pruebas · 23/11, app web, firmware y simulador · 24/11, landing con los tres productos. **Fotos: PENDIENTE.**

---

## 11. Manufactura, DFM y circularidad

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semanas 5, 7 y 8) |
| **Decisión** | 10 unidades el año 1 (impresión 3D en PETG + ensamble manual) y 100 el año 2. |
| **Evidencia** | [Excel: hojas BOM_final, DFM y Costos](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx); [Actividad 8, DFM y circularidad](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-08/). |
| **Qué cambió** | El prototipo no lleva PCB ni módulo celular; su BOM se registra aparte del BOM del modelo. |
| **Qué falta** | Llenar el precio real del prototipo (hoja BOM_final, celdas amarillas) y cotizar el resto del BOM. |

| BOM del modelo (por unidad) | Precio | Estado |
|---|--:|---|
| Módulo celular SIM7600E-H | $2,100 | Cotizado (US$129) |
| ESP32-S3 · MPU6050 + PIR · batería · PCB · carcasa | $870 | Estimados |
| **BOM** → **costo unitario** (+ 15 % overhead + 25 % contingencia) | **$2,970 → $4,158** | |

**DFM (Actividad 8):** costo unitario de **$3,491 → $1,723** (−50.7 %), casi todo por usar el chip celular LCC sobre un PCB propio. ⚠️ El ensamble no está cronometrado.

**Circularidad:** ¿se abre sin destruirla? ✅ cierre a presión · ¿módulos reemplazables? ⚠️ la batería sí (JST), el ESP32 no · ¿materiales identificables? ⚠️ un solo plástico, falta el código de reciclaje · ¿se actualiza sin reemplazarse? ✅ firmware por USB-C.

**Reproducir una unidad:** ver [Anexo C](#c-archivos-de-diseno-cad-esquematicos-y-firmware).

---

## 12. Aplicación conectada

| Campo | Contenido |
|---|---|
| **Versión** | v2.0 · 24/11/2026 (origen: semanas 6 y 9) |
| **Decisión** | App web de un solo archivo, abierta por link y sin tienda de apps, con modo **Demo** y modo **Dispositivo real** (MQTT). |
| **Evidencia** | [App publicada](https://jesushernandez2005.github.io/Proyecto4/app/); [código en el repositorio](https://github.com/jesushernandez2005/Proyecto4/tree/main/docs/app); [Actividad 6, wireframes](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-06/). |
| **Qué cambió** | Del prototipo de Figma Make con datos de ejemplo a una app que escucha al ESP32. |
| **Qué falta** | Servidor propio con usuario y contraseña; historial de 30 días; WhatsApp. |

<div style="display:grid;grid-template-columns:repeat(4,1fr);gap:8px">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/app-onboarding-qr.jpg" alt="Onboarding: escanear el código y elegir el objeto" style="width:100%;border-radius:6px">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/app-normal.jpg" alt="Estado normal" style="width:100%;border-radius:6px">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/app-alerta.jpg" alt="Alerta activa" style="width:100%;border-radius:6px">
<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/app-circulo.jpg" alt="Círculo de cuidado" style="width:100%;border-radius:6px">
</div>

**Flujo:** 5 pasos de bienvenida (quién eres → ¿alguien lo visita? → código del sensor y objeto → detección → consentimiento) → inicio → alerta → "Ya lo revisé".

**Estados:** *cargando* "Esperando al sensor" · *normal* "Todo bien" · *atención* "Un día más tranquilo" · *crítico/alerta* · *sin conexión* "Perdimos contacto con el sensor" (sin señal por más de 3 min) · *error* "No se pudo conectar con el servidor MQTT" · *pausa* "Avisos en pausa".

**Conexión:** MQTT en `distanciacero/<CÓDIGO>/estado` (retenido, cada 30 s). Formato: `{"id","obj","fw","bat","rssi","inactivoSeg","huboActividad","umbralMin","alerta","sensor","t"}`.

**Cómo ejecutarla:** abrir la URL; para probar sin hardware, `python sim_dispositivo.py --id DC-SIM1` ([simulador](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/firmware/sim_dispositivo.py)).

**Limitaciones:** el broker público lo puede leer cualquiera que conozca el código; si nadie tiene la app abierta, el estado no se calcula; teléfonos, tarjeta y correo de la app son ficticios. **Los commits del repositorio no siguen las sesiones de trabajo** (mensajes como "actualiza"; ver [Anexo B](#b-repositorio-readme-y-bitacoras)).

---

## Parte III. Negocio

## 13. Modelo de negocio (Business Blueprint)

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (origen: semanas 4 y 7) |
| **Decisión** | Equipo + suscripción mensual. El equipo se vende $168 por debajo de su costo y lo recupera la suscripción. |
| **Evidencia** | [Actividad 7, benchmarking](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-07/); [Excel, hojas Resumen y Economia_unitaria](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx). |
| **Qué cambió** | El precio del equipo bajó de $4,490 (Actividad 7) a $3,990 (modelo final). |
| **Qué falta** | Validar que alguien paga el equipo. |

| Caja | Contenido | Sustento |
|---|---|---|
| Clientes | Hijo/a de 35–55 años que vive lejos de su mamá o papá de 65+ | [§3](#3-usuario-y-evidencia-de-campo) |
| Oferta | Sensor en sillón, bastón o portavasos + app | [§7](#7-especificacion-del-producto-pds) |
| Modelo de ingresos y precio | $3,990 + $449/mes | [§14](#14-costos-precio-y-viabilidad-financiera) |
| Canales | Meta y Google Ads; piloto en Puebla | [§15](#15-go-to-market-y-economia-unitaria) |
| Propuesta de valor | Certeza diaria, sin preguntar, sin culpa | [§5](#5-propuesta-de-valor-y-oferta) |
| Costos | $4,158 por equipo; $90.14 al mes por suscriptor | [§14](#14-costos-precio-y-viabilidad-financiera) |
| Socios | Proveedores (LCSC, JLCPCB, MercadoLibre); broker y notificaciones | [§11](#11-manufactura-dfm-y-circularidad) |
| Equipo y recursos | Dos integrantes, hardware y firmware propios | [§1](#1-equipo) |

**Benchmarking:** Medical Guardian (equipo US$149.95–199.95 + US$31.95–49.95/mes) · Ring (hardware + planes de US$4.99–19.99/mes) · CarePredict (hardware + servicio, pagado por agencias públicas). Los tres cobran equipo + cuota.

**Desafío de diseño:** si el equipo se tuviera que regalar, el modelo no cierra con el costo actual.

---

## 14. Costos, precio y viabilidad financiera

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semana 7) |
| **Decisión** | $3,990 por el equipo (por debajo del piso de $4,158) y $449/mes (59 % del camino entre el piso y el techo). |
| **Evidencia** | [Excel](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx): Costos_DFS, IA_costo, Desarrollo, Precio_rango, Flujo_24m, Resumen. |
| **Qué cambió** | Se unificó el precio en la landing, el Excel y la presentación. |
| **Qué falta** | **Medir el costo de la IA con tokens reales**; cotizar 5 de las 6 líneas del BOM. |

| Indicador | Valor | Hoja |
|---|---|---|
| Costos D / F / S | 17 costos: 5 D, 6 F, 6 S | Costos_DFS |
| Costo de la IA por usuario | ≈ $0.02/mes (Haiku 5.5); el modelo usa $0.14 como cota. **No medido** | IA_costo |
| Desarrollo (3 / 5 / 8 ciclos) | $42,921 / **$71,536** / $114,457 | Desarrollo |
| Precio cost-plus del equipo (+40 %) | $5,821 | Precio_rango |
| Equipo: piso (costo) / techo (semana 4, HIPÓTESIS) | $4,158 / $4,000 → hay que subsidiar | Precio_rango |
| Suscripción: piso / techo (lo más alto que dijeron) | $93.51 / $700 | Precio_rango |
| Punto de equilibrio del desarrollo | 25.5 familias (si se quedan 12 meses) · 10.3 (24 meses) | Economia_unitaria |
| Flujo acumulado a 12 meses | −$72,319 | Flujo_24m |
| VPN a 12 / 24 meses (15 % anual) | −$72,414 / **+$3,175** | Resumen |

**Tasa del 15 %:** la que fija la guía de la Actividad 7 para un proyecto en etapa temprana. **Lectura:** el VPN a 24 meses es casi cero y el modelo no incluye *churn*.

---

## 15. Go-to-market y economía unitaria

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semana 9) |
| **Decisión** | Empezar con un piloto sin costo de 10 familias en Puebla (unos 60 días) para medir *churn*, instalación y disposición a pagar el equipo. |
| **Evidencia** | [Actividad 9, sección 4.3](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-09/); [Excel, hojas Economia_unitaria, Churn y Sensibilidad](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx). |
| **Qué cambió** | Con $3,990 el payback pasa de 2.4 a 3.8 meses. |
| **Qué falta** | Medir CAC y *churn*; conectar el formulario de la landing. |

**Cliente número 1 (HIPÓTESIS, n = 1):** hija o hijo que vive fuera de Puebla, con su mamá o papá de 65+ que vive solo en Puebla y sin un cuidador que pase a diario (perfil de Lupita).

**Canales:** venta directa con Meta y Google Ads segmentados a hijos de 35–55 años (Actividad 4), más la landing con pre-registro. Se eligen porque el comprador está en línea y lejos del adulto mayor.

| Métrica | Valor | Estado |
|---|--:|---|
| CAC | $1,000 | **SUPUESTO** (5 demos × 1.5 h × $80 + $400 en anuncios) |
| Churn mensual | 0 % en el caso base; 3 %, 5 % y 8 % en escenarios | **SUPUESTO** |
| Contribución mensual | $342.70 | Cálculo |
| Inversión por familia | $1,311.64 | Cálculo (CAC + pérdida del equipo) |
| Payback | **3.8 meses** | Cálculo |
| LTV (churn 3 %) · LTV ÷ inversión | $11,423 · **8.7×** | Cálculo con SUPUESTO; con churn de 10 % baja a 2.6× |

**Palancas (acumulado a 24 meses):** base +$26,123 · suscripción de $549 → +$94,181 · equipo de $4,990 → +$132,163 · CAC de $1,200 → +$4,123 · churn de 3 % → −$2,013 · churn de 8 % → −$38,739.

---

## 16. Regulación y aspectos legales

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semanas 8 y 9) |
| **Decisión** | No vender a terceros hasta resolver los temas POR VERIFICAR. El piloto es sin costo y con consentimiento escrito. |
| **Evidencia** | [Actividad 9, checklist regulatorio (Prompt 4)](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-09/); aviso de privacidad en la [landing](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/landing/). |
| **Qué cambió** | El prototipo WiFi con un broker público añade un riesgo de datos. |
| **Qué falta** | Confirmar con la CRT o un organismo de certificación; términos de uso de la app. |

| Tema | Estatus |
|---|---|
| Radio y homologación | VERIFICADO el alcance; **POR VERIFICAR** el trámite. La ESP32-S3 Super Mini puede no tener certificación |
| Datos personales (ley de 2025) | VERIFICADO en fuente secundaria; **POR VERIFICAR** cómo da su consentimiento la persona monitoreada |
| Seguridad y etiquetado (NOM-001-SCFI-2018) | VERIFICADO el alcance general en fuente secundaria; **POR VERIFICAR** si aplica |
| Baterías LiPo | **POR VERIFICAR** (no se consultaron fuentes) |
| Licencias de software y del modelo de IA | **POR VERIFICAR** (bibliotecas de Arduino, MQTT.js, términos de la API de Claude) |
| Términos de venta (LFPC, precio con IVA) | **POR VERIFICAR**; el Excel ya calcula $4,628.40 con IVA |
| Economía circular | VERIFICADO en fuente secundaria: ley vigente desde el 20/01/2026, sin reglamento |
| Exportación | No aplica |

**Aviso de privacidad:** la landing tiene uno simplificado y la app una pantalla "Qué ve y qué NO ve". **Términos de la app: PENDIENTE.**

**Antes de vender a un tercero:** broker propio con usuario y contraseña · consentimiento del adulto mayor (y del cuidador local) · homologación · precio con IVA · términos de servicio.

---

## Parte IV. Validación y lanzamiento

## 17. Integración y pruebas del sistema

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semana 9) |
| **Decisión** | Cada frontera guarda un registro para que una falla en la demo se pueda diagnosticar. |
| **Evidencia** | [Actividad 9, sección 4.1](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-09/); monitor serie del firmware; simulador. |
| **Qué cambió** | Las fronteras se redefinieron para la arquitectura WiFi + MQTT. |
| **Qué falta** | Correr T1–T6 y subir los registros. |

<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/fronteras.jpg" alt="Las cuatro fronteras de la semana 9" style="max-width:560px;width:100%;border-radius:6px">

*Fronteras de la semana 9 (versión celular). Abajo, la versión actual.*

| Frontera | Registro | Estado |
|---|---|---|
| F1 · MPU6050 → ESP32 (I²C) | Monitor serie (`DEBUG_MOV`) | ✅ Lee \|a\| = 1.00 g en reposo |
| F2 · ESP32 → broker (WiFi/MQTT) | Monitor serie + LED de estado | ⏳ Firmware escrito; sin registro |
| F3 · Broker → app (WSS) | Pantalla Conexión + historial | ⏳ Se puede probar con el simulador; **sin registro guardado** |
| F4 · App → persona | Historial de eventos | ⏳ |

| Prueba | Aprobado si | Estado |
|---|---|---|
| T1 · Falla de un canal | Llega por el otro | ⏳ |
| T2 · Desconexión 10 min | La app dice "sin conexión" y no da el dato viejo por actual | ⏳ Implementado en la app; sin prueba |
| T3 · Instalación sin ayuda | ≤ 10 min | ⏳ |
| T4 · Latencia | Aviso ≤ 10 min en 10 corridas | ⏳ |
| T5 · Autonomía | ≥ 15 días | ⏳ |
| T6 · 48 h continuas | Sin reinicios | ⏳ |

**Fallas documentadas:** (1) **F3**: el visor de Claude bloquea conexiones externas, así que el modo real solo funciona desde GitHub Pages (se encontró al probar la app). (2) **F2**: la red de la universidad pide usuario y contraseña, y el ESP32 no se conecta; se usa el hotspot del celular (README). (3) **F2, versión celular**: el SIM7600E-H no trae las bandas LTE de México (se encontró al llenar el checklist regulatorio). (4) **Diseño**: el USB-C chocaba con el ESP32 en el modelo 3D (revisión en planta).

**Todavía no funciona:** aprendizaje de rutina, historial de 30 días, WhatsApp, servidor propio. Falta tiempo y un backend.

**Checklist de "listo":** hardware sin laptop ⏳ · app desplegada ✅ · landing publicada ⏳ (al hacer push de esta carpeta) · flujo completo sin intervención ⏳

---

## 18. Pruebas con usuarios

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (origen: semana 9) |
| **Decisión** | Probar con hijos e hijas adultos, no con personas mayores. Se graba solo con consentimiento. |
| **Evidencia** | [Actividad 9, sección 4.2 (protocolo y hoja)](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-09/). |
| **Qué cambió** | Nada: **no se ha hecho ninguna sesión.** |
| **Qué falta** | Las 5 sesiones (3 del segmento y 2 de otros equipos). |

**Protocolo de 30 min:** guion fijo (0–3) · T1, instalar y vincular (3–10) · T2, interpretar una alerta (10–20) · T3, encontrar el precio y pre-registrarse en la landing (20–25) · entrevista de cierre (25–30).

| Usuario | T1 sin ayuda · tiempo · SEQ | T2 sin ayuda · SEQ | T3 pre-registro | Cita | Hallazgo y severidad |
|---|---|---|---|---|---|
| 1–3 (segmento) | pendiente | pendiente | pendiente | — | — |
| 4–5 (otro equipo) | pendiente | pendiente | pendiente | — | — |

**Señal de negocio:** pre-registros reales = **0** (el formulario aún no está conectado). Las 3 entrevistas de la semana 3 son opiniones, no compromisos.

---

## 19. Landing page

| Campo | Contenido |
|---|---|
| **Versión** | v3.0 · 24/11/2026 (origen: semana 8) |
| **Decisión** | Una landing general y una página por objeto, con un solo CTA: "Aparta tu lugar en el piloto". |
| **Evidencia** | [Landing](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/landing/) · [Sillón](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/landing/sillon/) · [Bastón](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/landing/baston/) · [Portavasos](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/landing/portavasos/) · [Excel, hoja Landing](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx). |
| **Qué cambió** | v1, un archivo sin formulario (semana 8). v2, con formulario, centrada en el sillón y con "sin wifi". v3, los tres productos, WiFi, USB-C y $3,990. |
| **Qué falta** | Conectar `FORM_ENDPOINT` y `GOATCOUNTER`, y poner el correo de contacto. |

**URL:** `https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/landing/` (activa después del push).

**Checklist:** headline ✅ · visual (ilustración + teléfono "Sin avisos hoy") ✅ · beneficios ✅ · precio visible ✅ · un solo CTA ✅ · evidencia en la página ("3 de 3", "$450 a $700") ✅ · metadatos y Open Graph ✅ (imagen por página).

| Métrica | Valor |
|---|---|
| Visitas | **sin medir** (GoatCounter sin configurar) |
| Clics en el CTA | **sin medir** |
| Pre-registros | **0** |

**Prompt con el que se construyó:** v1, Prompt 6 de la [Actividad 8](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-08/). v3, en Claude (24/11/2026): *"necesito que cambies el landing de la carpeta que te mande y lo corrigas/adaptes a lo que hemos cambiado, incluye todos los productos"*. La IA comparó la landing con la app y la memoria del proyecto, y quitó lo que ya no era cierto ("sin wifi", base magnética, anillo de luz). Después el equipo corrigió el precio a $3,990.

---

## 20. Pitch y demo

| Campo | Contenido |
|---|---|
| **Versión** | v1.1 · 24/11/2026 (origen: semana 9) |
| **Decisión** | Una sola confesión en el pitch: "hoy el prototipo usa WiFi". Pedimos $15,000 y diez familias. |
| **Evidencia** | [Guion de pitch y demo (PDF)](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/DistanciaCero_guion_pitch_y_demo.pdf), con la fuente de cada cifra. |
| **Qué cambió** | El guion ya usa $3,990, igual que la landing y el Excel. |
| **Qué falta** | Grabar el video del pitch y el video de respaldo de la demo; tres ensayos con cronómetro; llenar los corchetes del guion. |

**Pitch de 3 min:** 331 palabras (≈ 2:33). Video: **PENDIENTE**.

<img src="https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/img/demo-7-min.jpg" alt="Los seis tramos de la demo de 7 minutos" style="max-width:560px;width:100%;border-radius:6px">

| Tramo | Plan B |
|---|---|
| Contexto (0:00–0:45) | Foto del objeto |
| Camino principal (0:45–3:15) | Video de 90 s |
| Provocar el evento (3:15–4:45) | Datos precargados y video |
| Fallo manejado (4:45–5:45) | Registro del servidor |
| La compra (5:45–6:30) | Captura de la landing |
| Cierre (6:30–7:00) | — |

| Pregunta difícil | Respuesta corta | Dónde |
|---|---|---|
| ¿Por qué venden el equipo $168 debajo del costo? | La suscripción lo recupera en 3.8 meses; el precio no está validado | [§14](#14-costos-precio-y-viabilidad-financiera) |
| ¿Cuánto cuesta un cliente? | $1,000, SUPUESTO; con $1,200 sigue en +$4,123 | [§15](#15-go-to-market-y-economia-unitaria) |
| ¿Y si los clientes se van? | Con 3 % al mes, −$2,013 a 24 meses; lo mide el piloto | [§15](#15-go-to-market-y-economia-unitaria) |
| ¿Cuándo funciona sin WiFi? | El módulo celular es el 71 % del costo y no está integrado | [§8](#8-arquitectura-del-sistema) |
| ¿Qué funciona de verdad? | Sensor, firmware y app; falta el flujo completo | [§17](#17-integracion-y-pruebas-del-sistema) |

---

## Parte V. Cierre

## 21. Uso de IA en el proyecto

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (semanas 1–9) |
| **Decisión** | La IA propone y cuestiona; el equipo decide y verifica. |
| **Evidencia** | Cada actividad tiene los prompts y las respuestas completas. |
| **Qué cambió** | Del uso para generar ideas al uso para revisar contra datos reales. |
| **Qué falta** | Medir el costo de la IA del producto con tokens reales. |

| # | Qué se pidió | Qué respondió la IA | Qué corrigió el equipo y por qué |
|---|---|---|---|
| 1 | Cuestionar el Pain-Gain Map (Act. 2, P4) | El dolor real es el miedo a "la llamada", no la caída | Se cambió el problema y con él todo el producto |
| 2 | Auditoría digital de los nombres (Act. 3, P4) | SilencioActivo tiene un riesgo digital alto | Se eligió DistanciaCero, aunque gustaba menos |
| 3 | Matriz de Pugh (Act. 6, P5) | Sillón +80: es el único donde cabe el hardware | Se eligió el sillón; hoy, sin el celular, volvieron los tres |
| 4 | **BOM (Act. 5 → Act. 7)** | **Error de la IA:** en la semana 5 estimó el módulo celular en ~$350–450 y el BOM en ~$800–1,100 | Al cotizar costó $2,100 y el BOM $2,970. Desde entonces solo usamos precios con fuente |
| 5 | Checklist regulatorio (Act. 9, P4) | El SIM7600E-H no trae las bandas LTE de Telcel ni AT&T | Se marcó el riesgo; el prototipo actual usa WiFi y el módulo celular queda para el producto |

**IA en el producto (hoy):** la app decide por un **umbral fijo** de inactividad; todavía **no** hay un modelo. **Diseño:** un z-score contra su patrón por hora (estadístico, en la nube) y un modelo de lenguaje (Claude Haiku) que solo redacta el resumen semanal. Recibe el conteo de actividad por hora y devuelve un texto corto. Costo: ≈ $0.02 MXN por usuario al mes (**estimado, no medido**). Si falla, el resumen sale con una plantilla. Sin ella, un umbral igual para todos generaría falsas alarmas en quien duerme siesta y avisaría tarde a quien se levanta temprano (**HIPÓTESIS**).

---

## 22. Reflexión y siguientes pasos

| Campo | Contenido |
|---|---|
| **Versión** | v1.0 · 24/11/2026 (cierre del curso) |
| **Decisión** | El siguiente paso es el piloto, no más ingeniería. |
| **Evidencia** | Secciones 15, 17 y 18. |
| **Qué cambió** | — |
| **Qué falta** | Los párrafos firmados de cada integrante. |

**Aprendizaje más importante (un párrafo por integrante, firmado):**

- **Jesús:** *PENDIENTE: escribir y firmar.* (En la Actividad 9 escribió: "prepararse para presentar es lo contrario de maquillar".)
- **Andrea:** *PENDIENTE: escribir y firmar.*

**Qué haríamos distinto:** sentarnos con una persona del segmento antes de la semana 5; cotizar primero la pieza más cara; comparar las bandas del módem con las redes de México antes de elegirlo.

| Hipótesis crítica sin verificar | Cómo se verificará |
|---|---|
| Alguien paga $3,990 por el equipo | Pre-registros y cierre al final del piloto |
| Churn ≤ 3 % al mes | Piloto de 60 días |
| El MPU6050 distingue "se sentó", "tomó el bastón" o "levantó la taza" | T4 y T6 en los tres objetos |
| Se instala sin ayuda en ≤ 10 min | T3 con 5 usuarios |
| El adulto mayor y el cuidador local aceptan | Consentimiento escrito en el piloto |

**Plan de 90 días:** días 1–15, conectar el formulario, publicar la landing y hacer las 5 sesiones. Días 15–30, pedir $15,000 y fabricar 10 unidades. Días 30–90, piloto con 10 familias en Puebla y medir churn, instalación y pago.

**Riesgos principales:** nadie paga el equipo · el sensor confunde movimientos · el broker público expone datos · el módulo celular encarece el producto · el cuidador local veta la compra.

---

## Anexos

### A. BOM completo con cotizaciones y proveedores

El detalle, con fórmulas, está en la hoja **BOM_final** del [Excel](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx).

**Producto (el que usa el modelo financiero, con módulo celular)**

| Componente | Especificación | Precio (MXN) | Estado | Proveedor / referencia |
|---|---|--:|---|---|
| Módulo celular | SIM7600E-H, breakout 4G con antena | 2,100 | Cotizado | 4gltemall.com, US$129 (Actividad 7) |
| Módulo celular (alternativa DFM) | SIM7600E-H en formato LCC | 805 | "Desde" US$49.47, 6 en existencia | LCSC C5338795, consultado 05/11/2026 (Actividad 8) |
| Microcontrolador | ESP32-S3 (8 MB de flash) | 120 | Estimado | LCSC N8R8 "desde" US$3.48 (Actividad 8) |
| Sensores | MPU6050 + PIR HC-SR501 (sin PIR desde la semana 8) | 125 | Estimado | Sin cotizar |
| Batería y carga | 18650 + TP4056 (semana 7); LiPo Jauch LP103450JH 1.92 Ah (semana 8) | 175 | Estimado | Sin cotizar |
| PCB | 2 capas + ensamble | 250 | Estimado | JLCPCB |
| Carcasa | Impresión 3D (PETG, 2 piezas en la semana 8) | 200 | Estimado | Impresión propia |
| **Total** | | **2,970** | 1 de 6 líneas cotizada | |

**Prototipo que se demuestra (WiFi, sin PCB):** ESP32-S3 Super Mini · MPU6050 (GY-521) · LiPo 3.7 V · jumpers · objeto anfitrión. **Los precios pagados están por llenar** en las celdas amarillas de la hoja BOM_final; no se inventó ninguno.

### B. Repositorio, README y bitácoras

- **Repositorio:** [github.com/jesushernandez2005/Proyecto4](https://github.com/jesushernandez2005/Proyecto4) (MkDocs Material, publicado con GitHub Actions).
- **App:** `docs/app/index.html`. Firmware y simulador: [Anexo C](#c-archivos-de-diseno-cad-esquematicos-y-firmware).

**Bitácora de entregables semanales**

| Semana | Entregable | Fecha |
|---|---|---|
| 1 | [Actividad 1: SCAMPER](https://and070406.github.io/Proyecto4_andrea/semana1/) | agosto 2026 |
| 2 | [Actividad 2: búsqueda de oportunidad](https://and070406.github.io/Proyecto4_andrea/semana2/) | 02/09/2026 |
| 3 | [Actividad 3: PI, marca y vigilancia](https://and070406.github.io/Proyecto4_andrea/semana3/) | 09/09/2026 |
| 4 | [Actividad 4: mercado y propuesta de valor](https://and070406.github.io/Proyecto4_andrea/semana4/) | 17/09/2026 (entrevistas: 18/09) |
| 5 | [Actividad 5: PDS y arquitectura](https://and070406.github.io/Proyecto4_andrea/semana5/) | 24/09/2026 |
| 6 | [Actividad 6: concepto de diseño](https://and070406.github.io/Proyecto4_andrea/semana6/) | 01/10/2026 |
| 7 | [Actividad 7: viabilidad técnica y económica](https://and070406.github.io/Proyecto4_andrea/semana7/) | 08/10/2026 (act. 22/10) |
| 8 | [Actividad 8: prototipado y DFM](https://and070406.github.io/Proyecto4_andrea/semana8/) | 05/11/2026 |
| 9 | [Actividad 9: integración, go-to-market y pitch](https://and070406.github.io/Proyecto4_andrea/semana9/) | 06/11/2026 |
| Final | App web, firmware y simulador | 23/11/2026 |
| Final | Landing con los tres productos, Excel y esta página | 24/11/2026 |

**Bitácora de commits (resumen):** 30 commits entre el 21/08/2026 y el 06/11/2026. Los mensajes son genéricos ("actualiza", "aa"), así que no permiten seguir las sesiones de trabajo. **Pendiente:** desde ahora, un commit por sesión con un mensaje que diga qué cambió. Ejemplo: `landing: precio a $3,990 y tres productos`.

### C. Archivos de diseño: CAD, esquemáticos y firmware

| Archivo | Estado |
|---|---|
| [Firmware del sensor (`DistanciaCero_Sensor.ino`, v0.2-supermini)](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/firmware/DistanciaCero_Sensor.ino) | Se quitaron la red WiFi y la contraseña reales antes de publicarlo |
| [Simulador del sensor (`sim_dispositivo.py`)](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/firmware/sim_dispositivo.py) | Para probar el modo real de la app sin hardware |
| STL de la carcasa (variantes A y B) y planos | Entregados con la [Actividad 8](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-08/); **subir los STL al repositorio: PENDIENTE** |
| PCB | No aplica en el prototipo actual (sin PCB) |

**Conexiones (esquema del prototipo):**

| MPU6050 (GY-521) | ESP32-S3 Super Mini |
|---|---|
| VCC | 3V3 |
| GND | GND |
| SDA | GPIO 5 |
| SCL | GPIO 6 |
| LiPo 3.7 V | Pads B+ / B− (se carga por USB-C) |

**Cómo reproducir una unidad:**

1. En Arduino IDE instala el paquete **esp32** de Espressif y la biblioteca **PubSubClient**.
2. Elige la placa **ESP32S3 Dev Module** con **USB CDC On Boot: Enabled**.
3. Conecta el MPU6050 como en la tabla y suelda la LiPo a B+ / B−.
4. En el `.ino` escribe tu red WiFi de 2.4 GHz y el `OBJETO` (`sillon`, `baston` o `portavasos`).
5. Sube el código y abre el monitor serie a 115200: ahí aparece el código del sensor (por ejemplo, `DC-7F3A`).
6. Escribe ese código en la [app](https://jesushernandez2005.github.io/Proyecto4/app/) (Ajustes → Conexión al dispositivo).
7. Calibra con `DEBUG_MOV = true` y ajusta `UMBRAL_GIRO_DPS` y `UMBRAL_ACC_G`.

**Protocolo MQTT** (base: `distanciacero/<CÓDIGO>/`)

| Tema | Quién publica | Contenido |
|---|---|---|
| `conexion` (retenido) | ESP32 | `{"estado":"online"}`; si se desconecta, el broker publica `"offline"` |
| `estado` (retenido, cada 30 s) | ESP32 | batería, señal, `inactivoSeg`, `umbralMin`, `alerta` |
| `actividad` | ESP32 | un mensaje al inicio de cada episodio de movimiento |
| `cmd` | App | `umbral`, `reiniciar`, `identificar` |
| `app` | App | respuestas del cuidador, confirmaciones y botones del adulto mayor |

### D. Datos crudos de entrevistas y pruebas de usuario

- [Resultados de validación, semana 3 (PDF)](https://jesushernandez2005.github.io/Proyecto4/actividades/resultados_validacion_semana3.pdf): tres entrevistas con citas.
- Hoja **Entrevistas** del [Excel](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx).
- **Consentimiento de las entrevistas: PENDIENTE documentar** (cómo se pidió y si se puede publicar el nombre de pila).
- Pruebas con usuarios: **0 sesiones** (protocolo y hoja en la [Actividad 9](https://jesushernandez2005.github.io/Proyecto4/actividades/actividad-09/)).
- [Presentación final (PPTX)](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/DistanciaCero_presentacion_final.pptx) y [guion de pitch y demo (PDF)](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/anexos/DistanciaCero_guion_pitch_y_demo.pdf).

### E. Hojas de cálculo del modelo financiero

[DistanciaCero_costos_y_calculos.xlsx](https://jesushernandez2005.github.io/Proyecto4/proyecto-final-distanciacero/DistanciaCero_costos_y_calculos.xlsx), con las fórmulas visibles. Azul = dato capturado · negro = fórmula · verde = viene de otra hoja · amarillo = supuesto clave o celda por llenar.

| Hoja | Qué contiene |
|---|---|
| Resumen | Indicadores para la presentación y qué es dato y qué es supuesto |
| **Landing** | Cada número de la landing con su fórmula y su fuente |
| Supuestos | Precio, CAC, comisiones, tasa y costo operativo |
| Costos · BOM_final · DFM | BOM del producto, BOM del prototipo (por llenar) y DFM antes y después |
| Costos_DFS · Desarrollo · IA_costo | Costos D/F/S, ciclos de aprendizaje y costo de la IA |
| Precio_rango | Cost-plus, value-based, piso y techo |
| Economia_unitaria · Flujo_24m · Churn · Sensibilidad | CAC, LTV, payback, flujo a 24 meses, VPN y escenarios |
| Mercado · Entrevistas | TAM, SAM y SOM; las tres entrevistas |

### F. Bibliografía y fuentes de datos

- INEGI, ENIGH 2024 (hogares, ingreso y gasto).
- INEGI, Comunicado 475/19, ENADID 2018 (1.7 millones de personas de 60+ que viven solas).
- Coneval 2020 (hogares unipersonales de 65+), citado en la Actividad 4.
- Giraldo-Rodríguez et al., *Revista de Saúde Pública*, 2013 (piloto de teleasistencia en CDMX).
- Banxico, tipo de cambio FIX del 09/10/2026 ($18.4163 por USD).
- seniorliving.org, precios de Medical Guardian, consultado el 25/08/2026; security.org, planes de Ring, consultado el 28/09/2026.
- LCSC: SIM7600E-H LCC (C5338795) y ESP32-S3-WROOM-1-N8R8, consultado el 05/11/2026.
- Documentación de Espressif sobre el consumo del ESP32-S3, consultada el 06/11/2026.
- IMPI (MARCanet, SIGA), LATIPAT y Lens.org; patente MX 351729 B.
- Ley General de Economía Circular (vigente desde el 20/01/2026); NOM-001-SCFI-2018; Ley Federal de Protección al Consumidor.
- Entrevistas propias de la semana 3 (n = 3).