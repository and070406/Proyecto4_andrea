# Semana 6
## Generación y Selección de Concepto de Diseño

**Tema:** DistanciaCero — Tabla morfológica, analogías tecnológicas, 3 conceptos de diseño, Matriz de Pugh y crítica técnica del boceto
**Blueprint:** Creación de valor · **DVF:** 🔴 Deseable · 🟢 Factible

---

## Objetivo

Hasta semana 5 sabíamos **qué** debía hacer el sistema (el PDS) y **cómo se conectaban** sus componentes (la arquitectura). Esta semana fue para decidir **cómo se ve, cómo se toca y cómo se usa** — el concepto de diseño no es decoración, es la primera decisión que el usuario va a juzgar antes de entender cómo funciona el producto por dentro.

El trabajo siguió un flujo de 6 prompts en secuencia: tabla morfológica → analogías tecnológicas → 3 conceptos de diseño completos (artefacto + app + landing) → prompts de render → Matriz de Pugh para elegir entre los 3 → crítica técnica del boceto del concepto ganador.

---

## Contexto del producto

- **Restricciones del PDS relevantes para el diseño:** uso en interior sin exigencia de IP alta; presupuesto de manufactura ~$800–1,100 MXN por unidad; instalación por el hijo/a en ≤10 min sin participación del adulto mayor (RI-03, RR-02); el componente más grande del hardware interno es el módulo celular SIM7600E-H + batería 18650, lo que impone un volumen mínimo a cualquier carcasa.
- **Punto de partida:** desde semana 2 el producto se describía integrado en "un objeto cotidiano (bastón, sillón, taza)" sin haber decidido cuál ni cómo. Esta semana convertimos esa frase en tres conceptos concretos y elegimos uno con criterios explícitos, no por preferencia estética.

---

## Trabajo con IA

### Prompt 1 — Tabla morfológica

**IA utilizada:** Claude (Anthropic) — rol de diseñador industrial especializado en productos de hardware conectado para mercados latinoamericanos, con sesgo hacia opciones construibles con medios universitarios

```text
Actúa como diseñador industrial especializado en productos de
hardware conectado para mercados latinoamericanos. Tu sesgo es
hacia opciones construibles con medios universitarios — nada
que no pueda salir de un laboratorio con impresora 3D, CNC
básica y acceso a componentes en México.

Producto: DistanciaCero — sistema que detecta pasivamente la
rutina diaria de un adulto mayor que vive solo, integrado en un
objeto cotidiano, notificando al hijo/a solo por excepción.
Usuario y contexto: adulto mayor 65+ en su propia casa (objeto
anfitrión) + hijo/a 35-55 que instala y monitorea desde la app.

Restricciones del PDS relevantes:
· Resistencia ambiental: interior, IP54 razonable
· Presupuesto de manufactura: ~$800-1,100 MXN/unidad
· Instalación: por el hijo/a en ≤10 min, sin participación del
  adulto mayor
· Dimensiones mínimas: deben alojar un módulo celular
  SIM7600E-H (~30×30mm) + batería 18650 (18mm × 65mm)

Genera tabla morfológica con 7 parámetros, 3 variantes cada
uno, cada variante fabricable con los medios del equipo.
```

**Resultado de la IA**

> Se generaron 7 parámetros (objeto anfitrión, forma de carcasa, método de instalación, indicador de estado, material/acabado, interfaz física y fuente de energía), 3 variantes cada uno, cada variante anotada con su implicación de manufactura (impresión 3D, mecanizado, sobremoldeo). El parámetro "objeto anfitrión" no estaba en la plantilla original del prompt base — lo agregamos como séptimo parámetro porque era justo la decisión que el proyecto había dejado abierta desde semana 2 (bastón/sillón/taza, sin decidir cuál).

| Parámetro | Variante A | Variante B | Variante C |
|---|---|---|---|
| Objeto anfitrión | Bastón (impresión 3D + inserto) | Sillón/silla (módulo adherido bajo cojín o brazo) | Taza/posavasos (cápsula removible) |
| Forma de la carcasa | Cilíndrica integrada al eje | Placa delgada rectangular redondeada | Cápsula circular plana removible |
| Método de instalación | Inserto deslizante dentro del bastón | Velcro industrial bajo el cojín | Adhesivo/magnético bajo la taza o posavasos |
| Indicador de estado | LED tipo detector de humo (parpadeo breve periódico) | Sin indicador físico — todo en app | Anillo luminoso tenue en la base |
| Material y acabado | ABS acabado "madera" mate | Silicona suave, textura de tapicería | Acabado "cerámico" satinado |
| Interfaz física | Sin botones — automático | Botón único de reset recesado | Touch capacitivo oculto |
| Fuente de energía | Batería 18650 removible, acceso por tapa inferior | Batería 18650, acceso por panel trasero | Batería sellada, reemplazo de cápsula completa |

---

### Prompt 2 — Analogías tecnológicas

**IA utilizada:** Claude (Anthropic) — rol de consultor de innovación de diseño especializado en transferencia de soluciones entre sectores

```text
Actúa como consultor de innovación de diseño con experiencia
en transferencia de soluciones entre sectores. No buscas
inspiración estética — buscas mecanismos de interacción,
formas de instalación y lógicas de feedback que ya funcionaron
en otro contexto.

Producto: DistanciaCero. Usuario: adulto mayor 65+ que no debe
sentir vigilancia activa + hijo/a que sí necesita señal de que
el aparato funciona.

Tabla morfológica adjunta [Prompt 1].

Parámetros donde quiero más inspiración:
- Indicador de estado (evitar ansiedad, dar confirmación sin
  sentirse como vigilancia)
- Material y acabado (evitar que se sienta como dispositivo
  médico)
- Fuente de energía (cero acción del adulto mayor — RR-02)

Para cada uno, encuentra 2 productos de sectores
completamente distintos que resuelvan el mismo problema de
experiencia, y cómo trasplantar la lógica.
```

**Resultado de la IA**

> Para **indicador de estado**: el detector de humo doméstico (parpadeo casi imperceptible en uso normal, prominente solo ante falla real) y los wearables sin pantalla tipo anillo Oura (la confirmación vive 100% en el teléfono, nunca en el objeto).
>
> Para **material y acabado**: fabricantes de bastones de gama alta (acabados en madera que evitan la estética clínica) y electrodomésticos de cocina retro (curvas generosas, colores cálidos en vez de "gadget" técnico).
>
> Para **fuente de energía**: la base de carga por inducción de un cepillo eléctrico (recargar sin que el usuario conecte nada — trasplantada como carga por contacto magnético en el soporte donde el bastón siempre se guarda) y las cámaras de seguridad con batería de meses (mantenimiento espaciado vía visitas programadas, no carga diaria).

**Variante que agregamos a la tabla a partir de estas analogías:** fuente de energía → "carga por contacto magnético en soporte fijo", inspirada en la base del cepillo eléctrico.

---

### Prompt 3 — Los 3 conceptos de diseño

**IA utilizada:** Claude (Anthropic) — rol de diseñador industrial y UX designer, articulando el sistema completo de tres componentes (artefacto, app, landing page)

```text
Actúa como diseñador industrial y UX designer. Articula
conceptos de diseño completos para los tres componentes del
producto, de forma que cada uno refuerce la misma propuesta
de valor.

Producto: DistanciaCero
Propuesta de valor: "Para hijos que viven lejos de su padre o
  madre mayor, DistanciaCero reemplaza el miedo a 'la llamada'
  por la certeza diaria de que todo está bien — sin preguntar,
  sin culpa."

Tabla morfológica final [con variantes de Prompt 1 y 2].

CONCEPTO 1 — Bastón: cilíndrico integrado, inserto deslizante,
  LED tipo detector de humo, acabado madera, sin botones,
  batería con carga por contacto magnético.
CONCEPTO 2 — Sillón: placa delgada, velcro bajo cojín, sin
  indicador físico, silicona neutra, botón único recesado,
  batería con acceso por panel trasero.
CONCEPTO 3 — Taza: cápsula removible, adhesivo/magnético,
  anillo luminoso tenue, acabado cerámico, touch capacitivo
  oculto, batería sellada.

Desarrolla para cada uno: artefacto (instalación, uso
cotidiano, principios activos), app (pantalla principal) y
landing page (headline, visual, CTA).
```

**Resultado de la IA**

**Concepto 1 — "El Bastón Centinela"**

| | |
|---|---|
| Instalación | Insertar el módulo en la base hasta hacer clic → colocar en su soporte de carga → esperar luz verde breve → escanear QR en la app |
| Uso cotidiano | Se usa como un bastón normal; el único cambio de hábito es guardarlo siempre en su soporte, que también lo carga |
| Principios activos | Affordances (el soporte solo encaja en una orientación) · Contour bias (torneado sin aristas) · Confirmación (LED breve solo en instalación) |
| App — normal | Ícono de bastón en verde + "Todo tranquilo hoy" |
| App — alerta | Ícono en rojo + "Mamá no se ha movido en las últimas 3 horas" |
| App — omisión deliberada | Sin gráficas de movimiento ni datos crudos |
| Landing — headline | "El bastón de tu mamá ahora también cuida de ti." |

**Concepto 2 — "El Reposabrazos Centinela"**

| | |
|---|---|
| Instalación | Elegir el sillón de mayor uso → levantar cojín → adherir con velcro → recolocar cojín → confirmar detección de peso en la app |
| Uso cotidiano | Completamente invisible — el adulto mayor se sienta como siempre, sin saber que el sensor está ahí |
| Principios activos | Constraints (el velcro solo cabe en una posición) · Costo-beneficio (LED eliminado a propósito, refuerza discreción) · Consistencia (acabado imita la tapicería) |
| App — normal | Check verde grande + "Todo bien, se ha movido normalmente hoy" |
| App — alerta | Aviso rojo + "No detectamos actividad desde las 2:00pm" |
| App — omisión deliberada | No revela bajo qué cojín específico está el sensor (privacidad) |
| Landing — headline | "Sabrás que está bien sin tener que preguntarle." |

**Concepto 3 — "El Posavasos Guardián"**

| | |
|---|---|
| Instalación | Colocar el posavasos donde se toma café/té → tocar el centro una vez → confirmar anillo luminoso → vincular en la app |
| Uso cotidiano | Se usa como cualquier posavasos; el anillo se ilumina tenue al detectar uso, sin delatar su función real |
| Principios activos | Affordances (forma circular invita a poner la taza, sin instrucción) · Confirmación (anillo inmediato pero ambiguo a propósito) · Contour bias (completamente circular) |
| App — normal | Taza llena en verde + "Desayunó esta mañana, como siempre" |
| App — alerta | Taza vacía/gris + "Hoy no ha usado su posavasos todavía" |
| App — omisión deliberada | No muestra conteo de usos en el día — solo el primero relevante |
| Landing — headline | "Un café, una señal de que todo está bien." |

---

### Prompt 4 — Prompts de render (Midjourney / Imagen 3)

**IA utilizada:** Claude (Anthropic) — rol de director de arte especializado en prompts de render para diseño industrial, con conocimiento de la sintaxis de Midjourney v6 e Imagen 3

**Resultado de la IA** (para el concepto que terminó ganando en la Matriz de Pugh — ver abajo)

> **Midjourney:** `soft silicone rectangular sensor pad, neutral taupe color, seamless integration under armchair cushion fabric, no visible electronics, gentle rounded edges 4mm radius, warm living room lighting, three-quarter view, photorealistic product render, minimal, no text, no logos --ar 4:3 --style raw --v 6`
>
> **Imagen 3:** "A soft silicone pad in neutral grey, roughly the size of a hand, with gently rounded edges and a matte upholstery-like texture, photographed at a three-quarter angle as it would sit tucked under the cushion of a cozy armchair in a warm living room. No visible buttons, lights, or electronic ports. Soft natural daylight, shallow depth of field."
>
> Los renders todavía no se generaron a partir de estos prompts — quedan listos para la siguiente sesión.

---

### Prompt 5 — Matriz de Pugh

**IA utilizada:** Claude (Anthropic) — rol de ingeniero de producto especializado en selección de concepto, asegurando balance entre deseabilidad (≥40% del peso) y factibilidad

```text
Actúa como ingeniero de producto con experiencia en Matriz de
Pugh. No permitas que la matriz esté dominada por criterios
técnicos.

3 conceptos [descripción de cada uno — ver Prompt 3].
Datum: Concepto 1 (Bastón) — la opción descrita desde semana 2.

Usuario: hijo/a 35-55 que instala, adulto mayor 65+ que no
debe sentir vigilancia.
Restricciones de manufactura: JLCPCB+PCBA para 8 unidades,
presupuesto ~$800-1,100 MXN/unidad.

Construye la matriz con mínimo 3 criterios de deseabilidad y
3 de factibilidad, deseabilidad ≥40% del peso total.
```

**Resultado de la IA**

> **Criterios y pesos** — deseabilidad: facilidad de instalación (15%), discreción/no parecer dispositivo médico (15%), confianza del material (10%), tamaño apropiado (10%) → 50% total. Factibilidad: costo de manufactura (15%), complejidad de ensamble (10%), disponibilidad de materiales (10%), compatibilidad JLCPCB (10%), facilidad de mantenimiento (5%) → 50% total.

| Criterio (peso) | C1 — Bastón (datum) | C2 — Sillón | C3 — Taza |
|---|:--:|:--:|:--:|
| Instalación sin instrucciones (15%) | datum | + | + |
| Discreción (15%) | datum | + | + |
| Confianza del material (10%) | datum | S | S |
| Tamaño — ¿cabe SIM7600+18650? (10%) | datum | + | – |
| Costo de manufactura (15%) | datum | + | + |
| Complejidad de ensamble (10%) | datum | + | + |
| Disponibilidad de materiales (10%) | datum | S | S |
| Compatibilidad JLCPCB (10%) | datum | + | + |
| Facilidad de mantenimiento (5%) | datum | + | – |

**Puntuación ponderada:** C2 (Sillón) = **+80** · C3 (Taza) = +60 · C1 (datum) = 0

> **Concepto ganador: Concepto 2 — "El Reposabrazos Centinela"** — domina los dos criterios de deseabilidad de mayor peso y resuelve mejor la restricción física real del proyecto: el volumen del SIM7600E-H + batería 18650 cabe con holgura en un sillón, apretado en un bastón o un posavasos.
>
> **Riesgo principal señalado por la IA (fuera de la matriz):** el diseño asume que el adulto mayor se sienta siempre en el mismo sillón — si no es así, el periodo de aprendizaje de rutina (RF-03, semana 5) puede confundirse con falsos positivos.
>
> **Iteración recomendada:** adoptar del Concepto 1 el acabado cálido (imitar la tela del sillón en vez de silicona técnica) y del Concepto 3 el diseño de cápsula de batería fácilmente removible.

---

### Prompt 6 — Crítica técnica del boceto

**IA utilizada:** Claude (Anthropic) — rol de ingeniero de diseño industrial especializado en revisión de bocetos técnicos pre-CAD, priorizando los 3 problemas más importantes

```text
Actúa como ingeniero de diseño industrial revisando bocetos
pre-CAD. Prioriza los 3 problemas más importantes, no corrijas
todo.

Concepto elegido: "El Reposabrazos Centinela" (Matriz de Pugh).

Boceto técnico: placa 90×60×15mm, ABS con sobremoldeo de
silicona gris topo, radio de esquina 4mm, PCB interna 70×45mm
(ESP32-S3 + MPU6050 + SIM7600E-H + 18650), instalación por
velcro industrial bajo el cojín, acceso a batería por tapa
trasera con 2 tornillos Torx de seguridad, sin LED visible.

Wireframe: pantalla principal con check verde/alerta roja,
botón único de acción, sin gráficas técnicas.
```

**Resultado de la IA**

| Problema | Por qué es crítico | Solución |
|---|---|---|
| **Sin confirmación en instalación** — ningún indicador físico y el primer reporte tarda 15-30 min | Viola el principio de Confirmación — genera dudas y reinstalaciones innecesarias justo cuando más se necesita certeza | LED temporal que enciende solo los primeros 2 min tras el primer encendido, luego se apaga permanentemente |
| **Asume un único sillón de uso consistente** — si el adulto mayor usa varios asientos, "ausencia" se marca como anomalía constantemente | Genera falsos positivos que violan RD-02 (<5%, semana 5) y erosiona la confianza en las alertas | Validar con observación real cuál es el mueble de uso más consistente antes de fabricar, o detectar "zona" en vez de peso en un cojín específico |
| **Tornillos de seguridad dificultan el mantenimiento que sí debe ser fácil** — pensados contra el adulto mayor, estorban al hijo/a que abre cada 15-20 días | Contradice el objetivo de mantenimiento simple para quien sí necesita acceso frecuente | Mecanismo de apertura sin herramienta pero no obvio (pestaña a presión oculta) |

**Preguntas sin resolver:** ¿el velcro resiste movimiento si el sillón es reclinable o mecedora? ¿aguanta meses de fricción diaria sin despegarse? ¿cómo distingue el hijo/a cuál sillón tiene el sensor si hay varios similares en casa?

**Fortaleza del diseño:** eliminar el indicador LED permanente fue la decisión correcta — consistente con el posicionamiento del producto desde semana 4 ("silencio = tranquilidad") y evita que el objeto se sienta como vigilancia activa.

**Listo para CAD:** ⚠️ con ajustes — los tres problemas son resolubles sin rediseñar el concepto, pero deben resolverse antes de modelar.

---

## Entregable de la semana

**Concepto elegido:** El Reposabrazos Centinela

### Boceto técnico

| Especificación | Valor |
|---|---|
| Dimensiones | 90 × 60 × 15 mm |
| Material exterior | ABS con sobremoldeo de silicona, gris topo |
| Radio de esquina | 4 mm (contour bias) |
| PCB interna | 70 × 45 mm — ESP32-S3, MPU6050, SIM7600E-H, batería 18650 |
| Instalación | Velcro industrial bajo el cojín del sillón de mayor uso |
| Acceso a batería | Panel trasero — pendiente rediseño de apertura (ver Problema 3) |
| Indicador | Ninguno permanente — LED temporal de confirmación pendiente de agregar (ver Problema 1) |

### Wireframe de la app

| Pantalla | Estado normal | Estado de alerta |
|---|---|---|
| Principal | Check verde + "Todo bien, se ha movido normalmente hoy" | Aviso rojo + "No detectamos actividad desde las 2:00pm" |
| Acción principal | "Ver detalle" | "Ver detalle" / "Llamar ahora" |
| Flujo de instalación | Elegir sillón → adherir módulo → confirmar detección en la app (3 pasos) | — |

---

## Veredicto de la semana

**QUEDA RESUELTO:** 3 conceptos genuinamente distintos (difieren en objeto anfitrión, forma, instalación, indicador, material e interfaz) evaluados con una Matriz de Pugh balanceada (50% deseabilidad / 50% factibilidad) · concepto ganador elegido con criterios defendibles, no por preferencia estética · boceto técnico con dimensiones, materiales y ubicación de componentes definidos.

**QUEDA PENDIENTE:** los 3 problemas críticos señalados en la crítica del boceto (confirmación de instalación, consistencia del mueble de uso, mecanismo de apertura para mantenimiento) deben resolverse antes de pasar a CAD — el estado es "con ajustes", no "listo". El render visual (Midjourney/Imagen 3) está en prompt listo pero no generado todavía.

**Próximo paso:** generar los renders con los prompts del Prompt 4, resolver los 3 problemas del boceto, y validar con observación real cuál es el mueble de mayor uso consistente del adulto mayor antes de comprometernos con el diseño final en CAD.

---

## Reflexión personal

> Antes de esta semana, "diseño" era para mí básicamente "elegir cómo se ve la caja" — una decisión casi cosmética, al final del proceso técnico. Construir la tabla morfológica y después forzar tres conceptos genuinamente distintos me hizo ver que el diseño está tan amarrado a las restricciones técnicas como cualquier decisión de arquitectura: no pudimos elegir el bastón como ganador aunque fue la primera idea del proyecto desde semana 2, porque al compararlo en serio contra el sillón, el espacio físico real para el hardware simplemente no alcanzaba igual de bien. Lo más incómodo — y más útil — fue la crítica del boceto: encontrar que nuestra propia decisión de "sin indicador, todo discreto" generaba un problema real de confirmación en el momento de instalación. Es el mismo patrón que ya habíamos visto en semanas anteriores: cada vez que el análisis es honesto sobre dónde hay una debilidad, en vez de maquillarla, es cuando el trabajo realmente avanza.
