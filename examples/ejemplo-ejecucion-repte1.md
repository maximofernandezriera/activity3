# Ejemplo de ejecución con actividad real

Sesión real ejecutada con OpenCode v2.0.18 (modelo `github-copilot/gpt-6-luna`)
sobre una actividad real: el Repte 1 del módulo *Fonaments de ciberseguretat*
del Màster en ciberseguretat i privadesa (UOC), convertido a Markdown en
`examples/repte-1-ciberseguretat.md` a partir del enunciado original en PDF
(`examples/3.pdf`).

## 1. Invocación del comando

```
/rubrica examples/repte-1-ciberseguretat.md
```

El agente lee el documento y analiza la actividad:

> La actividad se entrega en una copia de la plantilla de Google Sheets
> «Anàlisi de riscos UOC» e incluye ocho partes: selección y justificación de
> activos, categorización ENS, selección y aplicación de amenazas, análisis de
> riesgos, medidas de seguridad y conclusiones. Se pueden evaluar, entre otros
> aspectos, la adecuación de las selecciones al contexto IT/OT, la justificación
> con evidencias del enunciado, la coherencia de las valoraciones de impacto y
> riesgo, la pertinencia de las medidas y la calidad de las conclusiones,
> además del cumplimiento del formato de entrega.

## 2. Interacción con el usuario

El agente carga el skill `rubricas` y pregunta:

- ¿Cuántos criterios de evaluación debe tener la rúbrica?
- ¿Cuántos niveles de logro?

Respuesta del usuario: **6 criterios y 4 niveles**.

## 3. Resultado: rúbrica generada

| Criterio | Insuficiente (1) | Suficiente (4) | Notable (7) | Sobresaliente (10) |
|---|---|---|---|---|
| **Selección y justificación de activos** | Omite categorías o selecciona activos que no corresponden al escenario. No justifica los activos esenciales con evidencias del enunciado. | Identifica algunos activos pertinentes, pero deja categorías relevantes incompletas o incluye selecciones poco adecuadas. Justifica los activos esenciales de forma genérica o parcial. | Selecciona activos pertinentes en las categorías y límites establecidos. Justifica los activos esenciales con fragmentos adecuados del enunciado, aunque alguna relación podría explicarse mejor. | Selecciona de forma completa y precisa los activos pertinentes, respetando las categorías y sus límites. Justifica cada activo esencial con evidencias concretas y claramente vinculadas a su elección. |
| **Categorización del sistema según el ENS** | No valora las dimensiones de seguridad o asigna una categoría sin relación con los impactos descritos. | Valora algunas dimensiones, pero omite otras o presenta inconsistencias que afectan a la categoría propuesta. | Valora de forma coherente las dimensiones aplicables a los activos esenciales y asigna una categoría razonable, con alguna imprecisión menor. | Valora de forma completa y coherente los impactos en las dimensiones de seguridad para los activos esenciales y justifica correctamente la categoría resultante del sistema. |
| **Selección y aplicación de amenazas** | Selecciona pocas amenazas o amenazas poco relevantes, y no establece relaciones comprensibles con los activos. | Selecciona amenazas parcialmente pertinentes o no completa las doce; relaciona algunas con activos, pero con omisiones o errores importantes. | Selecciona doce amenazas pertinentes y las relaciona con los activos afectados de forma generalmente coherente, con pocas asociaciones discutibles. | Selecciona las doce amenazas más relevantes para el contexto IT/OT y establece relaciones completas y precisas con los activos sobre los que tendrían mayor trascendencia. |
| **Análisis de riesgos** | No estima la probabilidad y el impacto para las tuplas activo-amenaza, o las valoraciones carecen de coherencia. | Analiza parte de las tuplas, pero las estimaciones de probabilidad o impacto son incompletas o débilmente relacionadas con el contexto. | Analiza las tuplas resultantes y estima probabilidad e impacto de manera mayoritariamente coherente, aunque algunas valoraciones requieren más fundamento. | Analiza todas las tuplas activo-amenaza con estimaciones diferenciadas y coherentes de probabilidad e impacto, atendiendo a las características y consecuencias para ADD. |
| **Selección y justificación de medidas de seguridad** | Selecciona menos de diez medidas o propone medidas no pertinentes; no las clasifica ni justifica adecuadamente. | Propone algunas medidas pertinentes, pero no completa las diez, incumple parcialmente las condiciones o presenta justificaciones genéricas. | Selecciona diez medidas del anexo II del ENS no mencionadas en el enunciado, las clasifica y justifica de forma adecuada, con alguna conexión al riesgo residual mejorable. | Selecciona y clasifica correctamente diez medidas elegibles del anexo II del ENS. Cada justificación, de un máximo de 150 palabras, vincula claramente la medida con la reducción del riesgo residual del sistema. |
| **Conclusiones y cumplimiento del entregable** | Las conclusiones están ausentes o no tratan el análisis realizado. El archivo no sigue los requisitos básicos de entrega. | Presenta conclusiones generales que abordan solo algunos aspectos solicitados. Cumple parcialmente el formato o los requisitos de entrega. | Reflexiona sobre la importancia y las implicaciones del análisis, las limitaciones de la herramienta y la aplicabilidad de MAGERIT. Entrega la hoja con el formato y los requisitos principales. | Presenta conclusiones claras y fundamentadas que abordan todos los aspectos solicitados y se apoyan en el trabajo realizado. Entrega la copia completa, con el nombre requerido y el enlace accesible. |

Puntuación máxima total: 60 puntos (6 criterios × 10 puntos).

## Trazabilidad de la sesión

Exportada con `opencode session export` (sesión `ses_eef198812ffejsdFLxfog59Xik`):

1. `read` → lectura de `examples/repte-1-ciberseguretat.md`.
2. Análisis de la actividad y preguntas al usuario (criterios y niveles).
3. `skill` → carga del skill `rubricas`.
4. Respuesta final → tabla Markdown anterior.
