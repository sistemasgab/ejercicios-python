# 10 — Funciones reutilizables

**Nivel:** básico  
**Tiempo:** 35 min  
**Conceptos:** `def`, parámetros, `return`

## Objetivo

Sacar la lógica a funciones que devuelven un valor, sin imprimir dentro.

## Enunciado

Escribe estas funciones:

- `es_par(n)` devuelve `True` o `False`.
- `clasificar_temperatura(celsius)` devuelve `"frio"` si es menor que 15,
  `"templado"` si es menor que 25 y `"caliente"` en cualquier otro caso.
- `resumen(numeros)` devuelve un diccionario con las claves `total`,
  `promedio` y `maximo`. Si la lista está vacía, devuelve `None`.

En el programa principal, fuera de las funciones:

1. Imprime si `0`, `7` y `8` son pares, una línea por número:
   `0: True`
2. Imprime la clasificación de `10`, `15` y `30`:
   `10: frio`
3. Imprime el resumen de `[4, 8, 15, 16, 23, 42]`.
4. Imprime el resumen de `[]`.

No uses `print` dentro de las funciones.

## Resultados esperados

```text
0: True
7: False
8: True
10: frio
15: templado
30: caliente
{'total': 108, 'promedio': 18.0, 'maximo': 42}
None
```

`15` es templado porque la regla de frío es "menor que 15".

## Listo cuando

- Cada función hace una sola tarea y devuelve el resultado.
- El promedio no está escrito a mano.
- Las funciones no imprimen.

## Reto extra

Agrega `celsius_a_fahrenheit(c)`, que devuelve el valor convertido.
La fórmula es `(c * 9 / 5) + 32`.
Imprime la conversión de `[0, 20, 37, 100]`, una por línea.

## Pista

`return` entrega el valor a quien llamó la función. Quien imprime es el
programa principal. Un número es par cuando `n % 2 == 0`.
