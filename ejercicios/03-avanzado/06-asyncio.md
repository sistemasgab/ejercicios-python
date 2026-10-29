# 06 — Tareas concurrentes

**Nivel:** avanzado  
**Tiempo:** 40 min  
**Conceptos:** `async`, `await`, `asyncio.gather`, tiempo real

## Objetivo

Lanzar varias esperas juntas y comprobar que no se suman los tiempos.

## Enunciado

No uses red. La espera se simula con `asyncio.sleep`.

Escribe `preparar(nombre, segundos)`. Espera esos segundos y devuelve el texto
`"{nombre} listo"`.

Escribe dos corrutinas:

- `en_paralelo()` lanza a la vez `sopa` (1 s), `ensalada` (2 s) y `postre` (3 s)
  con `asyncio.gather`. Devuelve la lista de textos y la duración.
- `en_serie()` espera las mismas tres, una después de otra. Devuelve lo mismo.

Mide con `time.perf_counter`, justo antes de empezar y justo después de
terminar.

`main()` ejecuta las dos, imprime las listas y las duraciones con tres
decimales, y al final imprime `ok` si el paralelo duró menos de 4 segundos y
el serie duró más de 5.5. Si no, imprime `revisar tiempos`.

Arranca con `asyncio.run(main())`.

## Ejemplo de forma

Los decimales cambian un poco en cada máquina.

```text
paralelo: ['sopa listo', 'ensalada listo', 'postre listo'] 3.012
serie: ['sopa listo', 'ensalada listo', 'postre listo'] 6.021
ok
```

`gather` conserva el orden de las tareas que le pasaste, aunque `postre`
termine al último.

## Listo cuando

- La línea final es `ok` en una corrida normal, sin acortar los `sleep` para hacer trampa.
- En paralelo no escribes tres `await` seguidos.
- En serie no usas `gather`.

## Reto extra

Imprime también el orden en que terminan, usando `asyncio.as_completed`.
Ese orden sí sigue los tiempos: sopa, luego ensalada, luego postre.
No sustituye la lista de `gather`; es una impresión aparte.

## Pista

`await` dentro de una corrutina cede el control. `gather` agenda las tres
antes de esperar a que acaben. Por eso el tiempo del paralelo se parece al
de la tarea más larga, no a la suma.
