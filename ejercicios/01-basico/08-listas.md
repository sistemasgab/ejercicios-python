# 08 — Lista de pendientes

**Nivel:** básico  
**Tiempo:** 30 min  
**Conceptos:** `list`, `append`, `insert`, `remove`, índices, `in`

## Objetivo

Modificar una misma lista paso a paso.

## Enunciado

Empieza con:

```python
pendientes = ["leer", "correr"]
```

Haz estos cambios sobre esa lista. Después de cada uno, imprime la lista:

1. Agrega `"estudiar"` al final.
2. Inserta `"desayunar"` al inicio.
3. Quita `"correr"`.
4. Sustituye el último elemento por `"repasar"`.
5. Pregunta una tarea. Si ya está en la lista, imprime `ya existe`.
   Si no está, agrégala e imprime `agregada`.
   Después imprime la lista otra vez.

La comparación distingue mayúsculas: `"Leer"` no es `"leer"`.

## Salida de los cuatro primeros pasos

```text
['leer', 'correr', 'estudiar']
['desayunar', 'leer', 'correr', 'estudiar']
['desayunar', 'leer', 'estudiar']
['desayunar', 'leer', 'repasar']
```

Si en el paso 5 escriben `leer`:

```text
ya existe
['desayunar', 'leer', 'repasar']
```

Si escriben `dormir`:

```text
agregada
['desayunar', 'leer', 'repasar', 'dormir']
```

## Listo cuando

- No armas una lista nueva escrita a mano en cada paso.
- `"correr"` desaparece por un método de lista, no porque hayas borrado la variable y creado otra.
- El paso 5 cubre el caso que ya existe y el caso nuevo.

## Reto extra

Antes de imprimir la lista del paso 5, ordénala alfabéticamente.
El mensaje `ya existe` o `agregada` se imprime igual.

## Pista

`append` agrega al final. `insert(0, valor)` pone un elemento al inicio.
`lista[-1]` es el último. `valor in lista` pregunta si ya está.
