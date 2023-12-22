# Practica-No.4-ESP32-con-Ultrasonico-y-LCD
## Introduccion
Dentro de este algoritmo y proyecto se muestra la manera de programar una ESP32 con el sensor ultrasonico y que los datos obtenidos se muestren en una pantalla LCD, así como información personal.
### MATERIAL DE TRABAJO 
-WORKI 
-Tarjeta ESP 32
-Sensor HC-SR04
#### INTRUCCIONES
*Abrir la terminal de programación y colocar el siguiente código:

#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);
  lcd.clear(); 
  lcd.setCursor(0,0);
  lcd.print("Ing. Industrial");
  lcd.setCursor(0,1);
  lcd.print("Ing. Armando");
  delay(2000);
}
*Instalar la libreria de LiquidCrystal I2C como se muestra en la siguiente imagen
![](https://github.com/ArmandoGl98/Practica-No.4-ESP32-con-Ultrasonico-y-LCD/blob/main/Captura%20de%20pantalla%202023-12-21%20211827.png)
*Hacer la conexion de ULTRASONICO y LCD 16x2 (I2C) con la ESP32 como se muestra en la siguente imagen.
![](https://github.com/ArmandoGl98/Practica-No.4-ESP32-con-Ultrasonico-y-LCD/blob/main/Captura%20de%20pantalla%202023-12-21%20210056.png)
