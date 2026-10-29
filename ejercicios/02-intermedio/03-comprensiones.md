# 03 — Comprensiones

**Nivel:** intermedio  
**Tiempo:** 30 min  
**Conceptos:** listas por comprensión, diccionarios por comprensión, `sorted`

## Objetivo

Filtrar y transformar una lista de diccionarios sin bucles `for`.

## Enunciado

Parte de estos datos:

```python
alumnos = [
    {"nombre": "Ana", "curso": "python", "calificacion": 92},
    {"nombre": "Luis", "curso": "sql", "calificacion": 75},
    {"nombre": "Mara", "curso": "python", "calificacion": 88},
    {"nombre": "Leo", "curso": "python", "calificacion": 61},
    {"nombre": "Iris", "curso": "sql", "calificacion": 95},
]
```

Calcula, con comprensiones:

1. Los nombres de quien cursa `python` y tiene calificación mayor o igual
   que 70, ordenados alfabéticamente.
2. Un diccionario `nombre -> calificacion` solo de `python`.
3. El promedio de `sql`. Si no hubiera nadie en `sql`, el promedio es `None`.

Imprime los tres resultados, cada uno en su línea, con esta etiqueta:

```text
aprobados_python: ['Ana', 'Mara']
calificaciones_python: {'Ana': 92, 'Mara': 88, 'Leo': 61}
promedio_sql: 85.0
```

El orden de las claves del diccionario puede seguir el orden original.

No uses `for` ni `while` para armar esos tres resultados. Sí puedes usar
`sorted`, `sum` y `len`.

## Listo cuando

- Leo no aparece entre los aprobados, porque 61 es menor que 70.
- El promedio de sql es `(75 + 95) / 2`.
- Las tres transformaciones están hechas con comprensiones.

## Reto extra

Arma una lista de tuplas `(curso, promedio)` con un promedio por cada curso
distinto. Puedes obtener los cursos únicos primero. Imprímela ordenada por
nombre de curso.

## Pista

La forma general es `[expresion for elemento in secuencia if condicion]`.
Para diccionarios cambia las llaves: `{clave: valor for ...}`.
Filtra primero y ordena el resultado con `sorted`.
