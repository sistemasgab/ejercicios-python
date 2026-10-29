# 08 — Gestor de tareas

**Nivel:** avanzado  
**Tiempo:** 90 min  
**Conceptos:** `argparse`, JSON, códigos de salida, juntar lo anterior

## Objetivo

Construir un programa de consola que guarda tareas entre una ejecución y otra.

## Enunciado

Un solo archivo, `08-proyecto-cli.py`. Sin librerías de terceros.
Los datos viven en `tareas.json`, en esta misma carpeta, con esta forma:

```json
{
  "siguiente_id": 1,
  "tareas": []
}
```

Cada tarea tiene `id` (entero), `texto` (str), `hecha` (bool) y `creada`
(fecha de hoy en ISO, solo la fecha, con `date.today().isoformat()`).

`siguiente_id` es el id que tocará en el próximo alta. Empieza en 1.
Cuando agregas, usas ese número y lo aumentas en 1. Borrar una tarea no
reutiliza su id.

Si el archivo no existe, empieza con la estructura vacía de arriba.
Si existe pero no tiene esa forma, imprime `archivo danado` en la salida de
error y termina con código 1. No lo repares en silencio.

Comandos, por `argparse`:

| comando | efecto |
| --- | --- |
| `agregar TEXTO` | crea una tarea pendiente |
| `listar` | muestra solo las pendientes |
| `listar --todas` | muestra pendientes y hechas |
| `completar ID` | marca `hecha` en true |
| `borrar ID` | la quita de la lista |

Salida de `listar`, una tarea por línea:

```text
[ ] 1  leer el enunciado
[x] 2  guardar el archivo
```

`[ ]` es pendiente y `[x]` es hecha. Un espacio, el id, dos espacios y el texto.
Si no hay nada que mostrar, imprime `sin tareas`.

Errores, siempre por la salida de error, con código 2:

- `agregar` con texto vacío o solo espacios: `texto vacio`
- `completar` o `borrar` de un id que no está: `no existe: 5`
- completar una que ya estaba hecha no es error: no cambia nada y no imprime

`agregar` y `completar` tampoco imprimen un mensaje de éxito. El usuario
lo comprueba con `listar`.

Guarda el JSON con UTF-8, `indent=2` y `ensure_ascii=False` después de cada
comando que cambie datos. `listar` no reescribe el archivo.

## Prueba a mano

Desde `03-avanzado`, con un `tareas.json` borrado antes de empezar:

```bash
python 08-proyecto-cli.py agregar "leer el enunciado"
python 08-proyecto-cli.py agregar "guardar el archivo"
python 08-proyecto-cli.py listar
python 08-proyecto-cli.py completar 2
python 08-proyecto-cli.py listar
python 08-proyecto-cli.py listar --todas
python 08-proyecto-cli.py borrar 1
python 08-proyecto-cli.py listar --todas
python 08-proyecto-cli.py completar 9
python 08-proyecto-cli.py agregar "   "
```

Las dos últimas terminan con código 2.
Después de `borrar 1`, un alta nueva recibe el id `3`, no el `1`.

## Listo cuando

- Cierras la terminal, vuelves a abrirla y `listar --todas` muestra lo mismo.
- Los id no se reciclan.
- `listar` sin tareas pendientes, habiendo una hecha, imprime `sin tareas`.
- El texto con acentos se guarda y se lee igual.

## Reto extra

Agrega `buscar PALABRA`. Lista las tareas, hechas o no, cuyo texto contiene
esa palabra sin distinguir mayúsculas. Si no hay coincidencias, `sin tareas`.

## Pista

`argparse` con subparsers da un comando por verbo.
Separa tres responsabilidades: cargar/guardar, operaciones sobre la lista
y el armado del parser. Así `completar` se puede probar sin pasar por la
terminal.
La salida de error en Python es `print(..., file=sys.stderr)`.
