# Ejemplo de ejecución del agente

Sesión real ejecutada con OpenCode v2.0.18 (modelo `github-copilot/gpt-6-luna`)
en el directorio del proyecto.

## 1. Invocación del comando

El usuario abre `opencode` en el directorio del proyecto y escribe:

```
/rubrica examples/actividad-ejemplo.md
```

El comando lee el documento `examples/actividad-ejemplo.md` (una práctica de
programación en Python) y analiza la actividad:

> La actividad se evalúa mediante un `.zip` con una aplicación de consola en
> Python para gestionar tareas con persistencia JSON y un `README.md`. Son
> observables el funcionamiento de las operaciones y el menú, la carga y el
> guardado de datos, la organización y el estilo del código, la documentación
> y el manejo de errores.

## 2. Interacción con el usuario

El agente pregunta mediante el diálogo interactivo de OpenCode:

- **¿Cuántos criterios de evaluación debe tener la rúbrica?** → `4`
- **¿Cuántos niveles de logro debe tener la rúbrica?** → `3`

## 3. Generación de la rúbrica

El agente carga el skill `rubricas`, propone los 4 criterios y redacta los
descriptores de los 3 niveles con sus valores numéricos.

## 4. Resultado: rúbrica generada

| Criterio | Insuficiente (2) | Suficiente (6) | Sobresaliente (10) |
|---|---|---|---|
| Funcionamiento y manejo de errores | El menú no permite realizar varias de las operaciones solicitadas (añadir, listar, completar o eliminar tareas), o los errores de entrada provocan fallos que impiden continuar. | El menú permite realizar las operaciones principales, aunque alguna presenta fallos o las entradas inválidas no siempre se gestionan sin interrumpir el programa. | El menú permite añadir, listar, completar y eliminar tareas correctamente; las entradas inválidas se gestionan y el programa continúa funcionando. |
| Persistencia en JSON | No se guardan o cargan correctamente las tareas desde `tareas.json`; los datos se pierden o no se recuperan al reiniciar. | Guarda y carga las tareas, pero hay fallos puntuales; el tratamiento de un fichero inexistente o corrupto es incompleto. | Guarda los cambios en `tareas.json` y los carga al iniciar; también contempla de forma adecuada un fichero inexistente o corrupto. |
| Organización y estilo del código | El código está poco organizado en funciones y se aparta notablemente de las convenciones PEP 8, dificultando su lectura. | El código está organizado en funciones, aunque algunas responsabilidades no están bien separadas o hay incumplimientos puntuales de PEP 8. | El código está organizado en funciones con responsabilidades claras y sigue de forma consistente las convenciones PEP 8. |
| Documentación y entrega | Falta el `README.md`, no explica cómo ejecutar el programa o el `.zip` no incluye los elementos necesarios. | El `.zip` incluye el código y el `README.md`, pero las instrucciones de ejecución o la descripción de la estructura son incompletas. | El `.zip` incluye el código fuente y un `README.md` con instrucciones claras para ejecutar el programa y una breve descripción de su estructura. |

Puntuación máxima total: 40 puntos (4 criterios × 10 puntos).

## Trazabilidad de la sesión

Exportada con `opencode session export` (sesión `ses_f023944d6ffenVKQyL5F1CGFY3`):

1. `read` → lectura de `examples/actividad-ejemplo.md`.
2. `question` → dos preguntas al usuario (criterios y niveles).
3. `skill` → carga del skill `rubricas`.
4. Respuesta final → tabla Markdown anterior.
