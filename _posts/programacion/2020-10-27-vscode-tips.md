---
layout: post
title: Tips para Codear en VS Code
author: david
category: programacion
tags: ["VScode", "Tips"]
description: >-
    Si te gusta programar y crea código. sabrás que es una tarea que implica mucha creatividad y orden. 
    Por eso te comparto unos tips breves pero que potenciaran tu habilidad para escribir código.
---
Si te gusta programar y crear código. sabrás que es una tarea que implica mucha creatividad y orden. Por eso es importante conocer algunas ayudas que te permitan ahorrar tiempo en la escritura del código y te permitan enfocar en la creatividad.

**VS Code** es uno de los IDE's más usados en la actualidad por sus múltiples beneficios y extensiones que te permiten codear casi en cualquier lenguaje de manera amigable. En este articulo te comparto unos breves pero increíbles tips. Que puedes usar en este IDE para mejorar tu desarrollo 😉

## múltiples cursores

Emplear varios cursores es muy útil cuando crearas bloques de código similares.

Supongamos que quieres escribir este codigo.

{% highlight html %}
<div class="col"></div>
<div class="col"></div>
<div class="col"></div>
<div class="col"></div>
{% endhighlight %}

Una opción es escribir una línea y copiarla, pero una más sencilla es usar cuatro cursores y escribir todo de una sola vez. cómo hacerlo?

Usando el comando.

{% highlight console %}
    Ctrl. + Alt. + [⬆️ or ⬇️]
{% endhighlight %}

Dependiendo de la flecha que presiones el cursor se desplazara hacia arriba o hacia abajo creando un nuevo cursor.

Si este comando no sirviera en Windows 10, sino por el contrario te pusiera patas arriba la ventana. agrégale **shift** al comando y ya está.

{% highlight console %}
    Ctrl. + Shift + Alt. + [⬆️ or ⬇️]
{% endhighlight %}

El resultado será algo así.

{% highlight html %}
<div class="col">|</div>
<div class="col">|</div>
<div class="col">|</div>
<div class="col">|</div>
{% endhighlight %}

Si quieres usar varios cursores, pero en lugares diferentes. es sencillo!

Simplemente presiona **Alt.** y con el botón izq. del mouse da clic en la posición que quieres crear el nuevo cursor. tendrás algo así.

Tendrás algo así.

{% highlight html %}
<div class="container">|
    <div class="row">|
        <div class="col"></div>|
        <div class="col"></div>
        <div class="col"></div>
    </div>|
</div>
{% endhighlight %}

<hr/>

## Copiar, Cortar, eliminar ... rapido!

Si quieres copiar, cortar, eliminar líneas rápidamente. no uses el clásico **Ctrl. + X** y **Ctrl. + V**. por el contrario, prueba con:

#### Copiar y pegar

{% highlight console %}
    Shift. + Alt. + [⬆️ or ⬇️]
{% endhighlight %}

Copia la línea que en donde está posicionado el cursor y la pega arriba o abajo dependiendo de la flecha que hayas seleccionado.

#### Eliminar una fila

{% highlight console %}
    Ctrl. + Shift. + k
{% endhighlight %}

Eliminaras toda la línea en donde está posicionado el cursor.

#### Desplazar una fila

Si lo que quieres es mover toda una fila a una posición diferente dentro del mismo código. simplemente usa el comando

{% highlight console %}
    Alt. + [⬆️ or ⬇️]
{% endhighlight %}

<hr>

## Encontrar ocurrencias

Si quieres seleccionar todas las ocurrencias dentro del archivo de una selección de texto. Usa el comando.

{% highlight console %}
    Ctrl. + F2
{% endhighlight %}

Si buscas es seleccionar las ocurrencias a partir del curso. simplemente posiciona el cursor en alguna parte de la palabra y presiona

{% highlight console %}
    Ctrl. + D
{% endhighlight %}

Esto hará que se seleccione la palabra y si vuelves a presionar el comando. se seleccionará la siguiente ocurrencia. así hasta que no haya más ocurrencias o el programador no lo vea más necesario.

<hr>

## Dar formato al código

Para dar formato al código. en lugar de presionar **Tab, Space, Del**. puedes presionar

{% highlight console %}
    Shift. + Alt. + F
{% endhighlight %}

Esto automáticamente ajustara el formato de tu código al lenguaje que estas usando.

Por defecto **VS Code** trae instaladas extensiones para formatear código JS, HTML, CSS, entre otros. pero fácilmente puedes buscar formateadores para otros lenguajes como Python y PHP en la tienda de la App.

<hr>

## Contraer y expandir bloques de código

Algunas veces el codigo se vuevle extenso. y algunos bloques que ya hemos terminado ocupan mucho espacio. y es claro que no puedes eliminarlo pero su puedes contraer esos bloques de tal forma que no ocupen tanto espacio en la venta. es sencillo de hacer.

spon que tienes el siguiente comando.

{% highlight console %}
    Ctrl. + Shift. + [' or ¿]
{% endhighlight %}

Si usas la tecla **'** contraerás el bloque de Código. pero si presionas **¿** expandirás los bloques (si es que es posible)

Supón el siguiente ejemplo. En donde quieres contraer el *contenedor-1*. entonces presionamos el comando con la tecla **'**

{% highlight html %}
<div class="container-1">
    <div class="row">
        <div class="col"></div>
        <div class="col"></div>
        <div class="col"></div>
    </div>
</div>

<div class="container-2">
    <div class="row">
        <div class="col"></div>
        <div class="col"></div>
        <div class="col"></div>
    </div>
</div>
{% endhighlight %}

se contraerá el bloque superior y veras algo así.

{% highlight html %}
<div class="container-1">...

<div class="container-2">
    <div class="row">
        <div class="col"></div>
        <div class="col"></div>
        <div class="col"></div>
    </div>
</div>
{% endhighlight %}

Espero estos pequeños tips te ayuden a la hora de codear y te permitan concentrar mas en la creatividad y en el ingenio. 🤓