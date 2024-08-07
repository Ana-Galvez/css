# *NOTAS SOBRE CSS*

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

### Otras funciones
- función url()  para poner una ruta o dirección de internet
- función calc() sirve para hacer cálculos
- funciones min() y max()
- función clamp(min, ideal, max)

### Estilos de fuentes
1. **font**    shorthand que une font-style font-variant font-weight font-size line-height font-family
2. regla @font-face se utiliza para agregar un tipo de letra que no tiene font-family, ya sea de un archivo o de un sitio web. @font-face { font-family: Monserrat; src: url("src: url(https://fonts.gstatic.com/s/montserrat/v26/JTUQjIg1_i6t8kCHKm459WxRyS7m.woff2))} y luego en el elemento que se quiere usar  p{ font-family: monserrat, sans-serif}  sans-serif o cualquier tipografía que agarra css por si no anda el enlace. Al usar archivos woff2 o woff (woff1) conviene agregar font-display:swap, ya que hasta que cargue la fuente woff2 va a aparecer el valor predeterminado.

### Estilos de texto
1. text-align: start(left) end(right)
2. text-align-last   -   alinea la última línea del párrafo
3. text-indent   -   para dar sangría de primera línea
4. text-overflow  - pone 1 sola línea y ...  hay que usar overflow:hidden y white-space:nowrap(para que solo sea 1 línea);
5. text-transform / letter-spacing/ white-space(pre:respeta todos los espacios como lo pusimos en el html) / word-break:break-all(separa la última palabra de cada línea) / word-spacing: pone más o menos espacio entre las palabras / writing-mode: orientación horizontal o vertical

### Bordes
1. border-radius  -  es un shorthand de border-top-left(border-start-start)  border-top-right(border-start-end) border-bottom-right(border-end-end) border-bottom-left(border-end-start)   si se usara / entre los valores va a dar forma de elipse no circular ej  border-radius: 3rem / 5rem   si se quiere hacer un círculo border-radius:50%, siendo el width y height de igual tamaño

### Outline
- es como un borde pero no forma parte del box-model, o sea, si le aumentamos el ancho va a ocupar espacio de otros elementos.
- es un shorthand de outline-width outline-style outline-color   ej outline:2px solid blue
- outline-offset  se aleja o se acerca al elemento  ej  outline-offset: 1rem (se aleja)  outline-offset: -1rem(se acerca)

### Estilos de fondo
1. background - shorthand de (pongo bg para hacerlo más corto pero hay que escribir background)  bg-image bg position bg-size bg-repeat bg-origin bg-clip bg-attachment bg-color
2. background-image: url("ruta") sea de un archivo o web (OJO que no se acomoda al tamaño del contenedor)
3. background-size: setea el tamaño de la imágen
  1. background-size: 250px; /* si se usa 1 valor es para el ancho y el alto calcula automáticamente, si queda lugar repite parte de la imágen*/
  2. background-size: 250px 50px; /* si se usa 2 valores es para el ancho y el alto, si el contenedor es más alto que el ancho o alto, repite parte de la imagen*/
  3. background-size: contain; ajusta la imagen al contenedor para que se vea proporcional, si queda lugar repite parte de la imagen
  4. background-size: cover; escala la imagen (conservando su proporción) al tamaño más pequeño posible para llenar el contenedor
4. background-repeat: setea la repetición de la img si es más chica que el contenedor 
  1. background-repeat:no-repeat; /* no repeat borra las img que se repiten y queda el color de fondo(si no hay background-color, entonces es el color por defecto del navegador)*/
  2. background-repeat: repeat-x; repite solo horizontalmente y queda el color de fondo(si no hay background-color, entonces es el color por defecto del navegador)
  3. background-repeat: repeat-x; repite solo verticalmente y queda el color de fondo(si no hay background-color, entonces es el color por defecto del navegador)
5. background-position: setea posición de la img respecto al contenedor. (Para ver que funciona se debe poner background-repeat:no-repeat)
  1. background-position: 25px 50px; 1 valor es para el horizontal y 2 valores, el primero el horizontal y el segundo para el vertical
  2. background-position: top center; se puede combinar center left right top bottom
6. background-clip: setea desde cuando comienza a mostrarse la img respecto al borde, padding o contenido del contenedor
  1. background-clip:border-box; la img no comienza en los bordes del contenedor pero si le ponemos un background-color,este sí está en los bordes, es el valor por defecto
  2. background-clip: padding-box; la img comienza sin incluir los bordes, pero tampoco el background-color, o sea en el padding del contenedor
  3. background-clip: content-box; la img comienza sin incluir el padding puesto, o sea desde el contenido del contenedor (padding > 0)
7. background-origin: funciona igual que background-clip, siendo su valor por defecto padding-box
  1. background-origin: padding-box; igual que en background-clip:padding box,  es el valor por defecto
  2. background-origin: border-box; a diferencia de clip, sí incluye la img en el borde
8. background-attachment: da efecto tipo parallax a la img con el valor fixed (atención al tamaño del contenedor)

### Estilos de imágenes
- Para hacer las img responsive 
<pre> img{
        max-width: 100%;
        height: auto;
      }
</pre>
1. object-fit: es parecido a bg-position que usa contain y cover
2. object-position: al usar object-fit, este usa 50% 50%, permite usar como bg-position  center left right bottom

### Estilos de listas
1. list-style-image: url(ruta)   para poner una img como viñeta (ver tamaño)
2. list-style-type: dar forma a la viñeta o número
3. list-style-position: inline   la viñeta va dentro del contenido si tiene más de 1 línea
4. list-style: shorthand   type  image position
- IMPORTANTE: a etiquetas ol se le puede agregar atributos html reversed para que cuente de atrás hacia adelante y start="nº" para comenzar por un número específico y no el 1.

### Estilos en columnas
1. columns: column-count column-width  shorthand
2. column-count:   cantidad de columnas
3. column-width:  ancho mínimo de cada columna
4. column-rule: style width color  shorthand para poner una línea vertical entre cada columna
5. column-rule-style: define el tipo de línea
6. column-rule-width: define el ancho de la línea
7. column-rule-color:
8. column-gap: define la distancia mínima entre cada columna
9. column-fill:auto   define según la cantidad de columnas que se asigne cubre un %
10. column-span:all   poniendo en un elemento hace que ese elemento no esté dentro de las columnas

### Estilos de tablas
1. border-collapse:separate/collapse  solo se pone en la etiqueta table y cuando se usa bordes para tr td y table. Muestra los border o no en cada celda
2. border-spacing:   se usa con border-collapse:separate   da un poco más de espaciado entre las celdas.
3. empty-cells:hide  solo en table y con border-collapse:separate   oculta las celdas que no tienen contenido

### Estilos de formularios
- No hay estilos únicos para los elementos de formularios, se usan los atributos conocidos, ya sean color, bg, align, margin, padding, etc. Uno interesante es caret-color   que en input o text-area permite cambiar el color del cursor cuando se apreta en esos elementos

### Estilos de sombras
1. box-shadow: x   y   blur   spread   color   se aplica a los bordes. Se puede agregar a lo último inset, si queremos que la sombra esté dentro del contenedor.
- box-shadow: x   y   blur   spread   color, x  y  blur  spread  color (separado por , se pueden agregar más capas de sombras)
2. text-shadow: x  y  blur  color, más sobras si se quiere.   Se aplica a las letras.
3. filter: drop-shadow( x  y  blur  color)  drop-shadow( x  y  blur  color)(si se quiere más sombras)   Se aplica a imágenes svg o png con transparencia, sino no va a funcionar

### Estilos de degradados
1. background o background-image: linear-gradient(sentido de los colores, color1, color2, etc)
- Linear-gradient mínimo 2 colores y el sentido de los colores es opcional (deg, turn o palabras claves(to top, bottom, right, left))
- A cada color se le puede poner un % que define cuanto ocupa ese color ej  linear-gradient(0.25turn, #ead 30%, red, blue)
- se puede usar repeating-linear-gradient para repetir los colores.
2. radial-gradient(forma sentido, color1 %, color2 %, etc)
- tiene sentido circular o elíptica. La forma circle medida o  ellipse medidax mediday. El sentido puede ser en unidades de medidas o también con closest-side, closest-corner, farthest-corner, farthest-side poniendo % para la x y % para la y. EJ  radia-gradient(closest-side at 45% 33%, red,blue,yellow)   también at left, right,bottom, top ej radial-gradient(ellipse 50px 80px at left,red %45%,blue)
- se puede usar repeating-radial-gradient para repetir
3. conic-gradient(sentido, colores)   el sentido es   from deg,turn o rad at x  y , colores%.
- se puede usar repeating-conic-gradient para repetir

### Estilos de filtros
- conviene usar con imágenes y se usa con el atributo filter
- son funciones y se pueden repetir en un solo filter  ej filter:sepia(60%) blur(1px) brightness(50%) hue-rotate(120deg) invert(20%);
1. filter: blur(unidad de medida);
2. filter: brightness(% o 0 a 1);
3. filter: contrast(% o 0 a 1);
4. filter: drop-shadow VISTO EN ESTILOS DE SOMBRAS
5. filter: grayscale(% o 0 a 1);
6. filter: hue-rotate(deg);
7. filter: invert(% o 0 a 1);
8. filter: opacity(% o 0 a 1);
9. filter: saturate(% o 0 a 1);
10. filter: sepia(% o 0 a 1);

