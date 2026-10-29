# 09 — Agenda

**Nivel:** básico  
**Tiempo:** 35 min  
**Conceptos:** `dict`, claves, `.get`, `.items()`

## Objetivo

Guardar pares nombre-teléfono y consultarlos desde un menú.

## Enunciado

Crea esta agenda:

```python
agenda = {
    "ana": "555-0101",
    "luis": "555-0188",
}
```

Repite un menú hasta que escriban `salir`. En cada vuelta pide una opción.

- `ver`: imprime cada contacto en su línea, `ana: 555-0101`.
- `buscar`: pide un nombre. Muestra el teléfono, o `no encontrado`.
- `agregar`: pide nombre y teléfono. Si el nombre ya existe, no lo cambies
  e imprime `ya existe`. Si es nuevo, guárdalo e imprime `agregado`.
- `salir`: termina sin imprimir nada más.
- Cualquier otro texto: `opcion no valida`.

Guarda y busca los nombres en minúsculas. Si escriben `Ana`, búscalo como `ana`.

## Ejemplo

```text
opcion: ver
ana: 555-0101
luis: 555-0188
opcion: buscar
nombre: ANA
555-0101
opcion: buscar
nombre: maria
no encontrado
opcion: agregar
nombre: Maria
telefono: 555-0142
agregado
opcion: salir
```

El orden de `ver` puede variar.

## Listo cuando

- `buscar` no truena cuando el nombre no está.
- `ver` recorre el diccionario. No hay un `print` fijo por cada contacto inicial.
- `agregar` no pisa un teléfono que ya existía.

## Reto extra

Agrega la opción `borrar`. Pide un nombre, lo elimina si existe e imprime
`borrado`. Si no existe, imprime `no encontrado`.

## Pista

`agenda.get("maria")` devuelve `None` cuando la clave no está.
Para recorrer: `for nombre, telefono in agenda.items()`.
Convierte el nombre con `.lower()` justo después de leerlo.
