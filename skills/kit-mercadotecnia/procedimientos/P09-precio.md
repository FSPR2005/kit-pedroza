# P09 · Recomendar una estrategia de precio

Origen: [Curso] piso y techo, tres familias, fórmula de precio por costo, precio por ciclo de vida, productos nuevos, mezcla, cambios de precio, lista de verificación · [K&A caps. 10-11 y apéndice "Marketing by the Numbers"] · reglas [Kit].
Marcos de apoyo: `references/09-precios.md`. Para cálculos de dinero, también la skill de finanzas.

## Cuándo usarlo
Lanzar con precio, subir o bajar, responder a un competidor, poner precio a una línea o paquete.

## Información mínima
Primero hereda el encuadre de SKILL.md: mercado, objetivo, métrica, horizonte y
restricciones. No presupongas que el objetivo es maximizar margen o participación.
Evalúa precios según el resultado acordado, sin omitir demanda, contribución,
capacidad y efectos en clientes. Un volumen necesario no demuestra demanda.
Presenta margen objetivo solo si fue dado o como escenario supuesto explícito.
1. Costos: costo variable por unidad y costos fijos del periodo.
2. **Volumen esperado** (unidades, clientes o suscriptores por periodo) o capacidad. Sin volumen no hay costo unitario total.
3. Precios de competidores relevantes, con fuente y fecha.
4. Posicionamiento y mercado meta (P06).

Si faltan costos: se puede construir una **hipótesis preliminar** de precio basada en valor o en competencia, pero se dice que la rentabilidad no se puede validar.
Si falta el volumen: se entrega la tabla precio → volumen necesario (pasos 3-4) en lugar de un precio único.

## Conceptos que no se mezclan [Curso + K&A]
| Concepto | Fórmula | Nota |
|---|---|---|
| Costo variable unitario (CV) | dato | No cambia con el volumen (supuesto habitual; dilo) |
| Costo fijo del periodo (CF) | dato | No cambia con el volumen dentro de un rango; si crece por escalones, dilo |
| Costo total unitario | CV + CF ÷ N | **Baja cuando sube el volumen N**: el fijo se reparte entre más unidades |
| Margen sobre precio (m) | (P − costo) ÷ P | Precio = costo ÷ (1 − m) [Curso] |
| Markup sobre costo (k) | (P − costo) ÷ costo | Precio = costo × (1 + k). Un markup de 35% **no** da un margen de 35% |
| Punto de equilibrio | N = CF ÷ (P − CV) | Utilidad cero. **No** es el margen objetivo |
| Volumen para margen objetivo | N = CF ÷ (P × (1 − m) − CV) | Solo existe si P × (1 − m) > CV |

## Pasos
1. **Piso** [Curso]: con volumen dado, costo total unitario = CV + CF ÷ N; el precio mínimo con margen m es ese costo ÷ (1 − m). Sin volumen, el piso absoluto es CV ÷ (1 − m), que solo cubre el variable.
2. **Techo** [Curso]: valor percibido por el cliente. Sin evidencia, se marca **Supuesto** y se propone cómo medirlo.
3. **Referencia competitiva** [Curso]: precios de rivales, qué incluyen y con qué fuente. Si describes dónde cae un precio dentro del rango de la competencia, calcúlalo [Kit]: posición = (P − mínimo) ÷ (máximo − mínimo); punto medio = (mínimo + máximo) ÷ 2. Ejemplo: con rivales entre 300 y 500, el punto medio es 400 y 360 queda al 30% del recorrido ((360 − 300) ÷ 200); 360 no es el punto medio. La posición describe el precio; no prueba que el mercado lo acepte.
4. **Tabla precio → volumen** [Kit]: para 3-5 precios dentro del rango razonable, calcula el volumen de equilibrio y el volumen para el margen objetivo. **Redondea hacia arriba** cuando el resultado es un mínimo de clientes o unidades.
5. **Otros factores** [K&A cap. 10]: objetivos de la empresa, consistencia con el posicionamiento [Curso], mercado y demanda (sensibilidad al precio; elasticidad solo si hay datos), economía, intermediarios, regulación.
6. **Familia de estrategia** [Curso]: basada en el **costo** (parte del costo y suma margen; ignora al cliente), en la **competencia** (parte de los precios rivales; riesgo de guerra de precios) o en el **valor percibido** (parte de lo que el cliente valora; el precio define el costo que puedes tener). Di cuál usas y por qué.
7. **Situación específica** [Curso]: producto nuevo (descremado con sus 3 condiciones, o penetración), mezcla (cautivo, paquete), ciclo de vida, cambio de precio y reacción de la competencia.
8. **Recomendación con condición de viabilidad** [Kit]: el precio recomendado va junto al volumen que lo hace viable y a los supuestos de los que depende. Si el volumen esperado no se conoce, la recomendación se escribe como condición (con costo variable de 100 y fijos de 50,000 al mes: "a 400 se necesitan al menos 278 clientes para un margen de 30%"). Sin evidencia de demanda ni de valor percibido, la razón para escoger un precio dentro del rango es una hipótesis y se dice así; no se presenta como respaldada por el mercado.
9. **Lista de verificación** [Curso]: costo, mercado, calidad, demanda, competencia, posicionamiento, realismo, rentabilidad.
10. **Comprobación aritmética final** [Kit], obligatoria antes de entregar:
    - Recalcula cada cifra del resumen desde la tabla; el rango de precio y el rango de volumen del resumen deben corresponder fila por fila.
    - Comprueba una fila al revés: con el volumen redondeado N, el margen
      realizado = 1 − (CV + CF/N)/P debe ser igual o mayor al objetivo.
      Verifica P > 0, N > 0, 0 ≤ m < 1 y P(1 − m) > CV antes de calcular
      un volumen finito. Si no se cumplen, explica la inviabilidad del escenario.
    - Los porcentajes llevan su base explícita ("350 está 12.5% por debajo de 400", no "como 10% abajo").
    - Si la respuesta ubica el precio en el rango de la competencia, la palabra que usa coincide con el cálculo del paso 3.
    - Si algo no cuadra, se corrige antes de entregar; no se entrega con la nota "aprox.".

## Cómo interpretar [Kit]
- El costo dice cuánto no puedes bajar; no dice cuánto cobrar.
- Un precio que exige más clientes de los que el mercado meta puede dar no es viable aunque esté dentro del rango de la competencia.
- Una baja de precio puede leerse como "algo anda mal": revisa el mensaje.

## Entregable
Tabla piso / referencia / techo con fuentes; tabla precio → volumen de equilibrio → volumen para el margen; estrategia recomendada con su condición de viabilidad; supuestos numerados; resultado de la comprobación aritmética.

## Límites
Sin evidencia de disposición a pagar, el techo es supuesto. Claude no inventa elasticidades, volúmenes ni precios de competidores.
