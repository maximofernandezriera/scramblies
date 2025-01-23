# scramblies

- https://www.codewars.com/kata/55c04b4cc56a697bb0000048

**El kata te pide determinar si una cadena s2 puede formarse reordenando algunos o todos los caracteres de otra cadena s1. Es decir, debes verificar que s1 contenga al menos la misma cantidad de cada carácter presente en s2.**

### Ejemplo
Si s2 = "aabb", s1 debe tener al menos 2 'a' y 2 'b' (sin importar el orden). Si s1 tiene menos de alguno, retornas false.

Las claved del kata:

- Longitud: Si len(s2) > len(s1), automáticamente false.

- Frecuencias: Compara la cantidad de cada carácter en s2 vs s1.

- Caracteres faltantes: Si s2 tiene un carácter que no existe en s1, false.

### 1. Longitud de las cadenas
Antes de analizar los caracteres, si s2 tiene más caracteres en total que s1, es imposible que s1 contenga todos los caracteres necesarios para formar s2.

Ejemplo:

s1 = "abc" (longitud 3)

s2 = "abcd" (longitud 4) → false (s2 es más larga).

### ¿Qué saco en claro?

Aunque s1 tenga los caracteres 'a', 'b', 'c', no puede generar s2 que requiere 4 caracteres.

Es un filtro rápido:

Si len(s2) > len(s1), puedes retornar false inmediatamente sin contar frecuencias.

### 2. Frecuencias de caracteres
Si s2 tiene igual o menor longitud que s1, debes comparar la cantidad de cada carácter en s2 con los disponibles en s1.

Ejemplo:

s1 = "aabbccc" (tiene: 2 'a', 2 'b', 3 'c')

s2 = "aaabbb" (requiere: 3 'a', 3 'b') → false

### ¿Qué saco en claro?

s1 solo tiene 2 'a' y 2 'b' (insuficientes para s2).

Cómo validar:

Contar frecuencias de cada carácter en s1 y s2.

Para cada carácter en s2:

Si el carácter no existe en s1 → false.

Si la cantidad en s1 es menor que en s2 → false.

Ejemplo:

s1 = "aaaabbbcc", s2 = "aabbc" → true (s1 tiene suficientes 'a', 'b', 'c').

### Caracteres faltantes en s1
Si s2 contiene algún carácter que no existe en s1, automáticamente es imposible formar s2 con s1, incluso si las frecuencias de otros caracteres son suficientes.

Ejemplo:

s1 = "abc" (tiene 'a', 'b', 'c')

s2 = "abx" (contiene 'x') → false

### ¿Qué saco en claro?

s1 no tiene 'x'.

Cómo validarlo:

Al contar las frecuencias de s1, verifica que todos los caracteres únicos de s2 estén presentes en s1.

Si hay al menos un carácter en s2 que no está en s1, retorna false.

## IMPORTANTE:
Es un prerrequisito antes de comparar frecuencias. Si s2 usa un carácter que s1 no tiene, no importa cuántos otros caracteres coincidan: la respuesta es false.

Ejemplo:

s1 = "aaaabbb" (no tiene 'c')

s2 = "aaabbc" → false (por el 'c').
