# P01 · Diseñar una investigación de mercados

Origen: [Curso] proceso de 4 pasos y propuesta escrita · [K&A cap. 4] · reglas de operación [Kit].
Marcos de apoyo: `references/04-investigacion-de-mercados.md`. Si el estudio es para dimensionar, también `references/06-dimensionamiento-de-mercado.md`.

## Cuándo usarlo
Hay una decisión de negocio que depende de un dato que hoy no se tiene: lanzar o no, a qué precio, a quién, con qué mensaje, por qué cayeron las ventas.
Consultar un dato suelto no requiere este procedimiento. Una investigación
sistemática con fuentes secundarias sí lo sigue: evalúa pertinencia, calidad
y actualidad de las fuentes, aunque los datos ya existan.

## Qué puede hacer Claude y qué no [Kit]
| Modo | Qué es | Qué hace Claude |
|---|---|---|
| **Diseñar** la investigación | Plan, instrumento, muestra, presupuesto | Lo hace completo (pasos 1-2 y propuesta escrita) |
| **Trabajo de campo** | Aplicar encuestas, entrevistas, observación, experimentos con personas reales | No lo hace. Nunca dice que se levantó información que no se levantó; puede preparar guías, cuestionarios y protocolos para que alguien lo haga |
| **Procesar datos del cliente** | Respuestas, ventas, CRM o resultados que entrega el usuario | Sí: limpia, tabula, calcula e interpreta (pasos 3-4), etiquetando el resultado como basado en "Dato del cliente" y revisando antes calidad, tamaño y forma de la muestra |
| **Analizar fuentes existentes** | Bases públicas, reportes, estudios publicados | Sí, citando fuente y fecha; si no pudo abrir la fuente, lo dice |

Al analizar datos reales: primero la calidad (faltantes, duplicados, cómo se obtuvo la muestra), luego los resultados. Un resultado de una muestra no probabilística se reporta como descriptivo de quienes respondieron.

## Información mínima para arrancar
1. La decisión que se va a tomar y quién la toma.
2. Lo que ya se sabe (reportes internos, estudios previos, datos públicos).
3. Plazo y presupuesto aproximado.
Aplica primero el encuadre de SKILL.md. Distingue objetivo de negocio,
decisión y objetivo de investigación. Delimita población, unidad de análisis,
geografía y periodo. Si falta la decisión, usa el máximo compartido de preguntas
y continúa con una formulación provisional y objetivos exploratorios explícitos.
Vincula cada pregunta del estudio con una decisión y un criterio de éxito;
no inventes resultados, umbrales o representatividad para completarlos.

## Banco de preguntas: elegir dentro del máximo compartido de tres
- ¿Qué vas a decidir con el resultado y qué harías distinto según lo que salga?
- ¿Qué indicador te haría decidir que sí y cuál que no?
- ¿Qué información ya tienes (ventas, clientes, estudios, quejas)?
- ¿Cuánto tiempo y dinero hay para el estudio?

## Pasos
**Paso 1 · Definir la situación y los objetivos** [Curso]
- Escribe la situación de negocio en una frase y la decisión que alimenta.
- Define el alcance (extenso o acotado) y objetivos medibles.
- Nombra los indicadores que sostienen la decisión.
- Elige el tipo: exploratoria (no se sabe bien qué pasa), descriptiva (cuánto, quién, cómo) o causal (si cambio X, ¿pasa Y?).
- Regla: no se investiga para justificar una decisión ya tomada.

**Paso 2 · Plan de investigación** [Curso + K&A]
Traduce cada objetivo en necesidades de información concretas y decide, por cada una:
| Decisión | Opciones | Criterio |
|---|---|---|
| Enfoque | Cualitativo / cuantitativo | Cuali para explorar; cuanti para medir; generalización sujeta al diseño |
| Fuente | Fuentes secundarias primero, empezando por las de `fuentes-del-usuario.md` si existe; primaria si hace falta | Evaluar pertinencia, calidad y actualidad |
| Enfoque de obtención | Observación, etnografía, encuesta, experimento | Para causa, diseño con contrafactual defendible |
| Instrumento | Cuestionario (preguntas abiertas o cerradas) o instrumento mecánico/digital (analítica, escáner, medición de uso) [K&A] | Que mida lo que la decisión necesita |
| Muestreo | Probabilístico (aleatorio simple, estratificado, conglomerados) o no probabilístico (conveniencia, juicio, cuota) | Probabilístico solo si hay que generalizar |
| Contacto | Correo, teléfono, en línea, cara a cara | Costo, rapidez, calidad de respuesta, sesgo |

Para inferir sobre una población, declara población, marco, selección, cobertura
y no respuesta; cuantificar no garantiza representatividad. Para estimar, declara
precisión y confianza, según variabilidad y diseño. Para causa, explicita
contrafactual, supuestos y límites; distingue muestreo de asignación de tratamiento.

**Propuesta escrita** [Curso]: situación de negocio, objetivos, información necesaria, cómo ayudarán los resultados a decidir y presupuesto.

**Paso 3 · Implementar** [Curso]
Recopilar (supervisar la calidad de las respuestas), procesar y analizar (tabular, medidas estadísticas). Claude no hace trabajo de campo ni inventa resultados; si el usuario entrega los datos, Claude sí los procesa y analiza (ver tabla de modos).

**Paso 4 · Interpretar y presentar** [Curso]
Hallazgos ligados a los objetivos del paso 1, insights (verdad + fricción + solución) y la recomendación para la decisión. Investigador y responsable de marketing comparten la responsabilidad de la decisión.

## Cómo interpretar [Kit]
- Separa lo que dice la gente (declarado) de lo que hace (observado). La intención de compra declarada sobreestima la compra real.
- Una muestra de conveniencia describe a quien contestó, no al mercado.
- Una correlación o un antes/después no prueba causa: hace falta un diseño con contrafactual defendible, supuestos y límites explícitos.
- Revisa los sesgos de recolección: cortesía, presión social, identidad en línea [Curso].

## Entregable
Propuesta de investigación de una página: decisión, objetivos, tabla de necesidades de información → fuente → método → muestra → indicador, cronograma y presupuesto en rangos, y qué resultado lleva a qué decisión.

## Decisiones que apoya
Entrar o no a un mercado, lanzar o no, elegir segmento, fijar precio, elegir mensaje, explicar una caída.

## Límites
- Claude no tiene datos de campo: todo resultado sin fuente se marca `SUPUESTO` o `[NO ENCONTRADO]`.
- Costos de estudios y tamaños de muestra concretos dependen del proveedor y del margen de error que se acepte: se dan como rangos con su supuesto, nunca como precio cerrado.
