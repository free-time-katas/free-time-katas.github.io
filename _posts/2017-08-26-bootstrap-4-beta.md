---
layout: post
title:  "Bootstrap 4 beta, os contamos sus novedades"
date:   2017-08-26 07:27:47 +0200
categories: bootstrap
permalink: /bootstrap-4-beta.html
excerpt: "Si, has leído bien, después de dos años ya esta aquí la versión beta de la última versión de bootstrap. Así que vamos a jugar con ella."
img: novedades-bootstrap-4-beta.jpg
author: "David Díaz"
---
El equipo de unos de los framework css más usado lleva dos años trabajando en su nueva versión y por fin ya tenemos su
versión beta.

En su página web nos cuentan un poco como ha ido en desarrollo en números, han escrito 67.000 nuevas líneas, ha borrado
82.000 líneas, han realizado 5.000 commit y han cambiado más de 650 ficheros. Estos números nos indica que básicamente 
han reescrito en framework entero.

Dicho esto... vamos a probar esta versión beta de bootstrap 4 y veamos que cosas nuevas trae.

> 1. [Novedades bootstrap 4](#novedades-bootstrap-4)
>       1. [Cambio en el preprocesador de css](#cambio-en-el-preprocesador-de-css)
>       1. [Nuevo sistema de grid](#nuevo-sistema-de-grid)
>       1. [Nuevas tarjetas tipo material design](#nuevas-tarjetas-tipo-material-design)
>       1. [Reset de normalize css](#reset-de-normalize-css)
>       1. [Nuevos diseños](#nuevos-diseños)
>       1. [Componentes javascript](#componentes-javascript)
>       1. [Colocación automática de tooltips, popovers y dropdowns](#colocación-automática-de-tooltips-popovers-y-dropdowns)
>       1. [Adios a los iconos](#adios-a-los-iconos)
> 1. [Libros bootstrap 4](#libros-bootstrap-4)
>       1. [Bootstrap 4 Cookbook (Inglés)](#bootstrap-4-cookbook-inglés)
>       1. [Learning Bootstrap 4 Second Edition (Inglés)](#learning-bootstrap-4-second-edition-inglés)
>       1. [Web Development with Bootstrap 4 and Angular 2, Second Edition (Inglés)](#web-development-with-bootstrap-4-and-angular-2-second-edition-inglés)

## Novedades bootstrap 4
### Cambio en el preprocesador de css
Bootstrap en versiones anteriores trabajaba con less y en esta última versión ha pasado todas sus líneas de código a 
sass. Es una buena decisión ya que la comunidad de desarrolladores que hay es más grande en sass.

### Nuevo sistema de grid
Uno de los cambios, a mi parecer, más importantes es el cambio del grid o de su sistema de rejilla. Ahora la nueva versión
de boostrap va a usar flexbox.

> Si quieres saber más sobre flexbox pasate por la [guia flebox](guia-flexbox.html) donde explico su potencia.

Este nuevo sistema de grib es mucho más fácil de implementar:

```
<div class="container">
    <div class="row">
        <div class="col">
            1 of 2
        </div>
        <div class="col">
            2 of 2
        </div>
    </div>
    <div class="row">
        <div class="col">
            1 of 3
        </div>
        <div class="col">
            2 of 3
        </div>
        <div class="col">
            3 of 3
        </div>
    </div>
</div>
```

![Ejemplo 1 grid bootstrap 4](/img/grid-1-bootstrap-4.jpg)

Ahora solo le indicamos que queremos una nueva columna y el automáticamente redimensiona las columnas automáticamente
sin tenerle que especificar los diferentes tamaños.

Podemos seguir forzando que una columna ocupe más que otras:

```
<div class="container">
    <div class="row">
        <div class="col">
            1 of 3
        </div>
        <div class="col-6">
            2 of 3 (wider)
        </div>
        <div class="col">
            3 of 3
        </div>
    </div>
    <div class="row">
        <div class="col">
            1 of 3
        </div>
        <div class="col-5">
            2 of 3 (wider)
        </div>
        <div class="col">
            3 of 3
        </div>
    </div>
</div>
```

![Ejemplo 2 grid bootstrap 4](/img/grid-2-bootstrap-4.jpg)

### Nuevas tarjetas tipo material design
Esto es una de las cosas más chulas porque en versiones anteriores de bootstrap no existía. Este cambio permite hacer
cosas como estas:

![Tarjetas bootstrap 4](/img/tarjetas-bootstrap-4.jpg)

Con tan solo estas líneas de código:

```
<div class="card" style="width: 20rem;">
    <img class="card-img-top" src="..." alt="Card image cap">
    <div class="card-body">
        <h4 class="card-title">Card title</h4>
        <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
</div>
```

### Reset de normalize css
Normalize css lo que hace es resetear todos los estilos por defecto que vienen en los diferentes navegadores para que 
nuestra maquetación se vea igual en todos ellos.
El equipo de bootstrap lo que ha hecho es mejorar esa normalización de estilo lo que se traduce en que nuestras webs 
se van a ver igual indistintamente del navegador que usemos.

### Nuevos diseños
Si, tenemos nuevos diseños. Si nos vamos a un elemento básico como los botones, ahora tenemos colores más planos y esquinas
menos redondeadas.

![Botones bootstrap 4](/img/botones-bootstrap-4.jpg)

### Componentes javascript
Han reescrito todos los componentes javascript para pasarlo al nuevo estándar ECMAScript 6 (ES6). De esta forma se puede
aprovechar todas las nuevas funcionalidades que ofrece el nuevo estándar.

Un ejemplo de un componente totalmente renovado es el carrusel:

![Carrusel bootstrap 4](/img/carrusel-bootstrap-4.jpg)

### Colocación automática de tooltips, popovers y dropdowns
Antiguamente teníamos que especificar la dirección donde queríamos que apareciese. En esta nueva versión ya es automático
en función del espacio que tiene disponible.

![Popover bootstrap 4](/img/popover-bootstrap-4.jpg)

En esta ocasión el equipo de bootstrap se ha apoyado en librería Popper.js.

### Adios a los iconos
En esta nueva versión han dicho adiós a los iconos y dejan la resposibilidad de añadir iconos al desarrollador. Esto es
una muy buena decisión ya que cada desarrollador se siente cómodo con unos iconos u otros.

![Iconos bootstrap 4](/img/iconos-bootstrap-4.jpg)

## Libros bootstrap 4
Os dejo unos libros de bootstrap por si queréis aprender un poco más.

### Bootstrap 4 Cookbook (Inglés)
[![Bootstrap 4 Cookbook](/img/bootstrap-4-cookbook.jpg)](https://www.amazon.es/Bootstrap-Cookbook-Snigdhendu-Bikas-Bhaumik/dp/178588929X/){:target="_blank"}

### Learning Bootstrap 4 Second Edition (Inglés)
[![Learning Bootstrap 4 Second Edition](/img/learning-bootstrap-4-second-edition.jpg)](https://www.amazon.es/Learning-Bootstrap-Second-Matt-Lambert/dp/1785881000/){:target="_blank"}

### Web Development with Bootstrap 4 and Angular 2, Second Edition (Inglés)
[![Web Development with Bootstrap 4 and Angular 2, Second Edition](/img/web-development-with-bootstrap-4-and-angular-2.jpg)](https://www.amazon.es/Web-Development-Bootstrap-Angular-Second/dp/1785880810/){:target="_blank"}