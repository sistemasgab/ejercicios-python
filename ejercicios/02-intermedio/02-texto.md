# 02 — Normalizar texto

**Nivel:** intermedio  
**Tiempo:** 35 min  
**Conceptos:** métodos de `str`, `split`, conjuntos, funciones

## Objetivo

Limpiar una frase y sacar información de sus palabras.

## Enunciado

Pide una frase. Trabaja sobre una copia en minúsculas y quita estos signos
donde aparezcan: `. , ; : ! ?`

Después imprime:

1. El número de palabras. Las palabras se separan por espacios.
   Varios espacios seguidos cuentan como un solo separador.
2. Las palabras únicas, ordenadas alfabéticamente, separadas por coma y espacio.
3. El resultado de `es_palindromo` sobre la frase original, pero la función
   ignora espacios, mayúsculas y esos mismos signos.

`es_palindromo(texto)` devuelve `True` o `False`. No imprime.
Una cadena vacía, o una frase que se queda sin letras ni números, devuelve `False`.

Prueba aparte, con llamadas directas en el código, estas dos frases e imprime
el booleano:

- `Anita lava la tina` → `True`
- `python` → `False`

Esas dos pruebas van después del resumen de la frase que escribió el usuario.

## Ejemplo

Frase escrita: `Ana, Ana!`

```text
palabras: 2
unicas: ana
palindromo: True
True
False
```

`Ana, Ana!` es palíndromo porque, ya limpia, queda `anaana`.

## Listo cuando

- `Anita lava la tina` da `True` sin quitar las letras a mano.
- Las palabras únicas no repiten y salen ordenadas.
- La función no usa `print`.

## Reto extra

Ignora también los acentos al armar el palíndromo: `á` cuenta como `a`,
`é` como `e`, `í` como `i`, `ó` como `o` y `ú` como `u`. La `ñ` se queda igual.
Con esa regla, `Ánana` da `True`.

## Pista

Puedes ir reemplazando cada signo por nada con `.replace`.
`split()` sin argumentos ya junta los espacios de más.
Para el palíndromo, compara la cadena limpia con su reverso: `texto[::-1]`.
