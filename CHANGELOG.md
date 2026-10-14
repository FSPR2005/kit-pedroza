# Cambios

Formato: [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/). Versiones: [SemVer](https://semver.org/lang/es/).
Cada versión tiene su etiqueta `vX.Y.Z` en el repo. Para que un perfil instalado tome los cambios:
`/plugin marketplace update` y reiniciar Claude Code.

## [0.3.0] · 2026-10-13

### Agregado
- Skill `elegir-modelo`: qué modelo (Haiku 5.5, Sonnet 5.5, Opus 5.5, Fable 5.1) y qué esfuerzo (low, medium,
  high, xhigh, max) usar en cada tarea, con tabla por plan de la cuenta (Pro, Max 5x, Max 20x, Team, Enterprise,
  API), fila de ultracode, procedimiento de decisión y ejemplos. Fuentes en `skills/elegir-modelo/referencias.md`.
- Carpeta `agents/` con 8 agentes de modelo y esfuerzo fijos: `lector-haiku`, `extractor-haiku`,
  `ejecutor-sonnet`, `investigador-sonnet`, `constructor-opus`, `revisor-opus`, `analista-opus-max` y
  `experto-fable`.
- Este `CHANGELOG.md` y las etiquetas de versión desde la 0.1.0.

## [0.2.0] · 2026-10-12

### Agregado
- Skill `revisar-push` y hook `gate-push`: revisión antes de subir, con el resultado en el PR. El gate es
  opcional y se prende por repo con `git config kit-pedroza.gate true`. Adaptado de `claude-kit-chema` (MIT);
  detalle en `CREDITOS.md`.

## [0.1.2] · 2026-09-23

### Cambiado
- Se quitó la marca de otro kit; las skills quedan autónomas.

## [0.1.1] · 2026-09-23

### Corregido
- Versión subida para que los perfiles instalados tomen la skill `handoff` corregida.

## [0.1.0] · 2026-09-23

### Agregado
- Marketplace `kit-pedroza` con cinco skills propias (`kit-mercadotecnia`, `kit-cv`, `handoff`,
  `auditoria-presentaciones`, `auditoria-git`) y el hook opcional de aviso sonoro.
- Plantilla de issue para reportar bugs de skills.

[0.3.0]: https://github.com/FSPR2005/kit-pedroza/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/FSPR2005/kit-pedroza/compare/v0.1.2...v0.2.0
[0.1.2]: https://github.com/FSPR2005/kit-pedroza/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/FSPR2005/kit-pedroza/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/FSPR2005/kit-pedroza/releases/tag/v0.1.0
