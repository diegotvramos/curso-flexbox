



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























