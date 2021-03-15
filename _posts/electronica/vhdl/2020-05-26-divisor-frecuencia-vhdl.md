---
layout: post
title: Divisor de frecuencia en VHDL
author: david
category: electronica
tags: ["vhdl"]
description: Un divisor de frecuencia te permitirá tener varios relojes en tu sistema digit al a partir de un único reloj.
image: /assets/images/posts/electronica/2020-05-26-divisor-frecuencia-vhdl/divisor_frecuencia.png
---

En ciertas ocasiones es necesario contar con varios relojes en nuestra aplicación o incluso usar un reloj de menor velocidad al que trae por defecto nuestro sistema, en estos casos lo mejor es usar un divisor de frecuencia.

Un divisor de frecuencia es un contador digital que opera con la frecuencia original del sistema y que al llegar a un valor **n**, el contador vuelve a empezar el conteo y la señal de salida cambia de estado. Como el ejemplo mostrado a continuación donde la señal de entrada es un reloj de 50MHz y la señal de salida es de 5Mhz teniendo un valor de conteo **n** = 10.

![Simulación divisor de frecuencia](/assets/images/electronica/2020-05-26-divisor-frecuencia-vhdl/simulacion-divisorfreq.jpg)

¿Pero y cómo calcular el valor de **n** para tener la frecuencia deseada a la salida de mi divisor? Es sencillo, se debe encontrar un valor de escalamiento (n) dado por la siguiente ecuación:

<img class="imagen-post" src="http://www.sciweavers.org/tex2img.php?eq=n%20%3D%20%5Cfrac%7BFrecuencia%5C%20Entrada%7D%7BFrecuencia%5C%20Salida%7D&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0" align="center" border="0" alt="n = \frac{Frecuencia\ Entrada}{Frecuencia\ Salida}" width="211" height="43" />

Para nuestro ejemplo anterior se tiene que la frecuencia de entrada es de 50MHz y la frecuencia deseada es de 5MHz, por lo que 50M/5M = 10, justo el valor **n** que tenemos definido.

## Código VHDL

A continuación te comparto el **código del divisor de frecuencia** que también encontrarás en el repositorio [módulos VHDL](https://github.com/Daca1953/modulos-VHDL) con el nombre de **divisor de frecuencia**

{% highlight vhdl linenos  %}
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity div_frq is
    generic(n: integer);
    Port(clk_in: in  STD_LOGIC;
         rst  : in  STD_LOGIC;
         clk_out : buffer STD_LOGIC);
end div_frq;

architecture Behavioral of div_frq is

signal contador: integer:=0;
constant max_cont: integer:= n/2;

begin
conteo: process(clk_in, rst)
begin
    if(rst = '1') then
        clk_out <= '0';
    else
        if (clk_in='1' and clk_in'event) then
            if (contador = (max_cont - 1)) then
                contador <= 0;
                clk_out <= not clk_out;
            else
                contador <= contador + 1;
            end if;
        end if;
    end if;
end process conteo;

end Behavioral;
{% endhighlight %}

Para utilizarlo solo debes **agregar el archivo a tu proyecto**, calcular el valor de **n** usando la fórmula que te di antes y finalmente **declarar el componente** dentro de tu entidad principal, aqui te comparto un ejemplo para **n=10**.

{% highlight vhdl linenos  %}
architecture Behavioral of mi_entidad is

--declaracion del componente
component div_frq
generic(n: integer);
port(clk_in: in  STD_LOGIC;
     rst  : in  STD_LOGIC;
     clk_out : buffer STD_LOGIC);
 end component;
--señales
signal clk_in, clk_out, rst: std_logic:='0';
constant n: integer:= 10;

begin
--instancia del componente
uut: div_frq
generic map(
    n => n
    )
port map(
    clk_in => clk_in,
    rst => rst,
    clk_out => clk_out
    );
end Behavioral;
{% endhighlight %}
