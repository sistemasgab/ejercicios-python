# 04 — Notas en SQLite

**Nivel:** avanzado  
**Tiempo:** 50 min  
**Conceptos:** `sqlite3`, SQL parametrizado, `with`

## Objetivo

Guardar notas en una base local y consultarlas con funciones claras.

## Enunciado

Usa el archivo `notas.db` en esta carpeta. La tabla se llama `notas`:

| columna | tipo | regla |
| --- | --- | --- |
| `id` | INTEGER | llave primaria, la asigna SQLite |
| `titulo` | TEXT | obligatorio |
| `contenido` | TEXT | obligatorio |
| `creado` | TEXT | fecha y hora en ISO 8601, UTC |

Escribe funciones que reciben la conexión. Ninguna abre el archivo por su cuenta
y ninguna imprime.

- `iniciar(conexion)` crea la tabla si no existe.
- `crear(conexion, titulo, contenido) -> int` inserta y devuelve el `id`.
  `creado` sale de `datetime.now(timezone.utc).isoformat()`.
- `listar(conexion) -> list` devuelve las filas ordenadas por `id`.
- `actualizar_titulo(conexion, id, titulo) -> bool` cambia el título.
  Devuelve `True` solo si modificó una fila.
- `borrar(conexion, id) -> bool` devuelve `True` solo si borró una fila.

Las consultas arman los valores con `?`. No interpoles titulo ni contenido
dentro del texto SQL.

El programa principal abre la base una vez:

```python
with sqlite3.connect(RUTA) as conexion:
    ...
```

Dentro, en este orden: `iniciar`, crea tres notas
(`compra`, `idea`, `luego`), lista, cambia el título de la segunda a
`idea revisada`, borra la tercera, vuelve a listar.

Imprime cada listado como `id | titulo | contenido`. Separa los dos listados
con una línea `---`.

Puedes borrar `notas.db` cuando quieras empezar de cero. Si lo dejas, los
`id` siguen creciendo: el ejercicio no tiene que vaciar la tabla al arrancar.

## Ejemplo de forma

Los `id` dependen de lo que ya hubiera en el archivo. Con una base nueva se ve
así. La fecha va en la nota, pero no hace falta imprimirla en este programa.

```text
1 | compra | leche
2 | idea | escribir
3 | luego | archivar
---
1 | compra | leche
2 | idea revisada | escribir
```

Usa esos tres contenidos: `leche`, `escribir`, `archivar`.

## Listo cuando

- Ejecutarlo dos veces no truena y la segunda vez los `id` nuevos son mayores.
- `actualizar_titulo` de un `id` que no existe devuelve `False`.
- El título se manda como parámetro `?`. Una comilla en el texto no rompe la consulta.

## Reto extra

Agrega `buscar(conexion, texto)` que devuelva las notas cuyo título o contenido
contenga ese texto, sin distinguir mayúsculas. Sigue usando parámetros.

## Pista

`CREATE TABLE IF NOT EXISTS` evita el error al repetir `iniciar`.
`cursor.lastrowid` es el id que acaba de insertar.
`conexion.execute("... WHERE id = ?", (id,))` separa el SQL de los datos.
La coma en `(id,)` importa: un solo valor tiene que ir en una tupla.
