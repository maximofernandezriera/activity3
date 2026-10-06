# Diseño de la arquitectura: agente generador de rúbricas

## Objetivo

Generar un borrador de rúbrica de evaluación (tabla Markdown) a partir de un
documento de texto que describe una actividad evaluable, usando una arquitectura
basada en **comandos y skills de OpenCode**.

## Componentes

La arquitectura se compone de dos elementos:

| Elemento | Tipo | Ubicación | Responsabilidad |
| --- | --- | --- | --- |
| `/rubrica` | Comando | `.opencode/commands/rubrica.md` | Orquestar el flujo completo: leer el documento, preguntar al usuario, invocar el skill y producir la tabla final. |
| `rubricas` | Skill | `.opencode/skills/rubricas/SKILL.md` | Aportar el conocimiento experto reutilizable: cómo elegir criterios pertinentes, redactar descriptores observables por nivel y asignar valores numéricos. |

### Comando `/rubrica`

- **Invocación:** `/rubrica <ruta-del-documento>`
- Recibe la ruta del documento mediante `$ARGUMENTS`.
- Es el **punto de entrada** del usuario: transforma una petición en una secuencia
  de pasos ordenados que el agente debe seguir.
- Garantiza el paso interactivo obligatorio: preguntar el número de criterios y
  de niveles antes de generar nada.

### Skill `rubricas`

- Encapsula el **criterio pedagógico**: qué hace que un criterio sea observable y
  evaluable, cómo redactar descriptores diferenciados por nivel y cómo
  distribuir los valores numéricos.
- Al estar definido como skill (y no incrustado en el comando), el conocimiento
  es **reutilizable** desde otros comandos o conversaciones, y el comando se
  mantiene corto y centrado en la orquestación.

## Flujo de ejecución

```
Usuario: /rubrica examples/actividad-ejemplo.md
        │
        ▼
1. El agente lee el documento y analiza la actividad
   (tipo de entregable, objetivos, aspectos evaluables).
        │
        ▼
2. Pregunta al usuario:
   - ¿Cuántos criterios? (ej. 4)
   - ¿Cuántos niveles?   (ej. 3)
        │
        ▼
3. Carga el skill `rubricas` y propone los criterios
   adecuados a la actividad.
        │
        ▼
4. Para cada criterio redacta los descriptores de cada
   nivel y asigna sus valores numéricos.
        │
        ▼
5. Devuelve la rúbrica como tabla Markdown:
   filas = criterios, columnas = niveles.
```

## Decisiones de diseño

- **Un solo comando, un solo skill.** El flujo es lineal; dividirlo en más
  comandos añadiría pasos manuales sin beneficio.
- **La interacción vive en el comando, el conocimiento en el skill.** Así el
  comando define *qué pasos* seguir y el skill define *cómo* hacerlos bien.
- **Salida solo Markdown.** El enunciado pide un borrador entregable; la tabla se
  devuelve en la respuesta para que el usuario pueda copiarla o iterar sobre
  ella.
