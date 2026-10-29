# 02 — Variables y tipos

**Nivel:** básico  
**Tiempo:** 20 min  
**Conceptos:** variables, `int`, `float`, `str`, `bool`, `type`

## Objetivo

Guardar datos en variables y reconocer de qué tipo son.

## Enunciado

Define estas cuatro variables:

- `nombre`: texto
- `edad`: número entero
- `altura_m`: número decimal
- `estudia_python`: `True` o `False`

Imprime cada una en su propia línea, con este formato:

```text
nombre: Ana (str)
```

El tipo sale de `type(variable).__name__`. Si cambias el valor de una
variable, la línea impresa debe cambiar sin que tengas que reescribir el
`print`.

## Ejemplo

```text
nombre: Ana (str)
edad: 28 (int)
altura_m: 1.68 (float)
estudia_python: True (bool)
```

## Listo cuando

- Existen las cuatro variables con los cuatro tipos pedidos.
- Cada línea se arma con la variable, no con el valor copiado otra vez dentro del texto.

## Reto extra

Guarda el año actual en `anio_actual`. Calcula `anio_nacimiento` restando
`edad`. Imprímelo con el mismo formato y su tipo.

## Pista

Una variable es un nombre pegado a un valor. `type(edad)` devuelve el tipo;
`.__name__` devuelve solo la palabra `int`, `float`, `str` o `bool`.
