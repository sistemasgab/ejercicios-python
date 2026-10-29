# 04 — Archivo de gastos

**Nivel:** intermedio  
**Tiempo:** 40 min  
**Conceptos:** `pathlib`, `with`, leer y escribir texto, `encoding`

## Objetivo

Crear un archivo, leerlo y agregarle una línea nueva.

## Enunciado

Trabaja con `datos/gastos.txt`, relativo a la carpeta del ejercicio.
Cada línea tiene concepto y monto separados por coma, sin espacios:

```text
cafe,45.50
pan,22.00
```

El programa hace esto:

1. Crea la carpeta `datos` si no existe.
2. Si `gastos.txt` no existe, escríbelo con estas cinco líneas:

   ```text
   cafe,45.50
   pan,22.00
   taxi,80.00
   cafe,30.00
   fruta,18.75
   ```

3. Léelo y calcula el total.
4. Encuentra el concepto con mayor monto. Si hay empate, quédate con el
   primero que apareció.
5. Pide un concepto y un monto. El concepto no lleva comas ni se deja vacío.
   El monto tiene que ser mayor que 0. Si algo no vale, imprime `dato no valido`
   y no toques el archivo.
6. Si el dato vale, agrega una línea al final sin borrar lo anterior.

Imprime siempre, antes de pedir el dato nuevo:

```text
total: 196.25
mas_caro: taxi 80.0
```

`196.25` es la suma de las cinco líneas iniciales. Si el archivo ya existía
de una ejecución anterior, el total debe salir de lo que realmente hay dentro,
no de esos cinco números fijos.

Usa `with` para abrir el archivo y `encoding="utf-8"`.

## Listo cuando

- La primera ejecución crea el archivo.
- La segunda no lo deja solo con las cinco líneas originales: conserva lo que agregaste.
- Un monto `0`, negativo o texto no se escribe.
- Un concepto vacío o con coma no se escribe.

## Reto extra

Imprime también el total agrupado por concepto, una línea por concepto,
ordenada por nombre:

```text
cafe: 75.5
fruta: 18.75
pan: 22.0
taxi: 80.0
```

## Pista

`Path("datos/gastos.txt")` y `.parent.mkdir(parents=True, exist_ok=True)`
crean la carpeta. `"a"` agrega al final. `"r"` lee. Revisa
`.exists()` antes de sembrar las cinco líneas.
