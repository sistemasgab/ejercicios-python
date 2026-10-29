# 01 — Movimientos

**Nivel:** avanzado  
**Tiempo:** 40 min  
**Conceptos:** `dataclass`, anotaciones, `__post_init__`

## Objetivo

Modelar un movimiento de dinero con tipos y reglas que no se puedan saltar.

## Enunciado

Crea `Movimiento` con `@dataclass(frozen=True)` y estos campos anotados:

- `tipo: str`, solo `"ingreso"` o `"gasto"`
- `monto: float`, tiene que ser mayor que 0
- `categoria: str`, no puede ir vacía ni ser solo espacios

Si algo no cumple, `__post_init__` lanza `ValueError`.
Como el dataclass es congelado, un movimiento ya creado no se puede modificar.

Escribe, con anotaciones en parámetros y retorno:

- `balance(movimientos: list[Movimiento]) -> float`
  Suma ingresos y resta gastos.
- `por_categoria(movimientos: list[Movimiento]) -> dict[str, float]`
  Devuelve el neto de cada categoría: los ingresos suman y los gastos restan.

Ninguna de las dos imprime. No redondees: usa los montos tal cual.

En el programa principal crea estos movimientos, en este orden:

1. ingreso `1000` en `salario`
2. gasto `200` en `comida`
3. gasto `50` en `comida`
4. ingreso `300` en `venta`

Imprime el balance y después cada categoría ordenada por nombre, con su neto.

## Resultado esperado

```text
balance: 1050.0
comida: -250.0
salario: 1000.0
venta: 300.0
```

Comprueba también, atrapando `ValueError`, que fallan un gasto de monto `0`,
un tipo `"traspaso"` y una categoría `"   "`. Por cada fallo imprime `rechazado`.

```text
balance: 1050.0
comida: -250.0
salario: 1000.0
venta: 300.0
rechazado
rechazado
rechazado
```

## Listo cuando

- Las tres creaciones inválidas fallan dentro del dataclass, no en el `print`.
- `balance` y `por_categoria` declaran tipos.
- No se puede hacer `movimiento.monto = 1` sin que Python lance `FrozenInstanceError`.

## Reto extra

Agrega `resumen(movimientos: list[Movimiento]) -> str` que devuelva el mismo
texto de las cuatro primeras líneas, ya unido con saltos de línea. El programa
principal solo imprime lo que esa función devuelve.

## Pista

En un dataclass congelado, `__post_init__` todavía puede validar.
`object.__setattr__` no hace falta aquí: no vas a cambiar campos, solo a rechazarlos.
El neto de una categoría puede salir negativo.
