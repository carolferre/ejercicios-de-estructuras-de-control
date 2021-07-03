# ejercicios-de-estructuras-de-control

2.2. Estructuras de Control de Flujo
Una estructura de control, es un bloque de código que permite agrupar instrucciones de manera controlada. En este capítulo, hablaremos sobre dos estructuras de control:

Estructuras de control condicionales
Estructuras de control iterativas

-----------------------------------------------------------------------------
2.2.1. Identación
Para hablar de estructuras de control de flujo en Python, es imprescindible primero, hablar de identación.

¿Qué es la identación? En un lenguaje informático, la identación es lo que la sangría al lenguaje humano escrito (a nivel formal). Así como para el lenguaje formal, cuando uno redacta una carta, debe respetar ciertas sangrías, los lenguajes informáticos, requieren una identación.


 
No todos los lenguajes de programación, necesitan de una identación, aunque sí, se estila implementarla, a fin de otorgar mayor legibilidad al código fuente. Pero en el caso de Python, la identación es obligatoria, ya que de ella, dependerá su estructura.

PEP 8: identación
Una identación de 4 (cuatro) espacios en blanco, indicará que las instrucciones identadas, forman parte de una misma estructura de control.

Una estructura de control, entonces, se define de la siguiente forma:

inicio de la estructura de control:
    expresiones
    
    
-----------------------------------------------------------------------------
2.2.2. Encoding
El encoding (o codificación) es otro de los elementos del lenguaje que no puede omitirse a la hora de hablar de estructuras de control.

Nota
El encoding no es más que una directiva que se coloca al inicio de un archivo Python, a fin de indicar al sistema, la codificación de caracteres utilizada en el archivo.

# -*- coding: utf-8 -*-
utf-8 podría ser cualquier codificación de caracteres. Si no se indica una codificación de caracteres, Python podría producir un error si encontrara caracteres extraños:

print "En el Ñágara encontré un Ñandú"
Producirá un error de sintaxis: SyntaxError: Non-ASCII character[...]

En cambio, indicando el encoding correspondiente, el archivo se ejecutará con éxito:


 
# -*- coding: utf-8 -*-
print "En el Ñágara encontré un Ñandú"
Produciendo la siguiente salida:

En el Ñágara encontré un Ñandú


-----------------------------------------------------------------------------
2.2.3. Asignación múltiple
Otra de las ventajas que Python nos provee, es la de poder asignar en una sola instrucción, múltiples variables:

a, b, c = 'string', 15, True
En una sola instrucción, estamos declarando tres variables: a, b y c y asignándoles un valor concreto a cada una:

>>> print a 
string 
>>> print b 
15 
>>> print c 
True
La asignación múltiple de variables, también puede darse utilizando como valores, el contenido de una tupla:

>>> mi_tupla = ('hola mundo', 2014) 
>>> texto, anio = mi_tupla 
>>> print texto
hola mundo
>>> print anio
2014
O también, de una lista:

>>> mi_lista = ['Argentina', 'Buenos Aires'] 
>>> pais, provincia = mi_lista 
>>> print pais 
Argentina 
>>> print provincia 
Buenos Aires


-----------------------------------------------------------------------------
2.2.4. Estructuras de control de flujo condicionales

 
"[...] Los condicionales nos permiten comprobar condiciones y hacer que nuestro programa se comporte de una forma u otra, que ejecute un fragmento de código u otro, dependiendo de esta condición [...]"

Cita textual del libro Python para Todos de Raúl González Duque (http://mundogeek.net/tutorial-python/)

Las estructuras de control condicionales, son aquellas que nos permiten evaluar si una o más condiciones se cumplen, para decir qué acción vamos a ejecutar. La evaluación de condiciones, solo puede arrojar 1 de 2 resultados: verdadero o falso (True o False).

En la vida diaria, actuamos de acuerdo a la evaluación de condiciones, de manera mucho más frecuente de lo que en realidad creemos: Si el semáforo está en verde, cruzar la calle. Si no, esperar a que el semáforo se ponga en verde. A veces, también evaluamos más de una condición para ejecutar una determinada acción: Si llega la factura de la luz y tengo dinero, pagar la boleta.

Para describir la evaluación a realizar sobre una condición, se utilizan operadores relacionales (o de comparación):

Símbolo	Significado	Ejemplo	Resultado
==	Igual que	5 == 7	False
!=	Distinto que	rojo != verde	True
<	Menor que	8 < 12	True
>	Mayor que	12 > 7	True
<=	Menor o igual que	12 <= 12	True
>=	Mayor o igual que	4 >= 5	False
Y para evaluar más de una condición simultáneamente, se utilizan operadores lógicos:

Operador	Ejemplo	Explicación	Resultado
and	5 == 7 and 7 < 12	False and False	False
and	9 < 12 and 12 > 7	True and True	True
and	9 < 12 and 12 > 15	True and False	False
or	12 == 12 or 15 < 7	True or False	True
or	7 > 5 or 9 < 12	True or True	True
xor	4 == 4 xor 9 > 3	True o True	False
xor	4 == 4 xor 9 < 3	True o False	True


-----------------------------------------------------------------------------
Las estructuras de control de flujo condicionales, se definen mediante el uso de tres palabras claves reservadas, del lenguaje: if (si), elif (sino, si) y else (sino).

Veamos algunos ejemplos:

1) Si semáforo esta en verde, cruzar la calle. Sino, esperar.

if semaforo == verde: 
    print "Cruzar la calle"
else: 
    print "Esperar"

 
2) Si gasto hasta $100, pago con dinero en efectivo. Si no, si gasto más de $100 pero menos de $300, pago con tarjeta de débito. Si no, pago con tarjeta de crédito.

if compra <= 100: 
    print "Pago en efectivo" 
elif compra > 100 and compra < 300: 
    print "Pago con tarjeta de débito" 
else: 
    print "Pago con tarjeta de crédito"
3) Si la compra es mayor a $100, obtengo un descuento del 10%.

importe_a_pagar = total_compra 
if total_compra > 100: 
    tasa_descuento = 10 
    importe_descuento = total_compra * tasa_descuento / 100 
    importe_a_pagar = total_compra – importe_descuento
    
    
-----------------------------------------------------------------------------
2.2.5. Estructuras de control iterativas
A diferencia de las estructuras de control condicionales, las iterativas (también llamadas cíclicas o bucles), nos permiten ejecutar un mismo código, de manera repetida, mientras se cumpla una condición.

En Python se dispone de dos estructuras cíclicas:

El bucle while
El bucle for
Las veremos en detalle a continuación.


-----------------------------------------------------------------------------
2.2.5.1. Bucle while
Este bucle, se encarga de ejecutar una misma acción "mientras que" una determinada condición se cumpla. Ejemplo: Mientras que año sea menor o igual a 2012, imprimir la frase "Informes del Año año".

# -*- coding: utf-8 -*-
anio = 2001 
while anio <= 2012: 
    print "Informes del Año", str(anio) 
    anio += 1

 
La iteración anterior, generará la siguiente salida:


 
Informes del año 2001 
Informes del año 2002 
Informes del año 2003 
Informes del año 2004 
Informes del año 2005 
Informes del año 2006 
Informes del año 2007 
Informes del año 2008 
Informes del año 2009 
Informes del año 2010 
Informes del año 2011 
Informes del año 2012
Si miras la última línea:

anio += 1
Podrás notar que en cada iteración, incrementamos el valor de la variable que condiciona el bucle (anio). Si no lo hiciéramos, esta variable siempre sería igual a 2001 y el bucle se ejecutaría de forma infinita, ya que la condición (anio <= 2012) siempre se estaría cumpliendo.

Pero ¿Qué sucede si el valor que condiciona la iteración no es numérico y no puede incrementarse? En ese caso, podremos utilizar una estructura de control condicional, anidada dentro del bucle, y frenar la ejecución cuando el condicional deje de cumplirse, con la palabra clave reservada break:

while True:
    nombre = raw_input("Indique su nombre: ")
    if nombre:
        break
El bucle anterior, incluye un condicional anidado que verifica si la variable nombre es verdadera (solo será verdadera si el usuario tipea un texto en pantalla cuando el nombre le es solicitado). Si es verdadera, el bucle para (break). Sino, seguirá ejecutándose hasta que el usuario, ingrese un texto en pantalla.


-----------------------------------------------------------------------------
2.2.5.2. Bucle for
El bucle for, en Python, es aquel que nos permitirá iterar sobre una variable compleja, del tipo lista o tupla:

1) Por cada nombre en mi_lista, imprimir nombre

mi_lista = ['Juan', 'Antonio', 'Pedro', 'Herminio'] 
for nombre in mi_lista: 
    print nombre
2) Por cada color en mi_tupla, imprimir color:

mi_tupla = ('rosa', 'verde', 'celeste', 'amarillo') 
for color in mi_tupla: 
    print color
En los ejemplos anteriores, nombre y color, son dos variables declaradas en tiempo de ejecución (es decir, se declaran dinámicamente durante el bucle), asumiendo como valor, el de cada elemento de la lista (o tupla) en cada iteración.

Otra forma de iterar con el bucle for, puede emular a while:

3) Por cada año en el rango 2001 a 2013, imprimir la frase "Informes del Año año":

# -*- coding: utf-8 -*- 
for anio in range(2001, 2013): 
    print "Informes del Año", str(anio)
