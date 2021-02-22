---
# layout
layout: post
toc: false
hide_share_buttons: false

# metadata
title: Extrae data de la web con Scrapy
author: david
category: programacion
tags: ["scrapy"]
summary: Scrapy es un framework de Python que te permite crear tu propia arana para obtener data de la web.
---


Scrapy es un framework de código abierto para Python que te permite implementar tu propia araña para raspar la web, es fácil de manejar pero debes tener claros ciertos conceptos para poder sacarle el mayor provecho a esta potente herramienta y en **Daca Programming** te enseñamos a usarla.

> Obtendremos las citas y sus respectivos autores que se encuentran en la siguiente página: <a  href="https://www.goodreads.com/quotes?page=1"  target="_blank">https://www.goodreads.com/quotes?page=1</a>

## Puesta en marcha

>- Para este tutorial necesitaras tener instalado el modulo **Scrapy**, ten en cuenta que este solo esta disponible para Python 3.5 o superior.

>- tambien necesitaras tener conocimientos de **selectores CSS** y de la estructura basica de **HTML** en el blog podras encontrar un articulo referente a los <a  href="/404"  target="_blank">Selectores CSS</a>

Para empezar abriremos nuestro entorno de trabajo de preferencia, en mi caso es **VSCode**, a continuación abriremos la *terminal* y nos dirigimos al directorio donde queremos crear nuestro proyecto. En mi caso se llama es *D:\programming* y crearé un proyecto denominado **tutorial_Scrapy**, para ello ejecutamos el comando.

{% highlight console linenos %}
scrapy startproject tutorial_scrapy
{% endhighlight %}

Al ejecutar el comando se creará un nuevo directorio con el nombre del proyecto, el siguiente paso será abrir el folder en VSCode o en el entorno que estés usando y encontraras una estructura de archivos como la siguiente.

<img  class="imagen-post"  src="/assets/images/posts/programacion/dir-princ.jpg"  alt="Directorio del proyecto">

Estos archivos tienen un propósito general que se abordaran en futuros artículos, pero por ahora nos centraremos en crear nuestra araña, para ello necesitamos crear un archivo dentro de la *carpeta spiders* en nuestro directorio de trabajo con el nombre que deseemos, en nuestro caso **quotes.py**. Abrimos el archivo y escribimos el siguiente código:

{% highlight python linenos %}
# -*- coding: utf-8 -*-
import scrapy

class QuotesSpider(scrapy.Spider):
    name = 'quotes'

    def start_requests(self):
        urls = ['https://www.goodreads.com/quotes?page=1']

        for url in urls:
            yield scrapy.Request(url=url, callback=self.parse)
{% endhighlight %}

En este código se define el nombre de nuestra araña con la variable **name** que en este caso es **'quotes'**, posteriormente se define el metodo **start_requests**. Dentro de esta función se declara la lista de **urls** en donde escribiremos cada una de las urls que queremos buscar(en nuestro caso una). Seguido de la lista se emplea un *for loop* para recorrer cada elemento de la lista **urls** y hacer una petición HTTP a cada una de ellas por medio de la función *Request* de Scrapy, la respuesta de esta solicitud será tratada por el método **parse** que escribiremos justo debajo del código que ya tenemos.

> El nombre de cada araña en un poryecto debe ser **unico** ya que este es usado por el modulo scrapy al ejecutar la araña.

{% highlight python linenos %}
def parse(self, response):
    for quote in response.css('div.quoteText'):
        yield {
            'texto': quote.css('::text').get(),
            'autor': quote.css('span.authorOrTitle::text').get()
        }
{% endhighlight %}

 La función **parse** que te compart    o realiza la extracción de información (cita y autor) empleando selectores CSS y el método **.css('expresion')**

> Si no tienes conocimientos de los selectores CSS <a  href="/404"  target="_blank">aqui</a> te doy una introducción a estos.

Para obtener la expresión del objeto que queremos extraer (cita y autor) debemos analizar la estructura HTML con ayuda de un navegador como firefox o Chrome, en mi caso empleo firefox. Estando en la <a  href="https://www.goodreads.com/quotes?page=1"  target="_blank">página</a> damos clic derecho sobre el elemento que queremos obtener y después en inspeccionar elemento

<img class="imagen-post" src="/assets/images/posts/programacion/inspeccionar.jpg" alt="Inspección de elementos">

Podemos observar que cada cita se encuentra dentro de la etiqueta **\<div>** cuya clase es **quoteText**. Teniendo esta información podemos generar nuestra expresión CCS de la siguiente manera.

{% highlight html %}
    'div.quoteText'
{% endhighlight %}

En donde le decimos al selector que busque todas las etiquetas **\<div>** de clase **quoteText**, y que cada elemento que coincida con la búsqueda sea guardado dentro de una lista.

La estructura de estos elementos tienen la siguiente forma:

{% highlight html %}
<div class="quoteText">
      “Be yourself; everyone else is already taken.”
  <br>  ―
  <span class="authorOrTitle">
    Oscar Wilde
  </span>
</div>
{% endhighlight %}

Analizando la estructura anterior podemos observar que el texto está contenido en las primeras líneas de la etiqueta **\<div>**, para extraerlo solo necesitamos traer el texto que está contenido en él (no etiquetas), para ellos empleamos la expresión **'::text'** la cual devolverá el texto contenido en la etiqueta y finalmente empleamos el método **.get()** para extraer el primer elemento, en caso que se encontraran más de un elemento.

Para el autor realizaremos el mismo proceso, podemos observar que el nombre del autor está contenido dentro de las etiquetas **\<span>** cuya clase es **authorOrTitle**, con esto podemos generar nuestro selector CSS, siendo esta **'span.authorOrTitle::text'** si te das cuenta empleamos la misma función para extraer el texto contenido entre las etiquetas y el método **.get()** para extraer el primer elemento.

Esto seria todo para nuestro código, puedes consultarlo todo completo en el <a  href="https://github.com/Daca1953/tutorial_scrapy"  target="_blank">repositorio</a> en donde sé ira completando el código a medida que se hagan publicaciones en el Blog.

Para poner en marcha la arana debes ejecutar en la consola el siguiente comando de scrapy:

{% highlight console linenos %}
scrapy crawl quotes -o quotes.json
{% endhighlight %}

Este comando lo que le especifica a scrapy es que ejecute la araña cuyo nombre es **quotes** y que los datos que este devuelva se guarden en el archivo **quotes.json**, al ejecutar el comando verás en consola algo como esto:

<img class="imagen-post" src="/assets/images/posts/programacion/consola-scrapy.jpg" alt="Araña en ejecución">

Al terminar la ejecución, en el directorio del proyecto encontrarás un nuevo archivo llamado **quotes.json** que contendrá las citas que se encontraban en la página, cuyo contenido debe ser parecido a este:

<img class="imagen-post" src="/assets/images/posts/programacion/resultado-scrapy.jpg" alt="Archivo generado">