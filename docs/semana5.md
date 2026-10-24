# Semana 5
## Product Design Specification y Arquitectura del Sistema

**Tema:** DistanciaCero — PDS completo (16 requisitos), decisión de arquitectura de IA, diseño de sistema en 3 capas y viabilidad de manufactura
**Fecha:** 24/09/2026 · Actualizado 22/10/2026 (prompts y respuestas completos en la página)
**Blueprint:** Creación de valor → Factible
**DVF:** 🟢 Factible (arquitectura definida) · ⚠️ Riesgo de costo identificado (componente celular)

---

## 1. Objetivo de la actividad

Esta semana el enfoque cambia de mercado a diseño técnico: traducir todo lo validado hasta ahora (segmento, propuesta de valor, hueco Blue Ocean de semana 4) en un **Product Design Specification** formal — requerimientos funcionales, de desempeño, de interfaz y de restricción, cada uno con criterio de verificación explícito — y en la **arquitectura del sistema** que hace posible cumplirlos: dónde corre el modelo de IA, cómo se comunican los tres componentes, y si el diseño es fabricable en el volumen que necesita una prueba de mercado real (5-10 unidades).

---

## 2. Contexto del producto

- **Punto de partida:** un PDS preliminar con 2 requisitos por categoría, que armé con Claude (Prompt 1) a partir de la propuesta de valor y el Blue Ocean de la semana 4.
- **Lo que exige esta semana:** expandir a mínimo 4 requisitos por categoría con criterio de verificación explícito, tomar y justificar la decisión de arquitectura de IA (edge/cloud/híbrido), diseñar la arquitectura completa en 3 capas con protocolos específicos, y evaluar viabilidad de manufactura para 5-10 unidades — el mínimo que permite una prueba de mercado real, no un demo.

---

## 3. Desarrollo: mis prompts y las respuestas de la IA

Trabajé toda la semana con una sola IA, **Claude**, en una misma conversación. Abajo está cada prompt tal como lo escribí (incluidos mis errores de dedazo) y la respuesta completa que recibí. Las respuestas se despliegan con un clic.


---

### Prompt 1 — PDS preliminar (2 requisitos por categoría)

**IA utilizada:** Claude


??? question "Mi prompt (clic para desplegar)"
    ```text
    Ayudame a formar el PDS  de mi prodcuto, el cual incluya dos requirimientos de cada uno de los siiguientes: funcionales, de desempeño, de interfaz y de restriccion
    ```


??? example "Respuesta de Claude (clic para desplegar)"
    Vamos con el PDS (Product Design Specification) de DistanciaCero. Te lo armo con 2 requisitos por categoría, redactados de forma verificable (medible, con criterio de aceptación claro) porque eso es justo lo que hace que un PDS sea útil en semanas posteriores para validar contra prototipo real.

    ════════════════════════════════════════════════════════
    **PRODUCT DESIGN SPECIFICATION (PDS)**
    Producto: DistanciaCero
    ════════════════════════════════════════════════════════

    **1. REQUISITOS FUNCIONALES** — *qué debe hacer el producto*

    - **F1 — Detección de rutina y desviación:** El sistema debe registrar los patrones de actividad diaria del adulto mayor (movimiento, uso del objeto instrumentado) y generar una alerta al hijo/a solo cuando detecte una desviación significativa del patrón aprendido para esa persona específica — no una regla genérica fija para todos los usuarios.
    - **F2 — Notificación por excepción:** El sistema debe permanecer en silencio (sin notificación) mientras la rutina se mantenga dentro de los parámetros normales aprendidos, y enviar una alerta a la app del hijo/a en un tiempo máximo definido desde que se detecta la anomalía (a definir con dato real, ej. ≤10 minutos desde la desviación).

    **2. REQUISITOS DE DESEMPEÑO** — *qué tan bien debe hacerlo (medible)*

    - **D1 — Autonomía energética del artefacto:** El artefacto físico debe operar sin necesidad de recarga o cambio de batería durante un mínimo de X días continuos (definir X según el objeto elegido — bastón, sillón, taza — y el consumo real del microcontrolador + módulo celular/LoRa).
    - **D2 — Tasa de falsos positivos/negativos:** El algoritmo de detección de anomalías debe mantener una tasa de falsos positivos menor a Y% (para evitar fatiga de alertas, uno de los riesgos que tú mismo identificaste frente a los sensores DIY) y una tasa de falsos negativos menor a Z% (para no fallar justo en el momento crítico — el escenario de "silencio que no significa que todo está bien").

    **3. REQUISITOS DE INTERFAZ** — *cómo se conecta con otros sistemas/personas*

    - **I1 — Interfaz app-hijo/a:** La app debe mostrar, sin necesidad de configuración técnica por parte del usuario, un estado claro de "todo normal" / "alerta activa" y el historial reciente de actividad del adulto mayor, en un lenguaje no clínico y accesible para un usuario sin conocimientos técnicos.
    - **I2 — Interfaz artefacto-red de conectividad:** El artefacto debe comunicarse con la nube exclusivamente vía celular/LoRa propio (no WiFi doméstico), transmitiendo los datos de sensor de forma segura (cifrada) al backend donde corre el modelo de IA.

    **4. REQUISITOS DE RESTRICCIÓN** — *límites que no se pueden violar*

    - **R1 — Restricción de precio:** El costo recurrente para el usuario final no debe exceder el rango validado por el mercado ($300–$600 MXN/mes), dado que por encima de ese techo el análisis competitivo mostró pérdida de ventaja frente al sustituto más peligroso (llamadas + red informal, costo marginal cero).
    - **R2 — Restricción de autonomía del adulto mayor:** El diseño no puede requerir ninguna acción activa recurrente por parte del adulto mayor (login, presionar botón, cargar un dispositivo separado) — esta es la restricción de diseño más importante del proyecto, porque es precisamente el atributo que el Marco de las Cuatro Acciones marcó como ELIMINAR frente a la competencia.

    ────────────────────────────────────────────────────────

    Dos cosas que te conviene tener en cuenta al usar esto:

    1. **D1 y D2 tienen variables sin cifra (X, Y, Z).** No las inventé a propósito — son números que dependen de decisiones de ingeniería que tu equipo todavía no ha tomado (qué microcontrolador, qué algoritmo, qué objeto). Si tu profesor pide cifras concretas, esas sí las puedes definir con tu equipo basándote en los componentes reales que van a usar (ESP32/RP2350, capacidad de batería elegida, etc.) — eso es un dato tuyo, no de mercado.
    2. **R1 y R2 sí están anclados en evidencia de tu propio análisis** (el rango de precio del TAM/SAM/SOM y el Marco de las Cuatro Acciones del Blue Ocean), así que esos dos puedes defenderlos frente al profesor citando de dónde salen.


**Mi decisión:** usé este PDS como base. Quedaron dos variables sin cifra (X, Y, Z en D1 y D2) que resolví en el Prompt 3.

---

### Prompt 2 — ¿Qué tengo que hacer esta semana?

**IA utilizada:** Claude


??? question "Mi prompt (clic para desplegar)"
    ```text
    [Adjunté la guía de la semana 5]
    explicame que es lo que debo hacer esta semana:
    ```


??? example "Respuesta de Claude (clic para desplegar)"
    Esta semana (Semana 5) el enfoque cambia: ya no es mercado, es **diseño técnico** — traducir todo lo que ya validaste (segmento, propuesta de valor, hueco Blue Ocean) en requerimientos técnicos concretos y en la arquitectura del sistema que los va a cumplir.

    Se divide en tres partes:

    **1. PDS (Product Design Specification) — el documento base**

    Es el "contrato técnico" del equipo: qué debe hacer el producto y bajo qué condiciones se considera exitoso, en 4 categorías (funcional, desempeño, interfaz, restricción). Ya tienes el esqueleto que armamos hace rato con 2 por categoría — esta semana el mínimo sube a **4 por categoría**, y cada uno necesita un criterio de verificación explícito (alguien más, sin preguntarte a ti, tiene que poder confirmar si se cumple o no).

    Ahí mismo entra una distinción importante que marca el documento: no estás describiendo un **prototipo de exploración** (feo, inestable, lo usa el equipo) sino un **first-iteration product** (funciona autónomo, lo usa un usuario real sin que ustedes estén ahí explicando). Tu PDS tiene que reflejar ese nivel de ambición.

    **2. Arquitectura del sistema — el taller de 60 min**

    Aquí hay una decisión que se toma *antes* de dibujar nada: **¿dónde corre el modelo de IA?** Edge (en el ESP32/RPi), Cloud, o Híbrido — con 3 puntos de justificación técnica, guiados por 3 preguntas: conectividad del usuario en el punto de uso, si la respuesta necesita ser <1seg o puede esperar, y si los datos pueden salir del dispositivo o no.

    Con esa decisión tomada, se construye el diagrama de bloques en 3 capas (física/hardware, datos/cloud, presentación/app), cada flecha con su protocolo específico (MQTT, HTTP, BLE, WebSocket — no "se comunican" sin más).

    **3. Viabilidad de manufactura — la pregunta que muchos equipos se saltan**

    No es diseñar para producción en serie, es preguntar: **¿pueden reproducir su diseño 5-10 veces?** Eso implica revisar disponibilidad de componentes en México en esa cantidad, si el PCB es compatible con JLCPCB+PCBA (el punto dulce para este volumen), y si el costo por unidad (BOM) deja margen para el precio que tu segmento pagaría (regla: BOM ≤ 30% del precio de venta).

    ---

    **Lo que te toca entregar en casa (~4h):**

    | Entregable | Tiempo |
    |---|---|
    | PDS completo — mínimo 4 requerimientos por categoría, con verificación explícita | 1.5h |
    | Diagrama de arquitectura anotado (draw.io/Miro) con protocolos y capa de IA marcada | 1.5h |
    | BOM preliminar de componentes críticos, con fuente, precio y tiempo de entrega | 1h |

    Y al final debes poder responder sin improvisar: dónde corre tu IA y por qué, qué protocolo usas entre artefacto y backend y por qué, cuál es tu componente más difícil de conseguir y tu plan B, y qué diferencia tu entrega de un simple prototipo de exploración.

    ¿Quieres que empecemos por expandir tu PDS de 2 a 4 requisitos por categoría, o por la decisión de arquitectura (edge/cloud/híbrido) primero? Esa decisión en realidad condiciona varios de los requisitos de desempeño del PDS, así que si no la has tomado formalmente, te conviene resolverla antes.


**Mi decisión:** con esta explicación entendí que el PDS sube de 2 a 4 requisitos por categoría y que la decisión de arquitectura de IA condiciona los requisitos de desempeño, así que pedí completar las tres partes juntas en el siguiente prompt.

---

### Prompt 3 — PDS a 4 requisitos, arquitectura y viabilidad de manufactura

**IA utilizada:** Claude


??? question "Mi prompt (clic para desplegar)"
    ```text
    okey, ayudame a terminar lo que debo hacer esta semana y posteriormente documentarlo en mi pagina web, te adjunto el PDS que me diste: (modifica y añade lo que consideres necesario para cumplir con las actividades de esta semana)

    PDS “DistanciaCero”
    ════════════════════════════════════════════════════════
    PRODUCT DESIGN SPECIFICATION (PDS)
    Producto: DistanciaCero
    ════════════════════════════════════════════════════════
    1. REQUISITOS FUNCIONALES — qué debe hacer el producto

    * F1 — Detección de rutina y desviación: El sistema debe registrar los patrones de actividad diaria del adulto mayor (movimiento, uso del objeto instrumentado) y generar una alerta al hijo/a solo cuando detecte una desviación significativa del patrón aprendido para esa persona específica — no una regla genérica fija para todos los usuarios.
    * F2 — Notificación por excepción: El sistema debe permanecer en silencio (sin notificación) mientras la rutina se mantenga dentro de los parámetros normales aprendidos, y enviar una alerta a la app del hijo/a en un tiempo máximo definido desde que se detecta la anomalía (a definir con dato real, ej. ≤10 minutos desde la desviación).

    2. REQUISITOS DE DESEMPEÑO — qué tan bien debe hacerlo (medible)

    * D1 — Autonomía energética del artefacto: El artefacto físico debe operar sin necesidad de recarga o cambio de batería durante un mínimo de X días continuos (definir X según el objeto elegido — bastón, sillón, taza — y el consumo real del microcontrolador + módulo celular/LoRa).
    * D2 — Tasa de falsos positivos/negativos: El algoritmo de detección de anomalías debe mantener una tasa de falsos positivos menor a Y% (para evitar fatiga de alertas, uno de los riesgos que tú mismo identificaste frente a los sensores DIY) y una tasa de falsos negativos menor a Z% (para no fallar justo en el momento crítico — el escenario de "silencio que no significa que todo está bien").

    3. REQUISITOS DE INTERFAZ — cómo se conecta con otros sistemas/personas

    * I1 — Interfaz app-hijo/a: La app debe mostrar, sin necesidad de configuración técnica por parte del usuario, un estado claro de "todo normal" / "alerta activa" y el historial reciente de actividad del adulto mayor, en un lenguaje no clínico y accesible para un usuario sin conocimientos técnicos.
    * I2 — Interfaz artefacto-red de conectividad: El artefacto debe comunicarse con la nube exclusivamente vía celular/LoRa propio (no WiFi doméstico), transmitiendo los datos de sensor de forma segura (cifrada) al backend donde corre el modelo de IA.

    4. REQUISITOS DE RESTRICCIÓN — límites que no se pueden violar

    * R1 — Restricción de precio: El costo recurrente para el usuario final no debe exceder el rango validado por el mercado ($300–$600 MXN/mes), dado que por encima de ese techo el análisis competitivo mostró pérdida de ventaja frente al sustituto más peligroso (llamadas + red informal, costo marginal cero).
    * R2 — Restricción de autonomía del adulto mayor: El diseño no puede requerir ninguna acción activa recurrente por parte del adulto mayor (login, presionar botón, cargar un dispositivo separado) — esta es la restricción de diseño más importante del proyecto, porque es precisamente el atributo que el Marco de las Cuatro Acciones marcó como ELIMINAR frente a la competencia.

    ────────────────────────────────────────────────────────
    ```


??? example "Respuesta de Claude (clic para desplegar)"
    Vamos a completar las tres partes de esta semana (PDS a 4 requisitos, arquitectura, viabilidad de manufactura) y al final armamos el documento para tu sitio.

    #### 1. PDS completo — 4 requisitos por categoría

    ════════════════════════════════════════════════════════
    **PRODUCT DESIGN SPECIFICATION (PDS)**
    Producto: DistanciaCero · Versión: 1.0
    ════════════════════════════════════════════════════════

    **REQUISITOS FUNCIONALES**

    - **RF-01** — El sistema debe registrar los patrones de actividad diaria del adulto mayor y generar una alerta al hijo/a solo cuando detecte una desviación significativa del patrón aprendido para esa persona específica. *Verificación:* prueba con dataset simulado de 14 días de actividad "normal" + inyección de eventos anómalos controlados; el sistema debe alertar en los eventos inyectados y no alertar en los días normales.
    - **RF-02** — El sistema debe permanecer en silencio mientras la rutina esté dentro de parámetros normales, y enviar alerta a la app en ≤10 minutos desde que se detecta la anomalía. *Verificación:* medición de timestamp entre evento inyectado y notificación recibida en la app, en 10 corridas de prueba.
    - **RF-03 (nuevo)** — El sistema debe tener un periodo de aprendizaje inicial (baseline) de 10–14 días durante el cual solo recopila datos sin generar alertas de anomalía, para construir el patrón base individual. *Verificación:* revisar logs del backend — cero alertas emitidas durante los primeros 10 días de un despliegue nuevo.
    - **RF-04 (nuevo)** — El sistema debe almacenar y mostrar al hijo/a el historial de actividad de los últimos 30 días, incluso sin conexión a internet al momento de consultarlo. *Verificación:* activar modo avión en el teléfono de prueba y confirmar que el historial de 30 días sigue visible (cacheado localmente).

    **REQUISITOS DE DESEMPEÑO**

    - **RD-01** — El artefacto debe operar sin recarga durante un mínimo de **15 días continuos**. *Criterio:* con batería 18650 (~3,000 mAh) y consumo promedio estimado de 6-8 mA (sensor en duty-cycle + transmisión celular periódica), esto da ~15-20 días — dato a validar con medición real de consumo en el primer prototipo.
    - **RD-02** — Tasa de falsos positivos <5% y tasa de falsos negativos <2%. *Criterio:* medido sobre un set de prueba de mínimo 50 eventos simulados (25 normales, 25 anómalos); un falso negativo es más costoso que uno positivo, por eso el umbral es más estricto ahí.
    - **RD-03 (nuevo)** — El módulo debe transmitir cada reporte de estado al backend en ≤30 segundos bajo cobertura celular nominal. *Criterio:* medir con logs de timestamp del módulo celular en 20 transmisiones consecutivas; existe para no comprometer la vida de batería con transmisiones largas.
    - **RD-04 (nuevo)** — El backend debe mantener disponibilidad ≥99% mensual. *Criterio:* monitoreo de uptime del servicio en la nube — una caída del backend equivale a un "falso silencio", el riesgo más peligroso que el propio lienzo Blue Ocean señaló.

    **REQUISITOS DE INTERFAZ**

    - **RI-01** — La app debe mostrar, sin configuración técnica del usuario, un estado claro "todo normal"/"alerta activa" y el historial reciente, en lenguaje no clínico. *Verificación:* prueba de usabilidad con un usuario que no conoce el producto — debe interpretar correctamente la pantalla en <10 segundos sin explicación previa.
    - **RI-02** — El artefacto debe comunicarse con la nube exclusivamente vía celular propio (no WiFi doméstico), transmitiendo datos cifrados. *Verificación:* desconectar/no proveer WiFi en la prueba de campo y confirmar transmisión exitosa vía red celular; inspección de tráfico para confirmar cifrado TLS.
    - **RI-03 (nuevo)** — La app debe permitir configurar el artefacto (activación, verificación de señal, asociación a la cuenta) en un proceso guiado de máximo 10 minutos, sin que el adulto mayor participe. *Verificación:* cronometrar el proceso de onboarding con un usuario de prueba (hijo/a), sin ayuda del equipo.
    - **RI-04 (nuevo)** — El sistema debe enviar cada alerta por al menos dos canales (push notification + WhatsApp/SMS), para no depender de un solo canal. *Verificación:* simular fallo de un canal (notificaciones push desactivadas) y confirmar que el segundo canal sí llega.

    **REQUISITOS DE RESTRICCIÓN**

    - **RR-01** — El costo recurrente no debe exceder $300–$600 MXN/mes (rango validado en el análisis de mercado de semana 4). *Verificación:* revisión del modelo de precios contra este techo antes de cada cambio de pricing.
    - **RR-02** — El diseño no puede requerir ninguna acción activa recurrente del adulto mayor. *Verificación:* checklist de revisión de diseño — cualquier feature propuesta que requiera login, botón o carga de dispositivo separado se rechaza en revisión de arquitectura.
    - **RR-03 (nuevo)** — El sistema no debe transmitir ni almacenar audio ni video del adulto mayor — solo datos de movimiento/actividad agregados. *Verificación:* auditoría del esquema de datos en el backend — ningún campo de tipo audio/imagen/video debe existir en la base de datos.
    - **RR-04 (nuevo)** — El diseño de PCB y los componentes deben ser compatibles con fabricación JLCPCB + PCBA para un volumen de 5–10 unidades, sin componentes BGA ni pitch <0.5mm. *Verificación:* correr el DRC (Design Rule Check) de JLCPCB sobre el diseño antes de enviar a fabricar.

    ---

    #### 2. Decisión de arquitectura de IA: **Híbrido**

    **Justificación (3 puntos):**
    1. **Conectividad intermitente pero no nula** — el adulto mayor vive en una casa fija con cobertura celular razonable, pero no garantizada al 100%; el dispositivo necesita seguir funcionando (acumulando datos localmente) durante huecos de señal cortos, lo cual descarta un modelo 100% cloud.
    2. **La detección personalizada de rutina no cabe en el microcontrolador** — aprender el patrón individual de cada usuario a lo largo de semanas requiere más memoria y capacidad de cómputo de la que un ESP32/RP2350 puede sostener con actualizaciones continuas del modelo; ese trabajo pesado vive en la nube.
    3. **La latencia no es crítica en milisegundos** — el sistema tolera perfectamente 2-10 minutos entre evento y alerta (RF-02), así que no hay necesidad de inferencia en tiempo real en el dispositivo — el edge solo necesita hacer preprocesamiento simple (detectar "hubo movimiento sí/no" y agregarlo en ventanas de tiempo).

    ---

    #### 3. Arquitectura del sistema

    ════════════════════════════════════════════════════════
    **ARQUITECTURA DEL SISTEMA**
    Producto: DistanciaCero · Decisión de IA: **Híbrido**
    ════════════════════════════════════════════════════════

    **CAPA FÍSICA — Hardware**

    - **Microcontrolador principal:** ESP32-S3 — elegido sobre el RP2350 (que ya conocen del curso) porque tiene soporte más maduro de TensorFlow Lite Micro y mejor ecosistema de librerías para módulos celulares vía UART; el conocimiento de registros GPIO de bajo nivel que ya tienen con el RP2350 es directamente transferible.
    - **Sensores:**
      - Acelerómetro **MPU6050** — detecta patrones de movimiento/vibración del objeto instrumentado (bastón, sillón).
      - Sensor de movimiento **PIR HC-SR501** — detecta presencia/actividad en el radio del objeto, complementa al acelerómetro para reducir falsos negativos (RD-02).
    - **Comunicación:** módulo celular **SIM7600E-H (4G LTE, con fallback 3G/2G)** vía UART — elegido sobre NB-IoT/LTE-M porque la cobertura 4G comercial en México es más consistente hoy que las redes IoT dedicadas, y sobre LoRa porque LoRa requeriría un gateway propio cerca de la casa del adulto mayor, algo que el equipo no puede garantizar por usuario (viola RI-02 en la práctica).
    - **Alimentación:** batería **18650 Li-ion (~3,000 mAh)** con módulo de carga TP4056. Vida estimada: ~15-20 días (RD-01), asumiendo duty-cycling del sensor y transmisiones celulares breves y espaciadas.

    **CAPA DE DATOS — Backend/Cloud**

    - **Servicio de datos:** **Firebase** (Firestore + Cloud Functions + Firebase Cloud Messaging) — elegido sobre AWS IoT Core por menor complejidad operativa para un equipo de 4 personas sin DevOps dedicado, y porque FCM resuelve directamente el requisito de notificaciones push (RI-04).
    - **Modelo de IA:**
      - Qué hace: detección de anomalía de rutina individual (comparación contra baseline aprendido en los primeros 10-14 días — RF-03).
      - Dónde corre: **Cloud Function** (Python) — no edge, por la razón 2 de la decisión híbrida.
      - Input: reportes agregados de actividad (ventanas de 15-30 min) del ESP32.
      - Output: score de anomalía → si supera umbral, dispara evento de alerta.
      - Modelo: estadístico simple al inicio (z-score sobre baseline por hora del día), con espacio para evolucionar a un modelo más sofisticado (ej. Isolation Forest) una vez haya datos reales de varios usuarios.
    - **Protocolo hardware → backend: HTTPS REST** (no MQTT) — decisión que se aparta del ejemplo del curso, justificada porque el dispositivo transmite reportes periódicos poco frecuentes (cada 15-30 min), no streaming continuo; mantener una conexión MQTT persistente en un módulo celular gastaría batería innecesariamente (viola RD-01). El módulo SIM7600 abre conexión, transmite vía HTTPS POST, y cierra — patrón más eficiente en energía para este caso de uso.

    **CAPA DE PRESENTACIÓN — App**

    - **Tipo:** React Native — aprovecha el conocimiento de React que ya tiene el equipo, código único para Android/iOS.
    - **Vistas principales:**
      1. **Estado diario** — indicador grande "todo normal" / "alerta activa", última actividad detectada.
      2. **Historial (30 días)** — línea de tiempo de actividad, cacheada localmente (RF-04).
      3. **Configuración/onboarding** — activación del artefacto, verificación de señal celular (RI-03).
    - **Actualización de datos:** listeners en tiempo real de Firestore (no polling).
    - **Notificaciones:** push vía FCM + respaldo por WhatsApp Business API/Twilio (RI-04).

    **FLUJO DE DATOS — caso de uso principal**

    ```
    [Sensor MPU6050/PIR] → ESP32-S3: lectura cruda — I2C/GPIO — ~10ms
    [ESP32-S3] → SIM7600 (agregación ventana 15-30min) → Firebase: 
        reporte JSON vía HTTPS POST — ~2-5s (apertura conexión celular incl.)
    [Firebase Firestore] → Cloud Function (trigger on write): 
        invocación — ~200-500ms
    [Cloud Function] → modelo de anomalía: 
        inferencia estadística — ~50-100ms
    [Cloud Function] → FCM + Twilio (si hay anomalía): 
        despacho de alerta — ~1-2s
    [App del hijo/a]: recepción de notificación push/WhatsApp — ~1-3s adicional

    Latencia total extremo a extremo (caso con anomalía): ~5-10 segundos
      desde que el backend recibe el reporte — bien dentro del margen de
      RF-02 (≤10 minutos), con holgura amplia para variabilidad de red celular real.

    Funcionamiento sin conexión: el ESP32 sigue registrando datos localmente
      en flash durante huecos de señal cortos y los transmite en el
      siguiente ciclo de reporte disponible — no se pierden datos, solo
      se retrasa la sincronización.
    ```

    ---

    #### 4. Viabilidad de prototipo (5-10 unidades)

    **Volumen objetivo:** 8 unidades (dentro del rango 5-10 recomendado por el curso)

    | Componente crítico | Disponibilidad MX (≥10 uds) | En librería JLCPCB | Costo unitario (vol. 8-10) |
    |---|:--:|:--:|:--:|
    | SIM7600E-H (módulo celular) | ✅ Mouser/DigiKey, ~10-15 días | ⚠️ requiere integración manual (módulo, no SMD directo) | ~$350-450 MXN |
    | ESP32-S3 (módulo) | ✅ MercadoLibre/Mouser, <1 semana | ✅ | ~$90-130 MXN |
    | MPU6050 + PIR HC-SR501 | ✅ MercadoLibre, <1 semana | ✅ (MPU6050) / ⚠️ (PIR, módulo externo) | ~$100-150 MXN combinados |
    | Batería 18650 + TP4056 | ✅ MercadoLibre, <1 semana | N/A (no va en PCB) | ~$150-200 MXN |

    **Alternativa si el SIM7600 no es viable en volumen:** módulo SIM800C (2G) es más barato y más común en librerías JLCPCB, pero **no se recomienda** porque Telcel y AT&T ya descontinuaron 2G en México — quedaría inutilizable en producción real, no solo en prototipo.

    **BOM estimado por unidad (vol. 8-10):** ~$800-1,100 MXN (componentes electrónicos + PCB + carcasa impresa en 3D + ensamble)

    **Precio de venta mínimo viable (BOM ÷ 30%):** ~$2,700-3,700 MXN por unidad de hardware (pago único, separado de la suscripción mensual)

    **¿El segmento pagaría ese precio?** ⚠️ — está en el rango que ya se había estimado en el dimensionamiento de mercado de semana 4 ($2,000-4,000 MXN), pero en el extremo alto. El componente que más presiona el costo es el módulo celular (SIM7600) — vale la pena evaluar en semana 6-7 si un módulo NB-IoT más barato, una vez que se confirme cobertura NB-IoT real en zonas del segmento, permite bajar el BOM.

    **Proceso de manufactura recomendado:** JLCPCB + PCBA para la PCB principal (ESP32 + MPU6050 + circuitería de energía), con el módulo SIM7600 y el PIR integrados manualmente por header/conector — es un punto medio razonable dado que el módulo celular no siempre viene en formato SMD estándar de su librería.


**Resultado:** el PDS pasó a 16 requisitos (4 por categoría) con criterio de verificación, tomé la decisión de arquitectura **híbrida** con 3 puntos de justificación, y quedó la arquitectura en 3 capas con protocolos específicos (HTTPS REST en lugar de MQTT) y el análisis de viabilidad para 8 unidades. Los valores de autonomía (RD-01) y tasas de error (RD-02) son **supuestos de diseño a validar con el primer prototipo**, no mediciones.

---

### Prompt 4 — Preguntas de salida de la semana

**IA utilizada:** Claude


??? question "Mi prompt (clic para desplegar)"
    ```text
    responde estas preguntas: ¿Dónde corre el modelo de IA de su producto y por qué esa decisión?

    * ¿Qué protocolo de comunicación usa entre el artefacto y el backend, y por qué ese y no otro?
    * ¿Cuál es el componente de hardware más difícil de conseguir en México y cuál es el plan B?
    * ¿Cuál es la diferencia entre lo que entregarán en semana 13 y un prototipo de exploración?
    ```


??? example "Respuesta de Claude (clic para desplegar)"
    **¿Dónde corre el modelo de IA y por qué?**

    Corre en modo **híbrido**. El ESP32-S3 solo hace preprocesamiento simple en el dispositivo (agregar lecturas del acelerómetro y el PIR en ventanas de 15-30 minutos: "hubo movimiento sí/no"). El modelo que de verdad detecta la anomalía — comparar la actividad de hoy contra el patrón individual aprendido de esa persona — corre en una **Cloud Function**. La razón: aprender y mantener actualizado un patrón de rutina personalizado por usuario, semana tras semana, necesita más memoria y cómputo del que un microcontrolador puede sostener; y como el producto tolera hasta 10 minutos de latencia (no milisegundos), no hay ninguna presión técnica que obligue a meter esa inferencia en el dispositivo.

    **¿Qué protocolo usan entre el artefacto y el backend, y por qué?**

    **HTTPS REST**, no MQTT. La decisión se aparta a propósito del default del curso: MQTT tiene sentido cuando hay mensajes frecuentes y quieres mantener una conexión persistente de bajo costo — pero nuestro dispositivo transmite reportes espaciados (cada 15-30 min), no streaming continuo. Mantener abierta una conexión MQTT en un módulo celular todo ese tiempo gastaría batería sin necesidad; con HTTPS el módulo abre conexión, hace el POST, y la cierra — mejor para el requisito RD-01 (15 días sin recarga).

    **¿Cuál es el componente más difícil de conseguir en México, y el plan B?**

    El **módulo celular SIM7600E-H**. Está disponible vía Mouser/DigiKey pero con 10-15 días de entrega (el más lento de los cuatro componentes críticos) y no está en la librería estándar de JLCPCB, así que hay que integrarlo manualmente por conector en vez de ensamblarlo automático. El plan B evaluado y descartado fue el SIM800C (2G) — más barato y más fácil de conseguir, pero Telcel y AT&T ya apagaron sus redes 2G en México, así que serviría solo para pruebas de laboratorio, no para un despliegue real en casa de un usuario. Si el SIM7600 sigue siendo un cuello de botella, el siguiente plan B real sería evaluar un módulo NB-IoT una vez que se confirme cobertura de esa red en zonas específicas del segmento — pendiente de validar, no resuelto todavía.

    **¿Cuál es la diferencia entre lo que entregarán en semana 13 y un prototipo de exploración?**

    Un prototipo de exploración serviría solo para responder "¿funciona el principio?" — por ejemplo, el ESP32 conectado a una laptop mostrando lecturas del acelerómetro en una terminal, operado por nosotros. Lo que define el PDS de esta semana es un **first-iteration product**: el sistema completo (artefacto + app + backend) instalado en la casa de un adulto mayor real, funcionando de forma autónoma durante semanas, sin que el equipo esté presente explicando nada — el adulto mayor no hace login ni presiona botones (RR-02), y el hijo/a recibe alertas reales por excepción sin que nosotros estemos monitoreando el sistema por detrás. La prueba de éxito no es "corrió una vez en la demo", es que un usuario que nunca nos ha visto pueda usarlo solo.


---

### Prompt 5 — PDS en el formato oficial del curso

**IA utilizada:** Claude


??? question "Mi prompt (clic para desplegar)"
    ```text
    [Adjunté la plantilla oficial del PDS]
    perfecto por ultimo necesito que añadas esto, pero ya modificado con la informacio que obtuviste de la ctividad: PRODUCT DESIGN SPECIFICATION
    Producto: _____________________ Versión: 1.0
    Equipo: _______________________ Fecha: _______

    REQUERIMIENTOS FUNCIONALES
    RF-01: [El sistema debe...] — Verificación: [cómo se verifica]
    RF-02: [El sistema debe...] — Verificación: [cómo se verifica]
    RF-03: [El sistema debe...] — Verificación: [cómo se verifica]
    RF-04: [El sistema debe...] — Verificación: [cómo se verifica]

    REQUERIMIENTOS DE DESEMPEÑO
    RD-01: [El sistema debe...] — Criterio: [valor numérico + condición]
    RD-02: [El sistema debe...] — Criterio: [valor numérico + condición]
    RD-03: [El sistema debe...] — Criterio: [valor numérico + condición]
    RD-04: [El sistema debe...] — Criterio: [valor numérico + condición]

    REQUERIMIENTOS DE INTERFAZ
    RI-01: [La interfaz debe...] — Verificación: [cómo se verifica]
    RI-02: [La interfaz debe...] — Verificación: [cómo se verifica]
    RI-03: [La interfaz debe...] — Verificación: [cómo se verifica]
    RI-04: [La interfaz debe...] — Verificación: [cómo se verifica]

    REQUERIMIENTOS DE RESTRICCIÓN
    RR-01: [El sistema no debe / debe cumplir...] — Verificación:
    RR-02: [El sistema no debe / debe cumplir...] — Verificación:
    RR-03: [El sistema no debe / debe cumplir...] — Verificación:
    RR-04: [El sistema no debe / debe cumplir...] — Verificación:

    DIAGRAMA DE ARQUITECTURA: [link a draw.io / Miro / imagen]
    BOM PRELIMINAR: [link a hoja de cálculo]


    Añadelo hasta el ultimo como resultado final, que se vea bien  en la pagina y sin necesidad de descargar el archivo
    ```


??? example "Respuesta de Claude (clic para desplegar)"
    Listo, agregado como sección final "Entregable final — Product Design Specification": el mismo formato oficial del curso (Producto/Versión/Equipo/Fecha, luego RF/RD/RI/RR) pero completamente lleno con el contenido real que ya construimos, en tablas — se ve directo en la página, nada que descargar.

    Dos cosas que dejé honestas a propósito ahí:

    - **"Equipo: Jesús + equipo DistanciaCero"** — no tengo el nombre real de tu equipo, cámbialo por el que corresponda.
    - **Diagrama de arquitectura y BOM preliminar** quedaron marcados ⚠️ **pendientes**, no con un link falso — porque el curso pide el diagrama en draw.io/Miro y el BOM en hoja de cálculo como archivos aparte, y esos dos todavía no existen. El contenido para hacerlos ya está completo arriba en el documento (la arquitectura en 3 capas y la tabla de componentes críticos); solo falta que los traslades a esas herramientas.

    *(El PDS completo que Claude generó en esta respuesta está al final de esta página, en "Entregable final — Product Design Specification".)*


---

## 4. PDS completo — DistanciaCero v1.0

**REQUISITOS FUNCIONALES**

| ID | Requisito | Verificación |
|---|---|---|
| RF-01 | Detectar desviación significativa del patrón de rutina aprendido por persona | Dataset simulado de 14 días + eventos anómalos inyectados |
| RF-02 | Silencio mientras rutina es normal; alerta en ≤10 min desde detección | Medición de timestamp evento→notificación en 10 corridas |
| RF-03 | Periodo de aprendizaje inicial (baseline) de 10-14 días sin alertas | Revisión de logs — cero alertas en los primeros 10 días |
| RF-04 | Historial de 30 días accesible incluso sin conexión | Prueba en modo avión — historial visible (cache local) |

**REQUISITOS DE DESEMPEÑO**

| ID | Requisito | Criterio |
|---|---|---|
| RD-01 | Autonomía sin recarga ≥15 días | Batería 18650 (~3,000 mAh), consumo estimado 6-8 mA promedio |
| RD-02 | Falsos positivos <5%, falsos negativos <2% | Set de prueba de 50 eventos simulados (25/25) |
| RD-03 | Transmisión de reporte al backend en ≤30s (cobertura nominal) | Logs de timestamp del módulo celular, 20 transmisiones |
| RD-04 | Disponibilidad de backend ≥99% mensual | Monitoreo de uptime del servicio en la nube |

**REQUISITOS DE INTERFAZ**

| ID | Requisito | Verificación |
|---|---|---|
| RI-01 | Estado claro "normal"/"alerta" sin configuración técnica, lenguaje no clínico | Prueba de usabilidad — interpretación correcta en <10s |
| RI-02 | Comunicación exclusivamente celular (no WiFi doméstico), datos cifrados | Prueba de campo sin WiFi + inspección de tráfico TLS |
| RI-03 | Onboarding guiado ≤10 min, sin participación activa del adulto mayor | Cronometraje del proceso con usuario de prueba |
| RI-04 | Alerta por ≥2 canales (push + WhatsApp/SMS) | Simular fallo de un canal, confirmar llegada por el otro |

**REQUISITOS DE RESTRICCIÓN**

| ID | Requisito | Verificación |
|---|---|---|
| RR-01 | Costo recurrente dentro de $300-$600 MXN/mes | Revisión del modelo de precios contra este techo |
| RR-02 | Ninguna acción activa recurrente requerida del adulto mayor | Checklist de revisión de diseño en cada feature nueva |
| RR-03 | Sin transmisión ni almacenamiento de audio/video | Auditoría del esquema de datos del backend |
| RR-04 | Compatible con JLCPCB+PCBA para 5-10 unidades, sin BGA ni pitch <0.5mm | DRC de JLCPCB sobre el diseño antes de fabricar |

---

## 5. Decisión de arquitectura de IA

**✓ HÍBRIDO — decisión tomada y justificada**

| Pregunta guía del curso | Respuesta para DistanciaCero |
|---|---|
| ¿Conectividad estable en el punto de uso? | Intermitente pero no nula — descarta cloud puro |
| ¿Respuesta en <1s o puede esperar 2-5s+? | Tolera minutos (RF-02: ≤10 min) — no exige edge puro |
| ¿Los datos pueden salir del dispositivo? | Sí, con cifrado (RI-02) — no hay restricción de privacidad que fuerce todo a edge |

**Justificación en 3 puntos:**
1. **Conectividad intermitente pero no nula** — el dispositivo necesita acumular datos localmente durante huecos de señal cortos; un modelo 100% cloud fallaría en esos momentos.
2. **La detección personalizada de rutina no cabe en el microcontrolador** — aprender el patrón individual a lo largo de semanas requiere más memoria y cómputo del que un ESP32/RP2350 puede sostener con actualizaciones continuas.
3. **Latencia tolerable en minutos, no milisegundos** — RF-02 permite hasta 10 minutos entre evento y alerta, así que no hace falta inferencia en tiempo real en el dispositivo; el edge solo hace preprocesamiento simple.

---

## 6. Arquitectura del sistema

<div style="margin:1rem 0"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 1280" role="img" aria-label="Arquitectura de DistanciaCero en tres capas: física, datos y presentación" style="width:100%;max-width:1000px;height:auto;font-family:Segoe UI,Roboto,Helvetica,Arial,sans-serif"><defs><filter id="sh" x="-10%" y="-10%" width="125%" height="130%"><feDropShadow dx="0" dy="3" stdDeviation="3" flood-color="#0f172a" flood-opacity="0.18"/></filter><marker id="ar" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="context-stroke"/></marker><linearGradient id="g1" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#0ea5e9"/><stop offset="1" stop-color="#2563eb"/></linearGradient><linearGradient id="g2" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#f59e0b"/><stop offset="1" stop-color="#ea580c"/></linearGradient><linearGradient id="g3" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#a855f7"/><stop offset="1" stop-color="#7c3aed"/></linearGradient><linearGradient id="g4" x1="0" y1="0" x2="1" y2="0"><stop offset="0" stop-color="#10b981"/><stop offset="1" stop-color="#059669"/></linearGradient></defs><rect width="1000" height="1280" rx="22" fill="#f8fafc"/><text x="500" y="48" font-size="28" fill="#0f172a" font-weight="800" text-anchor="middle" >DistanciaCero · Arquitectura del sistema</text><text x="500" y="74" font-size="15" fill="#475569" font-weight="500" text-anchor="middle" >IA híbrida: el dispositivo preprocesa, la nube detecta la anomalía</text><rect x="30" y="100" width="940" height="360" rx="22" fill="#e0f2fe" stroke="#0284c7" stroke-width="3"/><rect x="30" y="100" width="940" height="42" rx="22" fill="url(#g1)"/><rect x="30" y="122" width="940" height="20" fill="url(#g1)"/><text x="500" y="128" font-size="18" fill="#ffffff" font-weight="700" text-anchor="middle" >CAPA 1 · FÍSICA  —  el reposabrazos «Reposabrazos Centinela»</text><rect x="55" y="170" width="170" height="86" rx="14" fill="#ffffff" stroke="#0284c7" stroke-width="2.5" filter="url(#sh)"/><text x="140.0" y="196" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >MPU6050</text><text x="140.0" y="218" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Acelerómetro</text><text x="140.0" y="236" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >vibración / movimiento</text><rect x="55" y="272" width="170" height="86" rx="14" fill="#ffffff" stroke="#0284c7" stroke-width="2.5" filter="url(#sh)"/><text x="140.0" y="298" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >PIR HC-SR501</text><text x="140.0" y="320" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Sensor de presencia</text><text x="140.0" y="338" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >actividad en el radio</text><rect x="55" y="374" width="170" height="70" rx="14" fill="#ffffff" stroke="#16a34a" stroke-width="2.5" filter="url(#sh)"/><text x="140.0" y="400" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >Batería 18650</text><text x="140.0" y="422" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >+ TP4056 · ~3,000 mAh</text><text x="140.0" y="440" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >≥15 días sin recarga</text><rect x="330" y="222" width="210" height="140" rx="14" fill="#fef9c3" stroke="#ca8a04" stroke-width="2.5" filter="url(#sh)"/><text x="435.0" y="248" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >ESP32-S3</text><text x="435.0" y="270" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Preprocesamiento en el borde</text><text x="435.0" y="288" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Agrega en ventanas</text><text x="435.0" y="306" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >de 15–30 min</text><text x="435.0" y="324" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >«hubo movimiento sí/no»</text><text x="435.0" y="342" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Guarda en flash sin señal</text><rect x="640" y="222" width="200" height="140" rx="14" fill="#ffffff" stroke="#0284c7" stroke-width="2.5" filter="url(#sh)"/><text x="740.0" y="248" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >SIM7600E-H</text><text x="740.0" y="270" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Módulo celular 4G</text><text x="740.0" y="288" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >(fallback 3G/2G)</text><text x="740.0" y="306" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >No depende del WiFi</text><text x="740.0" y="324" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >de la casa</text><line x1="225" y1="213" x2="330" y2="262" stroke="#0284c7" stroke-width="3.2" marker-end="url(#ar)"/><rect x="226.0" y="209" width="84.0" height="20" rx="10" fill="#ffffff" stroke="#0284c7" stroke-width="1.2"/><text x="268" y="224" font-size="11.5" fill="#0284c7" font-weight="600" text-anchor="middle" >I²C / GPIO</text><line x1="225" y1="315" x2="330" y2="315" stroke="#0284c7" stroke-width="3.2" marker-end="url(#ar)"/><rect x="249.4" y="293" width="55.2" height="20" rx="10" fill="#ffffff" stroke="#0284c7" stroke-width="1.2"/><text x="277" y="308" font-size="11.5" fill="#0284c7" font-weight="600" text-anchor="middle" >~10 ms</text><line x1="225" y1="409" x2="330" y2="340" stroke="#16a34a" stroke-width="3.2" marker-end="url(#ar)"/><rect x="236.8" y="379" width="62.4" height="20" rx="10" fill="#ffffff" stroke="#16a34a" stroke-width="1.2"/><text x="268" y="394" font-size="11.5" fill="#16a34a" font-weight="600" text-anchor="middle" >energía</text><line x1="540" y1="292" x2="640" y2="292" stroke="#0284c7" stroke-width="3.2" marker-end="url(#ar)"/><rect x="569.6" y="269" width="40.8" height="20" rx="10" fill="#ffffff" stroke="#0284c7" stroke-width="1.2"/><text x="590" y="284" font-size="11.5" fill="#0284c7" font-weight="600" text-anchor="middle" >UART</text><g stroke="#0284c7" stroke-width="3" fill="none" stroke-linecap="round"><path d="M905 255 L905 330"/><path d="M885 340 L905 255 L925 340"/><path d="M880 245 q25 -22 50 0"/><path d="M866 228 q39 -34 78 0"/></g><circle cx="905" cy="255" r="6" fill="#0284c7"/><text x="905" y="362" font-size="13" fill="#0369a1" font-weight="700" text-anchor="middle" >Red celular</text><line x1="840" y1="292" x2="880" y2="292" stroke="#0284c7" stroke-width="3.2" marker-end="url(#ar)"/><line x1="740" y1="364" x2="740" y2="516" stroke="#ea580c" stroke-width="3.2" marker-end="url(#ar)"/><rect x="557.6" y="477" width="364.8" height="20" rx="10" fill="#ffffff" stroke="#ea580c" stroke-width="1.2"/><text x="740" y="492" font-size="11.5" fill="#ea580c" font-weight="600" text-anchor="middle" >HTTPS POST · JSON · TLS · cada 15–30 min · ~2–5 s</text><g transform="translate(0,40)"><rect x="30" y="480" width="940" height="360" rx="22" fill="#ffedd5" stroke="#ea580c" stroke-width="3"/><rect x="30" y="480" width="940" height="42" rx="22" fill="url(#g2)"/><rect x="30" y="502" width="940" height="20" fill="url(#g2)"/><text x="500" y="508" font-size="18" fill="#ffffff" font-weight="700" text-anchor="middle" >CAPA 2 · DATOS  —  Firebase (nube)</text><rect x="55" y="560" width="200" height="110" rx="14" fill="#ffffff" stroke="#ea580c" stroke-width="2.5" filter="url(#sh)"/><text x="155.0" y="586" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >Firestore</text><text x="155.0" y="608" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Guarda el reporte</text><text x="155.0" y="626" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >y el baseline</text><text x="155.0" y="644" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >de cada persona</text><rect x="305" y="560" width="200" height="110" rx="14" fill="#ffffff" stroke="#ea580c" stroke-width="2.5" filter="url(#sh)"/><text x="405.0" y="586" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >Cloud Function</text><text x="405.0" y="608" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Python · se dispara</text><text x="405.0" y="626" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >al escribir un reporte</text><text x="405.0" y="644" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >(orquesta el flujo)</text><rect x="555" y="545" width="230" height="140" rx="14" fill="#fef3c7" stroke="#d97706" stroke-width="2.5" filter="url(#sh)"/><text x="670.0" y="571" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >🧠 Modelo de anomalía</text><text x="670.0" y="593" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Estadístico · z-score</text><text x="670.0" y="611" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >vs baseline por hora</text><text x="670.0" y="629" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Aprende 10–14 días</text><text x="670.0" y="647" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >sin alertas (RF-03)</text><rect x="330" y="720" width="210" height="90" rx="14" fill="#ffffff" stroke="#ea580c" stroke-width="2.5" filter="url(#sh)"/><text x="435.0" y="746" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >Twilio / WhatsApp</text><text x="435.0" y="768" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Canal de respaldo</text><text x="435.0" y="786" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >(RI-04: ≥2 canales)</text><rect x="585" y="720" width="200" height="90" rx="14" fill="#ffffff" stroke="#ea580c" stroke-width="2.5" filter="url(#sh)"/><text x="685.0" y="746" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >FCM</text><text x="685.0" y="768" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Push al teléfono</text><text x="685.0" y="786" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >del hijo/a</text><line x1="255" y1="615" x2="305" y2="615" stroke="#ea580c" stroke-width="3.2" marker-end="url(#ar)"/><rect x="223.6" y="585" width="112.8" height="20" rx="10" fill="#ffffff" stroke="#ea580c" stroke-width="1.2"/><text x="280" y="600" font-size="11.5" fill="#ea580c" font-weight="600" text-anchor="middle" >trigger ~0.3 s</text><line x1="505" y1="615" x2="555" y2="615" stroke="#d97706" stroke-width="3.2" marker-end="url(#ar)"/><rect x="502.4" y="585" width="55.2" height="20" rx="10" fill="#ffffff" stroke="#d97706" stroke-width="1.2"/><text x="530" y="600" font-size="11.5" fill="#d97706" font-weight="600" text-anchor="middle" >~0.1 s</text><line x1="640" y1="685" x2="500" y2="718" stroke="#ea580c" stroke-width="3.2" marker-end="url(#ar)"/><line x1="685" y1="685" x2="685" y2="718" stroke="#ea580c" stroke-width="3.2" marker-end="url(#ar)"/><rect x="697" y="692" width="96" height="20" rx="10" fill="#ffffff" stroke="#ea580c" stroke-width="1.2"/><text x="745" y="706" font-size="11.5" fill="#ea580c" font-weight="600" text-anchor="middle" >si hay anomalía</text><rect x="805" y="560" width="145" height="250" rx="16" fill="#ffffff" stroke="#d97706" stroke-width="2" stroke-dasharray="6 4"/><text x="877" y="590" font-size="14" fill="#b45309" font-weight="800" text-anchor="middle" >¿Por qué híbrida?</text><text x="877" y="614" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >① Señal celular</text><text x="877" y="634" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >intermitente:</text><text x="877" y="654" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >el borde guarda</text><text x="877" y="674" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >② Aprender la rutina</text><text x="877" y="694" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >de cada persona</text><text x="877" y="714" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >no cabe en un</text><text x="877" y="734" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >microcontrolador</text><text x="877" y="754" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >③ Latencia tolerable:</text><text x="877" y="774" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >minutos, no ms</text><line x1="155" y1="672" x2="155" y2="886" stroke="#7c3aed" stroke-width="3.2" marker-end="url(#ar)"/><rect x="115.2" y="853" width="249.6" height="20" rx="10" fill="#ffffff" stroke="#7c3aed" stroke-width="1.2"/><text x="240" y="868" font-size="11.5" fill="#7c3aed" font-weight="600" text-anchor="middle" >Firestore listeners · tiempo real</text><line x1="435" y1="812" x2="435" y2="886" stroke="#7c3aed" stroke-width="3.2" marker-end="url(#ar)"/><line x1="685" y1="812" x2="685" y2="886" stroke="#7c3aed" stroke-width="3.2" marker-end="url(#ar)"/><rect x="592.6" y="853" width="184.8" height="20" rx="10" fill="#ffffff" stroke="#7c3aed" stroke-width="1.2"/><text x="685" y="868" font-size="11.5" fill="#7c3aed" font-weight="600" text-anchor="middle" >push + WhatsApp · ~1–3 s</text><rect x="30" y="890" width="940" height="200" rx="22" fill="#f3e8ff" stroke="#7c3aed" stroke-width="3"/><rect x="30" y="890" width="940" height="42" rx="22" fill="url(#g3)"/><rect x="30" y="912" width="940" height="20" fill="url(#g3)"/><text x="500" y="918" font-size="18" fill="#ffffff" font-weight="700" text-anchor="middle" >CAPA 3 · PRESENTACIÓN  —  app del hijo/a (React Native)</text><rect x="55" y="950" width="270" height="120" rx="14" fill="#ffffff" stroke="#7c3aed" stroke-width="2.5" filter="url(#sh)"/><text x="190.0" y="976" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >① Estado diario</text><text x="190.0" y="998" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Grande y claro:</text><text x="190.0" y="1016" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >🟢 «Todo normal»</text><text x="190.0" y="1034" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >🔴 «Alerta activa»</text><text x="190.0" y="1052" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Lenguaje no clínico</text><rect x="355" y="950" width="270" height="120" rx="14" fill="#ffffff" stroke="#7c3aed" stroke-width="2.5" filter="url(#sh)"/><text x="490.0" y="976" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >② Historial 30 días</text><text x="490.0" y="998" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Línea de tiempo</text><text x="490.0" y="1016" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Cacheada en el teléfono:</text><text x="490.0" y="1034" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >se ve incluso sin</text><text x="490.0" y="1052" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >conexión (RF-04)</text><rect x="655" y="950" width="295" height="120" rx="14" fill="#ffffff" stroke="#7c3aed" stroke-width="2.5" filter="url(#sh)"/><text x="802.5" y="976" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >③ Onboarding ≤ 10 min</text><text x="802.5" y="998" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Activar el artefacto,</text><text x="802.5" y="1016" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >verificar señal celular,</text><text x="802.5" y="1034" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >asociar la cuenta</text><text x="802.5" y="1052" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >sin ayuda del adulto mayor</text></g><rect x="30" y="1150" width="940" height="100" rx="20" fill="url(#g4)" filter="url(#sh)"/><text x="500" y="1188" font-size="24" fill="#ffffff" font-weight="800" text-anchor="middle" >⏱ Latencia total con anomalía: ~5–10 segundos</text><text x="500" y="1218" font-size="15" fill="#ecfdf5" font-weight="500" text-anchor="middle" >Límite del requisito RF-02: ≤ 10 minutos · holgura de más de 50×</text><text x="500" y="1238" font-size="13" fill="#d1fae5" font-weight="500" text-anchor="middle" >Sin acciones del adulto mayor (RR-02) · sin audio ni video (RR-03)</text></svg></div>

*Figura 1. Arquitectura de DistanciaCero en tres capas, con protocolo y latencia en cada flecha. Versión en texto, abajo.*

```
┌─────────────────────────────────────────────────────────────────┐
│                    CAPA FÍSICA (Hardware)                       │
│                                                                 │
│  [MPU6050 accel]──┐                                             │
│  [PIR HC-SR501]───┼──[ESP32-S3]──[SIM7600E-H]──(red celular)    │
│  [Batería 18650    │   preprocesamiento                         │
│   + TP4056]────────┘   (agregación ventana 15-30min)            │
└─────────────────────────────────┬───────────────────────────────┘
                                  │ HTTPS POST (JSON, periódico)
┌─────────────────────────────────▼───────────────────────────────┐
│                    CAPA DE DATOS (Firebase)                     │
│                                                                 │
│  [Firestore]──trigger──[Cloud Function]──[Modelo anomalía]      │
│  (guarda reporte)      (orquesta)         (z-score vs baseline) │
│                              │                                  │
│                    [FCM] + [Twilio/WhatsApp]                    │
│                    (si hay anomalía → despacha alerta)          │
└─────────────────────────────────┬───────────────────────────────┘
                                  │ Firestore listeners (tiempo real)
┌─────────────────────────────────▼───────────────────────────────┐
│                    CAPA DE PRESENTACIÓN (App)                   │
│                                                                 │
│  [React Native]──3 vistas: Estado diario / Historial 30d /       │
│                              Onboarding                          │
│  Notificaciones: push (FCM) + WhatsApp (respaldo)                │
└─────────────────────────────────────────────────────────────────┘
```

**Decisiones de componente clave, con justificación:**

| Componente | Elección | Por qué (y qué se descartó) |
|---|---|---|
| Microcontrolador | ESP32-S3 | Soporte más maduro de TFLite Micro que RP2350; conocimiento de GPIO del equipo (curso de Sistemas Embebidos) es transferible |
| Conectividad | SIM7600E-H (4G, fallback 3G/2G) | LoRa se descartó — requeriría gateway propio cerca de cada casa, inviable por usuario. NB-IoT se descartó por cobertura incierta en México hoy |
| Backend | Firebase (Firestore + Cloud Functions + FCM) | Menor complejidad operativa que AWS IoT Core para un equipo de 4 sin DevOps dedicado; FCM resuelve RI-04 directamente |
| Protocolo hardware→backend | HTTPS REST | Se aparta del ejemplo del curso (MQTT) — justificado: transmisión poco frecuente (15-30 min), MQTT persistente gastaría batería innecesaria (RD-01) |

**Flujo de datos — caso de uso principal (con anomalía detectada):**

| Paso | Componente | Mecanismo | Latencia est. |
|---|---|---|---|
| 1 | Sensores → ESP32-S3 | I2C/GPIO | ~10 ms |
| 2 | ESP32-S3 → Firebase | HTTPS POST vía SIM7600 | ~2-5 s |
| 3 | Firestore → Cloud Function | Trigger on write | ~200-500 ms |
| 4 | Cloud Function → modelo | Inferencia estadística | ~50-100 ms |
| 5 | Cloud Function → FCM/Twilio | Despacho de alerta | ~1-2 s |
| 6 | App del hijo/a | Recepción push/WhatsApp | ~1-3 s |

**Latencia total extremo a extremo:** ~5-10 segundos — muy por debajo del margen de RF-02 (≤10 minutos).

**Funcionamiento sin conexión:** el ESP32 sigue registrando en flash local durante huecos de señal y transmite en el siguiente ciclo disponible — no se pierden datos, solo se retrasa la sincronización.

---

## 7. Viabilidad de prototipo (5-10 unidades)

**Volumen objetivo:** 8 unidades

| Componente crítico | Disponibilidad MX (≥10 uds) | En librería JLCPCB | Costo unitario (vol. 8-10) |
|---|:--:|:--:|:--:|
| SIM7600E-H (celular 4G) | ✅ Mouser/DigiKey, 10-15 días | ⚠️ integración manual | ~$350-450 MXN |
| ESP32-S3 | ✅ MercadoLibre/Mouser, <1 sem | ✅ | ~$90-130 MXN |
| MPU6050 + PIR HC-SR501 | ✅ MercadoLibre, <1 sem | ✅ / ⚠️ | ~$100-150 MXN |
| Batería 18650 + TP4056 | ✅ MercadoLibre, <1 sem | N/A | ~$150-200 MXN |

**Alternativa evaluada y descartada:** módulo SIM800C (2G) — más barato y más estándar en librería JLCPCB, pero Telcel y AT&T ya descontinuaron 2G en México; serviría para un prototipo de laboratorio pero no para una prueba de mercado real con usuarios en sus casas.

| Métrica | Valor |
|---|---|
| BOM estimado por unidad (vol. 8-10) | ~$800-1,100 MXN |
| Precio de venta mínimo viable (BOM ÷ 30%) | ~$2,700-3,700 MXN |
| ¿Cae dentro del rango ya estimado en semana 4 ($2,000-4,000 MXN)? | ⚠️ Sí, pero en el extremo alto |
| Proceso recomendado | JLCPCB + PCBA para PCB principal; SIM7600 y PIR integrados manualmente por conector |

!!! warning "Actualización (semana 7): el BOM real es mayor"
    Al cotizar el módulo celular en una fuente real, el SIM7600E-H (breakout con antena) cuesta ~$2,100 MXN y no los ~$350-450 MXN estimados aquí. El BOM por unidad pasa de ~$800-1,100 MXN a ~$2,970 MXN, y el precio mínimo viable sube en consecuencia. El detalle está en la Semana 7.

---

## 8. Veredicto de la semana

**QUEDA RESUELTO:** decisión de arquitectura de IA tomada y justificada con los 3 criterios que pide el curso · arquitectura completa en 3 capas con componentes y protocolos específicos, no genéricos · flujo de datos extremo a extremo dentro del margen del requisito funcional (RF-02) con holgura amplia · componentes disponibles en México en volumen 8-10 con tiempos de entrega razonables.

**QUEDA PENDIENTE:** el BOM del hardware presiona el precio mínimo viable hacia el extremo alto del rango que el mercado (semana 4) ya mostró que está dispuesto a pagar — no es un problema resuelto, es una tensión de diseño real que las próximas semanas tienen que negociar, probablemente optimizando o sustituyendo el módulo celular. Los valores de RD-01 (autonomía) y RD-02 (tasas de error) son **supuestos de diseño razonados**, no mediciones — quedan por validar con el primer prototipo físico.

**Próximo paso:** si el curso exige el archivo editable, trasladar el diagrama de la sección 6 a draw.io/Miro; medir consumo real de batería en el primer prototipo, y confirmar cobertura celular real (4G) en al menos una ubicación representativa del segmento antes de comprometerse con el SIM7600E-H para la tirada de 8 unidades.


---

## 9. ¿Qué aprendí?

Lo que más me quedó de esta semana es que un PDS no es una lista de buenas intenciones — es solo tan útil como su criterio de verificación. Los primeros dos requisitos por categoría que ya tenía sonaban bien, pero al pasarlos por el diagnóstico formal (bien redactado / con problema / faltante) varios necesitaron números concretos que antes no tenía (los 15 días de batería, el ≤30s de transmisión, el ≥99% de uptime). Lo más útil fue notar que esos números, aunque son supuestos de diseño y no datos de mercado verificados, sí tienen que estar razonados — no puse "15 días" porque sonaba bien, sino porque salió de una cuenta real de capacidad de batería contra consumo estimado, y eso es algo que puedo defender y, más importante, algo que puedo estar equivocado y corregir con medición real.

En la arquitectura, lo que más me hizo pensar fue la decisión de protocolo HTTPS en vez de MQTT — el ejemplo del curso usa MQTT por default, y tuve que justificar explícitamente por qué mi caso es diferente. Eso fue un buen recordatorio de que las plantillas del curso son puntos de partida, no respuestas correctas automáticas para cualquier producto. Y la viabilidad de manufactura fue la parte más incómoda pero más valiosa: ver el número del BOM empujando el precio al límite de lo que el mercado pagaría no es un resultado "malo" del ejercicio — es exactamente la señal que esta semana está diseñada para sacar a la luz antes de fabricar, no después.

---

## 10. Reflexión personal

> Lo que más cambió para mí esta semana fue la forma de justificar una decisión técnica. Antes de armar el PDS, elegir el protocolo o el módulo de comunicación era cuestión de "lo que ya conozco"; al redactar cada requisito con su criterio de verificación entendí que toda elección tiene que poder rastrearse hasta un requisito concreto: usamos HTTPS en lugar de MQTT porque la autonomía de 15 días (RD-01) no tolera una conexión persistente, no porque fuera más fácil. También me quedé con que los números del PDS —15 días de batería, ≤30 s de transmisión, 99 % de disponibilidad— valen porque están razonados y se pueden medir y corregir, no porque suenen bien. Lo más incómodo fue ver que la viabilidad de manufactura ya empujaba el costo hacia el extremo alto de lo que el mercado pagaría, y que al cotizar después el módulo celular en una fuente real la diferencia fue todavía mayor. Prefiero enterarme ahora, con el número incómodo sobre la mesa, que cuando ya hubiera ocho unidades fabricadas.


---

## 11. Estado de la actividad

✅ **Actividad completada** — PDS con 16 requisitos verificables, decisión de arquitectura de IA justificada, diagrama de sistema en 3 capas con protocolos específicos, y análisis de viabilidad de manufactura para 5-10 unidades.

⚠️ **Pendiente antes de fabricar:** versión editable del diagrama en draw.io/Miro (si el curso la exige), validación de consumo de batería con medición real, y confirmación de cobertura celular 4G en ubicación representativa del segmento.

**Tema:** Product Design Specification y Arquitectura del Sistema
**Evidencias:** 5 prompts con sus respuestas completas (PDS preliminar, explicación de la semana, PDS + arquitectura + viabilidad, preguntas de salida, formato oficial) + PDS completo (16 requisitos con verificación) + decisión de arquitectura de IA justificada + diagrama de arquitectura en 3 capas + flujo de datos con latencias + análisis de viabilidad de manufactura

---

## 12. Entregable final — Product Design Specification

> Documento formal de PDS en el formato de entrega que pide el curso, con el contenido ya desarrollado en esta actividad.

**Producto:** DistanciaCero · **Versión:** 1.0
**Equipo:** Jesús + Andrea · **Fecha:** 24/09/2026

**REQUERIMIENTOS FUNCIONALES**

| ID | El sistema debe... | Verificación |
|---|---|---|
| RF-01 | Registrar los patrones de actividad diaria del adulto mayor y generar alerta solo ante desviación significativa del patrón individual aprendido — no una regla genérica fija | Dataset simulado de 14 días + eventos anómalos inyectados; el sistema debe alertar en los eventos inyectados y no en los días normales |
| RF-02 | Permanecer en silencio mientras la rutina esté dentro de parámetros normales, y enviar alerta a la app en ≤10 minutos desde la detección | Medición de timestamp entre evento inyectado y notificación recibida, en 10 corridas de prueba |
| RF-03 | Tener un periodo de aprendizaje inicial (baseline) de 10-14 días durante el cual solo recopila datos sin generar alertas | Revisión de logs del backend — cero alertas emitidas durante los primeros 10 días de un despliegue nuevo |
| RF-04 | Almacenar y mostrar al hijo/a el historial de actividad de los últimos 30 días, incluso sin conexión a internet | Activar modo avión en el teléfono de prueba y confirmar que el historial sigue visible (cache local) |

**REQUERIMIENTOS DE DESEMPEÑO**

| ID | El sistema debe... | Criterio |
|---|---|---|
| RD-01 | Operar sin recarga durante un mínimo de 15 días continuos | Batería 18650 (~3,000 mAh), consumo promedio estimado 6-8 mA — a validar con medición real en el primer prototipo |
| RD-02 | Mantener tasa de falsos positivos <5% y tasa de falsos negativos <2% | Medido sobre set de prueba de 50 eventos simulados (25 normales, 25 anómalos) |
| RD-03 | Transmitir cada reporte de estado al backend en ≤30 segundos bajo cobertura celular nominal | Logs de timestamp del módulo celular en 20 transmisiones consecutivas |
| RD-04 | Mantener disponibilidad de backend ≥99% mensual | Monitoreo de uptime del servicio en la nube (Firebase) |

**REQUERIMIENTOS DE INTERFAZ**

| ID | La interfaz debe... | Verificación |
|---|---|---|
| RI-01 | Mostrar, sin configuración técnica del usuario, un estado claro "todo normal"/"alerta activa" y el historial reciente, en lenguaje no clínico | Prueba de usabilidad con usuario sin conocimiento previo — interpretación correcta en <10 segundos |
| RI-02 | Comunicarse con la nube exclusivamente vía celular propio (no WiFi doméstico), con datos cifrados | Prueba de campo sin proveer WiFi + inspección de tráfico para confirmar cifrado TLS |
| RI-03 | Permitir configurar el artefacto (activación, verificación de señal, asociación de cuenta) en un proceso guiado de máximo 10 minutos, sin participación del adulto mayor | Cronometraje del proceso de onboarding con un usuario de prueba, sin ayuda del equipo |
| RI-04 | Enviar cada alerta por al menos dos canales (push notification + WhatsApp/SMS) | Simular fallo de un canal (notificaciones push desactivadas) y confirmar llegada por el segundo canal |

**REQUERIMIENTOS DE RESTRICCIÓN**

| ID | El sistema no debe / debe cumplir... | Verificación |
|---|---|---|
| RR-01 | El costo recurrente no debe exceder $300–$600 MXN/mes | Revisión del modelo de precios contra este techo antes de cada cambio de pricing |
| RR-02 | El diseño no puede requerir ninguna acción activa recurrente del adulto mayor (login, botón, cargar dispositivo separado) | Checklist de revisión de diseño — cualquier feature que la requiera se rechaza en revisión de arquitectura |
| RR-03 | El sistema no debe transmitir ni almacenar audio ni video del adulto mayor — solo datos de movimiento/actividad agregados | Auditoría del esquema de datos del backend — ningún campo de tipo audio/imagen/video debe existir |
| RR-04 | El diseño de PCB y los componentes deben ser compatibles con fabricación JLCPCB+PCBA para 5-10 unidades, sin BGA ni pitch <0.5mm | DRC (Design Rule Check) de JLCPCB sobre el diseño antes de enviar a fabricar |

**DIAGRAMA DE ARQUITECTURA:** ✅ diagrama de bloques en 3 capas, con protocolos y latencias por flecha (también en la sección 6).

<div style="margin:1rem 0"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 1280" role="img" aria-label="Arquitectura de DistanciaCero en tres capas: física, datos y presentación" style="width:100%;max-width:1000px;height:auto;font-family:Segoe UI,Roboto,Helvetica,Arial,sans-serif"><defs><filter id="sh" x="-10%" y="-10%" width="125%" height="130%"><feDropShadow dx="0" dy="3" stdDeviation="3" flood-color="#0f172a" flood-opacity="0.18"/></filter><marker id="ar" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="context-stroke"/></marker><linearGradient id="g1" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#0ea5e9"/><stop offset="1" stop-color="#2563eb"/></linearGradient><linearGradient id="g2" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#f59e0b"/><stop offset="1" stop-color="#ea580c"/></linearGradient><linearGradient id="g3" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#a855f7"/><stop offset="1" stop-color="#7c3aed"/></linearGradient><linearGradient id="g4" x1="0" y1="0" x2="1" y2="0"><stop offset="0" stop-color="#10b981"/><stop offset="1" stop-color="#059669"/></linearGradient></defs><rect width="1000" height="1280" rx="22" fill="#f8fafc"/><text x="500" y="48" font-size="28" fill="#0f172a" font-weight="800" text-anchor="middle" >DistanciaCero · Arquitectura del sistema</text><text x="500" y="74" font-size="15" fill="#475569" font-weight="500" text-anchor="middle" >IA híbrida: el dispositivo preprocesa, la nube detecta la anomalía</text><rect x="30" y="100" width="940" height="360" rx="22" fill="#e0f2fe" stroke="#0284c7" stroke-width="3"/><rect x="30" y="100" width="940" height="42" rx="22" fill="url(#g1)"/><rect x="30" y="122" width="940" height="20" fill="url(#g1)"/><text x="500" y="128" font-size="18" fill="#ffffff" font-weight="700" text-anchor="middle" >CAPA 1 · FÍSICA  —  el reposabrazos «Reposabrazos Centinela»</text><rect x="55" y="170" width="170" height="86" rx="14" fill="#ffffff" stroke="#0284c7" stroke-width="2.5" filter="url(#sh)"/><text x="140.0" y="196" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >MPU6050</text><text x="140.0" y="218" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Acelerómetro</text><text x="140.0" y="236" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >vibración / movimiento</text><rect x="55" y="272" width="170" height="86" rx="14" fill="#ffffff" stroke="#0284c7" stroke-width="2.5" filter="url(#sh)"/><text x="140.0" y="298" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >PIR HC-SR501</text><text x="140.0" y="320" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Sensor de presencia</text><text x="140.0" y="338" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >actividad en el radio</text><rect x="55" y="374" width="170" height="70" rx="14" fill="#ffffff" stroke="#16a34a" stroke-width="2.5" filter="url(#sh)"/><text x="140.0" y="400" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >Batería 18650</text><text x="140.0" y="422" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >+ TP4056 · ~3,000 mAh</text><text x="140.0" y="440" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >≥15 días sin recarga</text><rect x="330" y="222" width="210" height="140" rx="14" fill="#fef9c3" stroke="#ca8a04" stroke-width="2.5" filter="url(#sh)"/><text x="435.0" y="248" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >ESP32-S3</text><text x="435.0" y="270" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Preprocesamiento en el borde</text><text x="435.0" y="288" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Agrega en ventanas</text><text x="435.0" y="306" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >de 15–30 min</text><text x="435.0" y="324" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >«hubo movimiento sí/no»</text><text x="435.0" y="342" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Guarda en flash sin señal</text><rect x="640" y="222" width="200" height="140" rx="14" fill="#ffffff" stroke="#0284c7" stroke-width="2.5" filter="url(#sh)"/><text x="740.0" y="248" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >SIM7600E-H</text><text x="740.0" y="270" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Módulo celular 4G</text><text x="740.0" y="288" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >(fallback 3G/2G)</text><text x="740.0" y="306" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >No depende del WiFi</text><text x="740.0" y="324" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >de la casa</text><line x1="225" y1="213" x2="330" y2="262" stroke="#0284c7" stroke-width="3.2" marker-end="url(#ar)"/><rect x="226.0" y="209" width="84.0" height="20" rx="10" fill="#ffffff" stroke="#0284c7" stroke-width="1.2"/><text x="268" y="224" font-size="11.5" fill="#0284c7" font-weight="600" text-anchor="middle" >I²C / GPIO</text><line x1="225" y1="315" x2="330" y2="315" stroke="#0284c7" stroke-width="3.2" marker-end="url(#ar)"/><rect x="249.4" y="293" width="55.2" height="20" rx="10" fill="#ffffff" stroke="#0284c7" stroke-width="1.2"/><text x="277" y="308" font-size="11.5" fill="#0284c7" font-weight="600" text-anchor="middle" >~10 ms</text><line x1="225" y1="409" x2="330" y2="340" stroke="#16a34a" stroke-width="3.2" marker-end="url(#ar)"/><rect x="236.8" y="379" width="62.4" height="20" rx="10" fill="#ffffff" stroke="#16a34a" stroke-width="1.2"/><text x="268" y="394" font-size="11.5" fill="#16a34a" font-weight="600" text-anchor="middle" >energía</text><line x1="540" y1="292" x2="640" y2="292" stroke="#0284c7" stroke-width="3.2" marker-end="url(#ar)"/><rect x="569.6" y="269" width="40.8" height="20" rx="10" fill="#ffffff" stroke="#0284c7" stroke-width="1.2"/><text x="590" y="284" font-size="11.5" fill="#0284c7" font-weight="600" text-anchor="middle" >UART</text><g stroke="#0284c7" stroke-width="3" fill="none" stroke-linecap="round"><path d="M905 255 L905 330"/><path d="M885 340 L905 255 L925 340"/><path d="M880 245 q25 -22 50 0"/><path d="M866 228 q39 -34 78 0"/></g><circle cx="905" cy="255" r="6" fill="#0284c7"/><text x="905" y="362" font-size="13" fill="#0369a1" font-weight="700" text-anchor="middle" >Red celular</text><line x1="840" y1="292" x2="880" y2="292" stroke="#0284c7" stroke-width="3.2" marker-end="url(#ar)"/><line x1="740" y1="364" x2="740" y2="516" stroke="#ea580c" stroke-width="3.2" marker-end="url(#ar)"/><rect x="557.6" y="477" width="364.8" height="20" rx="10" fill="#ffffff" stroke="#ea580c" stroke-width="1.2"/><text x="740" y="492" font-size="11.5" fill="#ea580c" font-weight="600" text-anchor="middle" >HTTPS POST · JSON · TLS · cada 15–30 min · ~2–5 s</text><g transform="translate(0,40)"><rect x="30" y="480" width="940" height="360" rx="22" fill="#ffedd5" stroke="#ea580c" stroke-width="3"/><rect x="30" y="480" width="940" height="42" rx="22" fill="url(#g2)"/><rect x="30" y="502" width="940" height="20" fill="url(#g2)"/><text x="500" y="508" font-size="18" fill="#ffffff" font-weight="700" text-anchor="middle" >CAPA 2 · DATOS  —  Firebase (nube)</text><rect x="55" y="560" width="200" height="110" rx="14" fill="#ffffff" stroke="#ea580c" stroke-width="2.5" filter="url(#sh)"/><text x="155.0" y="586" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >Firestore</text><text x="155.0" y="608" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Guarda el reporte</text><text x="155.0" y="626" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >y el baseline</text><text x="155.0" y="644" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >de cada persona</text><rect x="305" y="560" width="200" height="110" rx="14" fill="#ffffff" stroke="#ea580c" stroke-width="2.5" filter="url(#sh)"/><text x="405.0" y="586" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >Cloud Function</text><text x="405.0" y="608" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Python · se dispara</text><text x="405.0" y="626" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >al escribir un reporte</text><text x="405.0" y="644" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >(orquesta el flujo)</text><rect x="555" y="545" width="230" height="140" rx="14" fill="#fef3c7" stroke="#d97706" stroke-width="2.5" filter="url(#sh)"/><text x="670.0" y="571" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >🧠 Modelo de anomalía</text><text x="670.0" y="593" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Estadístico · z-score</text><text x="670.0" y="611" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >vs baseline por hora</text><text x="670.0" y="629" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Aprende 10–14 días</text><text x="670.0" y="647" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >sin alertas (RF-03)</text><rect x="330" y="720" width="210" height="90" rx="14" fill="#ffffff" stroke="#ea580c" stroke-width="2.5" filter="url(#sh)"/><text x="435.0" y="746" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >Twilio / WhatsApp</text><text x="435.0" y="768" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Canal de respaldo</text><text x="435.0" y="786" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >(RI-04: ≥2 canales)</text><rect x="585" y="720" width="200" height="90" rx="14" fill="#ffffff" stroke="#ea580c" stroke-width="2.5" filter="url(#sh)"/><text x="685.0" y="746" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >FCM</text><text x="685.0" y="768" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Push al teléfono</text><text x="685.0" y="786" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >del hijo/a</text><line x1="255" y1="615" x2="305" y2="615" stroke="#ea580c" stroke-width="3.2" marker-end="url(#ar)"/><rect x="223.6" y="585" width="112.8" height="20" rx="10" fill="#ffffff" stroke="#ea580c" stroke-width="1.2"/><text x="280" y="600" font-size="11.5" fill="#ea580c" font-weight="600" text-anchor="middle" >trigger ~0.3 s</text><line x1="505" y1="615" x2="555" y2="615" stroke="#d97706" stroke-width="3.2" marker-end="url(#ar)"/><rect x="502.4" y="585" width="55.2" height="20" rx="10" fill="#ffffff" stroke="#d97706" stroke-width="1.2"/><text x="530" y="600" font-size="11.5" fill="#d97706" font-weight="600" text-anchor="middle" >~0.1 s</text><line x1="640" y1="685" x2="500" y2="718" stroke="#ea580c" stroke-width="3.2" marker-end="url(#ar)"/><line x1="685" y1="685" x2="685" y2="718" stroke="#ea580c" stroke-width="3.2" marker-end="url(#ar)"/><rect x="697" y="692" width="96" height="20" rx="10" fill="#ffffff" stroke="#ea580c" stroke-width="1.2"/><text x="745" y="706" font-size="11.5" fill="#ea580c" font-weight="600" text-anchor="middle" >si hay anomalía</text><rect x="805" y="560" width="145" height="250" rx="16" fill="#ffffff" stroke="#d97706" stroke-width="2" stroke-dasharray="6 4"/><text x="877" y="590" font-size="14" fill="#b45309" font-weight="800" text-anchor="middle" >¿Por qué híbrida?</text><text x="877" y="614" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >① Señal celular</text><text x="877" y="634" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >intermitente:</text><text x="877" y="654" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >el borde guarda</text><text x="877" y="674" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >② Aprender la rutina</text><text x="877" y="694" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >de cada persona</text><text x="877" y="714" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >no cabe en un</text><text x="877" y="734" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >microcontrolador</text><text x="877" y="754" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >③ Latencia tolerable:</text><text x="877" y="774" font-size="12" fill="#78350f" font-weight="500" text-anchor="middle" >minutos, no ms</text><line x1="155" y1="672" x2="155" y2="886" stroke="#7c3aed" stroke-width="3.2" marker-end="url(#ar)"/><rect x="115.2" y="853" width="249.6" height="20" rx="10" fill="#ffffff" stroke="#7c3aed" stroke-width="1.2"/><text x="240" y="868" font-size="11.5" fill="#7c3aed" font-weight="600" text-anchor="middle" >Firestore listeners · tiempo real</text><line x1="435" y1="812" x2="435" y2="886" stroke="#7c3aed" stroke-width="3.2" marker-end="url(#ar)"/><line x1="685" y1="812" x2="685" y2="886" stroke="#7c3aed" stroke-width="3.2" marker-end="url(#ar)"/><rect x="592.6" y="853" width="184.8" height="20" rx="10" fill="#ffffff" stroke="#7c3aed" stroke-width="1.2"/><text x="685" y="868" font-size="11.5" fill="#7c3aed" font-weight="600" text-anchor="middle" >push + WhatsApp · ~1–3 s</text><rect x="30" y="890" width="940" height="200" rx="22" fill="#f3e8ff" stroke="#7c3aed" stroke-width="3"/><rect x="30" y="890" width="940" height="42" rx="22" fill="url(#g3)"/><rect x="30" y="912" width="940" height="20" fill="url(#g3)"/><text x="500" y="918" font-size="18" fill="#ffffff" font-weight="700" text-anchor="middle" >CAPA 3 · PRESENTACIÓN  —  app del hijo/a (React Native)</text><rect x="55" y="950" width="270" height="120" rx="14" fill="#ffffff" stroke="#7c3aed" stroke-width="2.5" filter="url(#sh)"/><text x="190.0" y="976" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >① Estado diario</text><text x="190.0" y="998" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Grande y claro:</text><text x="190.0" y="1016" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >🟢 «Todo normal»</text><text x="190.0" y="1034" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >🔴 «Alerta activa»</text><text x="190.0" y="1052" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Lenguaje no clínico</text><rect x="355" y="950" width="270" height="120" rx="14" fill="#ffffff" stroke="#7c3aed" stroke-width="2.5" filter="url(#sh)"/><text x="490.0" y="976" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >② Historial 30 días</text><text x="490.0" y="998" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Línea de tiempo</text><text x="490.0" y="1016" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Cacheada en el teléfono:</text><text x="490.0" y="1034" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >se ve incluso sin</text><text x="490.0" y="1052" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >conexión (RF-04)</text><rect x="655" y="950" width="295" height="120" rx="14" fill="#ffffff" stroke="#7c3aed" stroke-width="2.5" filter="url(#sh)"/><text x="802.5" y="976" font-size="16" fill="#111827" font-weight="700" text-anchor="middle" >③ Onboarding ≤ 10 min</text><text x="802.5" y="998" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >Activar el artefacto,</text><text x="802.5" y="1016" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >verificar señal celular,</text><text x="802.5" y="1034" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >asociar la cuenta</text><text x="802.5" y="1052" font-size="12.5" fill="#374151" font-weight="400" text-anchor="middle" >sin ayuda del adulto mayor</text></g><rect x="30" y="1150" width="940" height="100" rx="20" fill="url(#g4)" filter="url(#sh)"/><text x="500" y="1188" font-size="24" fill="#ffffff" font-weight="800" text-anchor="middle" >⏱ Latencia total con anomalía: ~5–10 segundos</text><text x="500" y="1218" font-size="15" fill="#ecfdf5" font-weight="500" text-anchor="middle" >Límite del requisito RF-02: ≤ 10 minutos · holgura de más de 50×</text><text x="500" y="1238" font-size="13" fill="#d1fae5" font-weight="500" text-anchor="middle" >Sin acciones del adulto mayor (RR-02) · sin audio ni video (RR-03)</text></svg></div>

**BOM PRELIMINAR:** ⚠️ pendiente — el análisis de componentes críticos con disponibilidad, precio y librería JLCPCB ya está hecho (ver sección de viabilidad de prototipo arriba); falta consolidarlo en una hoja de cálculo con todos los componentes, no solo los 4 críticos.