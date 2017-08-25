---
layout: post
title:  "Guía de composer en español"
date:   2017-08-12 07:27:47 +0200
categories: composer
permalink: /guia-composer.html
excerpt: "Si estas buscando una guía de composer... en este artículo te explicamos todo lo que necesitas para empezar a integrarlo en tus proyectos."
img: guia-composer.jpeg
author: "David Díaz"
---
En el año 2017 no concibo ningún proyecto sin un gestor de dependencias, da igual la tecnología que uses. Para Java
tenemos **Maven**, para android **Gradle**, para js **NPM**, para php **Composer**, etc.

Un gestor de dependencias te da la facilidad de poder descargar paquetes a tus proyectos y el solo va controlando las
versiones de los mismos. Ya se queda muy atrás eso de descargar un zip e introducir mil ficheros dentro de nuestros
proyectos.

Otras de las ventajas es el trabajo en el equipo, todos trabajan con la misma versión de las dependencias que pueda
tener nuestros proyectos. Nos olvidamos de que cada miembro del equipo trabaje con versiones distintas de un mismo
paquete.

Dicho todo esto vamos a ver lo fácil que es trabajar con **composer** en **php**.

> 1. [¿Qué es composer?](#qué-es-composer)
> 1. [¿Cómo instalar composer?](#cómo-instalar-composer)
> 1. [¿Cómo usar composer?](#cómo-usar-composer)
> 1. [¿Cómo añadir paquetes a composer?](#cómo-añadir-paquetes-a-composer)
> 1. [¿Para que sirve el composer.json?](#para-que-sirve-el-composerjson)
> 1. [¿Para que sirve el composer.lock?](#para-que-sirve-el-composerlock)
> 1. [¿Cómo actualizar composer?](#cómo-actualizar-composer)
> 1. [Preguntas comunes de composer](#preguntas-comunes-de-composer)
>       1. [Diferencia entre composer install y composer update](#diferencia-entre-composer-install-y-composer-update)
>       1. [Descargar repositorios privados](#descargar-repositorios-privados)

## ¿Qué es composer?
Como he dicho antes **composer** es un gestor de dependencias para **php**. Con el podemos descargar desde librerías
que alguien de la comunidad ha hecho y nos vienen fenomenal, hasta instalar framework enteros como es el caso de yii, 
laravel, doctrine, symfony, etc. Lo bueno es que hacer esto se tarda minutos en hacer y es automático.

## ¿Cómo instalar composer?
La instalación de composer ha mejorado mucho en los últimos tiempo y ahora es super sencillo instalarlo.
Para ello lo que hacemos es ejecutar los siguientes comandos:

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

Es generará un **composer.phar** en el directorio que estemos. No esta nada mal que cada proyecto tenga su **composer.phar**
pero, yo prefiero instalarlo globalmente en mi máquina.
Para tenerlo de forma global en **mac** lo que hago es sustituir la tercera línea del comando anterior añadiendole
algunos parámetros.

```
php composer-setup.php --filename=composer --install-dir=/usr/local/bin/
```

El comando entero quedaría:

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php --filename=composer --install-dir=/usr/local/bin/
php -r "unlink('composer-setup.php');"
```

Hecho esto desde cualquier directorio puedes ejecutar:

```
composer
```

Y ya puedo ver si la instalación se ha realizado correctamente.

## ¿Cómo usar composer?
Si el proyecto es nuevo tenemos dos opciones:
1. Crear el fichero de configuración a mano.
1. Ejecutar **composer init**

Aquí vamos usar la ley del mínimo esfuerzo y estando en el directorio donde va a estar nuestro proyecto, vamos a ejecutar:

```
composer init
```

Lo primero que nos pregutanrá es el nombre del paquete:

```
Package name (<vendor>/<name>) [daviddiaz/test]: diazdavid-info/test
```

Yo suelo poner mi **nombre de usuario de github/nombre del proyecto**

Después nos pide una descripción del proyecto:

```
Description []: Proyecto de prueba
```

Si no tenemos muy claro la descripción podemos dejarlo en blanco y después rellenarlo.

Lo siguiente es un dato importante y es el **autor de proyecto**:

```
Author [David Díaz <diazdavid.info@gmail.com>, n to skip]: David Diaz <diazdavid.info@gmail.com>
```

A continuación nos pregunta cual es la estabilidad mínima que puede tener una dependencia dentro de tu proyecto.
Esto es importante para que todas las dependencias de nuestro proyecto sean estables o por el contrario permitimos
dependencias que aún están en desarrollo.
Yo es este caso prefiero que todas las dependencias de mis proyecto sean estables.

```
Minimum Stability []: stable 
``` 

Las opciones posibles son: **dev, alpha, beta, RC y stable**.

La siguiente pregunta es el tipo de proyecto estamos creando. Normalmente yo pongo **project**:

```
Package Type (e.g. library, project, metapackage, composer-plugin) []: project
```

Lo siguiente es el tipo de licencia y esto ya es un mundo. Normalmente yo lo dejo en blanco para no complicarme mucho.

```
License []:
```

Ahora viene una parte importante que es indicarle a **composer** cuales van a ser nuestras dependencias. Normalmente
yo no las instalo por el asistente a nos ser que ya sepa cuales van a ser mis dependencias.
Vamos a suponer que queremos **Doctrine**:

```
Would you like to define your dependencies (require) interactively [yes]? yes

Search for a package: doctrine/orm 

Enter the version constraint to require (or leave blank to use the latest version):

Using version ^2.5 for doctrine/orm
```

Esto descarga la última versión de doctrine. Da la casualidad que yo me sabía el nombre completo de **Doctrine** pero 
podíamos haber buscado solo poniendo **Doctrine** y nos mostraría:

```
Found 15 packages matching Doctrine

   [0] kdyby/doctrine
   [1] portphp/doctrine
   [2] etten/doctrine
   [3] erdiko/doctrine
   [4] kappa/doctrine
   [5] huttopia/doctrine
   [6] xi/doctrine
   [7] zucchi/doctrine
   [8] nnx/doctrine
   [9] webdevbr/doctrine
  [10] instante/doctrine
  [11] lexpress/doctrine1
  [12] drak/doctrine1
  [13] doctrine/doctrine1
  [14] sabaki-dev/doctrine1

Enter package # to add, or the complete package name if it is not listed:
```

Pero en el caso de **doctrine** no esta en paquete que queremos. Más adelante os mostraré una forma más sencilla de
buscar paquetes.

Después nos pregunta las dependencias que queremos pero para desarrollo. Casi siempre usamos paquetes para desarrollo
como puede ser **phpUnit** y paquetes para producción como puede ser **Doctrine**. Por este motivo **Composer** lo
divide en dos.
En esta ocasión yo le digo que no y más adelante decidiré:

```
Would you like to define your dev dependencies (require-dev) interactively [yes]? no
```

Ya hemos llegado al final y nos pide confirmación:

```
{
    "name": "diazdavid-info/test",
    "description": "Proyecto de prueba",
    "type": "project",
    "require": {
        "doctrine/orm": "^2.5"
    },
    "authors": [
        {
            "name": "David Diaz",
            "email": "diazdavid.info@gmail.com"
        }
    ],
    "minimum-stability": "stable"
}

Do you confirm generation [yes]? yes
```

Esto generará un fichero **composer.json** que veremos más adelante para que sirve.

Solo nos queda ejecutar:

```
composer update
```

Este comando descarga todas las dependencias dentro de un directorio que se llama **vendor**.

## ¿Cómo añadir paquetes a composer?
Como hemos visto en el punto anterior podemos instalar paquetes con la ayuda del asistente pero ¿que pasa cuando
necesitamos más paquetes?
La respuesta es muy fácil, nos vamos a [packagist.org](https://packagist.org/){:target="_blank"} que es una web muy famosa y 
que recoge muchos paquetes de **composer**.
En ella buscamos lo que queremos y nos quedamos con el nombre del paquete. Ahora nos vamos a la consola y ejecutamos:

```
composer require symfony/console
```

Esto automáticamente nos añadirá el paquete a nuestras dependencias.

Si queremos añadir un paquete de desarrollo, por ejemplo phpUnit, ejecutaremos;

```
composer require --dev phpunit/phpunit
```

Así de fácil añadimos dependencias a nuestros proyectos.

## ¿Para que sirve el composer.json?
Este fichero contiene toda la configuración de nuestras dependencias, un ejemplo es el siguiente:

```
{
    "name": "diazdavid-info/test",
    "description": "Proyecto de prueba",
    "type": "project",
    "authors": [
        {
            "name": "David Diaz",
            "email": "diazdavid.info@gmail.com"
        }
    ],
    "minimum-stability": "stable",
    "require": {
        "doctrine/orm": "^2.5"
    },
    "require-dev": {
        "phpunit/phpunit": "^6.3"
    }
}
```

Las partes más importantes son: 
1. **require** que indica las dependencias de producción
1. **require-dev** que indica las dependencias de desarrollo

Las demás partes son configuraciones propias del proyecto.

## ¿Para que sirve el composer.lock?
Este fichero lo que almacena es la versión exacta de las dependencias que estamos usando. Esto hace que cuando subimos
el código a producción o otro compañero se lo descarga, **composer** descarga la versión que le indique este fichero.
Hay que tener cuidado porque solo se descarga la versión indicada por este fichero si ejecutamos **composer intall**
si por el contrario ejecutamos **composer update**, **composer** omitirá este fichero y descarga la última versión 
de todas nuestras dependencias.

## ¿Cómo actualizar composer?
En ocasiones necesitamos actualizar **composer** de versión, para ello ejecutamos:

```
composer self update
```

Este comando actualizará la versión de **composer**

## Preguntas comunes de composer

### Diferencia entre composer install y composer update
**Composer install** descarga todas las dependencias pero, teniendo en cuenta la versión que ha sido almacenado en el fichero
**composer.lock**
**Composer update** descarga todas las dependencias con la última versión disponible.

### Descargar repositorios privados
En alguna ocasión podemos querer descargar alguna dependencia de algún repositorio privado y para ello tenemos que editar
el fichero **composer.json** y añadir:
1. Url del repositorio privado.
1. Paquete que queremos descargas con su versión

Un ejemplo de **composer.json** con repositorio privado es el siguiente:

```
{
    "name": "diazdavid-info/test",
    "description": "Proyecto de prueba",
    "type": "project",
    "authors": [
        {
            "name": "David Diaz",
            "email": "diazdavid.info@gmail.com"
        }
    ],
    "minimum-stability": "stable",
    "require": {
        "repositorio/privado": "^2.5"
    },
    "repositories": [
        {
            "url": "git@bitbucket.org:repositorio-privado.git",
            "type": "vcs"
        }
      ]
}
```

Y con esto ya podemos ejecutar **composer update** y comprobar si todo esta correcto.
