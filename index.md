---
layout: page
title: "▷ Guías, Artículos y trucos sobre el Desarrollo Web"
description: "Si eres un apasionado del desarrollo web o quieres aprender, esta es tu web. ➤ ➤ En Free Time Kata tenemos artículos de css, javascript, framework y todo lo relacionado con la programación web. No lo dudes y ENTRA!!!"
principal-title: "Somos amantes del Desarrollo Web"
principal-image: "/img/desarrollo-web.jpg"
images-list:
enable-related: false
enable-principal-title: true
enable-principal-image: false
enable-index: true
---
## Disfrutas del desarrollo web mejorando tu css
{% assign list = site.posts | where:"categories","css" %}
{%- include features.html post-list=list -%}

## Árticulos que un programador web debe leer
{% assign git = site.posts | where:"categories","git" %}
{% assign composer = site.posts | where:"categories","composer" %}
{% assign list = git | concat: composer %}
{%- include features.html post-list=list -%}

## Mejora la presencia de tu web en google
{% assign list = site.posts | where:"categories","rich snippet" %}
{%- include features.html post-list=list -%}
