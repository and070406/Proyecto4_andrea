

---
title: Semana 5 · PDS y Arquitectura del Sistema
---

# Semana 5

## Product Design Specification y Arquitectura del Sistema

**Tema:** DistanciaCero — PDS completo (16 requisitos), decisión de arquitectura de IA, diseño de sistema en 3 capas y viabilidad de manufactura
**Blueprint:** Creación de valor → Factible · **DVF:** 🟢 Factible (arquitectura definida) · ⚠️ Riesgo de costo identificado (componente celular)

---

## Objetivo

Esta semana el enfoque cambia de mercado a diseño técnico: traducir todo lo validado hasta ahora (segmento, propuesta de valor, hueco Blue Ocean de semana 4) en un **Product Design Specification** formal — requisitos funcionales, de desempeño, de interfaz y de restricción, cada uno con criterio de verificación explícito — y en la **arquitectura del sistema** que hace posible cumplirlos: dónde corre el modelo de IA, cómo se comunican los tres componentes, y si el diseño es fabricable en el volumen que necesita una prueba de mercado real (5–10 unidades).

---

## Contexto del producto

- **Punto de partida:** un PDS preliminar con 2 requisitos por categoría, construido a partir de la propuesta de valor y el Blue Ocean de semana 4.
- **Lo que exige esta semana:** expandir a mínimo 4 requisitos por categoría con criterio de verificación explícito, tomar y justificar la decisión de arquitectura de IA (edge/cloud/híbrido), diseñar la arquitectura completa en 3 capas con protocolos específicos, y evaluar viabilidad de manufactura para 5–10 unidades — el mínimo que permite una prueba de mercado real, no un demo.

---

## Trabajo con IA

### Prompt 1 — Arquitectura del sistema

**IA utilizada:** Claude (Anthropic) — rol de arquitecto de sistemas embebidos especializado en productos mecatrónicos con IA para mercados latinoamericanos

```text
Actúa como un arquitecto de sistemas embebidos con experiencia
en productos mecatrónicos con inteligencia artificial para
mercados latinoamericanos. Tu especialidad es diseñar
arquitecturas de sistema que equilibran capacidad técnica,
restricciones de manufactura y viabilidad económica para
equipos de desarrollo universitario con presupuesto limitado.
No propones la arquitectura más sofisticada — propones la más
adecuada para las capacidades del equipo y los requerimientos
del producto.

Somos un equipo de ingeniería en México desarrollando un
producto mecatrónico con tres componentes: un artefacto físico
inteligente, una aplicación móvil/web, y una página de venta.
Tenemos 8 semanas de desarrollo efectivo para llegar a una
primera versión funcional que un usuario real pueda usar sin
que nosotros estemos presentes.

Nuestras capacidades técnicas:
- Hardware: ESP32, Raspberry Pi, diseño de PCB (2 capas),
  impresión 3D para carcasas, soldadura SMD
- Software: Python, C/C++, JavaScript/React, React Native
- IA: TensorFlow Lite, PyTorch, APIs de modelos (OpenAI,
  Anthropic, Google), bases de datos vectoriales básicas
- Presupuesto de materiales: máximo $3,000 MXN para prototipo

Nuestro producto:
Nombre: DistanciaCero
Descripción: sistema digital-físico que integra un artefacto en
  un objeto cotidiano (bastón, sillón, taza) con conectividad
  celular propia, sin depender de WiFi doméstico ni de que el
  adulto mayor haga nada. Detecta pasivamente su rutina diaria y
  notifica al hijo/a solo por excepción, cuando la IA detecta una
  desviación significativa del patrón de rutina aprendido para
  esa persona.
Propuesta de valor: "Para hijos que viven lejos de su padre o
  madre mayor, DistanciaCero reemplaza el miedo a 'la llamada'
  por la certeza diaria de que todo está bien — sin preguntar,
  sin culpa."

Requerimientos técnicos clave (del PDS preliminar):
- El sistema debe generar alerta solo ante desviación
  significativa del patrón individual aprendido (no regla
  genérica fija)
- El sistema debe permanecer en silencio en rutina normal, con
  alerta en ≤10 min desde la detección
- El artefacto debe operar sin recarga un mínimo de X días
  (a definir según objeto y consumo real)
- El diseño no puede requerir ninguna acción activa recurrente
  del adulto mayor (login, botón, cargar dispositivo separado)
- Comunicación exclusivamente celular/LoRa propia, no WiFi
  doméstico

Nuestra decisión de arquitectura de IA: Híbrido
Justificación (3 puntos):
1. Conectividad celular intermitente pero no nula en el punto de
   uso — descarta un modelo 100% cloud.
2. La detección personalizada de rutina individual, aprendida a
   lo largo de semanas, no cabe en el cómputo sostenido de un
   microcontrolador — ese trabajo pesado vive en la nube.
3. La latencia tolerable del producto es de minutos, no
   milisegundos — no exige inferencia en tiempo real en el
   dispositivo.

Entrega en 4 pasos: validación de la decisión de arquitectura de
IA, arquitectura en 3 capas con componentes y protocolos
específicos, flujo de datos extremo a extremo con latencias, y
viabilidad de prototipo/primera tirada para 5-10 unidades.
```

**Resultado de la IA**

> **Validación de la decisión de IA:** confirmada ✅ — el enfoque híbrido está bien justificado dados los requisitos (el silencio tolera minutos, no milisegundos) y las capacidades del equipo (sin experiencia previa manteniendo modelos de aprendizaje continuo en un microcontrolador).
>
> Se diseñó la arquitectura completa en 3 capas —física, datos y presentación— con componentes y protocolos específicos, incluyendo una desviación deliberada del protocolo por defecto del curso: **HTTPS REST en lugar de MQTT** entre el artefacto y el backend. La razón: el patrón de transmisión (reportes cada 15–30 min, no streaming continuo) hace que mantener una conexión MQTT persistente en un módulo celular gaste batería sin necesidad.
>
> En la viabilidad de manufactura para 8 unidades se identificó que el componente celular (SIM7600E-H) es el que más presiona el costo, empujando el precio mínimo viable de hardware al extremo alto del rango ya estimado en semana 4 ($2,000–4,000 MXN) — se documentó como riesgo pendiente, no como problema resuelto.

*(El detalle completo de esta arquitectura —capas, componentes, flujo de datos y viabilidad de manufactura— está en las secciones de abajo.)*

---

### Prompt 2 — Validar y completar el PDS

**IA utilizada:** Claude (Anthropic) — rol de ingeniero de producto senior especializado en redactar Product Design Specifications para hardware + software en etapa de prototipo avanzado

```text
Actúa como un ingeniero de producto senior con experiencia en
redactar Product Design Specifications para productos de
hardware + software en etapa de prototipo avanzado. Tu
especialidad es identificar requerimientos mal redactados —
demasiado vagos para verificarse, demasiado restrictivos para
ser alcanzables, o que faltan y harán falta en el desarrollo.

Somos un equipo de ingeniería en México desarrollando:
DistanciaCero — sistema digital-físico (app con IA + artefacto
conectado) que detecta pasivamente la rutina diaria de un
adulto mayor que vive solo, sin que él haga ninguna acción ni
dependa de WiFi doméstico, y notifica al hijo/a solo por
excepción.

Usuario final: hijos/as adultos de 35-55 años en México con un
padre/madre de 65+ que vive solo(a) — segmento con tres perfiles
identificados según si ya existe o no una red humana local de
apoyo (semana 4).

Primera iteración del producto: el sistema completo (artefacto +
app + backend) funcionando de forma autónoma, instalado en la
casa de un adulto mayor real durante varias semanas, sin que el
equipo esté presente explicando cómo usarlo — no un demo ni un
prototipo de laboratorio.

Este es nuestro PDS preliminar:

REQUERIMIENTOS FUNCIONALES:
1. El sistema debe registrar los patrones de actividad diaria y
   generar alerta solo ante desviación significativa del patrón
   aprendido para esa persona específica.
2. El sistema debe permanecer en silencio mientras la rutina sea
   normal, y alertar en un tiempo máximo definido desde la
   detección (a definir con dato real, ej. ≤10 min).

REQUERIMIENTOS DE DESEMPEÑO:
1. El artefacto debe operar sin recarga un mínimo de X días
   (a definir según objeto elegido y consumo real).
2. El algoritmo debe mantener tasa de falsos positivos menor a
   Y% y tasa de falsos negativos menor a Z%.

REQUERIMIENTOS DE INTERFAZ:
1. La app debe mostrar, sin configuración técnica, un estado
   claro "todo normal"/"alerta activa" y el historial reciente,
   en lenguaje no clínico.
2. El artefacto debe comunicarse con la nube exclusivamente vía
   celular/LoRa propio (no WiFi doméstico), con datos cifrados.

REQUERIMIENTOS DE RESTRICCIÓN:
1. El costo recurrente no debe exceder el rango validado por el
   mercado ($300-$600 MXN/mes).
2. El diseño no puede requerir ninguna acción activa recurrente
   del adulto mayor.

Entrega diagnóstico por categoría, correcciones con criterio de
verificación explícito, mínimo 2 requerimientos faltantes por
categoría, y el PDS completo corregido.
```

**Resultado de la IA — diagnóstico por categoría**

| Categoría | ✅ Bien redactados | ⚠️ Con problema | ❌ Faltantes (agregados) |
|---|---|---|---|
| Funcionales | El de detección de desviación (verificable con dataset de prueba) | El de alerta por excepción tenía una variable sin resolver ("tiempo a definir") | Periodo de aprendizaje inicial sin alertas · Historial accesible sin conexión |
| Desempeño | — | Ambos (autonomía y tasa de error) tenían variables sin resolver, no verificables tal cual | Latencia máxima de transmisión · Disponibilidad del backend |
| Interfaz | Ambos, ya verificables en principio | Faltaba profundidad en el criterio de verificación | Onboarding con tiempo límite · Redundancia de canal de notificación |
| Restricción | Ambos, claros y verificables | — | Privacidad de datos (sin audio/video) · Volumen de manufactura (compatibilidad JLCPCB) |

**Correcciones aplicadas:** las variables sin resolver (tiempo de alerta, días de autonomía, tasas de falsos positivos/negativos) se fijaron con valores concretos, razonados a partir de las capacidades técnicas del equipo (capacidad de batería, consumo estimado del hardware elegido). Quedan marcadas como *supuestos de diseño a validar con el primer prototipo*, no como datos ya medidos.

---

## PDS completo — DistanciaCero v1.0

**REQUISITOS FUNCIONALES**

| ID | Requisito | Verificación |
|---|---|---|
| RF-01 | Detectar desviación significativa del patrón de rutina aprendido por persona | Dataset simulado de 14 días + eventos anómalos inyectados |
| RF-02 | Silencio mientras rutina es normal; alerta en ≤10 min desde detección | Medición de timestamp evento→notificación en 10 corridas |
| RF-03 | Periodo de aprendizaje inicial (baseline) de 10–14 días sin alertas | Revisión de logs — cero alertas en los primeros 10 días |
| RF-04 | Historial de 30 días accesible incluso sin conexión | Prueba en modo avión — historial visible (cache local) |

**REQUISITOS DE DESEMPEÑO**

| ID | Requisito | Criterio |
|---|---|---|
| RD-01 | Autonomía sin recarga ≥15 días | Batería 18650 (~3,000 mAh), consumo estimado 6–8 mA promedio |
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
| RR-01 | Costo recurrente dentro de $300–$600 MXN/mes | Revisión del modelo de precios contra este techo |
| RR-02 | Ninguna acción activa recurrente requerida del adulto mayor | Checklist de revisión de diseño en cada feature nueva |
| RR-03 | Sin transmisión ni almacenamiento de audio/video | Auditoría del esquema de datos del backend |
| RR-04 | Compatible con JLCPCB+PCBA para 5–10 unidades, sin BGA ni pitch <0.5mm | DRC de JLCPCB sobre el diseño antes de fabricar |

---

## Decisión de arquitectura de IA

**✓ HÍBRIDO — decisión tomada y justificada**

| Pregunta guía | Respuesta para DistanciaCero |
|---|---|
| ¿Conectividad estable en el punto de uso? | Intermitente pero no nula — descarta cloud puro |
| ¿Respuesta en <1s o puede esperar minutos? | Tolera minutos (RF-02: ≤10 min) — no exige edge puro |
| ¿Los datos pueden salir del dispositivo? | Sí, con cifrado (RI-02) — no hay restricción de privacidad que fuerce todo a edge |

**Justificación en 3 puntos:**

1. **Conectividad intermitente pero no nula** — el dispositivo necesita acumular datos localmente durante huecos de señal cortos; un modelo 100% cloud fallaría en esos momentos.
2. **La detección personalizada de rutina no cabe en el microcontrolador** — aprender el patrón individual a lo largo de semanas requiere más memoria y cómputo del que un ESP32/RP2350 puede sostener con actualizaciones continuas.
3. **Latencia tolerable en minutos, no milisegundos** — RF-02 permite hasta 10 minutos entre evento y alerta, así que no hace falta inferencia en tiempo real en el dispositivo; el edge solo hace preprocesamiento simple.

---

## Arquitectura del sistema

```text
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

**Decisiones de componente clave**

| Componente | Elección | Por qué (y qué se descartó) |
|---|---|---|
| Microcontrolador | ESP32-S3 | Soporte más maduro de TFLite Micro que RP2350; conocimiento de GPIO del equipo (curso de Sistemas Embebidos) es transferible |
| Conectividad | SIM7600E-H (4G, fallback 3G/2G) | LoRa se descartó — requeriría gateway propio cerca de cada casa, inviable por usuario. NB-IoT se descartó por cobertura incierta en México hoy |
| Backend | Firebase (Firestore + Cloud Functions + FCM) | Menor complejidad operativa que AWS IoT Core para un equipo de 4 sin DevOps dedicado; FCM resuelve RI-04 directamente |
| Protocolo hardware→backend | HTTPS REST | Se aparta del ejemplo del curso (MQTT) — justificado: transmisión poco frecuente (15–30 min), MQTT persistente gastaría batería innecesaria (RD-01) |

**Flujo de datos — caso de uso principal (con anomalía detectada)**

| Paso | Componente | Mecanismo | Latencia est. |
|---|---|---|---|
| 1 | Sensores → ESP32-S3 | I2C/GPIO | ~10 ms |
| 2 | ESP32-S3 → Firebase | HTTPS POST vía SIM7600 | ~2–5 s |
| 3 | Firestore → Cloud Function | Trigger on write | ~200–500 ms |
| 4 | Cloud Function → modelo | Inferencia estadística | ~50–100 ms |
| 5 | Cloud Function → FCM/Twilio | Despacho de alerta | ~1–2 s |
| 6 | App del hijo/a | Recepción push/WhatsApp | ~1–3 s |

**Latencia total extremo a extremo:** ~5–10 segundos — muy por debajo del margen de RF-02 (≤10 minutos).

**Funcionamiento sin conexión:** el ESP32 sigue registrando en flash local durante huecos de señal y transmite en el siguiente ciclo disponible — no se pierden datos, solo se retrasa la sincronización.

---

## Viabilidad de prototipo (5–10 unidades)

**Volumen objetivo:** 8 unidades

| Componente crítico | Disponibilidad MX (≥10 uds) | En librería JLCPCB | Costo unitario (vol. 8–10) |
|---|---|---|---|
| SIM7600E-H (celular 4G) | ✅ Mouser/DigiKey, 10–15 días | ⚠️ integración manual | ~$350–450 MXN |
| ESP32-S3 | ✅ MercadoLibre/Mouser, <1 sem | ✅ | ~$90–130 MXN |
| MPU6050 + PIR HC-SR501 | ✅ MercadoLibre, <1 sem | ✅ / ⚠️ | ~$100–150 MXN |
| Batería 18650 + TP4056 | ✅ MercadoLibre, <1 sem | N/A | ~$150–200 MXN |

**Alternativa evaluada y descartada:** módulo SIM800C (2G) — más barato y más estándar en librería JLCPCB, pero Telcel y AT&T ya descontinuaron 2G en México; serviría para un prototipo de laboratorio, no para una prueba de mercado real con usuarios en sus casas.

| Métrica | Valor |
|---|---|
| BOM estimado por unidad (vol. 8–10) | ~$800–1,100 MXN |
| Precio de venta mínimo viable (BOM ÷ 30%) | ~$2,700–3,700 MXN |
| ¿Cae dentro del rango ya estimado en semana 4 ($2,000–4,000 MXN)? | ⚠️ Sí, pero en el extremo alto |
| Proceso recomendado | JLCPCB + PCBA para PCB principal; SIM7600 y PIR integrados manualmente por conector |

---

## ¿Qué aprendí?

Lo que más me quedó de esta semana es que un PDS no es una lista de buenas intenciones — es solo tan útil como su criterio de verificación. Los primeros dos requisitos por categoría que ya teníamos sonaban bien, pero al pasarlos por el diagnóstico formal varios necesitaron números concretos que antes no teníamos (los 15 días de batería, el ≤30s de transmisión, el ≥99% de uptime). Lo más útil fue notar que esos números, aunque son supuestos de diseño y no datos de mercado verificados, sí tienen que estar razonados — no pusimos "15 días" porque sonaba bien, sino porque salió de una cuenta real de capacidad de batería contra consumo estimado, algo que podemos defender y, más importante, corregir con medición real.

En la arquitectura, lo que más nos hizo pensar fue la decisión de protocolo HTTPS en vez de MQTT — el ejemplo del curso usa MQTT por default, y tuvimos que justificar explícitamente por qué nuestro caso es diferente. Buen recordatorio de que las plantillas del curso son puntos de partida, no respuestas automáticas para cualquier producto. Y la viabilidad de manufactura fue la parte más incómoda pero más valiosa: ver el número del BOM empujando el precio al límite de lo que el mercado pagaría no es un resultado "malo" del ejercicio — es exactamente la señal que esta semana está diseñada para sacar a la luz antes de fabricar, no después.

## Reflexión personal

> Lo que más me quedó de esta actividad es lo distinto que se siente diseñar cuando ya tienes contra qué medir cada decisión. Antes de escribir el PDS a 4 capas, elegir el módulo celular o el protocolo de comunicación se sentía como una decisión más de "qué tecnología conozco o me late", y esta semana entendí que en realidad cada elección debería poder rastrearse hasta un requisito específico — el HTTPS en vez de MQTT existe porque RD-01 (batería) lo exige, no porque nos pareciera más simple. También fue revelador ver que la viabilidad de manufactura empuja el precio del hardware justo al límite superior de lo que ya habíamos estimado que el segmento pagaría — eso no es un problema resuelto, es una tensión real que el proyecto va a tener que negociar en las próximas semanas, probablemente optimizando el componente celular. Preferimos verlo así, con el número incómodo puesto sobre la mesa, que descubrirlo hasta que ya tengamos 8 unidades fabricadas.

