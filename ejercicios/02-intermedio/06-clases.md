# 06 — Libros

**Nivel:** intermedio  
**Tiempo:** 40 min  
**Conceptos:** `class`, `__init__`, métodos, `__str__`

## Objetivo

Representar un libro cuya página actual cambia al leer.

## Enunciado

Crea la clase `Libro` con:

- `titulo`, `autor` y `paginas` al construirla. `paginas` es el total y tiene
  que ser un entero mayor que 0. Si no, lanza `ValueError`.
- `pagina_actual`, que empieza en 0.
- `leer(n)` avanza `n` páginas. `n` tiene que ser un entero mayor que 0.
  Si al avanzar se pasaría del total, se queda en la última página.
  Devuelve cuántas páginas avanzó de verdad.
- `progreso()` devuelve el porcentaje de 0 a 100, con un decimal.
- `__str__` devuelve `titulo — autor (pagina_actual/paginas)`.

No imprimas dentro de la clase.

En el programa principal crea:

- `Libro("El túnel", "Ernesto Sabato", 160)`
- `Libro("Pedro Páramo", "Juan Rulfo", 128)`

Sobre el primero llama `leer(40)` y luego `leer(200)`.
Sobre el segundo llama `leer(128)`.
Imprime cada libro y su progreso en líneas separadas.

## Resultado esperado

```text
El túnel — Ernesto Sabato (160/160)
100.0
Pedro Páramo — Juan Rulfo (128/128)
100.0
```

Además, el primer `leer(40)` devuelve `40` y el `leer(200)` devuelve `120`,
porque solo faltaban 120 páginas. Compruébalo imprimiendo esos dos retornos
antes del resumen, así:

```text
avanzo: 40
avanzo: 120
El túnel — Ernesto Sabato (160/160)
100.0
Pedro Páramo — Juan Rulfo (128/128)
100.0
```

## Listo cuando

- Un libro de 0 páginas no se puede crear.
- `leer` no deja `pagina_actual` por encima de `paginas`.
- El texto sale de `__str__`, no de un método que imprima.

## Reto extra

Agrega `reiniciar()`, que vuelve `pagina_actual` a 0, y pruébalo con el
segundo libro. Imprime el libro otra vez después de reiniciarlo.

## Pista

`self` es el libro concreto sobre el que llamas el método.
`__str__` debe `return` un texto. Python lo usa cuando haces `print(libro)`.
