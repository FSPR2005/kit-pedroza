# Créditos

## Gate de push

La skill `revisar-push` y el hook `gate-push` son una adaptación del gate de push de
`claude-kit-chema` (https://github.com/chemaw8/claude-kit-chema), versión 1.31.0, commit
`91820df` (2026-10-06), que se publica con licencia MIT.

| Archivo de este repo | Archivo de origen |
|---|---|
| `hooks/gate-push.sh` | `hooks/sello-push.sh` |
| `hooks/test-gate-push.sh` | `hooks/test-sello-push.sh` |
| `skills/revisar-push/scripts/revisar-push.sh` | `scripts/sello-push.sh` |
| `skills/revisar-push/SKILL.md` | `commands/revisar-antes-de-subir.md` |

Cambios respecto al original: nombres de archivos, llaves de `git config` (`kit-pedroza.*`),
ledger dentro de la carpeta del perfil activo (`CLAUDE_CONFIG_DIR`), mensajes, un prompt del
revisor sin las piezas propias del kit original, y el paso que deja el resultado de la revisión
en el PR.

Aviso de licencia del original, como lo pide la licencia MIT:

```
MIT License

Copyright (c) 2026 chemaw8 (José Loyola, Innovattia)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
