# 05 — Módulos

**Nivel:** intermedio  
**Tiempo:** 35 min  
**Conceptos:** `import`, separar funciones, `__name__`

## Objetivo

Mover funciones a otro archivo y usarlas desde el programa principal.

## Enunciado

Crea dos archivos en esta misma carpeta:

`conversiones.py` solo define funciones. No pide datos y no imprime.

- `celsius_a_fahrenheit(c)` → `(c * 9 / 5) + 32`
- `km_a_millas(km)` → `km * 0.621371`
- `minutos_a_hhmm(minutos)` → texto. `65` se vuelve `1 h 05 min`.
  `5` se vuelve `0 h 05 min`. Los minutos del reloj van siempre con dos dígitos.
  Si `minutos` es negativo, lanza `ValueError`.

`05-modulos.py` pide qué conversión quieren y el valor.
Opciones: `f`, `k` o `t` (de tiempo). Luego pide el número.

Imprime el resultado con dos decimales en temperatura y distancia.
El tiempo se imprime con el texto de la función.

Si la opción no es `f`, `k` o `t`, imprime `opcion no valida` y termina.
Si los minutos son negativos, deja que se vea el `ValueError`: todavía no
hace falta atraparlo.

## Ejemplo

```text
conversion (f, k, t): t
valor: 65
1 h 05 min
```

```text
conversion (f, k, t): f
valor: 100
212.00
```

## Listo cuando

- `conversiones.py` no tiene `input` ni `print`.
- El programa principal obtiene las funciones con `import`, no las copia.
- Ejecutas `python 05-modulos.py` desde `02-intermedio`.

## Reto extra

Agrega en `conversiones.py` el bloque:

```python
if __name__ == "__main__":
    ...
```

Cuando alguien ejecute ese archivo directo, muestra tres ejemplos fijos:
0 °C, 1 km y 125 minutos. Cuando se importa desde el otro programa, esos
ejemplos no se imprimen.

## Pista

`from conversiones import celsius_a_fahrenheit, km_a_millas, minutos_a_hhmm`
trae solo lo que necesitas. Las horas son `minutos // 60` y los minutos que
sobran son `minutos % 60`.
