---
layout: post
title: Qué son los selectores en CSS y como afecta la especificidad en ellos
author: david
category: programacion
tags: ["CSS", "Tip"]
description: >-
   Conocer los stipos de selectores y su importancia en CSS te permite generar código CSS entendible y optimizado
---

Al momento de maquetar tu página o aplicación web. CSS entra a ser tu aliado imprescindible. Por eso es bueno conocer las buenas prácticas al momento de redactar tu código CSS. y conocer la especificidad es una de esas buenas practicas

Bueno, Vamos por partes...

### Qué es un selector?

Los selectores son identificadores que se usan para definir los elementos a los que cuales queremos aplicar estilos. En general existen dos tipos de selectores. El **id** y las **clases**. 

-   El id es usado para aplicar estilos a un elemento en específico. Su sintaxis es:
{% highlight css %}
    #my_id {
        color: yellow;
        ...
        ...
    }
{% endhighlight %}

El **id** se define al usar el caracter **#** al iniciar la sentencia.

-	Las clases son usadas para aplicar estilos a varios elementos al mismo tiempo. su sintaxis es:
{% highlight css %}
    .my_class {
        color: blue;
        ...
        ...
    }
{% endhighlight %}

Existen otra clase de selectores que son las mismas etiquetas HTML, las cuales permiten cambiar los valores de los estilos de esas etiquetas por defecto, su sintaxis consiste en solo definir la etiqueta que quiere modificar. Como el siguiente.
{% highlight css %}
    h1, h2, h3 {
        color: red;
        ...
        ...
    }
{% endhighlight %}

ya que conocermos un poco de los estilos ahora lo que sigue es...

### Cómo aplicar estilos?

Existen tres maneras de aplicar estilos a los elementos de una pagina web. Y estos tienen un orden de especificidad. Es decir, de importancia el cual veremos en el siguiente apartado.

1. **Inline Style**: son los estilos que son aplicados directamente en la etiqueta del elemento empleando la. Por ejemplo.
{% highlight html %}
    green;">Hello! Daca DEV</h1>
{% endhighlight %}
Es mala practica aplicar estilos directamente a la etiqueta HTML debido a que es más difícil de leer el código y su escalabilidad a mediano y largo plazo se vuelve una tarea tediosa.

2. Etiqueta **&lt;style&gt;** : consiste en definir los estilos CSS dentro del mismo archivo HTML, empleando las etiquetas &lt;style&gt; y dentro de ellas declarar los estilos. como ejemplo.
{% highlight html %}
    <style>
        h1 {
            color: green;
            font-weight: bolder;
        }
    </style>

    <h1>Hello! Daca DEV</h1>
{% endhighlight %}
Esta practica se usa en ocasiones cuando los estilos que se aplicaran son de unas pocas líneas. Sin embargo, sigue siendo mala practica combinar los estilos y la estructura de una página dentro de un mismo archivo

3.  **Archivo CSS**: es la forma como profesionalmente se debe aplicar estilos. Consiste en crear un archivo con extensión. CSS y allí definir los estilos. Y finalmente enlazar la hoja de estilos con el archivo HTML correspondiente con la etiqueta &lt;link&gt;. Un ejemplo seria:
{% highlight html %}
    <link rel="stylesheet" href="./css/style.css">
{% endhighlight %}

Ya teniendo claro las formas en que podemos aplicar estilos en CSS, ahora debemos tener en cuenta un tema que es de suma importancia...

## La especifícidad
La especificidad en CSS es el nivel de importancia que tiene un estilo especifico en un elemento con respecto a otros estilos definidos para el mismo archivo HTML.

Primero veamos la forma en que el navegador aplica estilos.

1.	El navegador al renderizar la página carga los archivos HTML y aplica los estilos predefinidos por el mismo navegador, estos estilos dependiendo de tu navegador van a variar, no mucho, pero si variaran 😉
2.	Lo siguiente que hará el navegador es coger los estilos enlazados al archivo HTML y los aplicará aplicarlos.
3.	Finalmente tomara aquellos estilos de suma importancia, definidos con el texto **!important** al final de la sentencia y los aplicara.

Los estilos serán aplicados de manera secuencial según como estén definidos dentro del archivo, es decir que los estilos que sean definidos al final de un archivo serán más importantes a los que se encuentran al inicio. Como ejemplo para explicar este tema tenemos que:
    {% highlight css %}
    h1 {
        color: blue;
    }

    #footer-home {
        color: green;
    }

    .main-p {
        color:yellow;
    }

    h1 {
        color:red;
    }
{% endhighlight %}
Como puedes observar al inicio del código se declara el color de fuente azul para títulos H1 pero más adelante se vuelve a declarar el color de fuente en color, y este se cambia a rojo. Ya que ese estilo sobre escribe al otro.

También debes considerar la especificidad, y aquí es donde a veces a los desarrolladores cuando estamos empezando se les genera un dolor de cabeza al trabajar con CSS, ya que en algunas veces al no tener claro estos principios podemos caer en errores que no son tan fáciles de encontrar.

La especificidad es el nivel de importancia que un estilo va a tener con respecto a otro, es decir que gracias a la especificidad podemos evitar casos como el anterior en donde un estilo pisa (sobrescribe) a otro.

Existen 5 tipos de especificidad, te voy a describir de mayor a menor en importancia cada uno de ellos.

1.	**!important**:la palabra clave !important sirve para definir que un estilo especifico debe estar por encima de cualquier otro, sin importar los demás estilos que más adelante vayan a cambiar el ese estilo en partículas. Ejemplo
{% highlight css %}
    h1 {
        color: blue !important;
        font-weight: bolder;
    }
{% endhighlight %}
2.	**Inline style**: son los estilos que son aplicados directamente dentro de la etiqueta HTML, estos se hacen empleando el atributo style dentro de la etiqueta. mira el ejemplo expuesto mas arriba al momento de aplicar estilos
3.	**#id:** todos los estilos que se apliquen por medio de un ID serán los siguientes en ser aplicados. se sigue la sintaxis mostrada en la descripción de un ID
4.	**.class**: todos los estilos que se apliquen por medio de una clase serán los siguientes en ser aplicados. se sigue la sintaxis mostrada en la descripción de una clase
5.	**Etiqueta HTML**: son los estilos aplicados directamente a las etiquetas HTML.

La siguiente tabla te puede ayudar a recordar la jerarquía de los especificadores.

<table class="table table-striped">
  <thead class="thead-dark">
    <tr>
      <th scope="col">Selector</th>
      <th scope="col">Especificador</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>!important</td>
      <td>1,0,0,0,0</td>
    </tr>
    <tr>
      <td>Inline</td>
      <td>0,1,0,0,0</td>
    </tr>
    <tr>
      <td>#id</td>
      <td>0,0,1,0,0</td>
    </tr>
    <tr>
      <td>.class</td>
      <td>0,0,0,1,0</td>
    </tr>
    <tr>
      <td>Etiqueta HTML</td>
      <td>0,0,0,0,1</td>
    </tr>
  </tbody>
</table>

Algunos editores como VSCode, te permiten identificar la importancia de los estilos que estas aplicando, solo debes pasar el puntero sobre la sentencia y eh un pop up te dará la información. Mira!

<img src="/assets/images/programacion/2020-11/01-code.jpg" alt="Código">