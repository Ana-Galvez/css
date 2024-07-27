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

#### Pseudoclases
- :first-child   -(p:first-child) - selecciona el primer hijo p de cualquier elemento.   (section p:first-child) - selecciona el primer hijo p de cada section
- :first-of-type  -(p:first-of-type)  -selecciona el primer p de cada elemento
- :last-of-type   -(p:last-of-type)  -selecciona el último p de cada elemento
- :last-child    -(p:last-child)  - selecciona el último p de cualquier elemento
- :only-child    -(p:only-child)  - selecciona el p si es el único descendiente. No se considera único si hay nietos o más
- :only-of-type  - es como :only-child pero de un determinado elemento
- :not(selector)  -(:not(p))       - selecciona todos los selectores que no sean p
- :nth-child(parámetro) - (p:nth-child(número))  - selecciona los p según el número, si es 1 es el primer p de cada elemento.
                          -  (div p:nth-child(3)) - selecciona el tercer p desde el primer div incluyendo los tercer p que tengan sus hijos.
                          -   p:nth-child(even o odd) - selecciona los p pares o impares
                          - p:nth-child(5n) - selecciona desde el quinto p y sus múltiplos, 5,10,15, etc
                          - p:nth-child(4n+3) - selecciona el tercer p y va sumando 4,    3,7,11,15, etc
- :nth-of-type(parámetro) - (p:nth-of-type(even)) - selecciona los p que sean pares
- :nth-last-child(parámetro) - es como :nth-child() pero comienza desde el último elemento
- :nth-last-of-type(parámetro) - es como :nth-of-type pero comienza desde el último elemento
- :hover                - p:hover - al pasar el cursor por algún p
- :link       -a:link   - muestra los cambios en el texto del a antes de cliquear en el link
- :visited    -a:visited - muestra los cambios cuando ya se hizo click
- :focus      -input:focus  - al tener el foco el input
- :required   -input:required  -los input con atributo required
- :disabled  -input:disabled   -los input con atributo disabled
- :enabled   -input:enabled  -los input que no tienen el atributo disabled
- :optional  -input:optional  -los input que no tienen el atributo required
- :read-only  -input:read-only  -los inpput que tienen el atributo read-only
- :read-write -input:read-write  - los input que no tienen el atributo read-only
- :empty      -textarea:empty   -los textarea que no tengan texto al principio
- :checked    - si tiene el check en los input

#### Pseudoelementos
- ::first-line  - p::first-line  - selecciona la primera linea de cada párrafo
- ::first-letter  -p::first-letter  -selecciona la primera letra de cada párrafo
- ::selection  -p::selection   -el usuario al seleccionar una parte de algún párrafo
- ::placeholder  -input::placeholder  - selecciona el input antes de que el usuario escriba algo
- ::marker   -li::marker  -selecciona las viñetas o números de una lista

#### Atributos de selectores
- [atributo] -[target] -selecciona todos los elementos que tengan el atributo target
- [atributo="value"] - [target="_blank"] - selecciona todos los elementos que tengan el atributo target con valor _blank
- elemento[atributo="value"]  -p[class="parrafo-importante"]  - selecciona los p que tengan el atributo class con el valor parrafo-importante
- [atributo ^= "value"] - [class ^= "par"]  - selecciona las clases que comiencen con la palabra par(puede comenzar con palabra, letras, símbolos)
- [atributo $= "value"] - [class $= "e"] - selecciona las clases que terminan con e
- [atributo *= "value"] - [class *= "impo"] - selecciona las clases que comiencen, terminen o tengan en cualquier lado el valor impo
- [atributo |= "value"] - [class |= "parrafo"] -selecciona las clases que comiencen con la palabra EXACTA parrafo y aplicará los estilos si la clase se llama por ej parrafo-loquevenga(debe tener sí o sí -)
- [atributo ~= "value"] - [class ~= "parrafo-importante"] - selecciona las clases que tengan de valor EXACTO parrafo-importante (el value debe estar separado por espacios para que haga los estilos)
