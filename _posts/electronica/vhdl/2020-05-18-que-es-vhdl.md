---
layout: post
title: ¿Qué es VHDL?
author: david
category: electronica
tags: ["vhdl"]
description: VHDL es un lenguaje de descripción de Hardware, con él puedes implementar enormes sistemas digitales dentro de pequeños circuitos integrados.
image: /assets/images/posts/electronica/2020-05-18-que-es-vhdl/infografia-vhdl.jpeg
---

 **VHDL** es un acrónimo de *"Very High Speed Integrated Circuit Hardware Description Language"*, en español lo conocemos como **lenguaje de descripción de hardware  para circuitos integrados de alta velocidad**. Hace referencia a un lenguaje con el cual podemos definir la configuracón del hardware de los circuitos digitales, es decir que no tiene el mismo comportamiento al de un lenguaje como C o Java.

Aunque parte de la sintaxis usada en **VHDL** es similar a C, su forma de funcionar es muy diferente, Mientras que en un lenguaje como Java o C++, las instrucciones se ejecutan de manera secuencial, es decir una tras de otra, un script de **VHDL** se ejecuta en **paralelo**, Esto debido a que los circuitos digitales al estar configurados trabajan en tiempo real y no cuando son llamados.

## De donde surgio?
<hr/>
**VHDL** no es una tecnología reciente, data de los años 80, específicamente de 1983, cuando empezó como un proyecto del Departamento de Defensa de Estados Unidos. Sin embargo, en aquella época los costos de fabricación de estos chips eran demasiado altos como para una industria de consumo, por lo que los principales campos de aplicación eran en el area aeroespacial, en telecomunicaciones y apliaciones militares. (*proyectos que tenian los recursos para adquirir la tecnología*)

No obstante, gracias a los avances tecnológicos en la fabricación de chips y otras tecnologías, el costo se ha reducido notablemente con el tiempo, por lo que ahora es posible adquirir tarjetas de desarrollo a un precio razonable, un ejemplo es la tarjeta [Basys 3 de Digilent](https://store.digilentinc.com/basys-3-artix-7-fpga-trainer-board-recommended-for-introductory-users/).

## Cuál es la ventaja de usar VHDL?
<hr/>
Bueno, la verdad es que con la miniaturización de los chips, estos se han vuelto tan pequeños que son capaces de implementar miles de transistores en ellos y con esto es posible crear SoC (System on Chip), chips que  implementan todo un sistema digital en un solo encapsulado, pero te podras imaginar que el proceso de diseño y desarrollo de estos chips no es tarea sencilla, es una tarea compleja y de un cuidado extremo.

Ahí es donde intervienen los lenguajes de HDL como **VHDL** estos permiten diseñar un circuto completamente y programarlo en un chip y hacer un debug mas rapido, evitandose el paso de fabricación de la oblea de silicio, entre otros pasos. ahora podrias diseñar todo un sistema y sacarlo al mercado en el menor tiempo posible y la mejor parte es que te permite podificarlo o agregarle mejoras al poder reprogramar el mismo chip!

Para darte una mejor idea, imagina que usas un microcontrolador en tu proyecto y junto con él usas multiplexores, convertidores BCD e incluso Chips para poder usar una pantalla HDMI o un mouse, tal vez sería una tarjeta de tamaño considerable si usaras cada elemento como un chip por separado, pero si se lograras encapsular todo el sistema en un solo Chip de apenas 1 cm2 empleando **VHDL** y ajustándolo a tus requerimientos, ¿no sería más fácil de implementar y desarrollar?

Otra ventaja no menos despreciable es la **escalabilidad** y **flexibilidad**, supón que ya tienes un diseño elaborado en una FPGA, pero quieres agregarle más funciones, en un Chip SoC esto no sería posible, pero en la FPGA si, solo es modificar el código fuente, agregarle las funciones, hacer pruebas e implementar, como puedes ver, es de gran ayuda el aprender **VHDL**.

![Tarjeta de desarrollo Basys 3](/assets/images/electronica/2020-05-18-que-es-vhdl/vhdl_basys.jpg)