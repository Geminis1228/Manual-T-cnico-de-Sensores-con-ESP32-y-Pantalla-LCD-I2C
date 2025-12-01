Proyecto de Sensores y Piano Digital con ESP32
🏫 Proyecto Escolar – Sistemas Programables

Este repositorio contiene tres proyectos electrónicos funcionales desarrollados con un ESP32, utilizando sensores, buzzer, pantallas LCD y pruebas controladas.

📂 Contenido del Proyecto

🎹 Piano digital con 7 botones y buzzer

🌱 Sensor de humedad del suelo (1 sensor, 3 macetas)

🌡️ Sensor DHT11 con LCD I2C

🧪 Evidencia en video

🔌 Conexiones y diagramas

📊 Resultados y conclusiones

🧰 1. Lista de Materiales (BOM)
🔧 Componentes generales

Cant.	Componente

1	ESP32 DevKit

1	Protoboard

—	Cables Dupont

—	PC con Arduino IDE


🎹 Para el Piano Digital

Cant.	Componente

7	Botones

1	Buzzer pasivo

7	Resistencias 10k (si no se usa INPUT_PULLUP)



🌱 Proyecto de Humedad del Suelo


Cant.	Componente

1	Sensor de humedad de tierra

1	Módulo amplificador

1	LCD 16x2 con I2C



🌡️ Proyecto DHT11

Cant.	Componente

1	DHT11

1	Pantalla LCD 16x2 con I2C

🔌 2. Conexiones

🎹 Piano de 7 botones – Pines del ESP32

Botón	Color	GPIO

1	Azul	26

2	Verde	27

3	Amarillo	14

4	Blanco	12

5	Rojo	33

6	Azul	25

7	Amarillo	32

Buzzer	—	13


🌱 Sensor de humedad (1 sensor)

Señal	ESP32

AO	34

VCC	3.3V

GND	GND

LCD I2C

LCD	ESP32

SDA	21

SCL	22

VCC	5V

GND	GND


🌡️ DHT11

Señal	GPIO

DATA	4

VCC	3.3V

GND	GND

📐 3. Diagramas Wokwi

(Agrega aquí tus enlaces cuando los genere)

Proyecto	Link Wokwi
Piano 7 botones	—
Humedad suelo	—
DHT11 + LCD	—

🧪  Sección de Pruebas – Sensor de Humedad

🎯 Objetivo

Evaluar el funcionamiento del sensor moviéndolo entre:

Maceta seca

Maceta semihúmeda

Maceta mojada

📊 Metodología

Insertar el sensor en la maceta seca → registrar valor.

Insertarlo en la maceta media → registrar valor.

Insertarlo en la maceta mojada → registrar valor.

📈 Interpretación típica

Tierra seca → valores altos

Tierra media → valores intermedios

Tierra mojada → valores bajos

✔️ Conclusión

El sensor responde adecuadamente mostrando variaciones coherentes según la humedad del suelo. La lectura en pantalla LCD facilita la comparación entre macetas.


🏁 Conclusión General

Los tres proyectos demuestran la integración exitosa de sensores y actuadores con el ESP32, aplicando lectura analógica, digital, PWM y comunicación I2C. Se comprobó el funcionamiento de cada módulo mediante pruebas controladas.
