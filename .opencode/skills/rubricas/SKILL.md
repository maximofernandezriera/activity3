---
name: rubricas
description: Diseña rúbricas de evaluación para actividades académicas. Usar cuando se pida generar, proponer o revisar criterios de evaluación, niveles de logro o tablas de rúbrica.
---

# Skill: diseño de rúbricas de evaluación

Aplica estas directrices cuando debas generar una rúbrica de evaluación a partir
de la descripción de una actividad evaluable.

## Selección de criterios

- Deriva los criterios directamente del enunciado de la actividad: qué se
  entrega, qué objetivos persigue y qué aspectos son observables en la entrega.
- Cada criterio debe ser **observable y evaluable de forma independiente**
  (evita criterios que se solapen, como "calidad" y "excelencia").
- Usa formulaciones en forma de sustantivo o frase nominal breve
  (ej. "Claridad expositiva", "Uso de fuentes", "Corrección técnica").
- Respeta el número de criterios que haya indicado el usuario. Si el documento
  sugiere criterios evidentes, priorízalos.

## Niveles y descriptores

- Respeta el número de niveles indicado por el usuario. Nombra los niveles de
  forma coherente con la escala elegida (ej. "Insuficiente / Suficiente /
  Notable / Sobresaliente" para 4 niveles).
- Cada descriptor debe describir **qué aspecto tiene el trabajo en ese nivel**,
  con lenguaje observable y sin juicios vagos ("no incluye referencias" mejor
  que "mal trabajo de investigación").
- Entre niveles consecutivos debe haber una diferencia cualitativa clara y
  progresiva.

## Valores numéricos

- Asigna una puntuación a cada nivel dentro de cada criterio.
- Opción por defecto si el usuario no indica lo contrario: escala uniforme donde
  el nivel máximo vale 10 y los niveles intermedios se reparten de forma lineal
  (ej. 3 niveles → 10 / 6 / 2).
- Indica junto a cada nivel su etiqueta y su valor (ej. "Notable (8)").

## Formato de salida

- Devuelve **una única tabla Markdown**: primera columna "Criterio" y una
  columna por nivel.
- Cada celda contiene el descriptor del criterio en ese nivel.
- Si conviene, añade debajo una fila o nota breve con la ponderación o la
  puntuación máxima total.
