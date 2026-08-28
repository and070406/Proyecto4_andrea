# Semana 1

La primera semana vimos como hacer el mejor prompt para poder utilizar y ayudarnos de la inteligencia artificial con nuestro trabajo, Lo que buscamos es que sea una herramienta que nos ayude a pensar mejor y hacer mejores análisis no que realice todo el trabajo.

Lo más importante al crear un prompt correcto son los siguientes aspectos:

``` codigo

- Definir el rol y nivel de expertise en el tema
- Para quien es el resultado
- Restricciones reales (tiempo, presupuesto, tecnología, etc)
- El "Para qué"
- El contexto 

```


---

# Ejercicio SCAMPER
El método SCAMPER consta de una técnica de creatividad e innovación. Sirve para generar ideas nuevas o mejorar productos, servicios y procesos que ya existen. Funciona como una lista de preguntas basada en siete acciones:

``` codigo

- Sustituir
- Combinar
- Adaptar
- Modificar/Magnificar
- Poner en otros usos
- Eliminar
- Revertir/Reorganizar

```

---
El ejercicio en clase consto de tirar un dado y de acuerdo a los números que te salieran era con lo que te tocaba trabajar en nuestro caso nos toco:

``` codigo

1. EL QUÉ (Formato/Entregable) : Un kit tangible o contenedor de Recursos (caja de herramientas, empaque inteligente, sistema de distribución física).
2. EL CÓMO (Restricción/Enfoque): Automatizado con IA / Digital (El núcleo de la solución debe operar de forma digital o automática).
3. EL PARA QUIÉN (Usuario/Contexto): Comunidad Rural / Migración Local (Zonas con intermitencia de servicios, familias separadas o migración constante).

```

---

# Prompt
El primer prompt que utilizamos fue el  que estaba en la página del profesor y lo editamos de acuerdo con lo que nos salió en el dado y es el siguiente:

Actúa como un Consultor Senior en Innovación, Diseño de Servicios y Estrategia de Negocios. Tengo un desafío de co-creación lúdico y disruptivo. He tirado tres dados que me han arrojado tres variables obligatorias para diseñar un proyecto: 1. EL QUÉ (Formato/Entregable) : Un Kit Tangible o Contenedor de Recursos (Caja de herramientas, empaque inteligente, sistema de distribución física). 2. EL CÓMO (Restricción/Enfoque): Automatizado con IA / Digital (El núcleo de la solución debe operar de forma digital o automática). 3. EL PARA QUIÉN (Usuario/Contexto): Comunidad Rural / Migración Local (Zonas con intermitencia de servicios, familias separadas o migración constante). Antes de comenzar a idear soluciones específicas, necesito que me ayudes a enmarcar y entender el problema profundamente. Haz lo siguiente de forma concisa: 1. CONTEXTO Y DOLOR: Define brevemente cuál es el principal punto de dolor (pain point) de este Usuario específico cuando se enfrenta a este Formato bajo esa Restricción técnica. 2. LA PARADOJA: Si existe una contradicción o incompatibilidad aparente entre las tres variables (por ejemplo, digital vs. brecha digital, o cero presupuesto vs. infraestructura), explica brevemente cómo podemos transformarla en una oportunidad de diseño inteligente (tecnología invisible, interfaces alternativas, etc.). 3. LAS 3 PREGUNTAS HMW: Genera 3 variantes del formato estricto "¿Cómo podríamos...?" (How Might We) que unan estas tres variables. Cada opción debe enfocarse en un ángulo diferente (eficiencia, impacto social o experiencia emocional). Termina tu respuesta preguntándome cuál de las 3 opciones de "¿Cómo podríamos...?" quiero elegir para pasar a la fase de ideación SCAMPER. 

# Imágenes

``` codigo
![Diagrama del sistema](recursos/imgs/ibero.jpeg)

<!-- Control de tamaño usando HTML (cuando se requiera) -->
<img src="../recursos/imgs/ibero.jpeg" alt="Diagrama del sistema" width="420">
```

![Diagrama del sistema](recursos/imgs/ibero.jpeg)

<img src="../recursos/imgs/ibero.jpeg" alt="Diagrama del sistema" width="420">

---

# PDFs (enlace y embebido)

``` codigo
[Descargar especificación (PDF)](recursos/archivos/Calendario.pdf)

<!-- Embed (requiere navegador compatible) -->
<object data="recursos/archivos/Calendario.pdf" type="application/pdf" width="100%" height="600">
  <p>No se pudo mostrar el PDF. <a href="../recursos/archivos/Calendario.pdf">Descargar</a></p>
</object>
```

[Descargar especificación (PDF)](recursos/archivos/Calendario.pdf)

<object data="../recursos/archivos/Calendario.pdf" type="application/pdf" width="100%" height="600">
  <p>No se pudo mostrar el PDF. <a href="../recursos/archivos/Calendario.pdf">Descargar</a></p>
</object>

---

# Admonitions (Material)

``` codigo
!!! note "Nota"
    Esto es una nota informativa.

!!! tip "Sugerencia"
    Un consejo breve para el usuario.

!!! warning "Advertencia"
    Precauciones o riesgos a considerar.

??? info "Más información (colapsable)"
    Contenido adicional que se puede expandir.
```

!!! note "Nota"
    Esto es una nota informativa.

!!! tip "Sugerencia"
    Un consejo breve para el usuario.

!!! warning "Advertencia"
    Precauciones o riesgos a considerar.

??? info "Más información (colapsable)"
    Contenido adicional que se puede expandir.

---

# Código con resaltado

``` codigo
```python
def medir(canal: int) -> dict:
    # Simulación de lectura
    return {"canal": canal, "valor": 523, "unidad": "mV"}

print(medir(1))
```
```

```python
def medir(canal: int) -> dict:
    # Simulación de lectura
    return {"canal": canal, "valor": 523, "unidad": "mV"}

print(medir(1))
```

---

# Separador horizontal

``` codigo
---
```

---

---

# Listas anidadas con código y notas

``` codigo
- **Módulo A**
  - Función: `procesar()`
  - Entrada:
    - `signal` (float)
    - `freq` (Hz)
  - Salida:
    - JSON con `valor`, `unidad`
  - !!! note
        Documenta rangos válidos y casos borde.
```

- **Módulo A**
  - Función: `procesar()`
  - Entrada:
    - `signal` (float)
    - `freq` (Hz)
  - Salida:
    - JSON con `valor`, `unidad`
  - !!! note
        Documenta rangos válidos y casos borde.

---

