# PropuestadeObra
Preexamen


#CODIGO
~~~#include <Servo.h>

Servo servoPinza;
const int potPinPinza = A0;
const int servoPinPinza = 11;

void setup() {
  servoPinza.attach(servoPinPinza);
  servoPinza.write(90);  // Posición semi-abierta
  delay(1500);           // Más tiempo para pinza
  Serial.begin(9600);
}

void loop() {
  int lectura = analogRead(potPinPinza);
  int angulo = map(lectura, 0, 1023, 60, 120); // Rango ajustado para pinza
  
  // Movimiento progresivo
  static int anguloObjetivo = 90;
  if(abs(angulo - anguloObjetivo) > 1) {
    anguloObjetivo += (angulo > anguloObjetivo) ? 1 : -1;
    servoPinza.write(anguloObjetivo);
    delay(30); // Velocidad controlada
  }
}~~~
