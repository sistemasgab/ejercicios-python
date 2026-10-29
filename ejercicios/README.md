# Ejercicios de Python

Ruta para aprender Python desde cero hasta un programa de consola completo.
Cada archivo es la **descripción** de un ejercicio. La solución la escribes tú,
en un `.py` con el mismo nombre, en la misma carpeta.

Ejemplo: junto a `01-basico/01-primer-programa.md` crea
`01-basico/01-primer-programa.py`.

## Antes de empezar

Necesitas Python 3.10 o superior. En esta máquina, pruébalo así:

```bash
python --version
```

Si ese comando no existe, prueba `py --version`.

Ejecuta cada solución desde la carpeta del ejercicio:

```bash
python 01-primer-programa.py
```

## Cómo usar la ruta

1. Sigue el número de cada archivo. Cada ejercicio usa lo anterior.
2. Lee el enunciado completo antes de escribir código.
3. Cumple la sección **Listo cuando** antes de pasar al siguiente.
4. El **reto extra** es opcional.
5. Si te atoras, vuelve a intentarlo con la pista. No busques la solución hecha.

No hay soluciones en esta carpeta a propósito.

## Básico

El programa hace una cosa, con variables, decisiones, bucles y funciones.

| # | Ejercicio | Idea |
| --- | --- | --- |
| 01 | [Primer programa](01-basico/01-primer-programa.md) | `print` y comentarios |
| 02 | [Variables y tipos](01-basico/02-variables-y-tipos.md) | `int`, `float`, `str`, `bool` |
| 03 | [Entrada del usuario](01-basico/03-entrada-del-usuario.md) | `input` y conversiones |
| 04 | [Calculadora](01-basico/04-calculadora.md) | operadores aritméticos |
| 05 | [Decisiones](01-basico/05-decisiones.md) | `if`, `elif`, `else` |
| 06 | [Repetir con while](01-basico/06-bucle-while.md) | condición de salida |
| 07 | [Recorrer con for](01-basico/07-bucle-for.md) | `range` y acumuladores |
| 08 | [Lista de pendientes](01-basico/08-listas.md) | modificar una lista |
| 09 | [Agenda](01-basico/09-diccionarios.md) | diccionarios |
| 10 | [Funciones](01-basico/10-funciones.md) | `def` y `return` |

## Intermedio

El programa organiza datos, archivos y objetos.

| # | Ejercicio | Idea |
| --- | --- | --- |
| 01 | [Validar entrada](02-intermedio/01-validar-entrada.md) | `try` / `except` |
| 02 | [Normalizar texto](02-intermedio/02-texto.md) | cadenas y palíndromos |
| 03 | [Comprensiones](02-intermedio/03-comprensiones.md) | filtrar y transformar |
| 04 | [Archivo de gastos](02-intermedio/04-archivos.md) | leer y escribir texto |
| 05 | [Módulos](02-intermedio/05-modulos.md) | separar código en archivos |
| 06 | [Libros](02-intermedio/06-clases.md) | clases y métodos |
| 07 | [Figuras](02-intermedio/07-herencia.md) | herencia |
| 08 | [Inventario JSON](02-intermedio/08-json.md) | persistir datos |
| 09 | [Generadores](02-intermedio/09-generadores.md) | `yield` |
| 10 | [Decoradores](02-intermedio/10-decoradores.md) | envolver funciones |

## Avanzado

Tipos, errores de dominio, base de datos, pruebas y un proyecto.

| # | Ejercicio | Idea |
| --- | --- | --- |
| 01 | [Movimientos](03-avanzado/01-dataclasses.md) | `dataclass` y anotaciones |
| 02 | [Registro](03-avanzado/02-context-managers.md) | `with` propio |
| 03 | [Errores de inventario](03-avanzado/03-excepciones.md) | excepciones propias |
| 04 | [Notas en SQLite](03-avanzado/04-sqlite.md) | base de datos local |
| 05 | [Pruebas con pytest](03-avanzado/05-pytest.md) | tests automáticos |
| 06 | [Tareas concurrentes](03-avanzado/06-asyncio.md) | `asyncio` |
| 07 | [Consultar una API](03-avanzado/07-api.md) | HTTP con la librería estándar |
| 08 | [Gestor de tareas](03-avanzado/08-proyecto-cli.md) | proyecto de consola |

Cuando termines un bloque, se pueden revisar tus `.py` y ajustar el siguiente
ejercicio a lo que ya te salió bien.
