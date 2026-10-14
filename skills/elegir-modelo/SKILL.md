---
name: elegir-modelo
description: 'Decide qué modelo (Haiku 5.5, Sonnet 5.5, Opus 5.5, Fable 5.1) y qué esfuerzo (low, medium, high, xhigh, max) usar en cada tarea según el tipo de trabajo y el plan de la cuenta (Pro, Max 5x, Max 20x, Team, Enterprise o API), y cuándo conviene ultracode. Úsala al planear subagentes, un fan-out o un workflow; al clasificar una tarea como trivial, mecánica, acotada o estructural; antes de lanzar agentes con la herramienta Agent o con agent() en un Workflow; y cuando el usuario pida rapidez, ahorro de tokens o de cuota, o calidad máxima ("hazlo rápido", "ahorra", "cuida la cuota", "me quedo sin límite", "con el mejor modelo", "qué modelo uso", "qué esfuerzo", "ultracode"). Dice cuándo preguntarle al usuario qué prioriza o en qué plan está, y cómo fijar el esfuerzo de un subagente.'
---

# Elegir modelo y esfuerzo

Datos al 2026-10-13. Cada cifra tiene su fuente en `referencias.md` (misma carpeta). Lo que no se pudo
comprobar lleva `[NO VERIFICADO]`. Si tienes instalado el kit Chema, esta skill es su capa fina: su
núcleo dice **cuándo** delegar y `kit-orquestacion` **cómo repartir**; aquí se decide **con qué modelo
y esfuerzo**. Sin el kit, funciona sola.

## Lo esencial

1. **Esfuerzo antes que modelo.** Ajusta el esfuerzo dentro del mismo modelo antes de cambiar de
   modelo. Anthropic: «Tuning effort is often a better lever than switching models».
2. **Opus 5.5 es el modelo de trabajo para todo lo que pide juicio.** En su esfuerzo por defecto
   (medium) iguala a Fable 5.1 en código (92.8 % contra 92.3 %) por cerca de 1/5 del costo por tarea
   resuelta (0.22 contra 1.19 USD). Fable 5.1 entra solo si Opus 5.5 en xhigh o max se quedó corto.
3. **Sonnet 5.5 ejecuta lo bien especificado; Haiku 5.5, lo mecánico y verificable.** Por token, Haiku
   cuesta 1/20 de Sonnet (con prompts de hasta 100 K tokens).
4. **El precio por token no predice el costo por tarea.** En tareas difíciles un modelo más fuerte con
   menos esfuerzo puede salir más barato: en una batería de código de Anthropic, Fable 5.1 en low
   resolvió 88.6 % a 0.54 USD por tarea resuelta y Sonnet 5, 77.4 % a 0.84 USD, pese a que Fable cuesta
   5 veces más por token. En tareas fáciles, donde todos aciertan, sí gana el más barato por token.
5. **La latencia depende más del esfuerzo que del modelo.** Si urge, baja el esfuerzo antes que el modelo.
6. **Delegar no es gratis.** Un subagente nuevo relee lo que tú ya tienes, y un fan-out cuesta del orden
   de 4 veces el hilo solo. Si el material está cargado y la tarea es corta, hazla tú.
7. **No cambies el modelo de la sesión a media tarea**: la caché es por modelo y se pierde.
8. **El plan fija el techo.** En Pro y en asientos estándar de Team o Enterprise, Fable no entra en el
   límite: se paga con créditos de uso. Cuando la cuota es el cuello de botella, Opus gasta «varias
   veces más por turno que Sonnet». No supongas el plan: si no lo sabes y la decisión depende de él,
   pregunta.

## Los cuatro modelos vigentes

| | Haiku 5.5 | Sonnet 5.5 | Opus 5.5 | Fable 5.1 |
|---|---|---|---|---|
| ID API | `claude-haiku-5-5` | `claude-sonnet-5-5` | `claude-opus-5-5` | `claude-fable-5-1` |
| Alias en Claude Code | `haiku` | `sonnet` | `opus` | `fable` |
| USD por millón (entrada / salida) | 0.10 / 0.50 hasta 100 K de prompt; 0.50 / 2.50 arriba | 2 / 10 | 4 / 20 | 10 / 50 |
| Precio relativo por token | 1 | 20 | 40 | 100 |
| Lectura de caché | 10 % de la entrada | 5 % | 5 % | 2.5 % |
| Contexto / salida máx. | 1 M / 128 K | 1 M / 128 K | 1 M / 128 K | 1 M / 128 K |
| Latencia (Anthropic) | la más rápida | rápida | moderada | más lenta |
| Esfuerzo por defecto (API · Claude Code) | medium · medium | high · medium | medium · medium | high · high |
| Para qué lo posiciona Anthropic | clasificar, extraer, enrutar, subagente | código y agentes del día a día | código agéntico largo y trabajo de conocimiento | razonamiento exigente, agentes de horas |

- Los alias `haiku` y `sonnet` apuntan a 5.5 en la API de Anthropic y en las suscripciones; en Bedrock y
  Google Cloud siguen en Haiku 4.5 y Sonnet 4.6.
- Haiku 5.5 usa el tokenizador nuevo: el mismo texto cuenta ~30 % más tokens que en Haiku 4.5.
- En los cuatro el razonamiento es adaptativo y el esfuerzo es el control principal. En Claude Code no
  se puede apagar el razonamiento en ninguno.

## Según el plan de la cuenta

| Plan | Qué trae (publicado) | Qué usar por defecto |
|---|---|---|
| **Pro** (20 USD al mes; 17 en pago anual) | Claude Code y Opus incluidos. Fable **no** entra en el límite: va con créditos de uso a tarifa de API. Workflows apagados por defecto y tamaño guía `small` (< 5 agentes) | Sesión: Sonnet 5.5 medium para lo rutinario y Opus 5.5 medium solo para planear y para lo estructural. Subagentes en Haiku o Sonnet, 3 como máximo. Sin Fable, max ni ultracode, salvo que el usuario acepte pagar créditos |
| **Max 5x** (100 USD) | 5 veces el uso por sesión de Pro. Fable incluido hasta el 50 % del límite semanal, con su propio tope semanal | Sesión: Opus 5.5 medium, y high en lo estructural. Ejecución en Sonnet 5.5 y lectura en Haiku 5.5. Hasta 5 agentes. Fable solo cuando Opus 5.5 en max se quedó corto. Ultracode solo por tarea, escribiendo la palabra |
| **Max 20x** (200 USD; a veces lo llaman «Ultra», pero ese plan no existe) | 20 veces el uso por sesión de Pro. Fable igual que en Max 5x | Sesión: Opus 5.5 high, y max en lo crítico. Hasta 10 agentes. Revisión con Opus. Fable para lo más difícil y la síntesis final. `/effort ultracode` en auditorías o migraciones grandes |
| **Team / Enterprise, asiento estándar** | Fable con créditos de uso. Límite por asiento cada 5 h y semanal, compartido con el chat; su tamaño no está publicado | Como Pro |
| **Team / Enterprise, asiento premium** | Fable incluido hasta el 50 % del límite semanal. Tamaño del límite no publicado | Como Max 5x |
| **API (Console) o Enterprise por uso** | Pago por token, sin límite semanal (puede haber tope de gasto) | Decide en dólares con la tabla de precios: la matriz de abajo, sin ajuste de cuota |
| **No se sabe** | — | Trátalo como Pro (sin Fable, max ni ultracode) y pregunta antes de lo caro |

Los topes de agentes por plan son criterio de esta skill. Se apoyan en el tamaño guía que Claude Code
fija por defecto: `small` en Pro y `medium` (< 10 agentes) en los demás planes.

**Si no sabes en qué plan está la cuenta**, no lo deduzcas por el nombre de la cuenta ni por su
correo. Pregunta una vez por sesión, y solo cuando la decisión dependa del plan (Fable, max, 5 o más
agentes, ultracode o cuota cerca del tope):

> ¿En qué plan corre esta cuenta: Pro, Max 5x, Max 20x, un asiento estándar o premium de Team o
> Enterprise, o clave de API? Si no lo sabes, `/status` muestra el método de inicio de sesión y
> `/usage`, cuánto llevas de la sesión y de la semana.

### Cuando la cuota es el cuello de botella

Lo que gasta la cuota:
- Los tokens que se procesan, pesados según el modelo. Anthropic: «Opus costs several times more per
  turn than Sonnet, and Sonnet more than Haiku».
- El historial, que se reenvía en cada turno.
- Cada subagente y cada agente de un workflow.
- En Max, Fable, hasta su tope del 50 % semanal.

`[NO VERIFICADO]`: la proporción exacta entre modelos y las cifras absolutas de los límites. Anthropic no
las publica.

Orden de recorte, de lo que menos calidad cuesta a lo que más:
1. `/clear` entre tareas que no tienen que ver y contexto corto. Es gratis.
2. Bajar un escalón de esfuerzo.
3. Planear con Opus y ejecutar con Sonnet («plan with Opus, execute with Sonnet»). Cambia el modelo de
   la sesión en el borde entre tareas, nunca a media tarea.
4. Mandar la lectura a Haiku 5.5.
5. Menos agentes en paralelo: nada de fan-out que se pueda evitar.
6. Nada de Fable, max ni ultracode hasta que se reinicie el límite.

- Si lo que aprieta es la ventana de 5 horas y la semana va holgada, reparte el trabajo o espera el
  reinicio; no bajes la calidad de lo estructural.
- Si aprieta la semana, baja los valores por defecto para el resto de la semana.
- Si el usuario fijó un tope propio de cuota semanal, trátalo como límite duro.
- Al agotar el límite, Pro y Max pueden seguir con créditos de uso a tarifa de API. *Fast mode* siempre
  se cobra con créditos, aunque quede límite.
- Un aviso de límite por familia («Opus limit») se esquiva cambiando de familia; el de sesión o el
  semanal, no.

## Procedimiento: preguntas en orden

1. **¿Hace falta delegar?** No, si el material ya está en tu contexto y la tarea es corta: hazla tú y,
   si acaso, ajusta el esfuerzo. Si la subtarea necesita tu contexto, un *fork* hereda modelo, historial
   y caché, y sale más barato que un agente nuevo.
2. **¿Qué tipo de tarea es?** Esto da la fila base:

   | Tipo | Fila base |
   |---|---|
   | Trivial: localizar, listar, renombrar | Haiku 5.5 · low |
   | Mecánica: extraer con esquema, cambios repetitivos con ejemplo, checklist | Haiku 5.5 · medium, o Sonnet 5.5 · low si hay matices |
   | Código acotado: sabes qué archivo, hay prueba, se revierte con git | Sonnet 5.5 · medium |
   | Código estructural: arquitectura, varios módulos, sin criterio de éxito, seguridad | Opus 5.5 · high, o max si el error es caro y difícil de ver |
   | Investigación con fuentes | Sonnet 5.5 · high como lectores; Opus 5.5 · high para integrar |
   | Síntesis y juicio crítico | Opus 5.5 · high/xhigh; Fable 5.1 si Opus en max no alcanza (ver ejemplo 6) |

3. **¿Cuánto cuesta un error y se puede verificar barato?**
   - Si el error es caro y difícil de detectar, sube un escalón de esfuerzo; después, de modelo.
   - Si hay una señal de falla barata (pruebas, validador), corre todo con poco esfuerzo y repite solo
     las fallas con más. Opus 5.5 en low y luego high solo en las fallas: ~97 % a 0.17 USD por tarea;
     todo en high: 95.3 % a 0.29 USD.
4. **¿Cuánto contexto necesita y ya está cargado?**
   - Con el material ya cargado, no cambies de modelo ni delegues sin necesidad.
   - Haiku 5.5 con más de 100 K tokens de prompt cobra 5 veces más. Sigue siendo el más barato, pero
     la ventaja sobre Sonnet baja a 4 veces.
   - Cada subagente arranca con prompt de sistema, CLAUDE.md y herramientas: ese piso se paga en cada uno.
5. **¿El usuario espera en vivo?** Baja el esfuerzo primero.
   - Haiku 5.5 en high tarda ~24 s al primer token; Sonnet 5.5 en medium, ~1 s.
   - Fable 5.1 no es la vía rápida frente a Opus 5.5: la evidencia está dividida.
   - Opus tiene *fast mode* (`/fast`): hasta 2.5 veces más rápido con la misma calidad, al doble de
     precio. En suscripción se paga solo con créditos de uso.
6. **¿La salida es larga?** La salida cuesta 5 veces la entrada en los cuatro modelos. Para redactar
   documentos largos, el modelo más barato cuya calidad alcance ahorra más que en tareas de lectura.
7. **¿Cuántos agentes en paralelo?**
   - El costo se multiplica por N; respeta el tope del plan.
   - En una misma tanda usa el mismo modelo, esfuerzo, tipo y herramientas: así comparten el prefijo de
     caché.
   - Si pasan de una decena de piezas, agrupa varias por agente.
   - Topes técnicos: 16 agentes concurrentes por workflow y 20 subagentes vivos por sesión.
8. **¿Es larga o depende de herramientas?** Haiku 5.5 en low tiende a saltarse búsquedas o chequeos en
   prompts de agente largos: para agentes usa medium o más. Tareas de más de 30 min → xhigh.
9. **¿Qué plan y cuánta cuota queda?** Aplica la tabla de planes. Si no sabes el plan y la decisión
   depende de él, pregunta.

**Antes de empezar, dilo en una línea:** `Tipo: estructural · recomiendo Opus 5.5 high · sesión: Opus 5.5 max · plan: Max 5x`.
Si la sesión es más débil que la tarea, detente y pide `/model opus`; si es más fuerte, sigue.

## Cuándo preguntarle al usuario qué prioriza

Pregunta **solo si** se cumplen las tres:
- el usuario no dijo ya qué prioriza en esta sesión («rápido», «barato», «lo mejor»);
- las opciones difieren 2 veces o más en costo o en tiempo: plan con 5 o más agentes, workflow o
  ultracode, Fable 5.1, esfuerzo max, o la cuota va cerca del tope;
- la decisión cambia el resultado, no solo el camino.

No preguntes en lo trivial ni cuando una regla ya decide (estructural → Opus alto). Si tampoco conoces
el plan, junta las dos preguntas en un solo mensaje.

**Una sola pregunta, la recomendada primero.** Cada opción dice la configuración y su costo y tiempo
relativos, estimados para el caso concreto (las cifras de esta plantilla son de ejemplo):

> ¿Qué priorizo para esto?
> 1. **Economía (recomendado)**: Sonnet 5.5 medium, 3 lectores y yo integro. ~1/3 del costo de la 3.
> 2. **Rapidez**: lo mismo con esfuerzo low; ~la mitad del tiempo, algo menos fino.
> 3. **Calidad máxima**: Opus 5.5 xhigh y verificación cruzada; ~3 veces más caro y más lento.

Si nadie puede contestar (corrida en segundo plano), sigue con la recomendada y dilo en el reporte.

## Matriz: modelo × esfuerzo

Costo y velocidad son relativos dentro de la tabla. Multiplicadores de esfuerzo medidos en Opus 5.5,
como costo por tarea frente a high: low ≈ 1/3, medium ≈ 0.7, xhigh ≈ 2.5. El kit Chema midió con Opus 5
que max cuesta ~1/3 más que el defecto. Aplicarlos a los otros modelos es `SUPUESTO`. La columna «Plan»
indica dónde la fila gasta cuota que conviene cuidar.

| Modelo · esfuerzo | Para qué sí | Para qué no | Costo | Velocidad | Plan |
|---|---|---|---|---|---|
| **Haiku 5.5 · low** | Localizar archivos o símbolos, listar, clasificar, resumir logs, lotes grandes con salida que se verifica | Agentes largos (se salta búsquedas y chequeos), cualquier juicio | mínimo | la más rápida | todos |
| **Haiku 5.5 · medium** (defecto) | Extraer datos de muchos archivos con esquema, cambios mecánicos con ejemplo, subagente lector, código simple | Diseño, revisión de seguridad, síntesis | muy bajo | muy rápida | todos; la mejor opción en Pro |
| **Haiku 5.5 · high** | Trabajo de conocimiento, tareas de agente más largas, instrucciones estrictas | Algo interactivo: Sonnet 5.5 medium responde antes y razona mejor | bajo | media (~24 s al primer token) | todos |
| **Haiku 5.5 · xhigh** | Solo si una prueba mostró ganancia; compáralo antes con Sonnet 5.5 | Por defecto; nada que espere el usuario | bajo | lenta | todos |
| **Haiku 5.5 · max** | Lotes nocturnos donde la latencia no importa: en el índice de Artificial Analysis rinde como Sonnet 5.5 medium por mucho menos | Nada interactivo (~5 min al primer token) | bajo | muy lenta | todos |
| **Sonnet 5.5 · low** | Chat y respuestas cortas, tareas sensibles a latencia | Código de varios archivos, agentes largos | bajo-medio | muy rápida | todos |
| **Sonnet 5.5 · medium** (defecto CC) | Código acotado bien especificado: features, endpoints, pruebas, refactor claro; ejecutor de una especificación | Causa raíz desconocida, diseño abierto | medio | rápida | todos; la sesión por defecto en Pro |
| **Sonnet 5.5 · high** (defecto API) | Bugs reproducibles difíciles, cambios en varios módulos con spec, revisión rutinaria, lector web con fuentes | Juicio sostenido y trabajo abierto: Opus 5.5 es «claramente más fuerte» | medio | media | todos |
| **Sonnet 5.5 · xhigh** | Tareas de terminal o código largas y bien especificadas (Terminal-Bench 70.6 % contra 66.4 % de Opus) | Por defecto; usar solo si una prueba muestra ganancia | medio-alto | lenta | Max o API |
| **Sonnet 5.5 · max** | Casi nunca | Cuesta casi lo que Opus 5.5 max y rinde menos | alto | muy lenta | — |
| **Opus 5.5 · low** | Consulta rápida con juicio; primer pase en tareas verificables (87.4 % en SWE-bench Pro, 0.12 USD por tarea resuelta) | Sin señal de falla en tareas difíciles; como ejecutor de un asesor (deja de pedir ayuda) | medio | rápida | todos |
| **Opus 5.5 · medium** (defecto) | La mayoría del trabajo con juicio: código general, borradores, evaluadores. Iguala a Fable 5.1 por defecto por ~1/5 del costo | Decisiones irreversibles sin verificación | medio-alto | media | todos; en Pro, solo para planear y lo estructural |
| **Opus 5.5 · high** | Estructural: arquitectura, refactor entre módulos, seguridad, auth, pagos, concurrencia, integridad de datos, council | Lo mecánico o lo que ya está especificado | alto | media-lenta | todos; en Pro, con medida |
| **Opus 5.5 · xhigh** | Agentes y código de más de 30 min, exploración con muchas llamadas | Por defecto: +1.4 puntos por 2.5 veces el costo de high | muy alto | lenta | Max o API |
| **Opus 5.5 · max** | Un problema donde el error es caro y difícil de ver; último escalón antes de Fable. Encabeza el índice de Artificial Analysis (58) | Tandas en paralelo; tareas con verificación barata | muy alto | muy lenta | Max o API; en Pro, una tarea y con permiso |
| **Fable 5.1 · low** | Investigación profunda multipaso: ahí solo paga en low (66 % contra 56 % de Sonnet 5) | Código: Opus 5.5 rinde igual por menos | alto | media | Max, premium o API; en Pro, con créditos |
| **Fable 5.1 · medium** | Trabajo rutinario si ya se decidió Fable | Lo que Opus 5.5 ya resuelve | muy alto | media-lenta | ídem |
| **Fable 5.1 · high** (defecto) | Síntesis final de veredictos (agente `sintetizador` del kit Chema), agentes de horas, análisis que termina en un documento completo | Paralelo; trabajo que Opus 5.5 en xhigh resuelve | máximo | lenta | ídem |
| **Fable 5.1 · xhigh** | Lo más sensible a capacidad, cuando Opus 5.5 en max ya se quedó corto | Por defecto | máximo | muy lenta | Max 20x o API |
| **Fable 5.1 · max** | Problemas frontera, en un solo hilo, cuando el costo no importa | Siempre en paralelo; siempre por defecto | máximo | la más lenta | Max 20x o API |
| **Ultracode** (no es esfuerzo) | Auditorías de muchos archivos, migraciones grandes, investigación con verificación cruzada, cuando el usuario ya pidió exhaustividad | Tareas en cadena, material que cabe en un contexto, preguntas puntuales, cuota cerca del tope | multiplica: cada tarea se vuelve uno o varios workflows | más lenta en reloj, aunque corre en paralelo | Max 20x o API; en Max 5x, por tarea; en Pro, no |

**Ultracode, en concreto.** Es un modo de orquestación de Claude Code, no un nivel de esfuerzo.
- `/effort ultracode` hace que Claude planee un workflow para cada tarea sustantiva de la sesión, en el
  esfuerzo que tenga la sesión.
- `claude --effort ultracode` hace lo mismo y además arranca la sesión en xhigh.
- Escribir la palabra `ultracode` en un solo prompt corre solo esa tarea como workflow, sin cambiar la
  sesión. Es la opción más barata.
- Con el modo activo desaparecen el aviso de «Large workflow» y el tope de subagentes concurrentes, y la
  cuota se acaba antes.
- Requiere los workflows encendidos (en Pro vienen apagados) y se apaga con `/effort ultracode off`.

## Cómo lanzar agentes

### Agentes que acompañan esta skill

Se instalan como archivos en `~/.claude/agents/` (de usuario) o `.claude/agents/` (de proyecto), o
llegan con un plugin. En ese caso aparecen con prefijo, por ejemplo `nombre-del-plugin:lector-haiku`.

| Agente | Modelo · esfuerzo | Para |
|---|---|---|
| `lector-haiku` | Haiku 5.5 · low | Localizar, listar, leer y resumir; solo lectura |
| `extractor-haiku` | Haiku 5.5 · medium | Extraer datos a un formato fijo de muchos archivos; solo lectura |
| `ejecutor-sonnet` | Sonnet 5.5 · medium | Código acotado con instrucciones cerradas |
| `investigador-sonnet` | Sonnet 5.5 · high | Un ángulo de investigación web con fuentes; sin escritura |
| `constructor-opus` | Opus 5.5 · high | Código estructural a partir de una especificación cerrada |
| `revisor-opus` | Opus 5.5 · high | Revisión de seguridad, corrección o diseño desde un lente; no edita |
| `analista-opus-max` | Opus 5.5 · max | Un solo problema difícil y caro de errar; nunca en paralelo |
| `experto-fable` | Fable 5.1 · high | Solo cuando Opus 5.5 en max se quedó corto |

Si no están instalados, lanza un agente general con `model` por llamada y fija el esfuerzo con el
parámetro `effort`, si tu versión lo ofrece.

Si usas el kit Chema, también trae `verificador` (Sonnet), `evaluador-council` y `lector-fresco` (Opus)
y `sintetizador` (Fable). Ninguno declara `effort`, así que heredan el de la sesión: con la sesión en
max, corren en max. Para evitarlo, pasa `effort` por llamada.

### Con la herramienta Agent

- **Modelo**: el parámetro `model` de la llamada manda. Después vienen el `model:` de la definición,
  `CLAUDE_CODE_SUBAGENT_MODEL` y, al final, el modelo de la sesión. Excepción: si la sesión ya es Opus
  y pides `opus`, el subagente corre exactamente el modelo de la sesión (con `[1m]` incluido).
- **Esfuerzo**: la variable `CLAUDE_CODE_EFFORT_LEVEL` gana sobre todo. Debajo van el parámetro
  `effort` de la llamada (Claude Code 2.1.292 o posterior), el `effort:` del frontmatter y, al final,
  el esfuerzo de la sesión. **Si tu herramienta Agent no muestra el parámetro `effort`, el esfuerzo
  solo se fija eligiendo un agente definido.**
- **Definiciones nuevas**: Claude Code vigila `~/.claude/agents/` (o `agents/` dentro de
  `CLAUDE_CONFIG_DIR`, si lo usas) y `.claude/agents/`. Un archivo nuevo o editado se toma en segundos,
  **salvo que la carpeta `agents` se haya creado después de abrir la sesión**: ahí hay que reiniciar. Es
  la causa típica del error «Agent type '…' not found».
- **Fork**: hereda el modelo, el historial y la caché del padre; el `model` que le pases se ignora.

### Dentro de un Workflow

- `agent(prompt, { model, effort, agentType, schema, isolation })` acepta modelo y esfuerzo **por
  llamada**. Si omites `model`, el agente hereda el de la sesión: para etapas mecánicas pon `haiku` o
  `sonnet` y `effort: 'low'` de forma explícita.
- `agentType` usa un agente definido (por ejemplo `revisor-opus`); `model` y `effort` de la llamada lo
  sobrescriben.
- Declara en el plan el modelo y el esfuerzo de cada etapa.
- Un solo escritor: el fan-out es solo para leer, medir o verificar.

### Errores típicos

- Mandar a Fable lo que Opus 5.5 en high resolvía: cuesta 2.5 veces más por token, en código no gana y,
  en Pro, se cobra aparte.
- Fan-out sobre una cadena dependiente: un solo modelo con menos esfuerzo sale más barato (Anthropic).
- Asesor con un ejecutor en low: el ejecutor deja de pedir ayuda y pagas sin ganar nada.
- Lanzar 20 agentes sin `model` en un workflow: los 20 corren con el modelo y el esfuerzo de la sesión.
- Cambiar `/model` a media tarea larga: se pierde la caché.
- Dar por hecho el plan de la cuenta.

## Ejemplos

1. **Extraer datos de 20 archivos.**
   - Si ya los leíste, hazlo tú.
   - Si no, usa `extractor-haiku` (Haiku 5.5 medium) con el formato exacto: de 2 a 4 agentes con 5 a 10
     archivos cada uno, o un `pipeline()` con `{model: 'haiku', effort: 'medium', schema}`.
   - Después, un verificador revisa una muestra contra los archivos.
   - Si cada agente pasa de 100 K tokens de prompt, Haiku cuesta 5 veces más y aún conviene.
   - Igual en todos los planes; en Pro, sin pasar de 3 agentes.
2. **Arreglar un bug localizado.**
   - Es una tarea acotada: `ejecutor-sonnet` (Sonnet 5.5 medium), o tú mismo si el archivo ya está en
     contexto.
   - Si falla dos veces o toca otro módulo, reclasifícala como estructural y pásala a Opus 5.5 high.
3. **Diseñar una arquitectura.**
   - El diseño no se delega: lo hace la sesión principal con Opus 5.5 (high; max en Max 20x o API).
   - Para revisar, de 2 a 3 `revisor-opus` con lentes distintos (riesgo, costo, operación). En Pro, uno.
   - Para construir, `constructor-opus` con la especificación cerrada.
4. **Revisar seguridad.**
   - Siempre es estructural; Haiku no sirve aquí.
   - De 2 a 4 `revisor-opus` (high) en solo lectura, uno por lente: autenticación, inyección, secretos,
     permisos. Luego, verificación adversarial de cada hallazgo.
   - Si el cambio es irreversible o sale a producción, la verificación final va en `analista-opus-max`.
   - En Pro: un solo revisor con los lentes en lista y sin max, salvo permiso.
5. **Investigar en la web.**
   - De 2 a 4 `investigador-sonnet` (high), ciegos entre sí y uno por ángulo; tú integras con Opus 5.5.
   - Para leer mucho sin juzgar basta Haiku 5.5 medium.
   - Si se pide investigación profunda y la calidad manda, Fable 5.1 en low: en Max, premium o API; en
     Pro, solo con créditos y permiso.
   - Hay un workflow incluido, `/deep-research`.
   - Los agentes que leen la web no tocan material confidencial.
6. **Sintetizar veredictos.**
   - El kit Chema manda al `sintetizador` (Fable 5.1). El kit eligió Fable por latencia frente a Opus 5,
     no frente a 5.5.
   - Anthropic hoy marca a Fable 5.1 como «más lento» que Opus 5.5 y dice que Opus 5.5 rinde como Fable
     en la mayoría del trabajo.
   - Si se prioriza economía o cuota, o el plan es Pro, sintetiza en la sesión principal con Opus 5.5
     high/xhigh.
   - Si se prioriza calidad máxima y el plan incluye Fable, usa el `sintetizador` o `experto-fable`.
   - Si no se sabe, pregunta.
