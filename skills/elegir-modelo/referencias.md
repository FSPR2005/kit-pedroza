# Referencias de `elegir-modelo`

Todas consultadas el **2026-10-13**, solo lectura, sin sesión iniciada. Orden: Anthropic, tablas
independientes, GitHub, kit Chema. Las cifras de páginas web se tomaron de un extracto automático de la
página; las que sostienen reglas se volvieron a pedir en cita textual (marcadas «textual»).

## 1. Anthropic: modelos y precios

| Fuente | URL | Qué aporta |
|---|---|---|
| Models overview | https://platform.claude.com/docs/en/about-claude/models/overview.md | Lineup vigente: Fable 5.1, Opus 5.5, Sonnet 5.5, Haiku 5.5. IDs (`claude-fable-5-1`, `claude-opus-5-5`, `claude-sonnet-5-5`, `claude-haiku-5-5`), precio base, latencia comparativa (más lenta / moderada / rápida / la más rápida), esfuerzo por defecto en la API (high / medium / high / medium), 1 M de contexto y 128 K de salida en los cuatro. «Start with Claude Opus 5.5 for most workloads». Legado: Fable 5, Opus 5, Opus 4.8–4.5, Sonnet 5, Sonnet 4.6, Haiku 4.5 |
| Pricing | https://platform.claude.com/docs/en/about-claude/pricing.md | Tabla completa: Opus 5.5 4/20, Sonnet 5.5 2/10, Fable 5.1 10/50, Haiku 5.5 0.10/0.50 hasta 100 K de prompt y 0.50/2.50 arriba, Haiku 4.5 1/5. Lectura de caché: 0.025× Fable 5.1, 0.05× Opus 5.5 y Sonnet 5.5, 0.1× el resto. Batch −50 %. Fast mode de Opus 5.5: 8/40. Haiku 5.5 es el único con precio por largo de prompt |
| Claude Haiku 5.5 | https://platform.claude.com/docs/en/models/haiku-5-5/overview | Lanzado el 2026-10-07. Para clasificar, enrutar, extraer y subagentes. Tokenizador nuevo, ~30 % más tokens que Haiku 4.5. Esfuerzo por defecto medium |
| Claude Sonnet 5.5 | https://platform.claude.com/docs/en/models/sonnet-5-5/overview | Lanzado el 2026-09-28. «Best combination of speed and intelligence». `between_tools` como mínimo de razonamiento. Esfuerzo por defecto high en la API |
| Choosing a model | https://platform.claude.com/docs/en/about-claude/models/choosing-a-model | «Tuning effort is often a better lever than switching models». Fable 5.1 solo si las pruebas con Opus 5.5 en xhigh/max se quedan cortas. Matriz de uso por modelo; Haiku 5.5 para subagentes |
| Effort | https://platform.claude.com/docs/en/build-with-claude/effort.md | Los cinco niveles con su uso típico: low para subagentes y tareas simples; medium equilibrio; high razonamiento complejo; xhigh tareas de más de 30 min; max frontera. Recomendaciones por modelo: Haiku 5.5 en low se salta búsquedas y chequeos en prompts largos; Sonnet 5.5 en medium para código bien especificado. Cambiar el esfuerzo de nivel superior invalida la caché |
| Optimizing for cost and intelligence | https://platform.claude.com/docs/en/about-claude/models/optimizing-for-cost-and-intelligence | Mediciones (textual): Opus 5.5 en SWE-bench Pro frente a high: medium −2.5 puntos a ~70 % del costo, low −8 a ~1/3, xhigh +1.4 a 2.5×. Opus 5.5 medium iguala a Fable 5.1 por defecto (92.8 % contra 92.3 %) a 0.22 contra 1.19 USD por tarea resuelta. Re-correr fallas: low y luego high, ~97 % a 0.17 USD, contra 95.3 % a 0.29 en todo high. Fable 5.1 low 88.6 % a 0.54 USD contra Sonnet 5 77.4 % a 0.84. Haiku 5.5 en GPQA: 85 % a ~1/20 del costo de Opus 5.5 (91 %). Orquestador Fable 5.1 + 25 Sonnet 5: 47–55 % menos costo, 10–12 puntos menos. Un asesor no sirve con un ejecutor que no consulta |
| Anuncio Claude Opus 5.5 | https://www.anthropic.com/news/claude-opus-5-5 | 2026-09-22. «Performs at the level of Claude Fable 5.1 on most work». Tabla: Terminal-Bench 4.0 66.4 % (Fable 5.1 55.8 %), GDPval-AA 1846 (1735), OSWorld 2.1 81.8 % (80.7 %). Un caso interno: Opus 5.5 terminó en 9.5 h contra 12 de Fable 5.1, 51 % más barato |
| Anuncio Claude Sonnet 5.5 | https://www.anthropic.com/claude-sonnet-5-5 | 2026-09-28. Complemento más rápido y barato de Opus 5.5; «Opus 5.5 remains clearly stronger at complex, open-ended work». Terminal-Bench 4.0 70.6 %, CursorBench 55.5 % (Opus 57.8 %). Más de 30 % más rápido que Sonnet 5 |
| Anuncio Claude Haiku 5.5 | https://www.anthropic.com/claude-haiku-5-5 | 2026-10-07. «Pairs well with Opus 5.5 and Sonnet 5.5 as a subagent on coding work». Terminal-Bench 4.0 39.2 %, OSWorld 2.1 72.4 % (crédito parcial) |
| Fable 5.1 (búsqueda) | https://www.anthropic.com/claude-fable-and-mythos-5-1 | 2026-09-01. Lectura de caché 75 % más barata que Fable 5. `[NO VERIFICADO]`: la URL `/news/claude-fable-5-1` dio 404 y el anuncio solo se vio en el resultado del buscador |

## 2. Anthropic: Claude Code

| Fuente | URL | Qué aporta |
|---|---|---|
| Model configuration | https://code.claude.com/docs/en/model-config.md | Alias en la API de Anthropic: `haiku` = Haiku 5.5, `sonnet` = Sonnet 5.5, `opus` = Opus 5.5, `fable` = Fable 5.1, `best` = Fable 5.1. En Bedrock y Google Cloud: Haiku 4.5 y Sonnet 4.6. Esfuerzo por defecto en Claude Code: medium en Opus, Sonnet y Haiku 5.5; high en Fable. `/effort`, `--effort`, `CLAUDE_CODE_EFFORT_LEVEL`, `modelSettings`. Ultracode: ajuste de orquestación, no de esfuerzo; `--effort ultracode` arranca en xhigh. Cambiar de modelo invalida la caché |
| Subagents | https://code.claude.com/docs/en/sub-agents.md | Frontmatter: `name` y `description` obligatorios; `tools`, `disallowedTools`, `model` (`haiku`, `sonnet`, `opus`, `fable`, ID o `inherit`), `effort` (low…max), `color`, `maxTurns`, etc. Precedencia del modelo: parámetro de la llamada, frontmatter, `CLAUDE_CODE_SUBAGENT_MODEL`, sesión. Precedencia del esfuerzo: `CLAUDE_CODE_EFFORT_LEVEL`, parámetro `effort` de la llamada (requiere 2.1.292+), frontmatter, sesión. Vigilancia de archivos (textual): «The watcher covers only directories that existed when the session started, so after creating a scope's first agent file in a new agents directory, restart to load it» |
| Dynamic workflows | https://code.claude.com/docs/en/workflows.md | `agent()`, `pipeline()`, `parallel()`; ultracode como palabra en el prompt (una tarea) o como modo de sesión (`/effort ultracode`), que gasta más tokens y llega antes a los límites. Hasta 16 agentes concurrentes y 1,000 por corrida; aviso de «Large workflow» arriba de 25 agentes o 1.5 M tokens; tamaño guía `small` < 5, `medium` < 10. Agentes con mismo modelo, esfuerzo, tipo y herramientas comparten la caché. Un `model` en el script cuenta como modelo por llamada |
| Skill `workflow-authoring` (incluida en Claude Code) | se carga con `/workflow-authoring` | Firma: `agent(prompt, {label, phase, schema, model, effort, isolation, agentType})`; `effort` por llamada `'low'…'max'`; si se omite `model`, hereda el de la sesión |
| Manage costs | https://code.claude.com/docs/en/costs.md | Los límites de sesión y semanal de la suscripción se comparten entre modelos; los de familia («Opus limit») se esquivan cambiando de familia. Los subagentes y workflows cuentan en el uso. Para subagentes simples, `model: haiku`. Equipos de agentes: ~7× tokens en plan mode. La caché dura 1 h en suscripción |
| Environment variables | https://code.claude.com/docs/en/env-vars.md | `CLAUDE_CODE_EFFORT_LEVEL` gana sobre `--effort`, `/effort` y la configuración. `CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS` (defecto 20). `CLAUDE_CONFIG_DIR` reubica la configuración |
| Blog: modelo y esfuerzo en Claude Code | https://claude.com/blog/claude-model-and-effort-level-in-claude-code | 2026-07-07. Si Claude falló teniendo todo el contexto, sube de modelo; si falló por saltarse un archivo o no correr las pruebas, sube el esfuerzo |
| Skill `claude-api` (incluida en Claude Code 2.1.280) | se carga con `/claude-api` | Guía de costos (`shared/cost-optimization.md`): esfuerzo antes que modelo, precio por tarea y no por token, cuándo paga un orquestador. Su tabla de modelos tiene fecha 2026-06-24 y ya no incluye Sonnet 5.5 ni Haiku 5.5: no usarla para nombres |

## 2b. Anthropic: planes de suscripción

| Fuente | URL | Qué aporta |
|---|---|---|
| Precios de Claude | https://claude.com/pricing | Pro: «$17 Per month with annual subscription discount ($200 billed up front). $20 if billed monthly», con Claude Code. Max: «Choose 5x or 20x more usage than Pro». Team: asiento estándar 25 USD al mes (20 en pago anual), premium 125 (100 en pago anual). No hay ningún plan llamado «Ultra» |
| ¿Qué es el plan Max? | https://support.claude.com/en/articles/11049741-what-is-the-max-plan | Max 5x 100 USD y Max 20x 200 USD al mes; 5 y 20 veces «the Pro plan's per-session usage allowance». Límite de sesión que se reinicia cada 5 horas y «a weekly usage limit that applies across all models» |
| ¿Qué es el plan Pro? | https://support.claude.com/en/articles/8325606-what-is-the-pro-plan | 20 USD al mes; incluye Claude Code; límite cada 5 horas y semanal entre todos los modelos; las horas de reinicio se ven en Settings > Usage |
| Claude Fable en tu plan | https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan | Actualizado el 2026-09-02. Max y asientos premium de Team y Enterprise: Fable incluido, «up to 50% of your weekly usage limits on Fable models at no extra cost». Pro y asientos estándar: «aren't included in your plan's usage limits. You can use them with usage credits». Free: sin Fable |
| Claude Code con Pro o Max | https://support.claude.com/en/articles/11145838-using-claude-code-with-your-pro-or-max-plan | Límites compartidos entre Claude y Claude Code; Max tiene además «a separate weekly limit for Fable». Al agotarlos: créditos de uso, subir de plan o esperar |
| Modelos, uso y límites en Claude Code | https://support.claude.com/en/articles/14552983-models-usage-and-limits-in-claude-code | «Opus costs several times more per turn than Sonnet, and Sonnet more than Haiku. Spending Opus on routine work is the fastest way to drain a daily limit.» Recomienda «plan with Opus, execute with Sonnet» |
| Créditos de uso | https://support.claude.com/en/articles/12429409-manage-usage-credits-for-paid-claude-plans | Pro, Max 5x y Max 20x pueden seguir después del límite con créditos; «billed at standard API rates» |
| Model configuration (por plan) | https://code.claude.com/docs/en/model-config.md | El alias `default` es Opus 5.5 en Pro, Max, Team, Enterprise y API, así que Opus está en Pro. Fable puede aparecer en `/model` como «Requires usage credits» según el plan y el asiento. No hay topes de esfuerzo por plan; solo `maxEffortLevel` y límites de organización en Enterprise |
| Fast mode | https://code.claude.com/docs/en/fast-mode.md | Solo Opus (5.5: 8/40 USD). En suscripción se paga solo con créditos de uso y «not included in the subscription rate limits», aunque quede límite. `/status` muestra el método de inicio de sesión (por ejemplo «Claude Max account») |
| Dynamic workflows (por plan) | https://code.claude.com/docs/en/workflows.md | «On Pro, turn them on from the Dynamic workflows row in /config». Tamaño guía por defecto `small` en Pro y `medium` en los demás planes. Una corrida en pausa por límite de uso espera el reinicio si es de menos de 24 h |
| Manage costs (Team y Enterprise) | https://code.claude.com/docs/en/costs.md | Asiento con límite que se reinicia cada 5 h y cada semana, compartido con el chat y Cowork; su tamaño depende del tipo de asiento (estándar o premium) |

## 3. Tablas independientes

| Fuente | URL | Qué aporta |
|---|---|---|
| Artificial Analysis (Anthropic) | https://artificialanalysis.ai/providers/anthropic | Índice de inteligencia y velocidad: Opus 5.5 max 58, Sonnet 5.5 max 56, Fable 5.1 max 53, Haiku 5.5 max 43, Sonnet 5.5 high 47, Haiku 5.5 low 29. Velocidad de salida: Haiku 5.5 170–237 t/s, Sonnet 5.5 97–137, Opus 5.5 95, Fable 5.1 71. Costo por tarea del índice: Opus max 5.98, Sonnet max 5.46, Fable max 7.63, Haiku max 0.21 USD |
| Artificial Analysis, Opus 5.5 | https://artificialanalysis.ai/models/claude-opus-5-5 | Variante max: índice 58 (#1 de 216), 94.8 t/s, 650 s al primer token |
| Artificial Analysis, Fable 5.1 | https://artificialanalysis.ai/models/claude-fable-5-1 | Variante max: índice 53 (#5), 71 t/s, 250 s al primer token. Marcado como caro y más lento que el promedio |
| Artificial Analysis, Haiku 5.5 high contra Sonnet 5.5 medium | https://artificialanalysis.ai/models/comparisons/claude-haiku-5-5-high-vs-claude-sonnet-5-5-medium | Haiku high: índice 38, 175 t/s, 24 s al primer token. Sonnet medium: 41, 95 t/s, 1.1 s. De aquí sale que la latencia depende más del esfuerzo que del modelo |
| LLM Stats (el sitio que se dictó «llm-status») | https://llm-stats.com/models/compare/claude-opus-5-5-vs-claude-sonnet-5-5 | Puntaje agregado: Opus 5.5 60.7, Sonnet 5.5 58.7; por categoría, Opus gana en razonamiento, código y agentes y Sonnet en uso de herramientas (35.4 contra 33.9). Fechas de lanzamiento 2026-09-22 y 2026-09-28 |
| LLM Stats, lanzamiento de Haiku 5.5 | https://llm-stats.com/blog/research/claude-haiku-5-5-launch | Advierte el «precipicio» de precio arriba de 100 K tokens y que el tokenizador nuevo puede empujar cargas por encima del umbral. Puntajes reportados por el fabricante, sin verificar por LLM Stats |
| Vals AI, SWE-bench Verified | https://www.vals.ai/benchmarks/swebench | Actualizado el 2026-09-01; aún sin los modelos 5.5. Generación anterior: Opus 5 97 % (1.29 USD, 9 min 37 s), Fable 5 95 % (2.05 USD, 5 min 56 s), Sonnet 5 79.6 %, Haiku 4.5 66.6 % |

`[NO VERIFICADO]`:
- **LMArena** (`lmarena.ai` redirige a `arena.ai/leaderboard`) devolvió 403. Las cifras de Elo que aparecieron en buscadores (Opus 5.5 1507, Sonnet 5.5 1476) vienen de agregadores de terceros y no se usaron.
- **OpenRouter** (https://openrouter.ai/rankings): el extracto mezcló el ranking de uso con índices de inteligencia, así que no se tomó ninguna cifra de uso.
- **SWE-bench oficial** (https://www.swebench.com/): la tabla se carga con JavaScript y no se pudo leer.
- **Aider** (https://aider.chat/docs/leaderboards/): actualizado por última vez el 2025-11-20, sin modelos Claude 5.x. No sirve para esta decisión.

## 4. GitHub: routers de modelo para Claude Code

| Repositorio | URL | Criterio |
|---|---|---|
| joaofatoretto/model_router | https://github.com/joaofatoretto/model_router | Sesión Opus 5.5 que coordina. Haiku 5.5 low para localizar o extraer listas y medium para ediciones mecánicas con ejemplo; Sonnet 5.5 medium para trabajo bien especificado y high para bugs reproducibles o varios módulos; Opus 5.5 medium para lo abierto y high para lo difícil de revertir (auth, pagos, concurrencia, datos). Si un trabajador falla dos veces: más esfuerzo o un escalón de modelo. 0 estrellas |
| jmjmalik22/claude-model-routing | https://github.com/jmjmalik22/claude-model-routing | Haiku explora y lee, Sonnet implementa tareas pequeñas, Opus planea y revisa; límite de turnos por rol. 0 estrellas |
| tzachbon/claude-model-router-hook | https://github.com/tzachbon/claude-model-router-hook | Hooks que cambian de nivel por heurística: Haiku solo para lo claramente mecánico, el código agéntico va por defecto a Opus con esfuerzo graduado. 102 estrellas |
| shaaz1000/claude-router, IuriiTurok/auto-model-router, nixfred/claude-router, aott33/model-router | https://github.com/shaaz1000/claude-router · https://github.com/IuriiTurok/auto-model-router · https://github.com/nixfred/claude-router · https://github.com/aott33/model-router | Clasifican cada prompt (trivial, estándar, complejo, profundo) y lo envían a Haiku, Sonnet u Opus. Vistos solo en el resultado del buscador |

Ninguno publica mediciones de ahorro. Coinciden con esta skill en el reparto por tipo de tarea y en
escalar por esfuerzo antes que por modelo.

## 5. Kit Chema v1.33.0 (repo público github.com/chemaw8/claude-kit-chema)

| Archivo | Qué aporta |
|---|---|
| `nucleo/CLAUDE.md`, líneas 84–111 | Cuándo delegar; escalera Haiku, Sonnet, Opus 5.5 y Fable 5.1; «antes de subir de Opus 5.5 a Fable, sube el esfuerzo»; Fable si manda la latencia (medido contra Opus 5) |
| `skills/kit-orquestacion/SKILL.md` | Un solo escritor; un fan-out cuesta ~4× el hilo solo; misma tanda, mismo modelo y esfuerzo; declarar modelo y esfuerzo por etapa; Fable cuesta 2.5 veces Opus 5.5 por token |
| `docs/pruebas/medicion-esfuerzo-v1.19.2.md` | Opus 5 en max contra el defecto: +32 % de costo y +46 % de tiempo (n = 4); Fable 5.1 +59 % de costo y −18 % de tiempo (n = 2). Batería saturada: no distingue calidad |
| `agents/*.md` | `verificador` (sonnet), `evaluador-council` (opus), `lector-fresco` (opus), `sintetizador` (fable). Ninguno declara `effort` |
| `CHANGELOG.md` v1.22.2 y v1.19.2 | Paso de Opus 5 a Opus 5.5 en el texto; la medición de latencia de Fable se hizo contra Opus 5 y no se re-midió contra 5.5 |
| `docs/bitacora.md` (2026-09-29) | «Claude Code 2.1.284: `sonnet` es Sonnet 5.5» |

## Otros `[NO VERIFICADO]`

**Planes:**
- **Cifras absolutas de los límites de 5 horas y semanales.** Anthropic no las publica en ningún plan; solo
  da proporciones (Max 5x y 20x frente a Pro, por sesión). Las cifras de terceros («50–225 prompts por
  ventana» en Max 5x, etc.) no se usaron.
- **Si el límite semanal de Max también es 5 y 20 veces el de Pro.** Lo publicado habla del uso por sesión.
- **Tamaño del límite de los asientos de Team y Enterprise frente a Pro y Max.** No está publicado.
- **Proporción exacta de cuota que gasta cada modelo.** Solo hay «several times more per turn» (Opus contra
  Sonnet) y «Sonnet more than Haiku».
- **Qué planes tienen límites por familia de modelo («You've hit your Opus limit»).** La documentación de
  costos los menciona, pero no dice en qué planes aplican.
- **Si `/status` distingue Max 5x de Max 20x.** El ejemplo publicado solo dice «Claude Max account».

**Claude Code:**
- **Si tu herramienta Agent expone `effort` por llamada.** Requiere Claude Code 2.1.292 o posterior. Una
  sesión abierta con una versión anterior no lo muestra, aunque el binario ya esté actualizado: reinicia y
  revisa.
- **Con qué esfuerzo corren los agentes sin `effort` cuando la sesión está en max.** La documentación dice
  que usan el esfuerzo de la sesión. No se probó si eso vale cuando el modelo del agente es otro.
- **Carpeta de agentes con `CLAUDE_CONFIG_DIR`.** La documentación no nombra `agents/`. En uso real, los
  agentes creados en `agents/` dentro de `CLAUDE_CONFIG_DIR` sí aparecieron como tipos disponibles.

**Modelos:**
- **Fable 5.1 contra Opus 5.5 en latencia.** Anthropic marca a Fable como más lento, y su caso interno lo
  confirma (12 h contra 9.5 h). Pero en Artificial Analysis, en max, Fable da el primer token antes (250 s
  contra 650 s), aunque genera más despacio (71 contra 95 t/s). No hay medición de síntesis.
