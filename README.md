



# CURSO DE FLEXBOX.



## (1/13) Introducción

Es uno de los dos grandes módulos de CSS con los que contamos para hacer maquetación.

el año 2012 es cuando se empieza implementar flexbox.

Te recomiendo la guia completa de [css-tricks](https://css-tricks.com/) uno de los mejores blogs para aprender desarrollo frontend

https://css-tricks.com/snippets/css/a-guide-to-flexbox/

algunos Frameworks como bootstrap, bulma, materializecss estan maquetadas con flexbox. busca row.

Muchas de las plantillas, de wordpress de drupal están maquetadas con esos frameworks, muchos desarrolladores backends no se complican y utilizan estos frameworks.

> te recomiendo que te descargues la extención: **CSS Flexbox Cheatsheet**


> ``Ctrl + shift + p `` puedes ver una pequeña guia en e vscode.

## (2/13) Conceptos Básicos 

flexbox es un sistema unidimencional(o tenemos filas o tenemos columnas) vamos a tener filas o vamos a tener columnas pero no podemos tener ambas

![conceptos Básicos](/assets/flex-conceptos.png)

propiedad **Display** el comportamiento por defecto de los hijos de una caja fexbox y se van a aliniear y la direccion por defecto es horizontal (Fila)

```css
    .container{
    background-color: #333;
    display: flex;
    display: inline-flex; /*hace que todos trabajen en linea*/
    display: flex; /*Se usa más el valor de FLEX*/
}

.item{
    background-color: cyan;
}

```

## (3/13) El flujo de Flexbox ( flex-direction + flex-wrap )

la propiedad **Flex direction**

![flex-direction](/assets/flex-direction.JPG)

![flex-wrap](/assets/flex-wrap.JPG)

```css
    /*El tamaño de la caja se comienza a considerar a partir del contenido si nosotros trabajamos Paddings, Border, Margin
    eso va aumentar el tamaño de la caja, por eso lo debemos RESETEAR el tamaño de la caja a box-sizing
*/
*,
*::after,
*::before{
    box-sizing: border-box; /*ya no considera desde el contenido sinó desde el border*/
}
.container{
    background-color: #333;
    height: 30vh;
    display: flex;
    display: inline-flex; /*hace que todos trabajen en linea*/
    display: flex; /*Se usa más el valor de FLEX*/
    flex-direction: row; /*por default*/
    flex-direction: column;
    /*no envuelvas. por default tambien depende de flex-direction*/
    flex-wrap: nowrap; /*va a tratar de alinear todo sus hijos en una sola linea (envoltorio)*/
    flex-wrap: wrap; /*si no caben genera otras filas abajo Lo usa Bootstrap*/
    flex-wrap: wrap-reverse;
    flex-flow: column wrap ;/*Shorthand de flex-direction y flex-wrap*/

    
}

.item{
    border: medium solid red;
    width: 20%;
    height: 20%; /*ya empieza a regir este valor por que la direcion es Column*/
    background-color: cyan;
}
```

## (4/13) Alineación del Main Axis ( justify-content )

Define la alineación de los elementos hijos, respecto del Eje pricipal(está definido por la propiedad flex-direction).

La propiedad Justify-content tiene 6 valores:

![Justify-content](/assets/justify-content.JPG)

Toda las alineaciones tienen efecto si sobra espacio.



## (5/13) Alineación del Cross Axis ( align-items y align-content )

**align-items**

Funciona por cada linea que tengamos. Define la alineación de los hijos en el eje transversal (cross axis) dentro de cada linea. 

![align-items](/assets/align-items.JPG)

Align-item trabaja de manera independiente por cada linea o columna que nosotros tengamos, pero si queremos alinear los elementos hijos como un todo tenemos a otra propiedad: align-content

**align-content**

Define la alineación de los hijos en el eje transversal (cross axis), no funciona cuando los hijos están en UNA sóla linea(CUANDO FLEX:NOWRAP NO FUNCIONA)


los elementos que tiene alto y ancho definido tienen mayor peso

trabaja en conjunto como si toda las lineas ya sean filas o columnas fuera uno solo

![align-content](/assets/align-content.JPG)

Cuando ya estamos maquetando sitios web nos podemos encontrar con un centrado perfecto una maquetacion fluida un stiki footer una cabecera stiky


```css
    .container{
    background-color: #333;
    height: 30vh;
    
    display: flex; /*define que una caja será  flexbox de bloque  o flexbox de linea*/
    display: inline-flex; /*hace que todos trabajen en linea*/
    display: flex; /*Se usa más el valor de FLEX*/
    flex-direction: row; /*por default*/
    flex-direction: row-reverse;
    flex-direction: column;
    flex-direction: column-reverse;
    flex-direction: row; /*Define el eje principal(main-axis) row - x & column - y*/
    flex-direction: column;

    /*no envuelvas. por default tambien depende de flex-direction*/
    flex-wrap: nowrap; /* por default va a tratar de alinear todo sus hijos en una sola linea (envoltorio)*/
    flex-wrap: wrap; /*si no caben genera otras filas abajo Lo usa Bootstrap*/
    /*define si la caja flexbox envuelve o NO a sus hijos*/
    flex-wrap: wrap-reverse;

    flex-flow: row wrap ;/*Shorthand de flex-direction y flex-wrap*/
    flex-flow: row nowrap ;
    flex-flow: row wrap ;
    /* flex-flow: column wrap ; */

    justify-content: flex-start;
    justify-content: flex-end;
    justify-content: center;
    justify-content: space-between;
    justify-content: space-around;/*mmm me parece que no se usa mucho porque no tiene simetria*/
    justify-content: space-evenly;/*los espacios ahora si son proporcionales*/
    justify-content: flex-start;

    align-items: stretch; /*por defecto*/
    align-items: start;
    align-items: center;
    align-items: flex-end;
    align-items: baseline; /*los elementos se alinean ala linea del texto*/
    align-items: start;
    align-items: baseline;
    align-items: center;

    align-content: stretch; /*valor por defecto*/
    align-content: flex-start;
    align-content: center;
    align-content: flex-end;
    align-content: space-between; /*no considera las orillas*/
    align-content: space-around;/*considera las orillas, pero se desborda*/
    align-content: space-evenly; /**/
}

.item{
    border: medium solid red;
    /* width: 20%; */
    height: 20%; /*ya empieza a regir este valor por que la direcion es Column*/
    background-color: cyan;
}

/* .item:nth-child(even){
    font-size: 2.5rem;
} */
```

## (6/13) Factor de Crecimiento ( flex-grow ) 

![flex Item Grow](/assets/flex-Item-grow.JPG)

![flex Shrink-basis](/assets/Flex-shrink%20basis.JPG)


```css
    .item{
    border: medium solid red;
    /* width: 20%; */
    /*height: 20%; /*ya empieza a regir este valor por que la direcion es Column*/
    /* width: 100px; */
    background-color: cyan;

    flex-grow: 0;
    flex-shrink: 1;
    flex-basis: auto;
}
```

**flex-grow:0;**

Cuando la caja fex-box tenga **espacio sobrante** los hijos va a poder aprovechar ese espacio sobrante, por que flex grow es el factor de crecimiento, valor por defecto es 0, NO se aceptan valores negativos

eje contenedor 1000px
    3 items de 100px
    El espacio sobrante es 700, lo dividimos a 3 y para cada uno corresponde a 233.33 mas 100px sumados cada un le corresponderia  333.33px. 

    ahora si uno de los hijos tiene el factor de crecimiento de 2 dos entonces 700 lo dividimos entre 4 = 175 al item 1 y 3  le corresponden (100+175) y al item 2 (100+175+175)=450px

**flex-shrink:1;**

Cuando la caja flexbox NO tenga espacio sobrante, es la habilidad o el factor de encogerse, valor por defecto es 1, NO se aceptan valores negativos.


## (7/13) Factor de Reducción ( flex-shrink )

![flex-shrink](/assets/flex-shrink.JPG)

Cuando una caja no tiene un tamaño especifico el valor que toma es el valor automático osea, ocupan el espacio que requieren segun la cantidad de letras, si le metemos mas texto a un item este crece. 

si lo encojemos los items se encojen, es a la inversa de flex-grow

``flex-shrink: 1;`` cuando está con esté valor  los items se encojen
``flex-shrink: 0;`` cuando está con esté valor  los items ya no se encojen, mentienen su tamaño fijo.

El contenedor padre mide (79.11*3)=237.33 siguidamente al contenedor padre lo reducimos a 200px sobran 37.33px.

si ese valor de (37.33/3)= 12.443 es lo que debemos restar a cada item (79.11-12.443 )=66.667

ahora el Item 2 tiene un factor de reduccion del doble entonces => al espacio reducido lo dividimos entre 4 (37.33/4)= 9.332

|-9.332|-18.664|-9.332|

|79.11-9.332|79.11-18.664|79.11-9.332|

|=69.778|=60.446|=69.778|   

Si el conetenedor está reduciendo mas su tamaño y un conetenedor hijo tiene un factor más pues significa si el contenedor padre en su totalidad eje 40 px y tenemos 3 elementos y uno de esos elementos tiene el doble que los otros dos significa que la perdida se divide entre cuatro toca a 10 los que tienen factor de 1 pierden 10px y los que tienen factor de 2 pierden 20px

## (8/13) Tamaño de los hijos flexbox ( flex-basis ) 


![flex-basis](/assets/flex-basis.JPG)

Es el tamaño del elemento hijo dentro de la linea de la caja flexbox
Si la caja flexbox tiene direccion de fila, flex-basis representa el width
Si la caja flexbox tiene dirección de columna, flex-basis representa el height
valor por defecto auto.

``flex-basis: auto;`` los elementos o cajas ocupan el texto que tienen es el valor por AUTO

``flex-basis: 100px;``Como las cajas flexbox tiene direccion de fila pues flex-basis representa el ancho.  y si abajo poner un ``width:200px`` No le le hace efecto por que para FlexBox flex-basis tiene mayor especificidad

es un Shorthand de las propiedades flex-grow flex-shrink y flex-basis en ese orden.


## (9/13) Orden y Alineación de hijos flexbox ( order y align-self ) 

**Order: ;**

> order: -2;

> order: 0;

> order: 1;


Nosotros podemos invertir el orden de los elementos.

Representa el orden que tendran los elementos hijos en la caja flexbox.

Valor por defecto 0.

Se aceptan valores positivos y negativos.

Un valor menor siempre irá antes que un valor mayor.

el orden de la direccion de la caja  si afecta al orenamiento  


**align-self**

![align-self](/assets/align-self.JPG)

A veces vamos a tener la necesidad  de cambiar el orden en el eje transversal (cross axsis).

Sobreescribe el valor que tenga la propiedad align-items sólo para el elemento hijo especificado.

SIGUIENTE: vamos a hablar como funcionan las Grids de estos frameworks populares como bootstrap  fundation materialize, bulma semantic iuay que la mayoria han dejado de utilizar los flots y utilizan una Grid tipo flexbox. con css purito y ejemplos de algunos patrones de maquetacion que podemos resolver con flexbox Css, le vamos a sacar provecho a el framework bootstrap. por que ya tenemos conocimientos de fex-box.

## (10/13) Maquetación y Responsive Design con Flexbox.


si copiamos el CDN del framework de bootstrap quitamos el punto min (.min) y lo pegamos al navegador, así:

`https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.css`

podemos ver que bootstrap usa flexbox.

Si, copiamos el CDN del framework materializecss podemos ver que usa floats.

`https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css`

Cuando una persona que no conoce nada de html y css y empieza a utilizar estas herramientas y solo activando y desactivando clases puede acomodar sus elementos

**Las columnas en Bootstrap**

![columnas](/assets/col-bootstrap.JPG)

El framework de bootstrap está basado en 12 columnas.

![col-11](/assets/col-11.JPG)

El 0 0 significa: ni creces ni te encojes

si 12 columnas representa el 100%
entonces cuanto representa:
11 columnas representa (11*100)/12= 91.66667%

```css
    $grid-breakpoints: (
  xs: 0,
  sm: 576px,
  md: 768px,
  lg: 992px,
  xl: 1200px,
  xxl: 1400px
);
```

si el tamaño de el dispositivo es menor a 576px usa: ``col-12`` es más no es necesario poner segun yo, 

Bootstrap y la mayoria de los frameworks ya son mobile fires,  es decir los estilos que definimos sin media querys son pensados para el mobil y con las media querys vamos creciendo hacia los demas tamaños

```css
    *,
*::after,
*::before{
    box-sizing: border-box;
}

.container{
    margin: auto;
    max-width: 1200px;
}

.flex-container{
    display: flex;
    flex-flow: row wrap; /*Fila Si Envuelve*/
}

.flex-item{
    border: thin solid #CCC;
    flex: 0 0 100%;
}


/*Estas media querys lo estamos copiando de Bootstrap*/

/*Dispositivos pequeños (teléfonos horizontales, 576 px y superiores)*/
@media (min-width: 576px) { 
    .flex-item{
        flex: 0 0 50%;
    }
 }

/*Medium devices (tablets, 768px and up)*/
@media (min-width: 768px) { 
    .flex-item{
        flex: 0 0 33.33333333333333%; /*es con (PUNTO)*/
    }
 }

/*Dispositivos grandes (computadoras de escritorio, 992 px y superiores)*/
@media (min-width: 992px) { 
    .flex-item{
        flex: 0 0 25%;
    }
 }

/*Dispositivos extragrandes (escritorios grandes, 1200 px y más)*/
@media (min-width: 1200px) { 
    .flex-item{
        flex: 0 0 16.66666666666667%;/*es con (PUNTO)*/
    }
 }

/*Dispositivos XX-Large (escritorios más grandes, 1400 px y más)*/
@media (min-width: 1400px) { 
    .flex-item{
        flex: 0 0 12.5%;
    }
 }
```

## 
















