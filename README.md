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
- :valid   - input[type="email"]:valid - a los input tipo email se le aplicarán los estilos si lo escrito está dentro de las validaciones de un email (en el caso html caracteres@caracteres)
- :invalid -input[type="email"]:invalid -a los input tipo email se le aplicarán los estilos si lo escrito está fuera de las validaciones de un email (en el caso html caracteres@caracteres)
- :target  - #link:target - aplicará los estilos cuando en el href de una etiqueta a tenga #link

#### Pseudoelementos
- ::first-line  - p::first-line  - selecciona la primera linea de cada párrafo
- ::first-letter  -p::first-letter  -selecciona la primera letra de cada párrafo
- ::selection  -p::selection   -el usuario al seleccionar una parte de algún párrafo
- ::placeholder  -input::placeholder  - selecciona el input antes de que el usuario escriba algo
- ::marker   -li::marker  -selecciona las viñetas o números de una lista
- ::before  -li::before{content:"texto"} - agregará el texto al principio de los textos de los li
- ::after -li::after{content:"texto"} - agregará el texto al final de los textos de los li
    - Para poner texto en el medio de otro texto se puede usar la etiqueta span

#### Selectores de atributos
- [atributo] -[target] -selecciona todos los elementos que tengan el atributo target
- [atributo="value"] - [target="_blank"] - selecciona todos los elementos que tengan el atributo target con valor _blank. ATENCIÓN: Si el value tiene palabras con espacios, se deben escribir todas, sino no aplicará los estilos.
- elemento[atributo="value"]  -p[class="parrafo-importante"]  - selecciona los p que tengan el atributo class con el valor parrafo-importante. ATENCIÓN: Si el value tiene palabras con espacios, se deben escribir todas, sino no aplicará los estilos.
- [atributo ^= "value"] - [class ^= "par"]  - selecciona las clases que comiencen con la palabra par(puede comenzar con palabra, letras, símbolos)
- [atributo $= "value"] - [class $= "e"] - selecciona las clases que terminan con e
- [atributo *= "value"] - [class *= "impo"] - selecciona las clases que comiencen, terminen o tengan en cualquier lado el valor impo
- [atributo |= "value"] - [class |= "parrafo"] -selecciona las clases que comiencen con la palabra EXACTA parrafo y aplicará los estilos si la clase se llama por ej parrafo-loquevenga(debe tener sí o sí -)
- [atributo ~= "value"] - [class ~= "parrafo-importante"] - selecciona las clases que tengan de valor EXACTO parrafo-importante. Si el value tiene palabras separadas con espacios, con que solo aparezca una, aplicará los estilos.

#### Selector Universal *
- *{
  font-size : 2rem;
}
Aplica a toda la página, aunque luego si algún elemento usa font-size, su valor va a cambiar.

- div *{
  font-size : 2rem;
}
Aplica a todos los elementos que estén adentro del div.

### Posicionamiento
1. position:static;   -  es el valor por defecto, y no cambia su posición aunque usemos las propiedades left, right, top o bottom.
2. position:relative  -  permite el uso de left, top, right y bottom, pero le da prioridad a left y top. Además al mover el elemento, su lugar original es ocupado por otro elemento.
3. position:absolute  -  para que sea relativo al padre, el padre o ascendentes deben tener position:relative o position:fixed. Si no hay ascendentes con relative o fixed, será relativo al html ( no body).    Permite el uso de left, top, right y bottom, pero le da prioridad a left y top. Además al mover el elemento, su lugar original no es ocupado por otro elemento.
4. position:fixed  - el elemento siempre queda a la vista, aunque se haga scroll. Es relativo a la pantalla. No mueve los demás elementos.
5. position:sticky  - es como una mezcla de relative y fixed. Se deben usar top o bottom para decirle al elemento sticky cuando queda fijo en la pantalla, mientras no llegue a esa altura se comporta como si fuera relative. Esa altura será según el body si el sticky es hijo directo. Si es hijo de otro elemento, este elemento debe tener tamaño fijado o no va a funcionar y el sticky solo se va a mantener mientras se vea el alto del elemento padre.

### Display
1. display: inline - ocupan el espacio de su contenido, si hay 2 elementos inline detrás de otro, en la página aparecen juntos en la misma línea. No permiten modificar su tamaño. Padding y margin solo de forma horizontal, o sea margin-left o margin-right. Vertical no funciona.
2. display: block  - ocupan todo el width, siempre van a estar en líneas diferentes. Permiten modificar su tamaño, todos los padding y todos los margin.
3. display: inline-block  - se comporta como inline pero se le puede modificar el tamaño y todos los padding y margin.
4. display: none - el elemento se oculta para la vista del usuario y los otros elementos ocupan su lugar, pero en el código html aparece, o sea el elemento con display:none igualmente se carga.
5. display: list-item  - este display lo utilizan los li. Con la propiedad y valor list-style-position: inside en algún elemento lo transforma como una lista, pone viñeta.
6. display: table/table-row/table-cells  - estos display y todos los que comienzan con table, los usan las etiquetas de tabla, pero se puede usar para maquetar otros elementos.

### Colores
1. Con nombre: css proporciona casi 140 colores con solo poner su nombre como valor. ej color: blue.
2. Hexadecimal: conjunto de 6 caracteres comenzando con #, las letras de a a f y números de 0 a 9, pudiendose combinarlos, si el código hexadecimal son los mismos números o letras solo se ponen 3 o también si cada par es la misma letra o número. Los 2 primeros pertenecen al red, el tercero y cuarto al verde y los 2 últimos al azul.
Ej: #afd356, #fff, #fe0, #000, #3d5a8b.  los más cercanos a f van tirando a claro, mientras que a 0, van tirando a oscuro. TAMBIÉN HAY hexadecimales con 8 caracteres y 4 caracteres. Las 2 últimas representan el alpha u opacidad. 00 sería oscuro y 99 más cercano al color original para 8 caracteres y de 0 a 1 para 4 caracteres. Ej: #3d5a8b, #ac45.
3. RGB: se forma en 3 conjuntos y cada conjunto puede ser de 0 a 255, el primero es para la tonalidad de rojo (red), el segundo para el verde (green) y el tercero para el azul (blue). por eso RGB.
ej: rgb(34, 234, 56). Cuanto más cerca de 255 se acerca a la tonalidad dependiendo al conjunto que pertenezca. Ej rgb(0,255,0) es el verde puro porque los demás tienen 0. Si los 3 tienen 0 va a ser negro, si los 3 tienen 255 va a ser blanco.
4. RGBA: igual que rgb, y la A se refiere al alpha, que sería la opacidad de 0 a 1 ej rgb(34,212,89, 0.4) sería 40% de opacidad.
5. HSL: hue-saturation-lightness: tono-saturación-luminosidad - El hue o tono se basa en un círculo cromático. El tono es por grados °. Cada 60 grados hay un tono diferente 0° rojo 60° amarillo 120° verde 180° cyan 240° azul 300° magenta. La saturación es la intensidad del color: 0% escala de grises al 100% color puro. La luminosidad 0% negro al 100% blanco.  ej: hsl(0,100%,50%). Los grados no se ponen. Sería un rojo puro. hsl(120,100%,50%) verde puro. Son 360 tonos que pertenecen a cada grado.
6. HSLA: igual que HSL siendo A la opacidad. de 0 a 1. ej hsla(34,55%,18%, 0.4).

### Unidades de medidas
1. Absolutas: son las unidades fijas. cm (centímetros), mm (milímetros), pc (picas), in(pulgadas) 96 px o 2.56 cm, pt(puntos que equivale a 1/72 in) y la más usada px (pixeles) equivale a 1/96 in, Q (cuartos de milímetros 1/40 de cm)
2. Relativas:
  1. Al tamaño de la fuente:
    1. em: se basa en el ancho de la letra m (que es la más ancha de las letras) de la propiedad font-size del elemento si lo tiene en pixeles. Si el elemento no tiene asignada esa propiedad, se va a basar en su primer antecesor que tenga esa propiedad en pixeles. Y si ningún antecesor lo tiene, lo toma del body si le hemos puesto la propiedad font-size en pixeles, sino lo toma de la etiqueta html que si no le ponemos la propiedad font-size va a ser de 16px. Ahora, cualquier propiedad del elemento que use em, se va a basar en el font-size del elemento, aunque el font-size sea en em. Si el font-size del elemento es 2em, y se basa en el html que es 16px, quiere decir que si al elemento le agregamos un border: 1em solid red; este 1em va a valer 32px, porque en el mismo elemento el font-size es 2em siendo cada em 16px.
    2. rem: se basa en el ancho de la letra m de la propiedad font-size del elemento raiz (html). Si la etiqueta html no tiene escrito por nosotros el font-size, entonces será de 16px. No importa si hay ascendientes con font-size, siempre va a tomar de la etiqueta html.
    3. ex: se basa en la altura de la letra x del font-size del elemento, sino del padre. Se maneja igual que el em pero con altura.
    4. rex: igual que ex pero tomando la altura de la etiqueta html.
    5. ch: se basa en la anchura del 0 cero de la fuente del elemento. Sirve si se quiere realizar algo que esté contado por caracteres.
    6. rch: igual que ch pero tomando la anchura del 0 de la etiqueta html.
    7. cap: se basa en la altura de las letras mayúsculas de la fuente actual del elemento.
    8. rcap: igual que cap pero tomando la altura de las letras mayúsculas del elemento html.
    9. lh: se basa en la altura de la línea del elemento.
    10. rlh: igual que lh pero toma la altura de la etiqueta html.
    11. ic:
    12. ric:
  2. %: se basa en el tamaño del contenedor.
  3. Al tamaño del viewport: que es la parte visible del navegador
    1. vw: se basa por el ancho de la pantalla (OJO QUE APARECE BARRA DE DESPLAZAMIENTO HORIZONTAL, CONVIENE USAR 100%)
    2. vh: se basa en la altura de la pantalla, si queremos que un elemento o contenedor cubra toda la altura se pone 100vh, no aparece barra vertical.
    3. vmin: 
    4. vmax:
    5. vi:
    6. vb:
    7. dvw:
    8. dvh:
    9. dvmin:
    10. dvmax:
    11. dvi:
    12. dvb:
    13. svw:
    14. svh:
    15. svi:
    16. svb:
    17. svmin:
    18. svmax:
    19. lvw:
    20. lvh:
    21. lvi:
    22. lvb:
    23. lvmin:
    24. lvmax:
  4. Al contenedor cuando se usa la regla @container (tiene que ver con las medias queries)
    1. cqw: es igual que vw pero con @container
    2. cqh: es igual que vh pero con @container
    3. cqi: porcentaje relativo al tamaño de línea
    4. cqb: porcentaje relativo al tamaño de bloque
    5. cqmin: igual que vmin
    6. cqmax: igual que vmax
    7. cqem: igual que em
    8. cqlh: igual que lh
    9. cqex: igual que ex
    10. cqch: igual que ch

### Variables (custom properties)
--nombre-variable:valor ej  div{ --primary-color: blue; color: var(--primary-color);}
- las variables son heredaras hacia los descendientes del elemento donde se declara la variable.
- div{--primary-color: blue; color: var(--primary-color,orange);}  el segundo parámetro es un valor por defecto si ese elemento no hereda la variable.
- Pueden existir varias variables con el mismo nombre, pero son diferentes si están en diferentes ámbitos (scope).
