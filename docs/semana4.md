

# Semana 4 
## Mercado, Valor y Propuesta de Valor

**Tema:** DistanciaCero — Segmento accionable, tamaño de mercado, análisis competitivo y propuesta de valor
**Blueprint:** Creación de valor → Captura de valor · **DVF:** 🔴 Deseable · 🟡 Viable

---

## Objetivo

Esta semana separa dos preguntas que suelen confundirse: **¿qué valor genera el producto?** (propuesta de valor) y **¿por qué me lo compran a mí y no a otro?** (diferenciación). Sin ambas claras, ni el pitch ni el modelo de negocio se sostienen.

El trabajo avanza en cuatro frentes: **segmento accionable en 4 capas** (marcando VERIFICADO / HIPÓTESIS), **dimensionamiento TAM/SAM/SOM** con lógica de reducción explícita, **mapa competitivo + lienzo Blue Ocean**, y **propuesta de valor** validada con IDEO y la Pirámide de Bain.

---

## Contexto del producto

- **Problema:** hijos e hijas de 35–55 años en México con un padre o madre de 65+ que vive solo y lejos — ansiedad y culpa permanentes, el miedo a "la llamada".
- **Mecanismo:** artefacto integrado en un objeto cotidiano (bastón, sillón, taza) con conectividad propia (celular/LoRa), que detecta de forma pasiva la rutina diaria sin que el adulto mayor haga nada ni dependa del WiFi de casa.
- **IA:** modelo en la nube que aprende el patrón de rutina de cada persona y notifica al hijo/a **solo por excepción**, cuando algo se rompe.
- **Advertencia metodológica:** _[indica aquí si ya hay entrevistas reales o si todo parte de investigación secundaria + Pain-Gain Map de semana 2]_

---

## Investigación con IA

Encadené un "rol" distinto de IA por bloque: perfil de segmento, dimensionamiento, mapa competitivo + Blue Ocean, y propuesta de valor.

### Prompt 1 — Perfil de segmento accionable (4 capas)

**IA utilizada:** _[Claude / otra]_ — rol: investigador de mercado en segmentación para negocios digital-físicos en LATAM

```text
Actúa como un investigador de mercado con especialización en
segmentación de clientes para negocios de producto digital-físico
en mercados emergentes latinoamericanos. Tu metodología combina
datos demográficos verificables con análisis conductual y
psicográfico basado en comportamiento observable — nunca en
suposiciones sobre actitudes o valores generales. Cuando el
equipo no tiene evidencia de una capa, lo señalas directamente
en lugar de rellenar con hipótesis no marcadas.

Concepto: DistanciaCero (app con IA + artefacto conectado +
canal de venta digital).
Segmento tentativo: hijos/as de 35-55 años en México con
padre/madre de 65+ que vive solo y lejos.

Evidencia secundaria disponible:
[pega aquí tus fuentes: INEGI, mercado de botones de pánico,
comunidades de cuidadores, pilotos de tele-asistencia, etc.]

Construye el perfil en 4 capas: demográfica, conductual,
psicográfica y de disposición a pagar. Marca cada dato como
VERIFICADO o HIPÓTESIS. Sé especialmente estricto con las capas
conductual y psicográfica: no pueden marcarse como confirmadas
sin entrevistas reales. Cierra con las hipótesis críticas que
las entrevistas deben resolver primero.
```

> **RESULTADO DE LA IA:**
>
> _[pega aquí]_

> **Hipótesis críticas identificadas:**
> 1. _[ ]_
> 2. _[ ]_
> 3. _[ ]_
>
> **Próximo paso señalado:** _[ ]_

---

### Prompt 2 — Dimensionamiento de mercado (TAM / SAM / SOM)

**IA utilizada:** _[ ]_ — rol: analista de dimensionamiento top-down con triangulación de fuentes (INEGI, CEPAL, BID)

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
Precio estimado: [rango MXN/mes]
Modelo: [suscripción / pago único / híbrido]
Mercado inicial: México. Expansión: LATAM año 3+.

Construye TAM, SAM y SOM con reducción paso a paso, cada
filtro con su fuente o supuesto de primer principio explícito.
Cierra con un análisis de sensibilidad: qué supuesto es el más
frágil y cuánto mueve el resultado si cambia.
```

> **RESULTADO DE LA IA:**
>
> _[pega aquí la construcción paso a paso]_

| Nivel | Universo | Valor anual |
|---|---|---|
| TAM | _[ ]_ | _[ ]_ |
| SAM (geografía + canal + deciles de ingreso) | _[ ]_ | _[ ]_ |
| SOM (años 1–2) | _[ ]_ | _[ ]_ |

> **Señal de viabilidad:** _[sólida / marginal / insuficiente]_ — _[justificación]_
>
> **Supuesto más frágil del modelo:** _[ ]_ — rango de sensibilidad: _[ ]_

---

### Prompt 3 — Mapa competitivo (directos, indirectos, sustitutos)

**IA utilizada:** _[ ]_ — rol: analista de inteligencia competitiva en producto digital-físico en LATAM

```text
Actúa como analista de inteligencia competitiva especializado
en mercados de producto digital-físico en América Latina. Para
cada competidor buscas su debilidad específica para el segmento
del equipo, no debilidades genéricas.

Concepto: DistanciaCero — [descripción en 2 líneas]
Segmento: [el segmento accionable del Prompt 1]
Dolor ⭐: [el dolor principal del Pain-Gain Map]
Precio estimado: [rango]

Mapea mínimo 3 competidores directos, 3 indirectos y 2
sustitutos. Para cada uno: dónde opera, precio y modelo de
negocio, y su debilidad específica frente a nuestro segmento.
Cierra señalando cuál es el competidor más peligroso y por qué
— considerando también sustitutos informales o no tecnológicos.
```

> **RESULTADO DE LA IA:**
>
> _[pega aquí]_

| Tipo | Competidor | Precio / modelo | Debilidad para nuestro segmento |
|---|---|---|---|
| Directo | _[ ]_ | _[ ]_ | _[ ]_ |
| Directo | _[ ]_ | _[ ]_ | _[ ]_ |
| Directo | _[ ]_ | _[ ]_ | _[ ]_ |
| Indirecto | _[ ]_ | _[ ]_ | _[ ]_ |
| Indirecto | _[ ]_ | _[ ]_ | _[ ]_ |
| Indirecto | _[ ]_ | _[ ]_ | _[ ]_ |
| Sustituto | _[ ]_ | _[ ]_ | _[ ]_ |
| Sustituto | _[ ]_ | _[ ]_ | _[ ]_ |

> **Competidor más peligroso:** _[ ]_ — **por qué:** _[ ]_

---

### Prompt 4 — Lienzo estratégico Blue Ocean

**IA utilizada:** _[ ]_ — rol: estratega de innovación en Blue Ocean Strategy para hardware + software

```text
Actúa como estratega de innovación con experiencia en Blue Ocean
Strategy. Aplica el Marco de las Cuatro Acciones (Eliminar /
Reducir / Incrementar / Crear) antes de construir el lienzo.
Cuando el equipo no tiene ventaja en un atributo, puntúalo bajo.

Mapa competitivo: [pega el resultado del Prompt 3]
Descripción técnica: [mecanismo del artefacto + rol de la IA]
Capacidades diferenciales del equipo: [sistemas embebidos,
diseño y manufactura física, firmware propio, etc.]
Segmento accionable: [del Prompt 1]

Entrega:
1. Marco de las Cuatro Acciones con justificación de cada una
2. Lienzo estratégico con puntajes 0-5 por atributo, comparando
   nuestra propuesta contra cada competidor del mapa
3. El océano azul en una oración
4. Advertencia de océano rojo: en qué atributo NO tenemos
   ventaja real y por qué eso es un riesgo
```

> **RESULTADO DE LA IA — Marco de las Cuatro Acciones:**
>
> - **ELIMINAR:** _[ ]_
> - **REDUCIR:** _[ ]_
> - **INCREMENTAR:** _[ ]_
> - **CREAR:** _[ ]_

> **Lienzo estratégico:**
>
> _[pega aquí la tabla de puntajes por atributo]_

> **Océano azul en una oración:** _[ ]_
>
> **Advertencia de océano rojo:** _[ ]_

---

### Prompt 5 — Propuesta de valor final

**IA utilizada:** _[ ]_ — rol: estratega de marca, combinando el framework Insightful/Unique/Targeted de IDEO con la Pirámide de Valor de Bain

```text
Actúa como estratega de marca y comunicación. Combina el
framework IDEO (Insightful / Unique / Targeted) con la Pirámide
de Valor de Bain. Nombra al usuario específico, nombra el
resultado concreto, implica por qué esta solución y no otra.
No uses "plataforma", "solución integral", "innovador" ni
"ecosistema". No describas el producto — describe el valor
que entrega.

Perfil de segmento: [del Prompt 1]
Dolor ⭐ y ganancia ⭐: [del Pain-Gain Map]
Competidor más peligroso y su debilidad: [del Prompt 3]
Hueco azul identificado: [del Prompt 4]
Precio estimado: [rango]

Entrega:
1. Tres versiones de propuesta de valor, máximo 25 palabras
   cada una
2. En qué nivel de la Pirámide de Bain opera cada una y hasta
   dónde es legítimo subir con la evidencia actual
3. Evaluación IDEO de la versión más fuerte (✅/⚠️/❌ por
   criterio, con justificación)
4. La diferencia entre nuestra oferta y nuestra propuesta de
   valor, explicada con nuestro propio caso
```

> **RESULTADO DE LA IA:**
>
> _[pega aquí las 3 versiones]_

> **Nivel en la Pirámide de Bain:** _[Funcional / Emocional / Transformador]_ — _[justificación]_
>
> **Evaluación IDEO:** Insightful _[✅/⚠️/❌]_ · Unique _[✅/⚠️/❌]_ · Targeted _[✅/⚠️/❌]_
>
> **Versión elegida:**
> > _[pega aquí la propuesta de valor final]_
>
> **Oferta vs. propuesta de valor en nuestro caso:** _[ ]_

---

## Conclusión de la semana

| Bloque | Resultado |
|---|---|
| Segmento accionable | _[ ]_ |
| TAM / SAM / SOM | _[ ]_ |
| Mapa competitivo | _[ ]_ |
| Blue Ocean | _[ ]_ |
| Propuesta de valor | _[ ]_ |

> **Pendiente explícito para la siguiente semana:** _[ ]_

---

## ¿Qué aprendí?

> _[escribe aquí 1–2 párrafos: qué te cambió la forma de ver el mercado, qué supuesto resultó más frágil de lo que creías, qué te sorprendió del lienzo]_

## Reflexión personal

> _[escribe aquí tu reflexión en primera persona: qué significaba "conocer al mercado" para ti antes de esta actividad y qué significa ahora]_

### Enlaces

- [Claude]( )
- [Perplexity]( )

## Estado de la actividad

🟡 **En curso** — _[describe qué quedó completo y qué falta para cerrar]_

**Evidencias:** prompts + resultados de IA + perfil de segmento en 4 capas + TAM/SAM/SOM + mapa competitivo + lienzo Blue Ocean + propuesta de valor en 3 versiones