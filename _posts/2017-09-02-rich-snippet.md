---
layout: post
title: "Los Rich Snippet. Marca la diferencia en Google."
date: 2017-09-02 07:27:47 +0200
categories: rich snippet
permalink: /rich-snippet/
excerpt: "¿Como implementarlo en nuestra web? ¿Qué tipos hay? ¿Lo puedo poner en wordpress? Estas preguntas y muchas más las tienes aquí."
img: rich-snippet.jpg
author: "David Díaz"
---
Cada día buscamos más que nuestros resultados en las SERP sea los más destacados y aumente el CRT. Ahora tenemos la 
posibilidad de añadir **los Rich Snippet (Fragmentos Enriquecidos)** para que nuestros resultados en Google sea más visibles.
Tengo que advertir que no por tener los Rich Snippet en nuetra web Google los va a usar en sus resultados. A día de hoy 
la decisión de interpretarlos y mostrarlos en los resultados de búsqueda es de Google pero, hay que decir que es interesante
ponerlos y esperar con ilusión que los saque.

Dicho esto, en este artículo explicaremos como podemos implementarlos en nuestras webs, algunos tipos, como validarlos, etc.

Aquí tenéis el índice:

> 1. [¿Qué son los Rich Snippets o Fragmentos Enriquecidos?](#qué-son-los-rich-snippets-o-fragmentos-enriquecidos)
>       1. [Ejemplo de resultado con Rich Snippet](#ejemplo-de-resultado-con-rich-snippet)
>       1. [Ejemplo de resultado sin Rich Snippet](#ejemplo-de-resultado-sin-rich-snippet)
> 1. [¿Comó crear los Rich Snippets?](#comó-crear-los-rich-snippets)
> 1. [¿Donde colocar los Rich Snippets?](#donde-colocar-los-rich-snippets)
> 1. [¿Como validar los Rich Snippets?](#como-validar-los-rich-snippets)

## ¿Qué son los Rich Snippets o Fragmentos Enriquecidos?
Son fragmentos de código que añadimos en nuestras webs y facilita tanto la lectura como la compresión a las arañas de los
buscadores. Esto hace que los buscadores modifiquen los resultados y los muestre de una forma diferente **en función del 
tipo de Rich Snippet.**

### Ejemplo de resultado con Rich Snippet
Aquí tenéis un ejemplo de un resultado con fragmentos enriquecidos

![Ejemplo con rich snippet](/img/ejemplo-con-rich-snippet.jpg)

### Ejemplo de resultado sin Rich Snippet
Como váis a ver en el siguiente resultado la diferencia entre con y sin es bastante significativa no?

![Ejemplo sin rich snippet](/img/ejemplo-sin-rich-snippet.jpg)

## ¿Comó crear los Rich Snippets?
Crealos es relativamente sencillo pero, tiene la dificultad de que no se nos olvide ningún atributo. Si esto pasase 
Google lo marcaría en Google Search Console como error.
Si no utilizamos ningún CMS que tenga algún plugin que nos ayude con la creación, siempre podemos acudir a alguna 
herramienta online que nos facilite la creación.

Os voy aconsejar algunas herramientas online para crear Rich Snippet:
1. [https://hallanalysis.com/json-ld-generator/](https://hallanalysis.com/json-ld-generator/){:target="_blank"}
![hallanalysis generador rich snippet](/img/hallanalysis-generador-rich-snippet.jpg)
Esta web nos permite seleccionar varios tipos y nos genera un código para que lo pegamos en nuestra web
1. [http://tools.ranksider.com/rich-snippets/product](http://tools.ranksider.com/rich-snippets/product){:target="_blank"}
![ranksider generador rich snippet](/img/ranksider-generador-rich-snippet.jpg)
Otra web muy parecida a la anterior donde nos da un formulario muy cómodo y tenemos que completarlo.
1. [http://microdatagenerator.com/generator.html](http://microdatagenerator.com/generator.html){:target="_blank"}
![microdatagenerator generador rich snippet](/img/microdatagenerator-generador-rich-snippet.jpg)
Lo interesante de esta web es que te genera los rich snippet para negocios locales y te deja elegir el tipo de negocio.

## ¿Donde colocar los Rich Snippets?
Normalmente los solemos encontrar en dos formatos: **JSON-LD** o **Microdata**.

En el caso del JSON-LD es un objeto json que se mete dentro de las etiquetas script de html. Este fragmento se podría
colocar en cualquier punto del código fuente de nuestra web pero, yo suelo aconsejar colocarlo lo más abajo posible
del código fuente y siempre dentro de la etiqueta html.

**Un ejemplo de JSON-LD**
```
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "Article",
  "author": "John Doe",
  "interactionStatistic": [
    {
      "@type": "InteractionCounter",
      "interactionService": {
        "@type": "Website",
        "name": "Twitter",
        "url": "http://www.twitter.com"
      },
      "interactionType": "http://schema.org/ShareAction",
      "userInteractionCount": "1203"
    },
    {
      "@type": "InteractionCounter",
      "interactionType": "http://schema.org/CommentAction",
      "userInteractionCount": "78"
    }
  ],
  "name": "How to Tie a Reef Knot"
}
</script>
```

En el caso de los microdata son atributos que se colocan en las etiquetas html.

**Un ejemplo de microdata**
```
<div itemscope itemtype="http://schema.org/Article">
  <span itemprop="name">How to Tie a Reef Knot</span>
  by <span itemprop="author">John Doe</span>
  This article has been tweeted 1203 times and contains 78 user comments.
  <div itemprop="interactionStatistic" itemscope itemtype="http://schema.org/InteractionCounter">
    <div itemprop="interactionService" itemscope itemid="http://www.twitter.com" itemtype="http://schema.org/Website">
      <meta itemprop="name" content="Twitter" />
    </div>
    <meta itemprop="interactionType" content="http://schema.org/ShareAction"/>
    <meta itemprop="userInteractionCount" content="1203" />
  </div>
  <div itemprop="interactionStatistic" itemscope itemtype="http://schema.org/InteractionCounter">
    <meta itemprop="interactionType" content="http://schema.org/CommentAction"/>
    <meta itemprop="userInteractionCount" content="78" />
  </div>
</div> 
```

Cualquiera de los dos formatos es totalmente válido y ya va por gustos para quien lo implemente.

## ¿Como validar los Rich Snippets?
Esto es una parte muy importante para que Google no nos reporte un error en los Rich Snippet.
Os voy a aconsejar varias herramientas online para poder validar vuestros códigos.

1. [https://search.google.com/structured-data/testing-tool?hl=es](https://search.google.com/structured-data/testing-tool?hl=es){:target="_blank"}
![google validador rich snippet](/img/google-validador-rich-snippet.jpg)
El propio google tiene su propia herramienta para la validación de los fragmentos enriquecidos así que... usémosla.
1. [https://webmaster.yandex.com/tools/microtest/](https://webmaster.yandex.com/tools/microtest/){:target="_blank"}
![yandex validador rich snippet](/img/yandex-validador-rich-snippet.jpg)
Aquí tenéis otra herramienta de validación muy buena por si la de google falla.