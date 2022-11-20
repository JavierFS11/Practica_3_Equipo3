# Practica_3_Equipo3
En esta practica realizamos la Creación de un servidor de captura de imágenes y vídeo con el microcontrolador ESP32 CAM.


## Objetivos
Programar un servidor webcam usando el controlador ESP32 CAM, el IDE de Arduino y Python para capturar y visualizar imágenes y vídeo.


EL ESP32 CAM es un SoC (System On a Chip), fabricado por la empresa AI Thinker, es una tarjeta de desarrollo que integra una pequeña cámara OV2640 2MP que puede funcionar de manera independiente además de un módulo WiFi con Bluetooth. La cámara OV2640 de 2MP integra un sensor de imagen CMOS UXGA (1632x1232) de 1/4 de pulgada. El pequeño tamaño del sensor y el bajo voltaje de operación brindan todas las características de una sola cámara UXGA y un procesador de imágenes. A través del control de bus SCCB, puede generar datos de imagen de 8/10 bits de varias resoluciones, como fotograma completo, submuestreo, zoom y ventanas. La imagen UXGA de esta cámara puede alcanzar hasta 15 cuadros por segundo (hasta 30 cuadros para SVGA y 60 cuadros para CIF). Los usuarios tienen un control completo sobre la calidad de la imagen, el formato de datos y la transmisión.
La plataforma ESP32 permite el desarrollo de aplicaciones en diferentes lenguajes de programación, frameworks, librerías y recursos diversos. Los más comunes a elegir son: Arduino (en lenguaje C++), Esp-idf (Espressif IoT Development Framework) desarrollado por el fabricante del chip, Simba Embedded Programming Platform (en lenguaje Python), RTOS's (como Zephyr Project, Mongoose OS, NuttX RTOS), MicroPython, LUA, Javascript (Espruino, Duktape, Mongoose JS), Basic. Al trabajar dentro del entorno Arduino podremos utilizar un lenguaje de programación conocido y hacer uso de un IDE sencillo de utilizar, además de hacer uso de toda la información sobre proyectos y librerías disponibles en internet. La comunidad de usuarios de Arduino es muy activa y da soporte a plataformas como el ESP32 y ESP8266. Dentro de las principales placas de desarrollo o módulos basados en el ESP32 tenemos: ESP32-WROOM-32, NodeMCU-32 ESP32 y ESP32-CAM y de la familia ESP8266 tenemos: ESP-01, ESP-12E, Wemos D1 mini y NodeMCU v2.
Todo lo anterior permite usar el controlador en una gran cantidad de sistemas embebidos que requieran el procesamiento de imágenes. 
Especificaciones técnicas del ESP32 CAM
	Voltaje de alimentación: 5VDC
	Voltaje entradas/salidas (GPIO): 3.3VDC
	SoM: ESP-32S (Ai-Thinker)
	SoC: ESP32 (ESP32-D0WDQ6)
	CPU: Dual core Tensilica Xtensa LX6 (32 bit)
	Frecuencia principal de hasta 240 MHz
	Potencia informática de hasta 600 DMIPS
	Velocidad de reloj de hasta 160 MHz
	Wifi 802.11b/g/n, Bluetooth 4.2
	Antena PCB, también disponible conexión a antena externa
	520KB SRAM interna, 4MB SRAM externa
	Soporta UART/SPI/I2C/PWM/ADC/DAC
	Incluye socket para TF card micro-SD
	Cámara OV2640
	Resolución fotos: 1600 x 1200 pixels
	Resolución vídeo: 1080p30, 720p60 y 640x480p90
	Incluye LED de flash en placa
	Óptica de 1/4"
	Dimensiones: 27*40.5*6 mm
	Peso: 20 gramos
	Para mayor cantidad de información revisar el datasheet de la tarjeta en este vínculo 

Lenguajes en los que se puede programar el ESP32 CAM
	Arduino IDE (en lenguaje C++),
	Esp-idf (Espressif IoT Development Framework) desarrollado por el fabricante del chip,
	Simba Embedded Programming Platform (en lenguaje Python)
	MicroPython
	Javascript (Espruino, Duktape, Mongoose JS)
	Atom
	Etc.
El esp32 es una placa de bajo costo y grandes capacidades, integra CPU, memoria RAM volátil y no volátil (Para el programa) y varios dispositivos de I/O (Entrada y salida) en un chip único, además de dispositivos de comunicaciones variados, que podemos emplear para recibir y enviar información al exterior. Básicamente el ESP32 es capaz de recibir señales digitales (Digital Inputs), enviar señales digitales (Digital Output), recibir señales analógicas en tensión (Analog Input) mediante ADCs,   enviar señales analógicas al exterior (Analog Output) como señales moduladas en pulsos PWM y con 2 convertidores digital a analógico (DAC) detectar variaciones de capacidad en los pines adecuados, además de comunicarse con el exterior de forma cableada con Buses I2C integrados, buses SPI integrados y  puertos UART o serie programables. También puede comunicarse con el exterior de forma inalámbrica: puerto WiFi integrado con stack TCPIP y puerto Bluetooth 5. En esta práctica usaremos la mayor cantidad de capacidades para obtener imágenes digitales. 
Imágenes del microcontrolador ESP32 CAM
![image](https://user-images.githubusercontent.com/114626288/202924951-53f0871c-e91e-42b4-b836-8d9ccb7a478c.png) 
Imagen 1. Vista posterior y anterior del microcontrolador ESP32 Cam con cámara OV2640 de 2 MP. En la imagen de abaja se muestra un ESP32 CAM conectado a un circuito convertidor usb-ttl para programarlo y alimentar la corriente de 5 V. El cable utilizado es USB a mini-usb.

![image](https://user-images.githubusercontent.com/114626288/202924934-920fa681-0764-4eee-afe2-d2c76fb2b219.png)
Imagen 2. Detalle del circuito convertidor usb-ttl, esta placa permite la comunicación serial entre la computadora el ESP32 CAM.
Material Necesario
	Microcontrolador ESP32 CAM con cámara OV2640
	Circuito convertidor USB-TTL
	Cable de datos USB-USB mini
	Cable de red
	Computadora 
	Modem (se conectará el esp32 con SSID y el password del modem)

Software necesario
El software se instalará en la computadora donde conectaremos nuestro ESP32 CAM. Respetar la versión del software que se indica para evitar conflictos entre las bibliotecas.  
•	IDE de Arduino 1.8.19
•	Drivers (Windows) para el esp32 cam (se comparte en el material semanal)
•	IDE de Python (se recomienda la versión 3.7 de Python)
o	La biblioteca OpenCv para python versión 4.2.x
•	Bibliotecas de Arduino para el manejo del esp32 CAM
o	https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json  (en preferencias-- Gestor de URLS)
o	Instalar en el <gestor de tarjetas del IDE de Arduino> la tarjeta ESP32 de Expressif Systemas
o	La biblioteca CameraWebServer de los ejemplos para la ESP32 CAM de AI Thinker
•	Navegador web  
