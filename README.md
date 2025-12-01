Proyecto de Sensores y Piano Digital con ESP32
🏫 Proyecto Escolar – Sistemas Programables

Este repositorio contiene tres proyectos electrónicos funcionales desarrollados con un ESP32, utilizando sensores, buzzer, pantallas LCD y pruebas controladas.

📂 Contenido del Proyecto

🎹 Piano digital con 7 botones y buzzer

🌱 Sensor de humedad del suelo (1 sensor, 3 macetas)

🌡️ Sensor DHT11 con LCD I2C

🧪 Evidencia en video

🔌 Conexiones y diagramas

💻 Códigos Arduino completos

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
💻 4. Códigos Arduino
🎹 Piano digital
#include <driver/ledc.h>

const int btn1 = 26;
const int btn2 = 27;
const int btn3 = 14;
const int btn4 = 12;
const int btn5 = 33;
const int btn6 = 25;
const int btn7 = 32;

const int buzzerPin = 13;

int notas[] = {262, 294, 330, 349, 392, 440, 494};
int botones[] = { btn1, btn2, btn3, btn4, btn5, btn6, btn7 };

void setup() {
  for (int i = 0; i < 7; i++) {
    pinMode(botones[i], INPUT_PULLUP);
  }

  ledcSetup(0, 2000, 10);
  ledcAttachPin(buzzerPin, 0);
}

void loop() {
  bool notaTocada = false;

  for (int i = 0; i < 7; i++) {
    if (digitalRead(botones[i]) == LOW) {
      ledcWriteTone(0, notas[i]);
      notaTocada = true;
      break;
    }
  }

  if (!notaTocada) {
    ledcWriteTone(0, 0);
  }
}

🌱 Sensor de humedad (1 sensor – 3 macetas)
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

int sensor = 34;

void setup() {
  Serial.begin(115200);
  lcd.init();
  lcd.backlight();
}

void loop() {
  int lectura = analogRead(sensor);

  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Humedad: ");
  lcd.print(lectura);

  lcd.setCursor(0, 1);
  lcd.print("Mover sensor...");

  delay(1500);
}

🌡️ DHT11 + LCD
#include <DHT.h>
#include <LiquidCrystal_I2C.h>

#define DHTPIN 4
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  dht.begin();
  lcd.init();
  lcd.backlight();
}

void loop() {
  float h = dht.readHumidity();
  float t = dht.readTemperature();

  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Temp: ");
  lcd.print(t);
  lcd.print("C");

  lcd.setCursor(0,1);
  lcd.print("Hum: ");
  lcd.print(h);
  lcd.print("%");

  delay(1000);
}

🧪 5. Sección de Pruebas – Sensor de Humedad
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
