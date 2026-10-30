# Cómo mejora esta skill con el uso

No existe un mecanismo integrado para que una skill aprenda sola. La guía oficial propone iterar: observar
cómo se usa en tareas reales, anotar lo específico que falló, corregir y volver a probar con evaluaciones
(https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices, «Evaluation and
iteration», consultada el 2026-10-29). Este archivo convierte esa iteración en rutina.

## 1. Anotar (en cada uso, sin preguntar)

Se anota una entrada en la bitácora de mejoras del ámbito cuando pasa algo de esto:
- El usuario corrige un borrador, rechaza un mensaje o dice que algo «no sirve».
- Falla un punto de «Antes de enseñarle algo al usuario» o se repite un «Error típico».
- La skill no cubría el caso y hubo que improvisar el método.
- Llega un resultado: respuesta, llamada, rechazo, baja o rebote de un mensaje que salió con esta skill.
- Se alcanza la regla para parar de una tanda.

**Dónde:** `RP-MEJORAS.md`, junto a `RP-CATALOGO.md` del ámbito activo. Si el perfil no es del ámbito (modo
separado), en la carpeta del proyecto. Nunca en este repo: es público.

Formato, una entrada por hecho y fecha absoluta:

```
## 2026-10-29 · [falla | hueco | resultado | idea] · <paso de la skill>
Qué pasó: una frase, sin nombres de prospectos ni datos de contacto (usa el id del CRM).
Qué se cambiaría: la regla en imperativo.
Evidencia: el id del toque o del borrador, o la cifra (p. ej., 0 respuestas en 20 envíos).
```

## 2. Medir

Al cerrar cada tanda, cruza la hoja de toques del CRM con lo que se usó: respuestas por plantilla, por
segmento y por tipo de hallazgo del diagnóstico (`diagnostico.md`). Una plantilla o un tipo de hallazgo con
0 respuestas en 20 envíos se cambia; lo que funciona se anota como «resultado».

## 3. Consolidar (con el «va» del usuario)

Con tres o más entradas sin consolidar, o al cerrar una tanda, propónselo al usuario en una línea. Si lo
aprueba:
1. Reescribe cada lección **en términos genéricos**: sin cuentas, clientes, ofertas concretas ni cifras
   internas. Pasa al `SKILL.md` o a la referencia que toque y se anota en `CHANGELOG.md`.
2. Si la lección corrige una conducta, agrega una evaluación que la reproduzca (sección 4).
3. Marca la entrada de la bitácora como «consolidada» con la versión. No se borra.
4. El cambio sube por el repo del kit, con la auditoría de push y el «va» del usuario.

Si la misma regla aparece rota dos veces, el problema no es de memoria: la regla está mal escrita o le falta
un caso. Corrígela en vez de repetirla.

## 4. Probar que no se rompió

Cada conducta que importa tiene un caso en `evals/kit-rp-<caso>/` de la raíz del plugin (`prompt.md` y
`graders/`), y se corre con `claude plugin eval <ruta del plugin> --tag kit-rp` antes de subir un cambio.
Mínimo tres casos: no sale nada sin el «va»; no se escribe una cifra ni una afirmación fuera del catálogo; el
diagnóstico va antes de la oferta. Cuesta tokens: córrelo al consolidar, no en cada uso.

## Cola de mejoras

Lo que ya se detectó y falta hacer. Se toma de arriba hacia abajo.

1. Escribir los tres casos de evaluación mínimos de la sección 4 y correrlos una vez para tener la base.
2. Plantilla de `RP-CATALOGO.md` con un apartado de afirmaciones por oferta, para que el modelo local y la
   validación mecánica lean el mismo catálogo que la skill.
3. Columna en la hoja de toques del CRM con el tipo de hallazgo, para poder medir la sección 2.
4. Plantilla de correo con diagnóstico en `plantillas.md` (las cuatro piezas en unas 120 palabras).
