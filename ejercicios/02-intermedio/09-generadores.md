# 09 — Generadores

**Nivel:** intermedio  
**Tiempo:** 35 min  
**Conceptos:** `yield`, generadores, pereza

## Objetivo

Producir valores de uno en uno, sin armar toda la lista por adelantado.

## Enunciado

Escribe dos generadores:

- `fibonacci(n)` produce los primeros `n` números de Fibonacci.
  Empieza en `0, 1`. Si `n` es 1, solo produce `0`. Si `n` es 0, no produce nada.
  Si `n` es negativo, lanza `ValueError`.
- `lotes(secuencia, tamano)` produce listas de hasta `tamano` elementos.
  El último lote puede venir más corto. `tamano` tiene que ser un entero mayor que 0.

No construyas de antemano la lista completa de Fibonacci para luego recorrerla.
El generador se va deteniendo en cada `yield`.

Imprime, un número por línea, el resultado de `fibonacci(8)`:

```text
0
1
1
2
3
5
8
13
```

Luego imprime cada lote de `lotes(range(7), 3)`:

```text
[0, 1, 2]
[3, 4, 5]
[6]
```

## Listo cuando

- `list(fibonacci(8))` es `[0, 1, 1, 2, 3, 5, 8, 13]`.
- `list(fibonacci(0))` es `[]` y `list(fibonacci(1))` es `[0]`.
- `lotes` no pierde el último elemento cuando la cantidad no es múltiplo del tamaño.

## Reto extra

Escribe `leer_lineas(ruta)` que haga `yield` de cada línea sin el salto final.
Úsalo para leer `datos/gastos.txt` del ejercicio de archivos, si ya existe,
e imprime solo las líneas. Si el archivo no está, imprime `sin archivo`.

## Pista

Un generador es una función con `yield`. Cuando el `for` pide el siguiente
valor, la función sigue desde donde se quedó. Para los lotes, acumula en una
lista temporal y entrégala al llegar al tamaño.
