---
layout: post
title: Ensambla tu Heatbed
author: david
category: impresion-3d
tags: ["prusa-i3"]
description: La cama caliente o heatbed es una pieza fundamental de tu impresora, ¡es la que soportara tu pieza!
---

El **Heatbed** o también conocido como cama caliente, es la pieza de tu impresora en donde se soportara la pieza durante la impresión y  es la encargada de mantener una temperatura constante en la base de tu pieza durante la impresión, esto ayuda a evitar problemas como el wraping.

> El wraping sucede cuando la temperatura del material tiene cambios bruscos y debido a la difernecia termica del material este tiende a contraerse y finalmente se despega de la cama caliente.

<img class="imagen-post" src="/assets/images/posts/impresion 3d/heatbed-ensamble.jpg" alt="Cama Caliente o heatbed">

La cama caliente que utilizaremos es el modelo [*Heatbed MK2A*](https://reprap.org/wiki/PCB_Heatbed), este tiene un tamaño total de 214x214 mm y un área de impresión de 200x200 mm, la ventaja de este modelo es que te permite configurar si la quieres usar para 24V o 12V, en mi caso será de 12V.

Los materiales que necesitas son:

- Heatbed MK2A
- Cable de dos hilos calibre (calibre 12 a 16)
- Resistencia SMD de 1Kohm (encapsulado 0805)
- Led SMD (encapsulado 0805)
- Sensor de Temperatura NTC de 100Kohm
- Cinta térmica
- Pasta térmica
- Soldadura y estación para soldar.

<img class="imagen-post" src="/assets/images/posts/impresion 3d/materiales-ensamble.jpg" alt="Materiales">

> Si la cama la usaras con una fuente de 24v, necesitarás emplear resistencias de 2Kohm

El siguiente paso es soldarlo teniendo en cuenta la polaridad de los LEDs.

<img class="imagen-post" src="https://reprap.org/mediawiki/images/0/02/PCB_HEATBED_DIAGRAM_r.jpg" alt="Esquema de conexión">

> Ten encuenta que los componentes SMD son sensibles al calor, por lo que si estas usando un cautin en vez de una pistola de soldar debes regular la temperatura.

En mi opinión deberías soldar primero la resistencia y los LEDs ya que es más sencilla hacerlo sin el cable soldado. Para el cable sería ideal usar un cautín de 35W para que te sea más sencillo soldarlo. Pero recuerda que si usas este mismo cautín para los componentes SMD podrías dañarlos, a menos que dispongas de una estación de soldar que te permita regular la potencia.

A continuación realiza la prueba a la cama caliente conectándola a una fuente de 12V (o 24V si es tu caso) y verifica que esta empieza a calentarse y que los LEDs prenden correctamente.

<img class="imagen-post" src="/assets/images/posts/impresion 3d/test-ensamble.jpg" alt="Prueba de la cama caliente">

> Has la verificacion y desconecta la cama caliente rapidamente, para evitar accidentes, ya que al conectarla directamente a la fuente no tienes forma de aplicar control de temperatura y esta se calentara a su maximo hasta dañarse.

Finalmente solo resta añadir el sensor de temperatura, para ello lo insertaremos en el agujero que tiene la cama en el centro y lo pegaremos con abundante cinta, que quede bien fijo a la cama y añadiremos un poco de crema para facilitar la transferencia térmica. Por último taparemos el agujero con el sensor con más cinta para evitar que el sensor o la crema térmica se salga de su posición. Teniendo como resultado:

<img class="imagen-post" src="/assets/images/posts/impresion 3d/sensor-ensamble.jpg" alt="Resultado final">