# 10 — Decoradores

**Nivel:** intermedio  
**Tiempo:** 40 min  
**Conceptos:** funciones como valores, `*args`, `functools.wraps`

## Objetivo

Envolver una función para registrar sus llamadas y rechazar números negativos.

## Enunciado

Crea una lista `historial` en el módulo. Cada llamada registrada agrega una
tupla `(nombre_de_la_funcion, args)`.

Escribe el decorador `registrar`. Después de cada llamada exitosa, o después
de una llamada que lanzó error, anota la tupla. Si la función lanza, el
decorador no se traga el error: lo vuelve a lanzar después de anotar.

Escribe el decorador `no_negativos`. Antes de llamar a la función, revisa sus
argumentos posicionales. Si alguno es `int` o `float` y es menor que 0, lanza
`ValueError` y no llama a la función. Los textos u otros tipos se ignoran.
El cero sí se permite.

Aplica los dos, en este orden de líneas, a `dividir(a, b)`:

```python
@no_negativos
@registrar
def dividir(a, b):
    ...
```

El decorador escrito más arriba queda por fuera. Así `no_negativos` revisa
antes y `registrar` solo ve las llamadas que sí pasan.

`dividir` devuelve `a / b`. Si `b` es 0, deja que ocurra `ZeroDivisionError`.
`registrar` anota la llamada aunque `dividir` falle, y después vuelve a
lanzar el mismo error. Anota `(nombre, args)` con el nombre de la función
original.

En el programa principal:

1. Imprime `dividir(10, 2)`.
2. Intenta `dividir(10, -1)` y, si hay `ValueError`, imprime `rechazado`.
3. Intenta `dividir(10, 0)` y, si hay `ZeroDivisionError`, imprime `division entre cero`.
4. Imprime `historial`.

## Resultado esperado

```text
5.0
rechazado
division entre cero
[('dividir', (10, 2)), ('dividir', (10, 0))]
```

`dividir(10, -1)` no entra al historial: `no_negativos` lo rechaza antes de
entrar a `registrar`. La división entre cero sí entra, porque llegó a ejecutarse.

Conserva el nombre original con `functools.wraps`.

## Listo cuando

- El historial queda exactamente con esas dos tuplas, en ese orden.
- `dividir.__name__` sigue siendo `"dividir"`.
- Un negativo no llega a ejecutarse.

## Reto extra

Invierte el orden de los decoradores para que `registrar` quede por fuera.
La llamada `dividir(10, -1)` también debe quedar en el historial.
En un comentario, explica por qué ese orden sí la alcanza a anotar.

## Pista

Un decorador recibe la función y devuelve otra. La de adentro acepta
`*args, **kwargs`, llama a la original y devuelve su resultado.
El decorador que está escrito más arriba es el que queda por fuera.
