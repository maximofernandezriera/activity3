---
description: Genera un borrador de rúbrica de evaluación a partir de un documento que describe una actividad evaluable
---

Genera un borrador de rúbrica de evaluación para la actividad descrita en el
documento: $ARGUMENTS

Sigue estos pasos en orden:

1. Lee el documento indicado y analiza la actividad evaluable que describe:
   tipo de entregable, objetivos y aspectos observables que se pueden evaluar.

2. Pregunta al usuario dos datos y espera su respuesta antes de continuar:
   - ¿Cuántos criterios de evaluación debe tener la rúbrica?
   - ¿Cuántos niveles de logro?

3. Usa el skill `rubricas` para proponer los criterios de evaluación adecuados
   a la actividad, en el número indicado por el usuario.

4. Para cada criterio, redacta la descripción de cada nivel de logro y asigna
   su valor numérico, siguiendo las directrices del skill.

5. Devuelve como resultado final una tabla Markdown con la rúbrica: primera
   columna "Criterio" y una columna por cada nivel, indicando en el encabezado
   la etiqueta del nivel y su valor numérico.
