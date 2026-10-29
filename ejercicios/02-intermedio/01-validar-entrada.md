# 01 — Validar entrada

**Nivel:** intermedio  
**Tiempo:** 30 min  
**Conceptos:** `try`, `except`, `ValueError`, bucles de reintento

## Objetivo

Pedir un dato hasta que sea un entero válido y usarlo.

## Enunciado

Pide un entero entre 1 y 10, incluidos.

- Si escriben texto que no es un entero, imprime `escribe un numero` y vuelve a preguntar.
- Si el entero está fuera de ese rango, imprime `fuera de rango` y vuelve a preguntar.
- `3.5` no es un entero: cuenta como `escribe un numero`.
- Cuando el número sea válido, imprime su tabla de multiplicar del 1 al 10.

No uses `except` sin un tipo de error. Atrapa solo `ValueError`.

## Ejemplo

```text
numero del 1 al 10: abc
escribe un numero
numero del 1 al 10: 3.5
escribe un numero
numero del 1 al 10: 12
fuera de rango
numero del 1 al 10: 4
4 x 1 = 4
4 x 2 = 8
4 x 3 = 12
4 x 4 = 16
4 x 5 = 20
4 x 6 = 24
4 x 7 = 28
4 x 8 = 32
4 x 9 = 36
4 x 10 = 40
```

## Listo cuando

- Un texto y un decimal no tumban el programa.
- `1` y `10` se aceptan.
- `0` y `11` se rechazan.
- La tabla sale de un bucle, no de diez `print` copiados.

## Reto extra

Limita los intentos fallidos a 5. Al sexto fallo imprime `demasiados intentos`
y termina sin mostrar la tabla.

## Pista

`int("3.5")` lanza `ValueError`. `int("4")` devuelve `4`.
Primero intenta convertir. Solo si eso funcionó, revisa el rango.
