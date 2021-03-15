---
layout: post
title: Declarar una entidad en VHDL
author: david
category: electronica
tags: ["vhdl"]
description: En VHDL la entidad es la parte del código que describe físicamente el sistema.
image: /assets/images/posts/electronica/2020-05-21-entidad-vhdl/entidad-vhdl.jpg
---
La estructura básica de una diseño en VHDL se basa en dos elementos, la entidad (*entity*) y la arquitectura (*architecture*). Estos elementos en conjunto forman la columna vertebral de un componente descrito en VHDL, en esta entrada hablaremos de la **entidad**.

## Entidad (*entity*)
<hr>

La entidad es la parte del código donde se realiza la descripción física del circuito que se va a diseñar, es decir, que corresponde a la descripción de los pines que la componen así como su modo de operación, el tipo de dato y su identificador. ¿pero qué es cada una de estas partes?

Primero el **identificador**, este es el nombre que se le asigna al pin o al puerto que se está creando, una buena practica es que el nombre sea descriptivo, para un mejor entendimiento del código. Puede contener letras, números y guiones bajos( _ ), sin embargo el primer carácter siempre debe empezar con una letra.

VHDL **NO es Case Sensitive**, lo que significa que no diferencia entre mayúsculas y minúsculas. es lo mismo escribir **PIN_A** que **pin_a**

Seguido del identificador se debe definir el **modo** de operación, el cual corresponde al estado del pin (o del puerto), definiendo si este será de entrada, salida, bidireccional o retroalimentado.

 - **IN**: configuración como entrada.
 - **OUT** : configuración como salida únicamente.
 - **INOUT**:   configura el pin como bidireccional.
 - **BUFFER**: en este modo el pin se comporta exclusivamente como salida pero tiene la ventaja de que se puede usar como retroalimentación dentro de la entidad.

![Tipos de entrada a una entidad](/assets/images/electronica/2020-05-21-entidad-vhdl/entidad-vhdl.jpg)

Por último el **tipo** de dato es la información que va a representar cada puerto, entre los tipos de datos más comunes se encuentran el bit, std_logic, Integer, entre otros.

Para explicar cada parte de la entidad desarrollemos el siguiente ejemplo, supongamos que queremos declarar el siguiente circuito digital, compuesto por dos compuertas AND y una compuerta OR.

![Circuito de guia](/assets/images/electronica/2020-05-21-entidad-vhdl/circuito-entidad-vhdl.jpg)

En él tenemos cuatro entradas **a, b, c** y **d** que son las entradas a las compuertas AND, y tenemos una salida que corresponde al pin **x**, para declarar la entidad debemos tener en cuenta la siguiente sintaxis

{% highlight vhdl linenos  %}
entity sistema_digital is
    port ( a,b,c,d: in std_logic;
           x: out std_logic);
end sistema_digital;
{% endhighlight %}

 Como puedes darte cuenta la declaración de una entidad empieza con la palabra reservada **entity** seguida del nombre que le asignaras, en este caso *sistema_digital* y finalmente seguida de la palabra reservada **is**. Posteriormente se declara los pines del componente dentro de la palabra definida ***port ( );***  donde declaran los pines **a, b, c** y **d** como entradas del tipo std_logic y separadas por comas, y el pin **x** como salida del tipo std_logic. Y finalmente se termina la declaración de la entidad con la palabra reservada **end** y el nombre de la entidad *sistema_digital*.

### Uso de vectores
En VHDL también es posible usar vectores para representar un puerto, esto facilita la asignación de pines y operaciones en conjuntos de bits. Para el ejemplo anterior el resultado del código podría ser el siguiente

{% highlight vhdl linenos  %}
entity sistema_digital is
    port ( a: in std_logic_vector (3 downto 0);
           x: out std_logic);
end sistema_digital;
{% endhighlight %}

o de la siguiente forma

{% highlight vhdl linenos  %}
entity sistema_digital is
    port ( a: in std_logic_vector (0 to 3);
           x: out std_logic);
end sistema_digital;
{% endhighlight %}

Donde él **(3 downto 0)** representa el indexado que se usará para el vector en este caso el bit más significativo sera asignado a la posición 3 y el menos significativo sera asignado a la posición 0.

De igual forma si se usará **(0 to 3)**, el bit más significativo se asignara a la posición 0 y el menos significativo a la posición 3.

![Vectores en VHDL](/assets/images/electronica/2020-05-21-entidad-vhdl/vector-entidad-vhdl.jpg)

