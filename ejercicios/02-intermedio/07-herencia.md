# 07 — Figuras

**Nivel:** intermedio  
**Tiempo:** 35 min  
**Conceptos:** herencia, `super()`, métodos compartidos

## Objetivo

Hacer que varias clases distintas respondan al mismo método.

## Enunciado

Crea `Figura` con un método `area()`. Ese método lanza `NotImplementedError`.

Crea `Rectangulo(Figura)` con `ancho` y `alto`. Los dos tienen que ser
mayores que 0; si no, `ValueError`. Su área es `ancho * alto`.

Crea `Circulo(Figura)` con `radio`, también mayor que 0.
Su área es `math.pi * radio ** 2`.

Escribe `imprimir_areas(figuras)`. Recibe una lista de figuras, no sabe si
cada una es rectángulo o círculo, y para cada una imprime la clase y el área
con dos decimales:

```text
Rectangulo: 12.00
Circulo: 28.27
```

Pruébala con un rectángulo de 3 por 4 y un círculo de radio 3.
`28.27` sale de redondear `math.pi * 9` a dos decimales.

Cada clase define su propio `__str__` o, si prefieres, `imprimir_areas`
usa `figura.__class__.__name__`. No hace falta guardar el nombre a mano.

## Listo cuando

- `imprimir_areas` no pregunta `isinstance` para decidir la fórmula.
- Crear un rectángulo con ancho `0` falla.
- Llamar `Figura().area()` lanza `NotImplementedError`.

## Reto extra

Agrega `Cuadrado(Rectangulo)`. Su constructor solo recibe `lado` y reutiliza
el de `Rectangulo`. Un cuadrado de lado 5 imprime `Cuadrado: 25.00`.

## Pista

La clase hija declara `class Rectangulo(Figura)`.
Dentro de `Cuadrado.__init__`, `super().__init__(lado, lado)` manda los dos
lados al rectángulo. Quien llama `area()` obtiene la versión de la clase real
del objeto.
