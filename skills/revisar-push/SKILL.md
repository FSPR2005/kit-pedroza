---
name: revisar-push
license: MIT
description: Revisa un cambio antes de subirlo al remoto y produce el sello que exige el gate de push — corre las pruebas del proyecto en una copia limpia, manda el diff a un revisor adversario (otra instancia de Claude, sin herramientas), corrige o discute cada hallazgo bloqueante, sube y deja el resultado en el PR para quien lo va a revisar. Úsala antes de cualquier git push en un repo con el gate activo (git config kit-pedroza.gate true), cuando el hook gate-push bloquee un push, o con frases como "revisa antes de subir", "sube mis cambios", "haz el push".
---

# Revisar antes de subir

Vas a subir un cambio a un repo con el gate de push activo (`git config kit-pedroza.gate true`).
El hook `gate-push` no deja pasar un `git push` sin sello de revisión para ese commit; esta skill
produce el sello sin atajos.

El helper `revisar-push.sh` hace lo mecánico. Cada llamada de Bash es un shell nuevo, así que
localízalo e invócalo **en el mismo comando**, con el nombre del helper visible (así el hook puede
exigir que corra en segundo plano):

```bash
RP="${CLAUDE_SKILL_DIR}/scripts/revisar-push.sh"
[ -f "$RP" ] || RP="$(ls -d "${CLAUDE_CONFIG_DIR:-$HOME/.claude}"/plugins/cache/kit-pedroza/kit-pedroza/*/skills/revisar-push/scripts/revisar-push.sh 2>/dev/null | sort -V | tail -1)"
bash "${RP:?no encontré revisar-push.sh}" revisar     # Bash con run_in_background: true
```

Los demás subcomandos (`estado`, `saltar`, `activar`, `desactivar`, `metricas`) se invocan igual,
cambiando la última palabra; esos sí corren en primer plano.

## Pasos

0. **Llave del repo.** Si `git config --get kit-pedroza.gate` no dice `true`, el gate está apagado
   en este repo y el push pasa sin sello. Para prenderlo: `bash "$RP" activar`. Prenderlo o
   apagarlo es decisión del usuario.
1. **Trabaja en una rama, no en `main`.** El resultado de la revisión viaja en el PR (paso 8), y
   sin rama no hay PR.
2. **Revisar.** Corre `revisar` en un Bash con `run_in_background: true` y espera el aviso de
   Claude Code. Primero corren las pruebas del proyecto en una copia desechable y luego el revisor;
   una revisión real ha tardado hasta 11 minutos, más que el tope de 10 del Bash en primer plano.
   En primer plano, el hook lo devuelve con la instrucción.
3. **Pruebas rojas (salida 1 con el hallazgo `P1`).** Arregla, haz commit y vuelve al paso 2. El
   revisor no se invoca con pruebas rojas: no gastas uso hasta que pasen.
4. **Hallazgos `bloquea`.** Por cada uno: si es real, corrígelo y haz commit; el sha nuevo invalida
   el sello, así que vuelves al paso 2 (el revisor recibe los hallazgos previos y dice cuál quedó
   resuelto). Si crees que es un falso positivo, muéstraselo al usuario con la evidencia y espera
   su respuesta: **solo con la palabra del usuario** corres `bash "$RP" saltar <n> "<razón>"`.
   Nunca saltes un hallazgo por juicio propio.
5. **Avisos y hallazgos sin evidencia.** Repórtalos al usuario en una línea cada uno; no obligan a
   nada.
6. **Revisor no disponible (salida 3).** No hay sello y el push sigue bloqueado. Díselo al usuario
   tal cual. Si el error dice que el modelo no está disponible en su plan, puede cambiarlo con
   `git config kit-pedroza.revisor sonnet`. `KIT_SELLO=omitir git push …` también es decisión
   suya, no tuya, y queda anotado en el ledger. No ejecutes ninguna de las dos sin que la pida.
   - **HEAD cambió mientras revisaba (salida 4).** Hubo un commit en paralelo con `revisar`: se
     selló el commit anterior y el nuevo sigue sin revisar. Vuelve al paso 2, en un paso aparte y
     sin commits en curso. Nunca lances `revisar` en el mismo bloque que el commit.
7. **Subir.** Con 0 pendientes, `git push` solo, en su propio **comando aparte** (nunca
   `git commit … && git push`: el hook rechaza comandos que mueven HEAD y empujan en la misma
   línea).
8. **Dejar el resultado en el PR.** Quien revisa el PR no vio esta sesión: el resultado del gate
   tiene que llegarle ahí. Si la rama no tiene PR, ábrelo con `gh pr create`. Luego escribe un
   comentario con `gh pr comment <rama> --body-file <archivo>` (el archivo, en una carpeta
   temporal) que diga, en lenguaje simple:
   - el commit sellado (sha corto) y el veredicto;
   - qué hallazgos se corrigieron y cómo;
   - cuáles se saltaron y la razón que dio el usuario;
   - los avisos que quedaron y el resultado de las pruebas (o «sin pruebas configuradas»);
   - qué quieres que revise la otra persona o qué duda tienes, si hay alguna.
9. **Reportar.** Dile al usuario qué se corrigió, qué se saltó y por qué, los tokens que gastó el
   gate (los imprime `revisar`) y el enlace del PR. Nunca declares subido algo que el hook bloqueó.
10. **Vigilar el CI.** Si el repo tiene CI, `gh pr checks <rama> --watch`. Si falla, el arreglo es
    un commit nuevo: vuelve al paso 2. La reparación nunca sube sobre una cabeza sin sello.

## Lo que no hace esta skill

No revisa pushes hechos desde la terminal ni desde scripts (eso lo mide
`bash "$RP" estado --contra-remoto`), no sustituye la protección de ramas ni la revisión humana
del PR, y no es un escáner de secretos: el revisor puede ver uno en el diff, pero no lo busca a
fondo.

## Créditos

Adaptada del gate de push de `claude-kit-chema` (licencia MIT). El aviso completo está en
`CREDITOS.md`, en la raíz de este repo.
