# 02 — Registro con context manager

**Nivel:** avanzado  
**Tiempo:** 40 min  
**Conceptos:** `__enter__`, `__exit__`, `with`

## Objetivo

Abrir un recurso, usarlo y cerrarlo aunque haya un error.

## Enunciado

Crea la clase `Registro`. Se construye con una ruta (`pathlib.Path` o `str`).

- Al entrar al `with`, abre el archivo en modo escritura de texto, UTF-8,
  escribe la línea `-- inicio --` y devuelve el propio registro.
- `linea(texto)` escribe ese texto en una línea nueva. Si el registro no está
  abierto, lanza `RuntimeError`.
- Al salir, escribe `-- fin --` y cierra el archivo. Esto ocurre también cuando
  el bloque lanzó una excepción.
- `__exit__` no se traga el error. Quien llamó sigue viendo la excepción.

Cada uso del `with` reescribe el archivo desde cero, no agrega a uno viejo.

Demostración:

```python
from pathlib import Path

ruta = Path("registro.txt")
try:
    with Registro(ruta) as registro:
        registro.linea("uno")
        registro.linea("dos")
        raise RuntimeError("fallo de prueba")
except RuntimeError:
    print("atrapado")

print(ruta.read_text(encoding="utf-8"), end="")
```

## Resultado esperado

En pantalla:

```text
atrapado
-- inicio --
uno
dos
-- fin --
```

Y el archivo `registro.txt` queda con ese mismo contenido.

## Listo cuando

- Quitas el `raise` y el archivo igual termina con `-- fin --`.
- Pones el `raise` antes de `linea("dos")` y `dos` no aparece, pero `-- fin --` sí.
- Llamar `linea` fuera del `with` lanza `RuntimeError`.

## Reto extra

Guarda en el registro cuántos segundos estuvo abierto el `with`, en una última
línea `duracion: 0.001` (los decimales pueden variar). Mide con
`time.perf_counter` entre `__enter__` y `__exit__`.

## Pista

`__exit__` recibe el tipo de la excepción, el error y el traceback.
Si no hubo error, el tipo llega como `None`. Devolver `False`, o no devolver
nada, deja que el error siga su camino. Devolver `True` lo escondería.
