



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

