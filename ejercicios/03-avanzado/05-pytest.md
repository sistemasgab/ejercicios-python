# 05 — Pruebas con pytest

**Nivel:** avanzado  
**Tiempo:** 40 min  
**Conceptos:** funciones puras, `pytest`, casos límite

## Objetivo

Fijar el comportamiento de una función con pruebas automáticas.

## Enunciado

En `descuentos.py` escribe solo esta lógica, sin `input` ni `print`:

`precio_final(precio, porcentaje) -> float`

- `precio` es el precio base y tiene que ser mayor o igual que 0.
- `porcentaje` es el descuento y tiene que estar entre 0 y 100, incluidos.
- Si alguno no cumple, lanza `ValueError`.
- El resultado es el precio ya descontado, redondeado a 2 decimales con `round`.

En `test_descuentos.py` cubre al menos estos casos:

| precio | porcentaje | resultado |
| --- | --- | --- |
| 100 | 10 | 90.0 |
| 50 | 0 | 50.0 |
| 80 | 100 | 0.0 |
| 19.99 | 15 | 16.99 |

Y estos rechazos, cada uno en su test, esperando `ValueError`:

- porcentaje `-1`
- porcentaje `100.1`
- precio `-0.01`

Para instalar y correr, desde esta carpeta:

```bash
python -m venv .venv
.venv/Scripts/python -m pip install pytest
.venv/Scripts/python -m pytest
```

`.venv/` es el entorno de este ejercicio. No hace falta activarlo si llamas
a ese `python` directo.

## Listo cuando

- `pytest` termina en verde con los siete tests.
- `descuentos.py` no depende de pytest.
- Un octavo caso que inventes, con descuento 50 sobre 10, da `5.0` sin tocar los tests viejos.

## Reto extra

Agrega un test parametrizado con `@pytest.mark.parametrize` que junte las
cuatro filas válidas de la tabla en una sola función de prueba.

## Pista

`19.99 * (1 - 15 / 100)` da `16.9915`, y `round(16.9915, 2)` da `16.99`.
`with pytest.raises(ValueError):` envuelve la llamada que debe fallar.
Cada comportamiento distinto merece su propia función `test_...`.
