# 03 — Errores de inventario

**Nivel:** avanzado  
**Tiempo:** 40 min  
**Conceptos:** excepciones propias, jerarquía, atributos del error

## Objetivo

Distinguir fallos de negocio con clases de error, no con textos sueltos.

## Enunciado

Crea esta jerarquía:

- `ErrorInventario(Exception)`, base de todos los fallos de este ejercicio.
- `SkuDuplicado(ErrorInventario)`, con atributo `sku`.
- `SkuNoEncontrado(ErrorInventario)`, con atributo `sku`.
- `StockInsuficiente(ErrorInventario)`, con atributos `sku`, `disponible` y `pedido`.

El mensaje de cada una puede ser corto. Lo importante es poder leer los
atributos en el `except`.

Crea `Inventario`. Por dentro guarda un diccionario `sku -> stock`.

- `agregar(sku, stock)` exige `stock` entero mayor o igual que 0.
  Si el sku ya existe, lanza `SkuDuplicado`.
- `retirar(sku, cantidad)` exige `cantidad` entera mayor que 0.
  Si el sku no está, lanza `SkuNoEncontrado`.
  Si la cantidad es mayor que el stock, lanza `StockInsuficiente` y no resta nada.

En el programa principal, sin menú:

1. Agrega `"A1"` con stock `5`.
2. Vuelve a agregar `"A1"` dentro de un `try`. Al capturar `SkuDuplicado`,
   imprime `sku duplicado: A1`.
3. Retira `2` de `"A1"`.
4. Intenta retirar `10` de `"A1"` y captura solo `StockInsuficiente`.
   Imprime `stock insuficiente: A1 disponible 3 pedido 10`.
5. Intenta retirar `1` de `"ZZ"` capturando la base `ErrorInventario`.
   Imprime `error de inventario: ZZ`.

Un `except Exception` no vale para estos tres casos. Cada `except` nombra
la clase que el enunciado pide.

## Resultado esperado

```text
sku duplicado: A1
stock insuficiente: A1 disponible 3 pedido 10
error de inventario: ZZ
```

Después de eso, el stock de `A1` sigue siendo `3`. Imprímelo en una cuarta línea:

```text
stock A1: 3
```

## Listo cuando

- `StockInsuficiente` también es un `ErrorInventario`. Puedes comprobarlo con
  `issubclass`.
- Retirar de más no modifica el stock.
- El caso de `ZZ` entra al `except ErrorInventario` sin una clase nueva en ese `except`.

## Reto extra

Agrega `CantidadInvalida(ErrorInventario)` y úsala cuando `stock` o `cantidad`
no cumplen las reglas numéricas, en lugar de un `ValueError` genérico.

## Pista

Puedes guardar datos en el error con `def __init__(self, sku, disponible, pedido)`.
Llama a `super().__init__(...)` para no perder el comportamiento de `Exception`.
Quien hace `except StockInsuficiente as error` lee `error.disponible`.
