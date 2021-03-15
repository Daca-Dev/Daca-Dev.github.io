---
layout: post
title: MicroPython y ESP8622 - Instalando el Firmware
author: david
category: electronica
tags: ["esp8266","micropython"]
description: descarga e instala el firmware necesario para empezar a programar microcontroladores usando MicroPython.
image: /assets/images/posts/electronica/upython.jpg
---

<a href="https://www.micropython.org/" target="_blank">MicroPython</a> es una nueva forma de programar que ha empezado a tomar fuerza en los últimos años, gracias a que permite programar una variada cantidad de microcontroladores empleando el lenguaje Python.

Debes tener en cuenta que no tiene completamente la potencia con que cuenta Python, debido a la limitación de Hardware, pero es capaz de hacer increíbles aplicaciones, al final es decisión del diseñador escoger las herramientas de diseño que mejor se adaptan a su proyecto.

> Para estas prácticas usare la tarjeta de desarrollo NodeMCU que emplea un chip **ESP8266**.

Para iniciar con MicroPython es necesario tener tres programas/Firmware, listados a continuación:


- **<a href="https://www.python.org/downloads/" target="_blank">Python 3.8:</a>** Lenguaje de programación python, que sera la base del interprete.
- **<a href="https://www.micropython.org/download/all/" target="_blank">Firmware de tu dispositivo:</a>** Debes buscar en la lista del enlace el Firmware relacionado con tu tarjeta de desarrollo, para mi caso es <a href="https://www.micropython.org/resources/firmware/esp8266-1m-20200408-v1.12-351-gbd5633778.bin" target="_blank">este</a>.
- **<a href="https://dfrobot.gitbooks.io/upycraft/content/" target="_blank">uPyCraft:</a>** IDE para programar y quemar el Fimraware de nuestras tarjetas, esta disponible para Windows y Mac

## Proceso de instalación:

Antes de empezar con el proceso te recomiendo crear una carpeta en donde guardes los ejecutables y los archivos de tus proyectos, en mi caso lo hice así.

<img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/micropython-dir.jpg" alt="Directorios de ejemplo">

1. Instalar la Python, recuerda que debe ser una versión 3.8.x
2. Abrir el programa **uPycraft.exe** como administrador, al abrirlo se desplegará la siguiente pantalla.

<img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/upychart-window.jpg" alt="uPyChart window">

> Si se abre un mensaje con el texto *"Please install SourceCodePro Font*, simplemente dale en cancelar.

3. Quemar el Firmware que previamente descargamos en nuestra tarjeta, para ello te debes dirigir al menú de la barra superior y seleccionar:

    - Tools > Serial > "El puerto al que esta conectada tu tarjeta (en mi caso COM7)"

    <img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/upychart-serial.jpg" alt="Serial port">

   - Tools > Board > "El modelo de microcontrolador"

   <img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/upychart-board.jpg" alt="Board">

   - Tools > BurnFrimware

    <img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/upychart-burn.jpg" alt="BurnFrimware">

    Se desplegará la siguiente ventana en donde deberás definir el path en donde está alojado el archivo .BIN del firmware de nuestra tarjeta, como se muestra en la imagen.

    <img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/upychart-burnfrimware.jpg" alt="bunrfrimware configuration">

    Finalmente presiona OK y se empezara el proceso de copiado del firmware en el dispositivo, es recomendable limpiar la memoria flash del dispositivo sobre todo si estas sobrescribiendo un firmware diferente como el de Arduino o Lua.

    <img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/burn-frimware-action.jpg" alt="Burnfrimware process">

## Prueba de funcionamiento

Al terminar el proceso de instalación, sigue el paso de verificar el resultado, para ello haremos el clásico Hola mundo, dado que el objetivo de este artículo es mostrar como instalar el firmware de MicroPython, no profundizaremos en el codigo.

> En futuras entradas del Blog se desarrollarán guías y proyectos con dicho lenguaje.

Al haber definido el puerto de comunicación y el tipo de tarjeta en tu ventana se debe de crear el siguiente directorio, que contendrá el archivo *Boot.py*.

<img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/upychart-probe.jpg" alt="Prueba funcionamiento">

para hacer la prueba de funcionamiento, crea un archivo nuevo y guárdalo como led.py (o el nombre que gustes) y escribe el siguiente código.

{% highlight python linenos %}
    from machine import Pin
    import time

    led = Pin(16, Pin.OUT)

    while True:
        led.on()
        time.sleep(0.5)
        led.off()
        time.sleep(0.5)
{% endhighlight %}

A groso modo este código importa el módulo time y la Clase Pin del módulo machine, declara una variable llamada led a la que asignamos la clase pin que relaciona el pin 16 de mi tarjeta y su modo de operación, en este caso como salida.

para probar el funcionamiento presionamos F5 o nos dirigimos al menú de la barra superior a Tools > DownloadAndRun

<img class="imagen-post" src="assets/images/posts/electronica/2020-07-16-micropython-esp8266/console-probe.jpg" alt="Mensaje de consola">

en este punto el LED implementado dentro de la tarjeta deberá estar parpadeando cada 500ms

> para saber que pin está asociada al LED incorporado en la tarjeta es útil guiarse del <a href="https://i1.wp.com/www.teachmemicro.com/wp-content/uploads/2018/04/NodeMCUv3.0-pinout.jpg?ssl=1" target="_blank">Esquema pinout</a> de la tarjeta de desarrollo en donde podemos observar que el LED de usuario bajo la etiqueta **User** está asignado al pin 16 de nuestra tarjeta.

> si estas usando otro microcontrolador es tu tarea buscar en la documentación técnica la distribución de pines y su referencia.
