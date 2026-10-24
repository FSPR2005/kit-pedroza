# Estructura del CRM

El CRM es una hoja de cálculo o una herramienta de CRM de la cuenta del ámbito
(nunca un repo). Cuatro hojas. Las columnas de datos personales solo existen en
«Contactos».

## Hoja «Cuentas» (una fila por empresa u organización)

| Columna | Qué va |
|---|---|
| id | C-001, C-002… |
| cuenta | Nombre de la empresa u organización |
| segmento | El del catálogo (por ejemplo, educación, salud, comercio) |
| estado o ciudad | Solo si importa para el territorio |
| fuente del encaje | Liga pública y fecha de consulta |
| disparador | Por qué ahora, con su fuente y fecha |
| oferta | Clave de la oferta del catálogo; «sin solución» si no hay |
| camino de venta | Marca propia o línea blanca o maquila; una campaña por camino |
| dato | El dato verificable de su página que va en la primera línea; «sin dato» si no hay |
| URL del dato | Liga exacta donde aparece, con fecha de consulta |
| dueño interno | Quién lleva la cuenta (una persona) |
| quién atiende | Quién contesta las respuestas; va en copia visible en cada correo |
| etapa | Ver «Etapas» |
| último toque | AAAA-MM-DD |
| siguiente paso | Qué sigue, en una línea |
| fecha del siguiente paso | AAAA-MM-DD; vacía = cuenta muerta |
| notas | Lo que no cabe arriba; nada de datos personales |

## Hoja «Contactos» (una fila por persona)

| Columna | Qué va |
|---|---|
| id | P-001… |
| cuenta | id de la cuenta |
| nombre y cargo | Como aparece en la fuente |
| de dónde salió y cómo se confirmó | Fuente con permiso de uso y fecha (o «sin confirmar»); nunca un raspado |
| canal | Correo, teléfono de oficina, LinkedIn a mano |
| dato de contacto | Solo aquí |
| aviso de privacidad | Fecha en que se le dio la liga |
| toque 1 | AAAA-MM-DD del primer correo |
| toque 2 | AAAA-MM-DD del segundo correo (día 3 o 4 hábil), o vacío si ya contestó |
| toque 3 | AAAA-MM-DD del tercer correo (día 9 a 11 hábil), o vacío si ya contestó |
| baja | Sí / no, con fecha. Con «sí» no se le vuelve a escribir. La palabra «baja» sola, como respuesta, cuenta como «sí» |
| derechos sobre sus datos | Si pidió acceso, rectificación, cancelación u oposición: fecha de la solicitud y de la respuesta |

## Hoja «Toques» (una fila por cada mensaje, llamada o reunión)

fecha · hora programada (en la hora del destinatario) · cuenta · contacto · canal · número de
toque (1, 2 o 3) · qué se envió o habló (asunto, sin pegar el cuerpo) · copias · respuesta ·
quién dio el «va».

## Hoja «Necesidades» (lo que piden y no tenemos)

Es interna: no se copia a propuestas ni a mensajes para otras cuentas.

fecha · cuenta · necesidad con sus palabras · cómo lo resuelven hoy · cuánto les
cuesta (si lo dijeron) · quién decide · presupuesto · para cuándo · salida
propuesta (construir / aliado / declinar) · dueño de la decisión.

## Etapas

Cada etapa se gana con un hecho, no con una sensación.

| Etapa | Se llega cuando |
|---|---|
| 0 · Investigada | Hay encaje y disparador con fuente |
| 1 · Contactada | Salió el primer mensaje, con «va» |
| 2 · Respondió | Hubo cualquier respuesta humana |
| 3 · Llamada agendada | Hay fecha aceptada por las dos partes |
| 4 · Llamada hecha | Hay minuta y siguiente paso |
| 5 · Propuesta | Se envió una propuesta formal |
| 6 · Ganada / Perdida / Sin respuesta | Con fecha y una línea de por qué |

«Sin respuesta» se pone tras el toque 3 sin contestar. No hay toque 4.
