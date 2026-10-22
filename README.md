# kit-pedroza

Skills propias. Cada una tiene una sola fuente: este repo.

| Skill | Para qué |
|---|---|
| `kit-mercadotecnia` | Mercadotecnia e investigación de mercado con marco y fuente (Kotler y Armstrong, 18.ª ed.) |
| `kit-cv` | Currículum y perfil profesional, compatible con sistemas de reclutamiento (ATS) |
| `handoff` | Traspaso entre sesiones de Claude Code |
| `auditoria-presentaciones` | Auditoría de presentaciones antes de entregarlas |
| `auditoria-git` | Auditoría del estado de un repositorio git |
| `revisar-push` | Revisión de un cambio antes de subirlo, con el resultado en el PR |
| `elegir-modelo` | Qué modelo (Haiku 5.5, Sonnet 5.5, Opus 5.5, Fable 5.1) y qué esfuerzo usar en cada tarea, según el plan de la cuenta (Pro, Max 5x, Max 20x, Team, Enterprise o API) |
| `kit-rp` | Relaciones con prospectos: a quién ofrecerle qué, primer mensaje, CRM y llamada, sin mezclar ámbitos |
| `kit-puntos-ciegos` | Encontrar lo que no estás viendo en un plan o una decisión, sin ceder a la insistencia |

## Agentes

Ocho agentes con modelo y esfuerzo fijos, para repartir trabajo sin gastar el modelo de la sesión
en lo que un modelo menor hace igual. La skill `elegir-modelo` dice cuándo usar cada uno.

| Agente | Modelo · esfuerzo | Para qué |
|---|---|---|
| `lector-haiku` | Haiku 5.5 · low | Localizar y leer sin juzgar (solo lectura) |
| `extractor-haiku` | Haiku 5.5 · medium | Extraer datos de muchos archivos a un formato fijo (solo lectura) |
| `ejecutor-sonnet` | Sonnet 5.5 · medium | Tareas acotadas con instrucciones cerradas |
| `investigador-sonnet` | Sonnet 5.5 · high | Investigar en la web un ángulo concreto, con fuentes (sin escritura) |
| `constructor-opus` | Opus 5.5 · high | Código nuevo con pruebas a partir de una especificación cerrada |
| `revisor-opus` | Opus 5.5 · high | Revisión con un lente asignado (no edita) |
| `analista-opus-max` | Opus 5.5 · max | Un problema difícil donde un error sería caro |
| `experto-fable` | Fable 5.1 · high | Solo cuando Opus 5.5 en xhigh o max ya se quedó corto |

Un agente nuevo se carga al abrir la sesión: después de actualizar el plugin, reinicia Claude Code.

`hooks/play-done-sound.ps1` es opcional y no se activa solo. Es un aviso sonoro al
terminar cada turno, solo para Windows.

## Gate de push (opcional, por repo)

El plugin registra el hook `hooks/gate-push.sh`, pero no hace nada hasta que un repo lo prende:

```
git config kit-pedroza.gate true
```

En ese repo, un `git push` desde Claude Code solo pasa si el commit ya pasó por la skill
`revisar-push`. En los demás repos el hook sale sin tocar nada. Pruebas:
`bash hooks/test-gate-push.sh` y `bash skills/revisar-push/scripts/revisar-push.sh autotest`.

## Instalar (igual en todas las máquinas y en todos los perfiles)

Dentro de Claude Code:

```
/plugin marketplace add FSPR2005/kit-pedroza
/plugin install kit-pedroza@kit-pedroza
```

Para actualizar: `/plugin marketplace update`.

## Regla

Las skills no se copian a mano a `~/.claude/skills/`. Todo cambio entra por este repo,
y cada máquina se actualiza desde el marketplace.

## Límites conocidos

- Los hooks de `handoff` son de PowerShell (Windows). En macOS la skill funciona, pero
  sin sus avisos automáticos.
- El gate de push necesita `bash`, `python3` y `git`. Si falta `python3`, el hook deja pasar el push y lo anota en el ledger.
- Ninguna skill guarda datos de clientes ni de empresas. Si aparece uno, es un error:
  se abstrae o se borra antes del commit.

## Créditos

El gate de push está adaptado de `claude-kit-chema` (MIT). `kit-rp` y `kit-puntos-ciegos` toman ideas, no texto,
de otros repos públicos. Detalle y avisos de licencia en `CREDITOS.md`.
