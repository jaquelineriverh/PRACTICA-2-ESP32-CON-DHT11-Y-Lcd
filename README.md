# PRACTICA-2-ESP32-CON-DHT11-Y-Lcd
este respositorio muestra como programar con DHT11 Y LCD
## INTRODUCCION

### DESCRIPCION

La Esp32 la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (DTH11) para adquirir temperatura y humedad del entorno; Cabe aclarar que esta practica se usara un simulador llamado WOKWI.
Se agregara asi mismo un LCD I2C para observar dichos datos en cada cierto tiempo

## MATERIAL NECESARIO

Para realizar esta practica necesitas lo siguiente:

-[WOKWI](https://wokwi.com/)

-Tarjeta ESP 32

-Sensor DHT11

-LCD 16X2 (I2C)

## INSTRUCCIONES

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://wokwi.com/)

### Instrucciones de preparación de entorno

1.Abrir la terminal de programación y colocar la siguente programación:

```
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
  lcd.print("   DIPLOMADO");
  lcd.setCursor(0, 1); 
  lcd.print(" AUTOMATIZACION");
   delay(2000);
  lcd.clear();

   lcd.setCursor(0, 0);
  lcd.print(" JAQUELINE R.H");
  lcd.setCursor(0, 1); 
  lcd.print("   INDUSTRIAL");
   delay(2000);
  lcd.clear();
   lcd.setCursor(0, 0);
  lcd.print("   07-06-2025");
  delay(2000);
  lcd.clear();
  
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1); 
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
 

  delay(2000);
   lcd.clear();
}
```


2.Instalar la libreria de DHT sensor library for ESPx como se muestra en la siguente imagen


![](https://github.com/jaquelineriverh/PRACTICA-ESP32-DHT11/blob/main/DHT.jpg)

3. Instalar la libreria de LiquidCrystal I2C como se muestra en la siguiente imagen



![](https://github.com/jaquelineriverh/PRACTICA-2-ESP32-CON-DHT11-Y-Lcd/blob/main/libreria%20liquid.png)



4.Hacer la conexion de DHT11 con la ESP32 como se muestra en la siguente imagen.

![](https://github.com/jaquelineriverh/PRACTICA-ESP32-DHT11/blob/main/CONEXION%20DE%20DHT11.png)


5.Hacer la conexion de LCD con la ESP32 como se muestra en la siguente imagen.


![]()


### Instrucciónes de operación
1.Iniciar simulador.

2.Visualizar los datos en el LCD 16x2.

3.Colocar la temperatura y humedad dando doble click al sensor DHT11

## Resultados

Cuando haya funcionado, verás los valores dentro del LCD 16x2 como se muestra en la siguente imagen.


![]()

### Evidencias








# Créditos

Desarrollado por **RIVERA HERNANDEZ JAQUELINE**

-[GITHUB](https://github.com/jaquelineriverh)
