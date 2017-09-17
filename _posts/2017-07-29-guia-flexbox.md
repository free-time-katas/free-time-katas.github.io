---
layout: post
title:  "Guía de flexbox css en español"
date:   2017-07-29 07:27:47 +0200
categories: 
    - flexbox
    - frontend
permalink: /guia-flexbox.html
excerpt: "Usar flexbox te asegura que los elementos siempre estarán como tu quieres en todas las situaciones, por eso te traigo esta guia en español."
img: guia-flexbox.jpg
author: "David Díaz"
post_in_home: true
---
Hoy os trigo una guia de flexbox, una de las últimas novedades css3. La tecnología avanza muy rápido y como 
desarrolladores necesitamos adaptarnos a los nuevos tiempo e intentar conocer las últimas tecnologías.

Auque css no es un lenguaje de programación si que es una pieza muy importante en el desarrollo de una página web. Los 
desarrolladores front-end cada día necesitan más potencia para explotar toda su creatividad.

Soy consciente de que flexbox no es agradado de todos los desarrolladores de front pero no deja de ser un recurso con 
el que puede o no trabajar.

Después de esta introducción pasemos a ver lo importante de hoy.

> 1. [¿Qué es flexbox?](#qué-es-flexbox)
> 1. [¿Para que sirve flexbox?](#para-que-sirve-flexbox)
> 1. [¿Cómo usar flexbox?](#cómo-usar-flexbox)
> 1. [Navegadores compatibles con flexbox](#navegadores-compatibles-con-flexbox)
> 1. [Ejemplos con flexbox](#ejemplos-con-flexbox)
> 1. [Términos de flexbox](#términos-de-flexbox)
>     1. [Flex container](#flex-container)
>     1. [Flex item](#flex-item)
>     1. [Ejes](#ejes)
>     1. [Direcciones](#direcciones)
>     1. [Líneas](#líneas)
>     1. [Dimensiones](#dimensiones)

## ¿Qué es flexbox?
Flexbox o caja flexible es un modelo de caja que viene dentro del estándar css3. Viene a sustituir a los ya conocimos 
como: block, inline, table, etc. Este modelo de caja ya es bidireccional y no solo de derecha a izquierda o de izquierda 
a derecha si no de arriba a abajo y viceversa. Estos contenedores flexibles tienen la virtud de que sus hijos también 
pueden ser flexibles y reorganizarse libremente en función del tamaño disponible.

## ¿Para que sirve flexbox?
Flexbox sirve para posicionar los elementos dentro de un contenedor libremente y casi sin restricciones, en 
función del espacio disponible.

## ¿Cómo usar flexbox?
Es muy fácil usar flexbox, solo hay que decirle a un contenedor que su display es flex. Con esto lo que haremos es que 
todos los elementos que hay dentro de ese contenedor sean flexibles.

```
display: flex;
```

## Navegadores compatibles con flexbox
En julio de 2017 esta es la tabla de compatibilidades con los navegadores.

![Navegadores compatibles flexbox](/img/navegadores-compatibles-flexbox.png)

## Ejemplos con flexbox

**Ejemplo básico de flexbox**

Este ejemplo muestra como se comportan los hijos de una caja flexible

```
<!DOCTYPE html>
<html>
<head>
    <style> 
        .flex-container {
            display: -webkit-flex;
            display: flex;
            background-color: lightgrey;
        }
        .flex-item {
            background-color: cornflowerblue;
            width: 100px;
            height: 100px;
            margin: 10px;
        }
    </style>
</head>
<body>

    <div class="flex-container">
        <div class="flex-item">flex item 1</div>
        <div class="flex-item">flex item 2</div>
        <div class="flex-item">flex item 3</div>  
    </div>

</body>
</html>
```

![Ejemplo básico flexbox](/img/ejemplo-basico-flexbox.png)

**Ejemplo dinámico y responsive**

Este ejemplo de nuestros amigo de [developer mozilla](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Flexible_Box_Layout/Usando_las_cajas_flexibles_CSS){:target="_blank"} 
se muestra como las cajas se adaptan no solo en su ancho si no en su orden para ocupar toda la pantalla.

![Ejemplo responsive flexbox](/img/ejemplo-responsive-flexbox.jpg)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>

        body {
            font: 24px Helvetica;
            background: #999999;
        }

        #main {
            min-height: 800px;
            margin: 0px;
            padding: 0px;
            display: -webkit-flex;
            display: flex;
            -webkit-flex-flow: row;
            flex-flow: row;
        }

        #main > article {
            margin: 4px;
            padding: 5px;
            border: 1px solid #cccc33;
            border-radius: 7pt;
            background: #dddd88;
            -webkit-flex: 3 1 60%;
            flex: 3 1 60%;
            -webkit-order: 2;
            order: 2;
        }

        #main > nav {
            margin: 4px;
            padding: 5px;
            border: 1px solid #8888bb;
            border-radius: 7pt;
            background: #ccccff;
            -webkit-flex: 1 6 20%;
            flex: 1 6 20%;
            -webkit-order: 1;
            order: 1;
        }

        #main > aside {
            margin: 4px;
            padding: 5px;
            border: 1px solid #8888bb;
            border-radius: 7pt;
            background: #ccccff;
            -webkit-flex: 1 6 20%;
            flex: 1 6 20%;
            -webkit-order: 3;
            order: 3;
        }

        header, footer {
            display: block;
            margin: 4px;
            padding: 5px;
            min-height: 100px;
            border: 1px solid #eebb55;
            border-radius: 7pt;
            background: #ffeebb;
        }

        /* Too narrow to support three columns */
        @media all and (max-width: 640px) {

            #main, #page {
                -webkit-flex-flow: column;
                flex-flow: column;
            }

            #main > article, #main > nav, #main > aside {
                /* Return them to document order */
                -webkit-order: 0;
                order: 0;
            }

            #main > nav, #main > aside, header, footer {
                min-height: 50px;
                max-height: 50px;
            }
        }

    </style>
</head>
<body>
<header>header</header>
<div id='main'>
    <article>article</article>
    <nav>nav</nav>
    <aside>aside</aside>
</div>
<footer>footer</footer>
</body>
</html>
```

**Ejemplo de una home entera**

Si aun quieres ver más ejemplos te dejo uno de [flexbox con sass](https://github.com/free-time-katas/kata-flex-sass){:target="_blank"}

![Ejemplo flexbox con sass](/img/ejemplo-flexbox-sass.png)

## Términos de flexbox

![Esquema flexbox](/img/esquema-flexbox.jpg)

### Flex container
Es el elemento padre de los elementos flexibles. Se difine así porque tiene la propiedad display flex en sus atributos de estilo.

### Flex item
Solo los elementos que estan dentro de un **flex container**. Si fuese el elemeto flexible fuese texto, automáticamente se
envuenlve en un elemento flexible anónimo.

### Ejes

1. **Flex-direction** es la propiedad que define el eje principal.
2. **Justify-content** es la propiedad que define como se colocan los elemento a lo largo del eje principal.
3. **Align-items** es la propiedad que define como se colocan los elemento a lo largo del eje secundario.
4. **Align-self** es la propiedad que define como se colocan los elementos con respecto al eje secundario.

### Direcciones

1. **Order** es la propiedad que elementos deben salir primero.
2. **Flex-flow** esta propiedad combina **flex-direction** y **flex-wrap** y lo que hace es colocar los elementos flexibles.

### Líneas
Los elementos flexibles se pueden colocar en una sola línea o en varias líneas pero, hay que incluir la propiedad **flex-wrap**.

### Dimensiones
Los atributos de **"altura"** y **"anchura"** para usarlos en los elementos flexibles son **(main size)** para el tamaño principal
y **(cross size)** para el tamaño secundario, que siempre siguen el eje principal y el eje secundario del contenedor flexible.