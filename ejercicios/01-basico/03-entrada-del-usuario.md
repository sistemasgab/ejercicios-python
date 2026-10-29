# 03 — Entrada del usuario

**Nivel:** básico  
**Tiempo:** 20 min  
**Conceptos:** `input`, `int`, `float`, f-strings

## Objetivo

Pedir datos por teclado y usarlos en una frase.

## Enunciado

Pide tres cosas:

1. El nombre.
2. Cuántas horas durmió anoche. Puede llevar decimales.
3. Cuántos cafés tomó hoy. Tiene que ser un entero.

Muestra un resumen en una sola línea:

```text
Ana durmió 6.5 horas y tomó 2 cafés.
```

Todavía no valides números negativos. Si alguien escribe letras donde iba un
número, el programa puede fallar: eso se arregla en el nivel intermedio.

## Ejemplo

```text
¿Cómo te llamas? Ana
¿Cuántas horas dormiste? 6.5
¿Cuántos cafés tomaste? 2
Ana durmió 6.5 horas y tomó 2 cafés.
```

## Listo cuando

- Usas `input` tres veces.
- Horas y cafés se convierten a número antes de reutilizarlos.
- La frase final usa una f-string.

## Reto extra

Con una variable `horas_recomendadas = 8`, imprime cuántas horas faltaron o
sobraron respecto a lo que la persona durmió. Muestra un decimal.

## Pista

`input` siempre devuelve texto. `"6.5" + 1` falla. `float("6.5")` y
`int("2")` convierten ese texto a número.
