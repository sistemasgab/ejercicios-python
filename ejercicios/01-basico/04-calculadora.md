# 04 — Calculadora de dos números

**Nivel:** básico  
**Tiempo:** 25 min  
**Conceptos:** `+`, `-`, `*`, `/`, `//`, `%`, `**`

## Objetivo

Usar las operaciones aritméticas de Python y decidir cuándo una no aplica.

## Enunciado

Pide dos números decimales, `a` y `b`. Imprime estas líneas:

- `suma`
- `resta`, calculada como `a - b`
- `multiplicacion`
- `division`, la división real
- `division_entera`
- `residuo`
- `potencia`: `a ** b` solo si `b` es un entero entre 0 y 10, incluidos.
  Si no, imprime `potencia: omitida`.

`b` cuenta como entero cuando `b == int(b)`. Así `2.0` sí vale y `2.5` no.

## Ejemplo

Con `a = 5` y `b = 2`:

```text
suma: 7.0
resta: 3.0
multiplicacion: 10.0
division: 2.5
division_entera: 2.0
residuo: 1.0
potencia: 25.0
```

Con `b = 2.5` o `b = 12`, la última línea es `potencia: omitida`.
El resto de operaciones sí se imprime.

## Listo cuando

- Las siete líneas aparecen en ese orden.
- Probaste al menos un caso en el que la potencia se omite.

## Reto extra

Si `b` es `0`, no calcules la división ni el residuo. En esas dos líneas
imprime `indefinido`.

## Pista

`/` conserva el decimal. `//` se queda con la parte entera de la división.
`%` es lo que sobra. `**` es la potencia.
