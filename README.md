# PRACTICA-ESP32-CON-SENSOR-ULTRASONICO-Y-LCD

## Introduccion

### Descripcion

Este repositorio muestra como podemos programar una ESP32 con el sensor ultrasonico (HC-SR04) y una pantalla LCD

## Material necesario

-WOKWI

-Tarjeta ESP32

-Sensor ultrasonico (HC-SR04)

-Pantalla LCD (16x2)

## Instrucciones de preparación de entorno

1. Abrir la terminal de programación y colocar la siguente programación:

```
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

const int Trigger = 4;   //Pin digital 2 para el Trigger del sensor
const int Echo = 15;   //Pin digital 3 para el Echo del sensor

void setup() {
  Serial.begin(9600);//inicializamos la comunicación
  pinMode(Trigger, OUTPUT); //pin como salida
  pinMode(Echo, INPUT);  //pin como entrada
  digitalWrite(Trigger, LOW);//Inicializamos el pin con 0

   lcd.init();
  lcd.backlight();

}

void loop()
{

  long t; //tiempo que demora en llegar el eco
  long d; //distancia en centimetros

  digitalWrite(Trigger, HIGH);
  delayMicroseconds(10);          //Enviamos un pulso de 10us
  digitalWrite(Trigger, LOW);
  
  t = pulseIn(Echo, HIGH); //obtenemos el ancho del pulso
  d = t/59;             //escalamos el tiempo a una distancia en cm
  
  Serial.print("Distancia: ");
  Serial.print(d);      //Enviamos serialmente el valor de la distancia
  Serial.print("cm");
  Serial.println();
  delay(1000);          //Hacemos una pausa de 1000ms

 lcd.setCursor(0, 0);
  lcd.print(" DIPLOMADO 5 ");
  lcd.setCursor(0, 1);
  lcd.print(" AUTOMATIZACION ");
delay(2000);
lcd.clear();
 
 lcd.setCursor(0, 0);
  lcd.print(" OSCAR OCAMPO ");
  lcd.setCursor(0, 1);
  lcd.print(" ING. MECANICO ");
delay(2000);
lcd.clear();

lcd.setCursor(0, 0);
  lcd.print(" 07 JUNIO 2025 ");
delay(2000);
lcd.clear();

 lcd.setCursor(0, 0);
  lcd.print("Distancia:" + String(d) +"cm");
  delay(2000);
  lcd.clear();

}
```

2. Instalar la libreria de LiquidCrystal I2C como se muestra en la siguente imagen.

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-SENSOR-ULTRASONICO/blob/main/image%20(9).png?raw=true)

3. Hacer la conexion del sensor ultrasonico y LCD con la ESP32 como se muestra en la siguente imagen.

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-SENSOR-ULTRASONICO/blob/main/image%20(8).png?raw=true)

## Instrucciónes de operación

1. Iniciar simulador.

2. Visualizar los datos en el monitor serial. (CURSO, NOMBRE Y CARRERA, FECHA).

3. Colocar la distancia dando doble click al sensor ultrasonico.

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en las siguentes imagenes.

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-SENSOR-ULTRASONICO/blob/main/image%20(10).png?raw=true)

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-SENSOR-ULTRASONICO/blob/main/image%20(11).png?raw=true)

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-SENSOR-ULTRASONICO/blob/main/image%20(12).png?raw=true)

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-SENSOR-ULTRASONICO/blob/main/image%20(13).png?raw=true)

## Creditos

Desarrollado por Ing. Oscar Jair Ocampo Villarreal
- ([github](https://github.com/OSCAROV2058))
