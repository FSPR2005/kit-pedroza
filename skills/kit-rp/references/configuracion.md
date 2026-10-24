# Configuración por ámbito

La skill no sabe nada de ninguna empresa ni de ninguna persona. Cada perfil le dice lo
suyo en un archivo corto: `${CLAUDE_CONFIG_DIR:-$HOME/.claude}/contexto/RP-CATALOGO.md`.
Si no existe, pide estos datos antes de preparar el primer mensaje.

```markdown
# RP: configuración de este ámbito
- Ámbito: empresa | personal
- Catálogo: <ruta al catálogo de este ámbito>
- Territorio: <dónde sí se vende; lo demás se descarta>
- Remitente: <nombre visible y cuenta desde la que sale el correo>
- Firma: <cómo firma>
- Quién atiende las respuestas: <quién da el seguimiento; si es otra persona, va en copia visible>
- Copias fijas: <a quién se copia en cada correo y seguimiento; quien atiende las respuestas va en CC visible; una copia que solo sirve de archivo, como otra cuenta del mismo remitente, puede ir en CCO>
- Trato: tú | usted
- Cierre: <qué se pide al final, por ejemplo una llamada de 20 minutos>
- Caminos de venta: <marca propia al usuario final | línea blanca o maquila para otras marcas o cadenas; cada uno es una campaña con su catálogo, requisitos, lista y correo>
- Horario de envío: <por defecto, martes a jueves de 7:00 a 10:00 en la hora del destinatario; en negocios con mostrador, la hora con menos gente dentro de su horario>
- Aviso de privacidad: <liga al aviso integral; el simplificado va al pie del primer correo>
- Medio para derechos ARCO: <correo o formulario que indica el aviso de privacidad>
- CRM: <dónde vive: hoja de cálculo, HubSpot, otro; nunca un repo>
- Dominio que envía: <para revisar DMARC antes de la primera tanda>
- Cuentas que lleva otra persona: <cuenta → con quién coordinarse>
- Regla para parar: <por ejemplo, 20 correos en 4 semanas; si no sale ninguna llamada, se cambia el método>
- Envío: uno por uno; se muestra el borrador en la sesión, con el id del contacto, y con el «va» sale o se programa con «Programar envío» del propio correo, en el horario de arriba
```

Lo que diga ese archivo manda sobre las plantillas de esta skill, pero no sobre «Lo que no se
negocia» ni sobre el envío uno por uno. Lo que no diga, se
pregunta una vez y se le propone al usuario agregarlo.

## Cuando hay dos caminos de venta

Si el mismo producto se vende con marca propia al usuario final y también como línea blanca
o maquila para otras marcas o cadenas, son dos campañas. Cada una lleva su catálogo, sus
requisitos, su lista y su correo; nunca un correo que ofrezca las dos cosas.

En cadenas grandes (departamentales, supermercados), los requisitos públicos suelen ser:

- RFC y factura electrónica.
- Código de barras GS1.
- Etiquetado conforme a la NOM de su categoría; en textiles, la NOM-004-SE-2021.
  https://dof.gob.mx/normasOficiales/8934/seeco/seeco.html
- Intercambio electrónico de datos (EDI).
- Auditoría social o de capacidad vigente (SEDEX-SMETA, amfori BSCI, WRAP).
- Plazos de pago largos.

Fuentes: https://www.walmartmexico.com/proveedores/como-aplicar y
https://www.elpuertodeliverpool.mx/compras-responsables.html (revisadas el 2026-10-22).

La puerta de entrada es el comprador de la categoría. Para un proveedor chico, primero el
camino intermedio: proveedores que ya les venden, cadenas regionales y tiendas en línea.
Antes de escribirle a una cadena, marca en el catálogo qué requisitos ya se cumplen, con su
constancia; lo que falte no se ofrece como cumplido.
