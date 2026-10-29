# 07 — Recorrer con for

**Nivel:** básico  
**Tiempo:** 25 min  
**Conceptos:** `for`, `range`, acumulador, `len`

## Objetivo

Recorrer una secuencia fija y sacar tres resúmenes.

## Enunciado

No pidas datos. Usa esta lista:

```python
ventas = [120, 80, 250, 40, 180, 90, 300]
```

Imprime:

1. Cada venta con su día, empezando en 1: `dia 1: 120`
2. El total.
3. El promedio con dos decimales.
4. Cuántas ventas fueron estrictamente mayores que 100.

## Ejemplo

```text
dia 1: 120
dia 2: 80
dia 3: 250
dia 4: 40
dia 5: 180
dia 6: 90
dia 7: 300
total: 1060
promedio: 151.43
mayores_a_100: 4
```

## Listo cuando

- Recorres `ventas` con `for`.
- El promedio sale de dividir el total entre `len(ventas)`, no de un número escrito a mano.
- El conteo de ventas mayores que 100 también sale del recorrido.

## Reto extra

Imprime el día de la venta más alta: `dia_maximo: 7`.
Si hubiera empate, quédate con el primer día.

## Pista

`for dia, venta in enumerate(ventas, start=1)` te da el número de día y el
valor en la misma vuelta. Para dos decimales puedes usar `round(promedio, 2)`
o un formato en la f-string.
