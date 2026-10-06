# Activity 3 — Agente generador de rúbricas con OpenCode

Agente basado en **comandos y skills de OpenCode** que, dada una actividad
evaluable descrita en un documento de texto, genera un borrador de rúbrica de
evaluación en formato tabla Markdown.

## Entregables

### 1. Documento de diseño de la arquitectura

📄 **[docs/arquitectura.md](docs/arquitectura.md)**

Describe los componentes del agente, sus responsabilidades y el flujo de
ejecución:

- **Comando `/rubrica`** (`.opencode/commands/rubrica.md`): punto de entrada del
  usuario. Orquesta el flujo — leer el documento, preguntar el número de
  criterios y niveles, y producir la tabla final.
- **Skill `rubricas`** (`.opencode/skills/rubricas/SKILL.md`): conocimiento
  pedagógico reutilizable — cómo elegir criterios observables, redactar
  descriptores por nivel y asignar valores numéricos.

```
Usuario: /rubrica <documento>
   → 1. Lee y analiza la actividad
   → 2. Pregunta nº de criterios y niveles
   → 3. Propone criterios (skill rubricas)
   → 4. Redacta descriptores y valores por nivel
   → 5. Devuelve tabla Markdown
```

### 2. Implementación de los comandos y skills

| Archivo | Tipo | Función |
| --- | --- | --- |
| [`.opencode/commands/rubrica.md`](.opencode/commands/rubrica.md) | Comando | `/rubrica <documento>` — orquesta los 5 pasos del agente, recibe la ruta del documento vía `$ARGUMENTS`. |
| [`.opencode/skills/rubricas/SKILL.md`](.opencode/skills/rubricas/SKILL.md) | Skill | Directrices expertas para diseñar rúbricas: criterios observables, descriptores diferenciados, escala numérica y formato de tabla. |

**Uso:** abrir `opencode` en este directorio y ejecutar:

```
/rubrica examples/repte-1-ciberseguretat.md
```

### 3. Ejemplo de ejecución del agente

Ejecución real (OpenCode v2.0.18) sobre una actividad real: el *Repte 1* del
módulo *Fonaments de ciberseguretat* (Màster en ciberseguretat i privadesa,
UOC), convertido a Markdown desde el PDF original:

- 📄 Enunciado original: [`examples/3.pdf`](examples/3.pdf) →
  [`examples/repte-1-ciberseguretat.md`](examples/repte-1-ciberseguretat.md)
- 📄 Documentación completa de la sesión:
  [`examples/ejemplo-ejecucion-repte1.md`](examples/ejemplo-ejecucion-repte1.md)
- 📄 Ejemplo adicional con actividad de prueba:
  [`examples/ejemplo-ejecucion.md`](examples/ejemplo-ejecucion.md)

**Flujo de la ejecución:** el agente leyó el documento, identificó las ocho
sub-actividades del repte, cargó el skill `rubricas`, preguntó al usuario
(**6 criterios, 4 niveles**) y generó la siguiente rúbrica:

| Criterio | Insuficiente (1) | Suficiente (4) | Notable (7) | Sobresaliente (10) |
|---|---|---|---|---|
| **Selección y justificación de activos** | Omite categorías o selecciona activos que no corresponden al escenario. No justifica los activos esenciales con evidencias del enunciado. | Identifica algunos activos pertinentes, pero deja categorías relevantes incompletas o incluye selecciones poco adecuadas. Justifica los activos esenciales de forma genérica o parcial. | Selecciona activos pertinentes en las categorías y límites establecidos. Justifica los activos esenciales con fragmentos adecuados del enunciado, aunque alguna relación podría explicarse mejor. | Selecciona de forma completa y precisa los activos pertinentes, respetando las categorías y sus límites. Justifica cada activo esencial con evidencias concretas y claramente vinculadas a su elección. |
| **Categorización del sistema según el ENS** | No valora las dimensiones de seguridad o asigna una categoría sin relación con los impactos descritos. | Valora algunas dimensiones, pero omite otras o presenta inconsistencias que afectan a la categoría propuesta. | Valora de forma coherente las dimensiones aplicables a los activos esenciales y asigna una categoría razonable, con alguna imprecisión menor. | Valora de forma completa y coherente los impactos en las dimensiones de seguridad para los activos esenciales y justifica correctamente la categoría resultante del sistema. |
| **Selección y aplicación de amenazas** | Selecciona pocas amenazas o amenazas poco relevantes, y no establece relaciones comprensibles con los activos. | Selecciona amenazas parcialmente pertinentes o no completa las doce; relaciona algunas con activos, pero con omisiones o errores importantes. | Selecciona doce amenazas pertinentes y las relaciona con los activos afectados de forma generalmente coherente, con pocas asociaciones discutibles. | Selecciona las doce amenazas más relevantes para el contexto IT/OT y establece relaciones completas y precisas con los activos sobre los que tendrían mayor trascendencia. |
| **Análisis de riesgos** | No estima la probabilidad y el impacto para las tuplas activo-amenaza, o las valoraciones carecen de coherencia. | Analiza parte de las tuplas, pero las estimaciones de probabilidad o impacto son incompletas o débilmente relacionadas con el contexto. | Analiza las tuplas resultantes y estima probabilidad e impacto de manera mayoritariamente coherente, aunque algunas valoraciones requieren más fundamento. | Analiza todas las tuplas activo-amenaza con estimaciones diferenciadas y coherentes de probabilidad e impacto, atendiendo a las características y consecuencias para ADD. |
| **Selección y justificación de medidas de seguridad** | Selecciona menos de diez medidas o propone medidas no pertinentes; no las clasifica ni justifica adecuadamente. | Propone algunas medidas pertinentes, pero no completa las diez, incumple parcialmente las condiciones o presenta justificaciones genéricas. | Selecciona diez medidas del anexo II del ENS no mencionadas en el enunciado, las clasifica y justifica de forma adecuada, con alguna conexión al riesgo residual mejorable. | Selecciona y clasifica correctamente diez medidas elegibles del anexo II del ENS. Cada justificación, de un máximo de 150 palabras, vincula claramente la medida con la reducción del riesgo residual del sistema. |
| **Conclusiones y cumplimiento del entregable** | Las conclusiones están ausentes o no tratan el análisis realizado. El archivo no sigue los requisitos básicos de entrega. | Presenta conclusiones generales que abordan solo algunos aspectos solicitados. Cumple parcialmente el formato o los requisitos de entrega. | Reflexiona sobre la importancia y las implicaciones del análisis, las limitaciones de la herramienta y la aplicabilidad de MAGERIT. Entrega la hoja con el formato y los requisitos principales. | Presenta conclusiones claras y fundamentadas que abordan todos los aspectos solicitados y se apoyan en el trabajo realizado. Entrega la copia completa, con el nombre requerido y el enlace accesible. |

Puntuación máxima total: 60 puntos (6 criterios × 10 puntos).

## Estructura del repositorio

```
├── .opencode/
│   ├── commands/rubrica.md          # Comando /rubrica
│   └── skills/rubricas/SKILL.md     # Skill de diseño de rúbricas
├── docs/
│   └── arquitectura.md              # Documento de diseño
├── examples/
│   ├── 3.pdf                        # Enunciado real (PDF original)
│   ├── repte-1-ciberseguretat.md    # Enunciado convertido a Markdown
│   ├── actividad-ejemplo.md         # Actividad de prueba
│   ├── ejemplo-ejecucion-repte1.md  # Ejecución real documentada
│   └── ejemplo-ejecucion.md         # Ejecución con actividad de prueba
└── activity-3.md                    # Enunciado de la tarea
```
