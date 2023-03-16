```
░██████╗██╗░██████╗████████╗███████╗███╗░░░███╗░█████╗░░██████╗  
██╔════╝██║██╔════╝╚══██╔══╝██╔════╝████╗░████║██╔══██╗██╔════╝  
╚█████╗░██║╚█████╗░░░░██║░░░█████╗░░██╔████╔██║███████║╚█████╗░ 
░╚═══██╗██║░╚═══██╗░░░██║░░░██╔══╝░░██║╚██╔╝██║██╔══██║░╚═══██╗  
██████╔╝██║██████╔╝░░░██║░░░███████╗██║░╚═╝░██║██║░░██║██████╔╝ 
╚═════╝░╚═╝╚═════╝░░░░╚═╝░░░╚══════╝╚═╝░░░░░╚═╝╚═╝░░╚═╝╚═════╝░  


██████╗░██████╗░░█████╗░░██████╗░██████╗░░█████╗░███╗░░░███╗░█████╗░██████╗░██╗░░░░░███████╗░██████╗
██╔══██╗██╔══██╗██╔══██╗██╔════╝░██╔══██╗██╔══██╗████╗░████║██╔══██╗██╔══██╗██║░░░░░██╔════╝██╔════╝
██████╔╝██████╔╝██║░░██║██║░░██╗░██████╔╝███████║██╔████╔██║███████║██████╦╝██║░░░░░█████╗░░╚█████╗░
██╔═══╝░██╔══██╗██║░░██║██║░░╚██╗██╔══██╗██╔══██║██║╚██╔╝██║██╔══██║██╔══██╗██║░░░░░██╔══╝░░░╚═══██╗
██║░░░░░██║░░██║╚█████╔╝╚██████╔╝██║░░██║██║░░██║██║░╚═╝░██║██║░░██║██████╦╝███████╗███████╗██████╔╝
╚═╝░░░░░╚═╝░░╚═╝░╚════╝░░╚═════╝░╚═╝░░╚═╝╚═╝░░╚═╝╚═╝░░░░░╚═╝╚═╝░░╚═╝╚═════╝░╚══════╝╚══════╝╚═════╝░


𝓝𝓸𝓶𝓫𝓻𝓮 𝓐𝓵𝓾𝓶𝓷𝓸: 𝓔𝓼𝓽𝓮𝓯𝓪𝓷𝓷𝔂 𝓒𝓻𝓾𝔃 𝓑𝓪𝓻𝓻𝓪𝓭𝓪𝓼
𝓟𝓻𝓸𝓯𝓮: 𝓡𝓮𝓷𝓮 𝓼𝓸𝓵𝓲𝓼 𝓻𝓮𝔂𝓮𝓼
```


# 74HC595, SHIFT REGISTER DE 8 bits

![pic](https://user-images.githubusercontent.com/71289132/223569643-3a687079-6397-413f-9282-c8bb4ea20221.png)

_74HC595 IC (Circuito integrado) es un IC de registro de turnos de 16 pines que consiste en un pestillo de tipo D junto con un registro de turnos dentro del chip. Recibe datos de entrada en serie y, a continuación, envía estos datos a través de pines paralelos. Además de las salidas paralelas, también proporciona una salida serie. Tiene entradas de reloj independientes para el registro de turnos y el pestillo D. Este IC pertenece a la familia HC de dispositivos lógicos que está diseñado para su uso en aplicaciones CMOS._

 # Configuracion de pines
 
 |   **Numero de Pin**  | **Nombre de pin**             | **Descripcion**                                                                                                 |
|-----------------------|-------------------------------|---------------------------------------------------------------------------------------------------------------|
| 1, 2, 3, 4, 5, 6, 7   | Pines de salida (de Q1 a Q7)  | El 74hc595 tiene 8 pines de salida de los cuales 7 son estos pines. Se pueden controlar en serie              |
|          8            | Tierra                        | Conectado al suelo del circuito                                                                               |
|          9            | (P7) Salida en serie          | Este pin se utiliza para conectar más de un 74hc595 como cascada                                              |
|          10           | (MR) Restablecimiento maestro | Restablece todas las salidas como bajas. Debe mantenerse alto para el funcionamiento normal                   |
|          11           | (SH_CP) Reloj                 | Éste es el pin del reloj al cual la señal del reloj tiene que ser proporcionada del MCU/MPU                   |
|          12           | (ST_CP) Pestillo              | El pasador de pestillo se utiliza para actualizar los datos a los pinesde salida. Es activo alto              |
|          13           | (OE) Activación de salida     | El permiso de salida se utiliza para desactivar las salidas. Debe mantenerse bajo para el funcionamiento norma|
|          14           | (DS) Datos en serie           | Este es el pin al que se envíanlos datos, basado en el cual se controlan las 8 salidas                        |
|          15           | (P0) salida                   | El primer pasador de salida.                                                                                  |
|          16           | Vcc                           | Este pin alimenta el IC, normalmente se utiliza +5V.                                                          |


# Registo de turnos
Un registro de turnos es básicamente un IC convertidor en seriea-paralelo. Básicamente toma una entrada en serie a través de un solo pin y lo convierte en salida paralela de 8 bits reduciendo así eficazmente el número de pines de interfaz entre un Microcontrolador y sus dispositivosde salida.

Si su proyecto necesita controlar 16 LED individuales, normalmente requeriría 16 pines de un Arduino. En el caso de que no tenga 16 pines de E/S disponibles, aquí es donde el registro de turnos es útil. Con dos registros de turnos conectados en serie, podemos realizar la tarea de controlar los 16 LED con el uso de sólo 3 pines de E/S. Y no sólo esto; puede guardar aún más pines cuantos más registros de turnos haya encadenado.

_Un ejemplo del mundo real que utiliza el registro de turnos es el ‘Controlador original de Nintendo’. El controlador principal del Nintendo Entertainment System necesitaba obtener todas las pulsaciones de botón en serie, y utilizó un registro de turnos para realizar esa tarea._

# Diagrama de circuitos

La siguiente imagen muestra el diagrama de circuitos de interconexión del registro de turnos 74HC595 con Arduino UNO.

Componentes requeridos

* Arduino UNO
* 74HC595 Registro de turnos IC
* Protoboard
* 8 X LED
* Resistencias de 8 X 1KΩ
* Fuente de alimentación de 5V
* Conexión de cables


