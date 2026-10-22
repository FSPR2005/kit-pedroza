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
- Firma: <cómo firma y a quién se copia>
- Trato: tú | usted
- Cierre: <qué se pide al final, por ejemplo una llamada de 20 minutos>
- Aviso de privacidad: <liga>
- Medio para derechos ARCO: <correo o formulario que indica el aviso de privacidad>
- CRM: <dónde vive: hoja de cálculo, HubSpot, otro; nunca un repo>
- Dominio que envía: <para revisar DMARC antes de la primera tanda>
- Cuentas que lleva otra persona: <cuenta → con quién coordinarse>
- Regla para parar: <por ejemplo, 20 correos en 4 semanas; si no sale ninguna llamada, se cambia el método>
- Envío: uno por uno; se muestra el borrador en la sesión, con el id del contacto, y sale en cuanto la persona dice «va»
```

Lo que diga ese archivo manda sobre las plantillas de esta skill, pero no sobre «Lo que no se
negocia» ni sobre el envío uno por uno. Lo que no diga, se
pregunta una vez y se le propone al usuario agregarlo.
