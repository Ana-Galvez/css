# NOTAS SOBRE CSS

### Especificidad (Hay que tener en cuenta los tipos de selectores, excepto en inline que solo puede ser una etiqueta)
1. css inline
2. css internal
3. css external

### Importancia en la especificidad
1. IDs   vale 100
2. Clases, pseudoclases y selectores de atributos  vale 10
3. Elementos y pseudoelementos  vale 1

### Selectores avanzados
- selector  selector (section p) - cambiarán las propiedades de todos los DESCENDIENTES p de todos los section que haya.
- selector > selector (section > p) - cambiarán las propiedades de todos los HIJOS o DESCENDIENTES DIRECTOS p de todos los section que haya
- selector + selector (h1 + p) - cambiarán las propiedades del PRIMER hermano p después de h1
- selector ~ selector (h1 ~ p) - cambiarán las propiedades de TODOS los hermanos p después de h1
