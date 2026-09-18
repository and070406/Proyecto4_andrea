

# Semana 4 
## Mercado, Valor y Propuesta de Valor

**Tema:** DistanciaCero — Segmento accionable, tamaño de mercado, análisis competitivo y propuesta de valor
**Blueprint:** Creación de valor → Captura de valor · **DVF:** 🔴 Deseable · 🟡 Viable

---

## Objetivo

Esta semana separa dos preguntas que suelen confundirse: **¿qué valor genera el producto?** (propuesta de valor) y **¿por qué me lo compran a mí y no a otro?** (diferenciación). Sin ambas claras, ni el pitch ni el modelo de negocio se sostienen.

El trabajo avanza en cuatro frentes articulados: **segmento accionable en 4 capas** (marcando explícitamente VERIFICADO / HIPÓTESIS), **dimensionamiento TAM/SAM/SOM** con lógica de reducción paso a paso, **mapa competitivo + lienzo estratégico Blue Ocean**, y **propuesta de valor** validada con IDEO y la Pirámide de Valor de Bain.

---

## Contexto del producto

- **Problema:** hijos e hijas de 35–55 años en México con un padre o madre de 65+ que vive solo y lejos — ansiedad y culpa permanentes, el miedo a "la llamada".
- **Mecanismo:** artefacto integrado en un objeto cotidiano (bastón, sillón, taza) con conectividad propia (celular/LoRa), que detecta de forma pasiva la rutina diaria del adulto mayor sin que él haga nada ni dependa del WiFi de casa.
- **IA:** modelo en la nube que aprende el patrón individual de rutina de cada usuario y notifica al hijo/a **solo por excepción**, cuando la rutina se rompe.
- **Punto de partida importante:** todavía no hay entrevistas de validación con usuarios reales. Todo lo documentado abajo parte de investigación de mercado secundaria (fuentes públicas y estadísticas oficiales) y del Pain-Gain Map de semana 2 — no de conversaciones directas con el segmento. Esto se marca explícitamente en cada bloque.

---

## Investigación con IA

Encadenamos un "rol" distinto de IA por bloque: perfil de segmento, dimensionamiento de mercado, mapa competitivo + Blue Ocean, y propuesta de valor final.

### Prompt 1 — Perfil de segmento accionable (4 capas)

**IA utilizada:** Claude (Anthropic) — rol de investigador de mercado en segmentación de clientes para negocios digital-físicos en mercados emergentes de LATAM

```text
Actúa como un investigador de mercado con especialización en
segmentación de clientes para negocios de producto digital-físico
en mercados emergentes latinoamericanos. Tu metodología combina
datos demográficos verificables con análisis conductual y
psicográfico basado en comportamiento observable — nunca en
suposiciones sobre actitudes o valores generales. Cuando el
equipo no tiene evidencia de una capa, lo señalas directamente
en lugar de rellenar con hipótesis no marcadas.

[Se incluyó la evidencia de mercado secundaria: INEGI (adultos
60+ que viven solos), mercado de botones de pánico en
Amazon/Mercado Libre, workarounds documentados por la startup
Kinnect, comunidad "Club de Cuidadores" en Facebook, y el
piloto académico de tele-asistencia en CDMX de 2013. Se pidió
marcar cada dato como VERIFICADO o HIPÓTESIS, siendo
especialmente estricto con las capas conductual y psicográfica,
que no pueden marcarse como "confirmadas por el usuario" sin
entrevistas reales.]
```

**Resultado de la IA**

> El perfil salió **incompleto por diseño**. Las capas 1 (demográfica) y 2 (conductual) arrojaron datos VERIFICADOS, pero únicamente sobre el adulto mayor y sobre la existencia del mercado y las comunidades — ninguna fuente secundaria caracteriza directamente al hijo o hija que compra. La Capa 3 (psicográfica) quedó **casi vacía**: no existe una sola cita textual de un hijo/hija adulto sobre su ansiedad o su culpa, así que la emoción central del Pain-Gain Map ("miedo a la llamada") se marcó como HIPÓTESIS y no como hallazgo.

**Hipótesis críticas identificadas:**

1. Que el segmento correcto sea el hijo/hija de 35–55 años — y no otro familiar — como comprador y usuario real.
2. Que la emoción central sea la culpa y que el disparador de compra sea "tranquilidad sin tener que preguntar", sin ninguna fuente secundaria que lo respalde.
3. Que exista disposición a pagar por una **suscripción recurrente**, frente al modelo de compra única que domina hoy en los botones de pánico.

**Próximo paso señalado:** las entrevistas deben confirmar, en este orden, (1) quién es el actor real que tiene el dolor y el poder de compra, (2) el lenguaje emocional real del hijo/hija al describir un momento reciente de preocupación, y (3) cuánto pagan hoy por manejar esa preocupación.

---

### Prompt 2 — Dimensionamiento de mercado (TAM / SAM / SOM)

**IA utilizada:** Claude (Anthropic) — rol de analista de dimensionamiento para startups de hardware y software en LATAM, con enfoque top-down y triangulación de fuentes verificables (INEGI, CEPAL, BID)

```text
Actúa como analista de mercado con especialización en
dimensionamiento para startups de hardware y software en
América Latina. Tu metodología es el enfoque top-down con
triangulación de fuentes verificables. No inventes cifras —
si no existe fuente verificable para un número, lo señalas y
explicas cómo estimarlo con lógica de primer principio.

Concepto: DistanciaCero (app + artefacto conectado + IA de
detección de rutina).
Segmento objetivo: hijos/as 35-55 en México con padre/madre 65+
que vive solo y lejos.
Precio estimado: $300–$600 MXN/mes.
Modelo: suscripción mensual.
Mercado inicial: México. Expansión: LATAM año 3+.

Construye TAM, SAM y SOM con reducción paso a paso, cada
filtro con su fuente o supuesto de primer principio explícito.
```

**Resultado de la IA**

> El TAM se construyó en 5 pasos de reducción partiendo de los 38.8 millones de hogares en México (ENIGH 2024): hogares con un adulto de 65+ (10.9%) → hogares unipersonales dentro de ese grupo (17.5%) → hogares con un hijo vivo (85%, supuesto de primer principio) → hijos que viven lejos (60%, supuesto conservador apoyado en literatura de migración interna) → disposición y capacidad de pago (25%, calibrado con las tasas de adopción de telesalud en México). El resultado: **94,350 hijos adultos** con disposición estimada de pago, y un TAM de **$509.5M MXN anuales**.

| Nivel | Universo | Valor anual |
|---|---|---|
| TAM | 94,350 personas | $509.5M MXN |
| SAM (CDMX/GDL/MTY/Puebla + canal digital + deciles de ingreso 6–10) | 17,832 personas | $96.3M MXN |
| SOM (años 1–2, meta de 850 clientes vía Meta/Google Ads) | 850 personas | $4.59M MXN |

**Señal de viabilidad:** marginal — el SOM alcanza para cubrir nómina básica e infraestructura de una startup de 4 personas, pero con un margen operativo estrecho (10–20%). Para ser cómodamente viable harían falta entre 1,500 y 2,000 clientes en el año 3, o introducir el hardware como pago único.

**Nota metodológica de la IA:** el supuesto más incierto de todo el modelo es el 25% de disposición de pago. Si cae a 15%, el TAM baja a 56,610 personas; si sube a 35% (validado con entrevistas reales), sube a 132,090. La IA recomendó explícitamente entre 15 y 20 entrevistas para afinar ese número antes de comprometer presupuesto de marketing con base en él.

---

### Prompt 3 — Mapa competitivo (directos, indirectos, sustitutos)

**IA utilizada:** Claude (Anthropic) — rol de analista de inteligencia competitiva en mercados de producto digital-físico en América Latina

```text
Actúa como analista de inteligencia competitiva especializado
en mercados de producto digital-físico en América Latina. Para
cada competidor buscas su debilidad específica para el segmento
del equipo, no debilidades genéricas.

[Se incluyó el concepto, segmento, dolor ⭐ y precio estimado.
Se pidió mapear mínimo 3 directos, 3 indirectos y 2 sustitutos,
cada uno con dónde opera, precio/modelo, y debilidad específica
para el segmento hijos/as 35-55.]
```

**Resultado de la IA**

> Se mapearon 3 competidores directos — **Estoy Bien** ($299 MXN/mes), **Cuida Más** ($800–928 MXN/mes con call center) y **Care 60+** (desde $6,588 MXN/año) —, 3 indirectos (**Life360**, **Google Family Link** y sensores WiFi DIY tipo Tuya/Aqara/Tapo) y 2 sustitutos (llamadas diarias apoyadas en la red informal, y cuidador por horas a $9,000–27,000 MXN/mes).

**Competidor más peligroso:** las llamadas diarias más la red informal. No por ser el más sofisticado, sino porque su costo marginal es cero, porque la confianza humana pesa más que la tecnología, y porque impone una barrera psicológica real: adoptar DistanciaCero obliga al hijo/a a admitir que "las llamadas ya no bastan", lo que activa culpa en vez de alivio.

---

### Prompt 4 — Lienzo estratégico Blue Ocean

**IA utilizada:** Claude (Anthropic) — rol de estratega de innovación en Blue Ocean Strategy para startups de hardware y software en mercados emergentes

```text
Actúa como estratega de innovación con experiencia en Blue Ocean
Strategy. Aplica el Marco de las Cuatro Acciones (Eliminar /
Reducir / Incrementar / Crear) antes de construir el lienzo.
Cuando el equipo no tiene ventaja en un atributo, puntúalo bajo.

[Se incluyó el mapa competitivo completo del Prompt 3, la
descripción técnica de DistanciaCero, las capacidades
diferenciales del equipo (sistemas embebidos ESP32/RP2350,
diseño y manufactura física CAD/PCB/impresión 3D) y el
segmento accionable.]
```

**Resultado de la IA — Marco de las Cuatro Acciones**

- **ELIMINAR** — toda interacción activa del adulto mayor con la tecnología: login, botón, responder una notificación.
- **REDUCIR** — el call center humano y la respuesta de emergencia en vivo (el modelo de Cuida Más).
- **INCREMENTAR** — el silencio y la ausencia total de fricción mientras todo está normal.
- **CREAR** — detección de rutina aprendida dentro de un objeto cotidiano, sin WiFi y sin batería que el usuario tenga que gestionar. Esto es posible por la capacidad interna del equipo en firmware propio y manufactura física, no por una promesa de marketing.

**Lienzo estratégico**

| Atributo | Estoy Bien | Cuida Más | Sensores DIY | Llamadas + red informal | DistanciaCero |
|---|---|---|---|---|---|
| Precio percibido | 3 | 1 | 4 | 5 | 4 |
| Autonomía requerida del adulto mayor (5 = no requiere nada) | 1 | 3 | 2 | 4 | **5** |
| Respuesta en emergencia real | 2 | 5 | 2 | 1 | 2 |
| Silencio / sin fricción diaria | 2 | 2 | 2 | 3 | **5** |
| Detección de anomalía de rutina | 2 | 1 | 1 | 0 | **5** |
| Independencia de infraestructura doméstica | 4 | 4 | 1 | 5 | **5** |
| Integración física invisible | 0 | 2 | 1 | 0 | **5** |
| Resuelve la culpa de "reemplazar" el vínculo | 1 | 2 | 1 | 3 | 3 |

**Océano azul en una oración:** DistanciaCero no compite por dar más visibilidad, más rapidez de respuesta ni más contacto humano — compite por exigir cero esfuerzo del adulto mayor y cero atención activa del hijo/a mientras todo está bien.

**Advertencia de océano rojo señalada por la IA:** el atributo "resuelve la culpa de reemplazar el vínculo humano" empata (3/5) con el sustituto más peligroso. Si el mercado percibe el producto como un simple automatizador de la llamada, la discusión se vuelve emocional y ninguna ventaja de hardware sirve ahí.

---

### Prompt 5 — Propuesta de valor final

**IA utilizada:** Claude (Anthropic) — rol de estratega de marca y comunicación, combinando el framework Insightful/Unique/Targeted de IDEO con la Pirámide de Valor de Bain

```text
Actúa como estratega de marca y comunicación. Combina el
framework IDEO con la Pirámide de Valor de Bain. Nombra al
usuario específico, nombra el resultado concreto, implica por
qué esta solución y no otra. No uses "plataforma", "solución
integral", "innovador", "ecosistema". No describas el producto
— describe el valor que entrega.

[Se incluyó el perfil de segmento, el dolor/ganancia del
Pain-Gain Map, el competidor más peligroso con su debilidad,
el hueco azul identificado, y el precio estimado. Se pidieron
tres versiones de máximo 25 palabras cada una.]
```

**Resultado de la IA**

> **Nivel en la Pirámide de Bain:** el concepto opera hoy en el nivel **Funcional**, con una oportunidad legítima de subir al **Emocional**, porque el dolor documentado en el Pain-Gain Map es miedo constante y no falta de información. Subir hasta el nivel Transformador se descartó como prematuro sin evidencia real de un cambio de identidad en el usuario.
>
> **Evaluación IDEO:** Insightful ✅ (ataca exactamente el vacío que deja el competidor más peligroso) · Unique ✅ (firmware propio + manufactura física interna) · Targeted ⚠️ (el segmento está bien acotado en papel, pero "lejos" sigue siendo narrativa, no un dato verificado con entrevistas).

**Versión 3 — la más fuerte:**

> "Para hijos que viven lejos de su padre o madre mayor, DistanciaCero reemplaza el miedo a 'la llamada' por la certeza diaria de que todo está bien — sin preguntar, sin culpa."

**Oferta vs. propuesta de valor:** la oferta describe qué hace el objeto (detectar, conectar, notificar); la propuesta describe qué deja de sentir el hijo/a (miedo, culpa). El sujeto pasa del artefacto al usuario, y el nivel sube de funcional a emocional sin nombrar nunca al competidor.

---

### Enlaces
_[Ver conversación con Claude](https://claude.ai/share/684e6038-b72b-41d0-a2f7-828ab7e78cf3)
_[Ver conversación con Perplexity](https://www.perplexity.ai/search/7820f1ea-a8dc-46bc-a5dc-156025a9cc32)

