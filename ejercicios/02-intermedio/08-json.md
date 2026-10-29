# 08 — Inventario JSON

**Nivel:** intermedio  
**Tiempo:** 45 min  
**Conceptos:** módulo `json`, persistencia, funciones sobre una lista de dicts

## Objetivo

Guardar un inventario en disco y volver a abrirlo.

## Enunciado

El archivo es `inventario.json`, en esta misma carpeta. Guarda una lista de
objetos con `sku`, `nombre` y `stock`. `stock` es un entero mayor o igual que 0.

Si el archivo no existe, el inventario empieza vacío.

Separa la lógica en funciones:

- `cargar(ruta)` devuelve la lista. Si el archivo no existe, devuelve `[]`.
- `guardar(ruta, productos)` escribe el JSON con `ensure_ascii=False` y
  `indent=2`, en UTF-8.
- `agregar(productos, sku, nombre, stock)` añade un producto.
  Si el `sku` ya existe, lanza `ValueError`. No guarda el archivo ella sola.
- `buscar(productos, sku)` devuelve el dict o `None`.

El programa principal ofrece este menú hasta `salir`:

- `ver`: una línea por producto, `SKU nombre (stock)`. Si no hay, `vacio`.
- `agregar`: pide sku, nombre y stock. Stock inválido o sku repetido imprime
  `no se pudo agregar` y no pierde lo que ya estaba cargado.
- `buscar`: pide sku e imprime el producto o `no encontrado`.
- `salir`: guarda y termina.

Cada `agregar` exitoso guarda de inmediato, para no perder datos si cierran
el programa a medias. `salir` también guarda.

## Ejemplo de archivo

```json
[
  {
    "sku": "A1",
    "nombre": "café",
    "stock": 4
  }
]
```

## Listo cuando

- Cierras el programa, lo vuelves a abrir y `ver` muestra lo que habías agregado.
- Un sku repetido no duplica la línea en el JSON.
- Los acentos del nombre se leen igual de como se escribieron.

## Reto extra

Agrega `retirar`. Pide sku y cantidad. Resta el stock si alcanza.
Si no alcanza o el sku no existe, imprime `no se pudo retirar` y no cambies el número.

## Pista

`json.dump` escribe y `json.load` lee. Ábrelos dentro de `with`.
`cargar` solo arma la lista en memoria; quien llama decide cuándo `guardar`.
