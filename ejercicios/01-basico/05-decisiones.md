# 05 — Decisiones

**Nivel:** básico  
**Tiempo:** 25 min  
**Conceptos:** `if`, `elif`, `else`, comparaciones, `and`, `or`

## Objetivo

Elegir un solo resultado a partir de varias condiciones.

## Enunciado

Pide la edad y si la persona tiene identificación. La respuesta de
identificación se acepta como `si`, `SI` o `Si`. Cualquier otro texto cuenta
como que no tiene.

Aplica estas reglas en este orden. Solo debe cumplirse una:

1. Si la edad es menor que 0 o mayor que 120, imprime `edad no valida`.
2. Si la edad es menor que 18, imprime `no puede votar`.
3. Si tiene 18 o más y respondió que sí tiene identificación, imprime `puede votar`.
4. En cualquier otro caso, imprime `necesita identificacion`.

## Ejemplos

| Edad | Identificación | Salida |
| --- | --- | --- |
| 17 | si | no puede votar |
| 18 | si | puede votar |
| 20 | no | necesita identificacion |
| -1 | si | edad no valida |
| 121 | no | edad no valida |

## Listo cuando

- Los cinco casos de la tabla salen como está escrito.
- La decisión principal es una sola cadena `if / elif / else`.

## Reto extra

Si la persona puede votar y tiene 65 años o más, la línea queda así:

```text
puede votar (fila preferente)
```

## Pista

Convierte la respuesta a minúsculas antes de compararla. Revisa primero el
caso imposible (edad fuera de rango) para no mezclarlo con las demás reglas.
