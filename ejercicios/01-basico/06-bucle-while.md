# 06 — Repetir con while

**Nivel:** básico  
**Tiempo:** 30 min  
**Conceptos:** `while`, contador, acumulador

## Objetivo

Repetir una pregunta hasta que ocurra una condición de salida.

## Enunciado

Simula un cajero. El saldo inicial es `1000`.

En cada vuelta pregunta un monto a retirar.

- Si el monto es `0`, termina e imprime el saldo final.
- Si el monto es negativo, imprime `monto no valido` y vuelve a preguntar.
- Si el monto es mayor que el saldo, imprime `fondos insuficientes` y vuelve a preguntar.
- Si se puede retirar, resta el monto, imprime el saldo y sigue.

Limita el ciclo a 100 vueltas. Si se agotan, termina con la línea
`limite de operaciones` y después el saldo final. Cuenta como vuelta también
los montos inválidos.

El monto se lee como número decimal.

## Ejemplo

```text
Saldo: 1000
Monto a retirar (0 para salir): 200
Saldo: 800
Monto a retirar (0 para salir): 900
fondos insuficientes
Monto a retirar (0 para salir): 0
Saldo final: 800
```

## Listo cuando

- Salir con `0` deja el saldo correcto.
- Un retiro mayor que el saldo no lo vuelve negativo.
- En el código existe el tope de 100 vueltas.

## Reto extra

Cuenta cuántos retiros válidos hubo y muéstralo al salir:
`retiros: 1`.

## Pista

La condición del `while` puede ser "mientras no haya pedido salir y queden
vueltas". Dentro, decide con `if` qué hacer con el monto.
