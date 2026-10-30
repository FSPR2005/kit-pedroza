# Diagnóstico: qué le pasa a la cuenta antes de ofrecerle algo

Un dato verificable en la primera línea (`personalizacion.md`) dice que la leímos. El diagnóstico dice
por qué le escribimos: qué le pasa hoy, qué le cuesta y por qué lo que ofrecemos lo resuelve. Sin
diagnóstico, el correo es una oferta a ciegas con el nombre de la cuenta pegado.

## Las cuatro piezas

| Pieza | Pregunta | Ejemplo (esqueleto) |
|---|---|---|
| Qué hacen | ¿Qué hacen y para quién? | «Forman a [público] con [formato].» |
| Hallazgo | ¿Qué se ve en sus propios datos que les cuesta? | «De sus últimos [n] videos, ninguno es corto, y la mediana es de [n] vistas.» |
| Por qué ahora | ¿Qué fecha reciente lo vuelve urgente? | «Su [evento] fue el [fecha].» |
| Propuesta a su medida | ¿Qué haríamos con su material o su tema, no con uno genérico? | «Sacar [piezas] de su [evento].» |

Cada pieza lleva la URL de donde salió, y el hallazgo se marca como **hecho** (está a la vista) o
**inferencia** (se deduce). Una inferencia no se escribe en el correo como si fuera un hecho: se plantea
como pregunta o se queda para la llamada.

## De dónde salen los hallazgos

Mejor un dato que se puede contar que un adjetivo:
- **Lo que publican y con qué frecuencia:** el feed público de su canal de video o de su pódcast (fechas,
  vistas, formato), su agenda de eventos, su blog con fechas.
- **Lo que dicen que les falta:** una vacante, una convocatoria, una queja pública, un aviso de «próximamente».
- **Lo que hacen a mano o tarde:** contenidos sin fecha reciente, secciones vacías, ligas rotas, un canal
  enlazado que ya no existe.

Cuida el alcance de cada dato: un feed que muestra los últimos 15 videos permite decir «en sus últimos 15
videos», no «nunca». Si el dato no alcanza para decir algo, no se dice.

## Quién hace qué, para gastar lo mínimo

1. **Un script** junta los hechos de cada cuenta (páginas propias, feeds públicos) y los guarda con su URL.
   Sin modelo.
2. **Un modelo local**, si lo hay, propone las cuatro piezas y un borrador a partir de esos hechos y del
   catálogo. Los datos de los prospectos no salen de la máquina.
3. **Una validación mecánica** marca lo que no cuadra: cifras o fechas del borrador que no están en los
   hechos ni en el catálogo.
4. **Claude audita** cada diagnóstico contra su fuente, corrige y escribe lo que sale. Lo que no se pudo
   comprobar queda marcado.

## Si no hay hallazgo

La cuenta no recibe un diagnóstico inventado. Queda «sin hallazgo» en el CRM, con la fecha. Si la mayoría
de una lista sale así, la lista está mal escogida o la oferta no les toca: díselo al usuario antes de seguir.
