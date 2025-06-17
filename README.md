# PropuestadeObra
Preexamen


# CODIGO PARA SERVO 1 , 2 y 3
~~~
#include <Servo.h>

Servo servoBase;
const int potPinBase = A0;
const int servoPinBase = 9;

void setup() {
  servoBase.attach(servoPinBase);
  servoBase.write(90);  // Posición inicial a 90°
  delay(1000);          // Tiempo para estabilizar
  Serial.begin(9600);
}

void loop() {
  int lectura = analogRead(potPinBase);
  int angulo = map(lectura, 0, 1023, 0, 180);
  
  // Filtro para reducir vibraciones
  static int anguloAnterior = 90;
  if(abs(angulo - anguloAnterior) > 2) {
    servoBase.write(angulo);
    anguloAnterior = angulo;
  }
  
  delay(15);
}
~~~
