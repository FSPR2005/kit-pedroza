# P05 · Evaluar y elegir mercados meta

Origen: [Curso] tres factores de evaluación, cinco fuerzas como atractivo estructural, cuatro estrategias de orientación, valor de mercado y cálculo de demanda · [K&A cap. 7] · reglas [Kit].
Marcos de apoyo: `references/07-stp-posicionamiento.md` (marcos 4 y 5) y `references/06-dimensionamiento-de-mercado.md`.

## Cuándo usarlo
Ya hay segmentos (P04) y hay que decidir a cuáles y a cuántos entrar.

## Información mínima
Hereda el encuadre de SKILL.md: candidatos, objetivo, métrica, horizonte y
restricciones. Aplica primero los límites duros; después compara alternativas
con criterios ligados al objetivo. Justifica pesos y escalas y revisa si cambios
razonables alteran la elección. Una diferencia documentada solo justifica prioridad
si es pertinente para el resultado buscado. No equipares tamaño con éxito.
Los segmentos candidatos y, para cada uno, algún dato de tamaño o la forma de estimarlo; recursos de la empresa (dinero, gente, canal) y cuántos segmentos puede atender.

## Investigar, seleccionar y pilotear [Kit]
La **investigación comparativa** reúne datos de varios segmentos y no vende; la **selección** elige dónde entrar; el **piloto comercial** vende en pequeño para confirmarla. Si el usuario solo puede atender o financiar un segmento (o un piloto), selección y piloto son de **un solo segmento**: nada de pilotos en varios segmentos, ni simultáneos ni "uno por segmento", y no llames concentrada a una estrategia que abarca varios. Fuera de esa restricción, clasifica la estrategia por su lógica de foco y oferta, no solo por el número de segmentos. Para validar alternativas antes de elegir, propone investigación que no venda (fuentes secundarias, encuesta, prueba de concepto, entrevistas).

## Pasos
1. **Tamaño y crecimiento** [Curso]: estima cada segmento con la cadena de proporciones del módulo 06 (potencial → disponible → meta → demanda en unidades → demanda en valor). Cada porcentaje lleva fuente o se marca `SUPUESTO`.
   **Bases y denominadores** [Kit], obligatorio antes de multiplicar:
   - Para cada dato, di sobre qué está calculado. Hay cuatro casos distintos: porcentaje del total de la población, porcentaje del total de hogares (o de empresas), porcentaje de un segmento que ya calculaste, o tamaño directo del segmento, cuando la fuente ya da la cifra.
   - Arma esta tabla, con una fila por cada operación. Si hay dos filtros, van en dos filas. La base de cada fila es el total del que sale ese porcentaje: el total original si el porcentaje es del total (como en la cadena del módulo 06), o el resultado de la fila anterior si es un porcentaje de ese segmento:

     | Segmento | Base | Porcentaje | Resultado | Unidad | Fuente |
     |---|---:|---:|---:|---|---|

   - Revisa la tabla antes de usarla: cada porcentaje del dato aparece una sola vez (ni omitido ni aplicado dos veces), y cada resultado es menor o igual que su base.
   - Si una cifra puede ser el total o el segmento ya filtrado (por ejemplo, un número escrito junto a un porcentaje), no elijas en silencio: calcula el total que implicaría cada lectura y descarta la que es imposible o choca con otro dato (por ejemplo, más hogares que habitantes). Si las dos son posibles, muestra los dos escenarios y di cuál asumes y qué dato lo confirma.
   **Registro de tasas** [Kit], antes de aplicar una tasa (intención, conversión, prevalencia, penetración):
   - Lista cada tasa con: segmento al que pertenece, qué mide, quién respondió y en qué unidad (persona, hogar, empresa), cómo se seleccionó la muestra y sus filtros, representatividad y los sesgos que documente la fuente, valor y la frase literal de la fuente donde aparece.
   - Declara un sesgo solo si la fuente o el enunciado dan evidencia de él; si no, escribe «sesgo: no documentado» y no lo deduzcas. Que una muestra esté filtrada por la misma condición que define al segmento no es, por sí solo, evidencia de sesgo; tampoco prueba que lo represente: su representatividad se juzga por cómo se seleccionó. Que dos tasas vengan del mismo instrumento no prueba que tengan el mismo sesgo: no lo afirmes ni lo uses como argumento.
   - Asigna cada tasa copiándola junto con el nombre de su segmento tal como lo dice la fuente; nunca por el orden de la lista, la posición en una tabla o la cercanía en el texto. Antes de multiplicar, comprueba fila por fila que la tasa de la tabla de bases es la misma del registro.
   - Si la fuente nombra grupos con letras, números o alias que no define (por ejemplo, "grupo 1" sin decir cuál es), no deduzcas la correspondencia por el orden: dilo y calcula cada asignación posible como escenario etiquetado, diciendo si la recomendación cambia.
   - Una tasa de prevalencia (qué parte de un grupo cumple una condición) define el tamaño del segmento; una de intención o conversión se aplica después, al segmento ya definido. No uses una en lugar de la otra ni pases una tasa de un grupo a otro.
   - Si no se puede comprobar que una tasa corresponde al segmento (o al subgrupo filtrado), úsala solo en un escenario condicional, marcado así, y no como dato. Si faltan la base de la muestra o su representatividad, preséntala como señal de la prueba, no como estimación de compradores del mercado.
2. **Atractivo estructural** [Curso]: rivalidad, nuevos entrantes, sustitutos, poder de clientes y poder de proveedores. Califica cada fuerza (alta, media, baja) con una razón.
3. **Objetivos y recursos** [Curso]: ¿puede la empresa crear valor superior y ganar ventaja en ese segmento?
4. **Matriz de decisión** [Kit]: segmentos en filas; tamaño, crecimiento, atractivo estructural y ajuste con la empresa en columnas. Pesos declarados y justificados; si no hay datos para un peso, se dice. Si los tamaños están en unidades distintas y no hay conversión válida, no los sumes ni los ordenes en una puntuación común: muéstralos por separado y marca el tamaño como no comparable. Un dato faltante no vale cero ni se reemplaza por una cifra inventada: se marca "no evaluado" y se dice cómo afecta la decisión.
5. **Estrategia de orientación** [Curso]: indiferenciado, diferenciado, concentrado o micromarketing (local o individual), según recursos, variabilidad del producto, etapa del ciclo de vida y estrategia de la competencia [K&A].

## Cómo interpretar [Kit]
- Grande y creciente no basta: con rivalidad feroz o sustitutos baratos, el segmento destruye valor.
- El tamaño del segmento no es la demanda que la empresa puede alcanzar: esta depende de la compra real (no solo la intención), la frecuencia, la cobertura del canal y la capacidad de atenderlo.
- Al multiplicar porcentajes de fuentes distintas (por ejemplo, % de nivel socioeconómico × % de edad) se supone que son independientes. Si no lo son, el resultado se desvía; dilo y, si se puede, usa un cruce real de la fuente.
- Revisa que anide: con el mismo universo y periodo, comprueba inclusión de conjuntos: penetrado dentro del meta ⊆ meta ⊆ disponible ⊆ potencial; sus tamaños cumplen ≤. El orden de tamaños no prueba inclusión. Distingue compradores actuales totales de los que pertenecen al meta elegido.
- **Unidades** [Kit]: personas, hogares, compradores, usuarios, empresas y unidades de consumo o de compra no se comparan como si fueran lo mismo. Para compararlas hace falta una conversión justificada (por ejemplo, a unidades de decisión de compra, volumen, frecuencia o valor), con su fuente o marcada `SUPUESTO`. El promedio de personas por hogar, por sí solo, no convierte personas en hogares compradores. Si no hay datos para convertir, dilo: los segmentos no son directamente comparables por tamaño, y la elección no puede basarse solo en ese tamaño. Tampoco se calculan umbrales, cocientes ni puntos de equilibrio entre resultados en unidades distintas, aunque se advierta la diferencia. Esto vale también para la investigación que propongas: no propongas conseguir personas por hogar para "convertir" segmentos; pide el dato que sí convierte (quién decide la compra, consumo o compra por hogar, frecuencia o valor).
- **Compradores no son compras** [Kit]: si el objetivo es el número de compradores, compara personas (o unidades de decisión) que compran en el periodo. La frecuencia y las unidades por comprador cambian compras y volumen, no compradores: no las multipliques para estimar compradores.
- **Umbrales de cambio** [Kit]: al decir qué cambiaría la recomendación, nombra una sola tasa con su numerador y su denominador (por ejemplo, compradores ÷ personas del segmento, o compradores ÷ personas con intención declarada) y calcula el umbral con esa misma tasa. No mezcles las dos en una frase: dan umbrales distintos.
- El tamaño de un grupo amplio no es el tamaño de un subgrupo que además cumple otra condición. Si falta el dato del subgrupo, queda como faltante o `SUPUESTO`; no se convierte en cifra confirmada.

## Nivel de la conclusión [Kit]
En el nivel 2 separa hechos, inferencias y supuestos. Una condición que solo
define mejor un segmento (por ejemplo, un filtro verificable) no es ventaja
comercial por sí sola: di qué efecto tiene en el objetivo.

Di cuál de estos tres niveles alcanza la respuesta y no los mezcles:
1. **Selección defendible:** los segmentos se comparan en una unidad común pertinente (demanda, ventas o contribución por periodo), con tasas que corresponden a cada segmento. Di los supuestos y qué cambiaría el resultado.
2. **Recomendación provisional para un piloto:** no hay comparación económica defendible, pero una diferencia documentada distingue a un candidato de **cada** alternativa. Antes de nombrarlo: lista todas las alternativas viables; da la evidencia a favor y en contra de cada una (tamaño en su unidad, calidad de su tasa, definición, ajuste con capacidad, presupuesto y canal, costo y riesgo de validarla); di qué distingue al candidato de cada una y por qué eso justifica probarlo primero; di qué falta y qué prueba confirmaría o rechazaría la hipótesis. Tener más datos cuenta solo si las otras alternativas no los tienen y si reduce de verdad la incertidumbre. No supongas canal más barato, acceso más fácil ni mejor ajuste sin datos. Solo autoriza un piloto acotado y reversible, no todo el presupuesto.
3. **Sin base suficiente para seleccionar un candidato:** si nada documentado distingue a un candidato de todas las alternativas, escribe esa frase, no inventes un desempate y propone la investigación de menor costo que lo resolvería, sin romper la restricción de un solo segmento.

## Condiciones del piloto [Kit]
Cada piloto se hace sobre un solo segmento. Cuántos pilotos se hacen depende de la
capacidad, la autorización y el presupuesto del encuadre: si solo se autoriza atender
uno, hay un solo piloto. Cada piloto define objetivo,
hipótesis, presupuesto máximo, duración, responsable, indicadores y criterios
de éxito, fracaso y detención antes de medir. Los valores faltantes quedan
pendientes, con responsable; no se inventan ni se presentan como autorizados.

## Entregable
Registro de tasas, tabla de bases y denominadores, nivel de la conclusión con la comparación del candidato frente a cada alternativa, matriz de evaluación con cálculo a la vista, segmento(s) elegido(s) o candidato, estrategia de orientación, condiciones del piloto si lo hay y lo que falta comprobar. Escenarios pesimista, base y optimista cuando hay supuestos.

## Límites
Las cifras salen de las fuentes que dé el usuario o que se consulten en la conversación. Sin ellas, Claude entrega la fórmula y la lista de datos, no un número. Una recomendación provisional no autoriza invertir todo el presupuesto.
