# 07 — Consultar una API

**Nivel:** avanzado  
**Tiempo:** 40 min  
**Conceptos:** `urllib.request`, JSON, errores de red, códigos de salida

## Objetivo

Pedir datos a un servicio HTTP usando solo la librería estándar.

## Enunciado

Necesitas internet. No instales `requests`.

Escribe `obtener_json(url)`, que hace un GET con `urllib.request`, espera como
máximo 10 segundos y devuelve el JSON ya convertido a dict o lista.
La respuesta se decodifica como UTF-8.

El programa:

1. Pide `https://jsonplaceholder.typicode.com/users/1`
   e imprime nombre, correo y ciudad en tres líneas:

   ```text
   Leanne Graham
   Sincere@april.biz
   Gwenborough
   ```

   La ciudad está en `address` → `city`.

2. Pide `https://jsonplaceholder.typicode.com/users`
   e imprime cuántos usuarios hay y después sus nombres, ordenados, uno por línea.
   Son 10 usuarios.

Si ocurre `urllib.error.URLError` o `TimeoutError`, imprime `sin conexion` y
termina con `sys.exit(1)`.
Si ocurre `urllib.error.HTTPError`, imprime `respuesta 404` (con el código real)
y termina con `sys.exit(1)`.

No captures `Exception` pelón.

## Listo cuando

- Las dos URLs pasan por la misma función `obtener_json`.
- Cambias a propósito la primera URL a `/users/999` y ves `respuesta 404`.
- Con la red desconectada, o con una URL de un host inventado, ves `sin conexion` y el programa no muestra un traceback.

## Reto extra

Agrega un tercer pedido a
`https://jsonplaceholder.typicode.com/todos?userId=1`
y cuenta cuántos pendientes tienen `"completed": false`. Imprime
`pendientes: N`.

## Pista

`urllib.request.urlopen(url, timeout=10)` devuelve la respuesta.
Léela dentro de `with` y pasa los bytes a `json.loads`.
`HTTPError` es un caso distinto de "no hubo red": el servidor sí contestó,
pero con un código de error.
