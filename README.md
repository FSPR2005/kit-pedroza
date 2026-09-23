# kit-pedroza

Skills propias que **complementan** al [Kit Chema](https://github.com/chemaw8/claude-kit-chema).
No lo reemplazan: las 9 skills base se siguen instalando desde el marketplace de Chema, y
este repo trae solo lo que no está allá. Así cada skill tiene una sola fuente.

| Skill | Para qué |
|---|---|
| `kit-mercadotecnia` | Mercadotecnia e investigación de mercado con marco y fuente (Kotler y Armstrong, 18.ª ed.) |
| `kit-cv` | Currículum y perfil profesional, compatible con sistemas de reclutamiento (ATS) |
| `handoff` | Traspaso entre sesiones de Claude Code |
| `auditoria-presentaciones` | Auditoría de presentaciones antes de entregarlas |
| `auditoria-git` | Auditoría del estado de un repositorio git |

`hooks/play-done-sound.ps1` es opcional y no se activa solo. Es un aviso sonoro al
terminar cada turno, solo para Windows.

## Instalar (igual en todas las máquinas y en todos los perfiles)

Dentro de Claude Code:

```
/plugin marketplace add chemaw8/claude-kit-chema
/plugin install kit-chema@kit-chema
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
- Ninguna skill guarda datos de clientes ni de empresas. Si aparece uno, es un error:
  se abstrae o se borra antes del commit.
