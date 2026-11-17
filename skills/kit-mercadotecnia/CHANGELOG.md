# CHANGELOG — kit-mercadotecnia

Formato: fecha (YYYY-MM-DD) · qué cambió · fuente o razón.

## 2026-11-13 — V2.7.3 (integrada en kit-pedroza 0.8.0; base: V2.7.2)

- **P05, registro de tasas:** un sesgo se declara solo con evidencia de la fuente; el filtro que define al segmento no es, por sí solo, evidencia de sesgo ni prueba de representatividad; el mismo instrumento no prueba el mismo sesgo.
- **P05, cómo interpretar:** compradores no son compras (frecuencia y unidades no cuentan compradores) y cada umbral de cambio usa una sola tasa con su denominador.
- **Módulo 06, paso 4:** se separa en 4a (compradores en el periodo) y 4b (unidades); el ejemplo muestra 292,500 personas antes de las 3,510,000 unidades, sin cambiar los demás cálculos.
- **Razón:** en las pruebas ciegas de la V2.7.2, sus respuestas a tres casos nuevos (var8 a var10) declararon sesgos sin evidencia, multiplicaron compradores por compras en el periodo y mezclaron denominadores en un umbral.
- **Incluye** las tres correcciones del 2026-11-14 en los módulos 07 y 11 (entrada de abajo).

## 2026-11-14 — Tres correcciones de auditoría

- **11** — «Puerta del dinero» al final del marco 7 (quién autoriza el gasto y con qué datos) y «Contrato mínimo de datos» bajo 9.5 (fórmula, ventana, denominador 0).
- **07** — Error típico «Segmentar por el público que se cree tener»: verificar con la analítica y presentar la estimación como cota.
## 2026-11-12 — PROPUESTA V2.7.2 (no integrada; base: V2.7.1)

- **SKILL, encuadre:** mercado, resultado, medición y restricciones compartidos; máximo de tres preguntas, supuestos explícitos y correcciones ligadas al objetivo.
- **SKILL, fuentes del usuario:** consultar el archivo del encargo y priorizar sus fuentes sin suponer accesos.
- **SKILL, procedencia:** documentar discrepancias del curso y usar la formulación mejor sustentada.
- **P01-P12:** propagar el encuadre; investigación secundaria sistemática, condiciones de inferencia y causa, bases de segmentación justificadas, pilotos según capacidad y autorización, controles de unidades y tasas, ruta B2B y comprobación correcta del margen.
- **Módulo 06:** separar demografía, interés e intención; respetar denominadores e inclusión de conjuntos; renombrar salidas del ejemplo sin cambiar cálculos.
- **Módulo 11:** separar ROAS, ingresos, CPA y CLV; evitar duplicar cierre y distinguir atribución de causalidad.
- **Módulo 04:** registrar fuentes del encargo fuera de la skill.
- **Razón:** auditoría de Codex de nivel doctorado; objetivo del dueño: segmentar bien e investigar bien.

## 2026-11-12 — PROPUESTA V2.7.1 (no integrada; base: V2.7)

- **P05, un solo segmento**: se separan investigación comparativa, selección y piloto comercial. Si la empresa solo puede atender o financiar un segmento, no se proponen pilotos en varios segmentos ni se llama concentrada a una estrategia que abarca varios; para validar alternativas se usa investigación que no vende. Razón: en pruebas de la V2.7, dos respuestas propusieron pilotear varios segmentos pese a esa restricción.
- **P05, candidato provisional**: antes de nombrarlo se listan todas las alternativas, la evidencia de cada una, lo que distingue al candidato de cada alternativa, por qué eso justifica probarlo primero, lo que falta y la prueba que lo confirmaría. Tener más datos cuenta solo si las otras alternativas no los tienen. El tercer nivel se llama «Sin base suficiente para seleccionar un candidato». Condiciones mínimas del piloto, con «pendiente» en lugar de cantidades inventadas.
- **P05, salvaguardas recuperadas de la V2.5** (no integrada): selección y representatividad de la muestra; tasa sin base muestral como señal y no como estimación; dato faltante no vale cero; no sumar ni ordenar tamaños en unidades distintas en una puntuación común; el promedio de personas por hogar no convierte unidades; no suponer canal más barato o mejor ajuste sin datos. Nuevas: alias de grupos sin definir como escenarios (tomada de la V2.5.1, no integrada); separar tasas de prevalencia y de intención; tamaño del segmento ≠ demanda alcanzable.

## 2026-11-12 — PROPUESTA V2.7 (no integrada; base: V2.6)

- **P05**: si una cifra puede ser el total o el segmento ya filtrado, se calculan las dos lecturas, se descarta la imposible o contradictoria y, si ambas son posibles, se muestran los dos escenarios. La V2.6 omitió esta regla (sí estaba en la V2.5) y en una corrida tomó un total como segmento.

## 2026-11-12 — PROPUESTA V2.6 (no integrada; base: V2.4)

- **P05**: registro de tasas antes de aplicarlas (segmento, qué mide, quién respondió y en qué unidad, filtros, valor y cita de la fuente), asignación copiando la tasa con su segmento y comprobación fila por fila; sin umbrales ni cocientes entre unidades distintas; tres niveles de conclusión (selección defendible, recomendación provisional para un piloto con una señal identificable, sin base). Retoma de forma compacta la mejora de accionabilidad probada en la V2.5 (no integrada), que en una corrida intercambió tasas entre segmentos.

## 2026-11-11 — PROPUESTA V2.4 (no integrada): YAML válido y control de denominadores

- **SKILL.md**: la descripción pasa a un bloque YAML plegado (`>-`); el texto es idéntico y el frontmatter ya se puede leer con un parser YAML estricto. En V1, V2.2 y V2.3, los dos puntos de "Frases típicas:" lo volvían inválido.
- **P05 y módulo 06**: antes de multiplicar porcentajes se dice de qué total sale cada uno (población, hogares, empresas o un segmento ya calculado), con una tabla de base, porcentaje, resultado, unidad y fuente, una fila por operación. Personas, hogares, empresas y unidades de compra no se comparan sin una conversión justificada; si no la hay, la elección no se basa solo en el tamaño. El tamaño de un grupo amplio no es el de un subgrupo con otra condición.
- **CHANGELOG y P09**: sin cifras de los casos de prueba (el ejemplo de porcentajes con base de P09, paso 10, venía del caso de prueba de precios y se cambió por uno neutro). En la regla de suficiencia de SKILL.md, la frase literal de un caso de prueba se cambió por "una cifra sin explicación"; la regla no cambia.

## 2026-11-11 — PROPUESTA V2.3 (no integrada): correcciones de la segunda auditoría externa

- **P09 y SKILL.md**: se añadió la obligación de calcular y justificar matemáticamente la posición de un precio dentro del rango competitivo; la razón para escoger un precio sin evidencia de demanda se presenta como hipótesis; la comprobación final revisa la posición. Los ejemplos de P09 usan cifras que no son de ningún caso de prueba (antes, el paso 8 citaba el resultado del caso de prueba de precios).
- **P12, módulo 02 y SKILL.md**: la pregunta estratégica va en prosa y sin huecos, pero no inventa problemas, oportunidades, fortalezas, amenazas, competidores ni rasgos de la oferta; si faltan, dice que están por identificar o por validar y qué información los completaría. Lo mismo para el FODA.

## 2026-11-11 — PROPUESTA V2 (no integrada): correcciones verificadas con pruebas ciegas

- **P09** reescrito: costo variable/fijo/total unitario, efecto del volumen, margen vs. markup, equilibrio vs. margen objetivo, tabla precio → volumen con redondeo hacia arriba, recomendación condicionada, comprobación aritmética obligatoria.
- **P02**: las 6 fuerzas del macroentorno y los 6 actores del microentorno, obligatorios; "sin información" en vez de omitir.
- **P01**: modos diseñar / campo / procesar datos del cliente / analizar fuentes.
- **SKILL.md**: revisión final de salida (decisión en la primera línea; sin corchetes ni códigos internos; resumen = tabla; supuestos definidos; no inventar problemas); regla de suficiencia: sin datos, la primera línea dice que no hay número defendible y el orden de magnitud va al final como rango; temas legales sin asesoría jurídica.
- **11 y P11**: ley mexicana de datos personales de 2025 (DOF 2025-03-20; última reforma 2025-11-14) con principios, consentimiento, datos sensibles, aviso de privacidad y autoridad verificados en el texto oficial.
- **08, 06, FUENTES**: Interbrand 2026; Thompson y Lyons 1993; función de demanda Q1/Q2/QF marcada como complemento de Kotler y Keller; estado de verificación por fuente.

## 2026-11-10 — PROPUESTA (no integrada): procedimientos operativos, protocolo de evidencia y fidelidad al curso

Razón: auditoría contra el PDF completo del curso (506 págs., texto + lectura de
las láminas que son imagen) y contra el índice verificado de K&A 18.ª. Detalle
y justificación de cada cambio en el expediente de auditoría (fuera del repo).

- **SKILL.md** — etiquetas de origen ([Curso], [K&A cap. N], [Externo], [Kit]);
  tabla de 12 procedimientos; protocolo de evidencia de 8 etiquetas y regla de
  suficiencia; prueba de coherencia; descripción con más frases de activación
  (precio, canal, plan de marketing, comunicación, B2B).
- **procedimientos/** (nuevo) — P01 a P12: investigación, entorno, SIM,
  segmentación, mercados meta, posicionamiento, comportamiento de compra,
  producto y marca, precio, canales, comunicación integrada, plan de marketing.
- **references/12-mercados-de-negocios.md** (nuevo) — K&A cap. 6 (B2B).
- **01** — elementos de cada P [Curso].
- **02** — pregunta estratégica del plan y tabla de programas de acción [Curso];
  Treacy y Wiersema corregido a 1993.
- **03** — VRIO marcado como contenido del curso; aviso de vigencia de Euromonitor.
- **04** — instrumentos de investigación (f).
- **05** — tipos de comportamiento de decisión de compra (marco 11).
- **06** — notas de independencia de porcentajes y de diferencias del ejercicio del curso.
- **08** — preguntas de paso por etapa del desarrollo de nuevos productos y
  categorías de adoptantes [Curso]; RWW completo de Day (2007) [Externo].
- **09** — otros factores del precio y elasticidad; punto de equilibrio; lista
  de verificación del curso; origen del ejemplo de costo marcado.
- **10** — proceso de venta personal (K&A cap. 16).
- **11** — nueva LFPDPPP (DOF 2025-03-20); principios del art. 5 del GDPR
  corregidos; nota de la diferencia curso/K&A en "impacto"; título de error típico.
- **FUENTES.md** — jerarquía, estados de verificación, tabla capítulo → módulo,
  fuentes que se citaban sin alta (Barney, Brown, Ries), fuentes de vigencia.
- Índice ("Contenido") al inicio de cada módulo de más de 100 líneas.

## 2026-07-15 — Auditoría de cobertura contra el material semilla

Razón: auditoría exhaustiva de la skill contra las 19 sesiones del compilado
del curso del que se destiló (verificación en dos fases: 19 comparadores
sesión-vs-módulo + 1 crítico transversal → 44 huecos reportados → cada uno
verificado adversarialmente contra la skill completa → 15 confirmados,
29 refutados). Fuente doctrinal de los cambios: Kotler & Armstrong 18.ª ed.,
salvo donde se indica fuente nueva.

- **01** — Definición ancla de *marketing* (Kotler + AMA) al abrir el marco 1;
  las formas de la oferta de mercado (servicios, experiencias, eventos,
  personas, lugares, propiedades, organizaciones, información, ideas) en el
  marco 3; nota que deshace la colisión terminológica "participación del
  cliente" (engagement, marco 10) vs. *share of customer* (métrica, módulo 06).
- **03** — Marco nuevo 9 "Marketing global: estandarizar vs. adaptar"
  (modos de entrada; extensión directa / adaptación de producto / adaptación
  de comunicación / doble adaptación; escalación de precios; whole-channel
  view) + pregunta en "Cuándo usar" + fila en la tabla de investigación.
  Cierra el hueco transversal más citado de la auditoría.
- **04** — Error típico nuevo: "Sobre-investigar (parálisis por análisis)" —
  la dimensión temporal/acumulativa que faltaba junto a "investigar sin
  decisión".
- **05** — Definición ancla de *comportamiento del consumidor* (eligen,
  compran, usan y desechan) al abrir "Marcos y conceptos".
- **06** — Marco nuevo 7 "Participación del cliente (share of customer /
  share of wallet)": definición, fórmula, contraste con participación de
  mercado, liga a CLV/customer equity + fila en la tabla de investigación.
- **07** — En el marco 8: encuadre del proceso de 4 pasos (A-D) para elegir
  la estrategia de diferenciación y posicionamiento + definición explícita
  de *ventaja competitiva*.
- **08** — *Retorno de la calidad* como cuarto concepto de Calidad (marco 4);
  definición formal de *marca* como preámbulo de brand equity (marco 8,
  retitulado "Marca, brand equity y brand value"); *personalidad de marca*
  con las 5 dimensiones de Aaker (marco 9.1; fuente nueva: Aaker 1997);
  definición de *crowdsourcing* y técnicas creativas (etapa 1 del proceso);
  *killer phrases* — resistencia organizacional a ideas nuevas (marco 12;
  fuente nueva: Thompson 1992/1994); marco nuevo 16 "Consideraciones
  adicionales: regulación e internacionalización del producto" (políticas
  públicas, patentes, seguridad, product liability; internacionalización con
  remisión a 03·9); "Proceso de adopción" pasa de 16 a 17.
- **09** — Definición ancla de *precio* (sentido estrecho y amplio) al abrir
  "Marcos y conceptos".
- **11** — "Nuevo modelo de comunicaciones y marketing de contenidos" con la
  clasificación paid/owned/earned/shared (dentro del marco 3, IMC); desglose
  de *estructura* y *formato* del mensaje en el paso 3 del proceso de 6 pasos
  (conclusión explícita vs. inferida, uno vs. dos lados, orden de argumentos;
  novedad/contraste/titulares); 9.7 "Organización para la publicidad"
  (agencia vs. in-house) y 9.8 "Publicidad internacional" (estandarizar vs.
  adaptar, remite a 03·9); formas tradicionales del marketing directo
  desglosadas (correo directo, telemarketing saliente/entrante, DRTV).
- **FUENTES.md** — Altas: Aaker (1997); Thompson (1992/1994).

**Pase de verificación adversarial posterior** (10 verificadores sobre los
archivos editados): 20 observaciones; se aplicaron las 10 de fidelidad
doctrinal — 1 bloqueante (la matriz precio × beneficios es el paso C
"seleccionar la estrategia global", no el B "elegir ventajas", en 07) y
correcciones de taxonomía: definición AMA completa y "engage" en 01; lista
de formas de oferta alineada a K&A 18.ª (sin "eventos"/"propiedades") en 01;
métodos de joint venturing canónicos en 03; definición de comportamiento del
consumidor alineada a K&A (consumidores finales, no organizaciones) en 05;
retorno de la calidad como enfoque, no cuarta dimensión, en 08 (y marcos
renumerados 16-17); componentes del valor entregado (tiempo, energía,
desgaste psicológico) en 09; catálogo/quiosco en vez de cupones como formas
de marketing directo en 11; fila nueva de marketing global en el mapa del
SKILL.md; notas de desambiguación 01↔06 simetrizadas.

Huecos detectados y descartados a propósito (con razón): taxonomías
propietarias de consultoras (Lexia, The Futures Company/9 megatendencias,
13 needstates de Bimbo) — el método genérico ya está y las listas atan la
skill a un proveedor/cliente; casos de marca puntuales (Innocent, Nokia
Lumia, Cadbury, Patagonia como framework) — ilustraciones, no doctrina;
figuras/recursos visuales del curso (rompecabezas del SIM, Fig. 2.5) —
redundantes con la prosa existente; broadcast faxing — obsoleto.
