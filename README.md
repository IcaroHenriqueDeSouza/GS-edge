#GSedge

O projeto usa os componentes: Arduino Uno, LED, sensor PIR, além de cabos jumper, protoboard e resistor de 220Ω. O objetivo é de reduzir o desperdício de energia. O projeto usa o Arduino Uno para dar instruções e energizar os demais componentes, o LED simula uma lâmpada e o sensor PIR detecta movimentos. O funcionamento do projeto deve seguir de maneira que quando o sensor PIR detectar movimento, ele manda um sinal para o Arduino Uno que por sua vez mandará outro sinal para acender o LED. Assim que o sensor PIR para de detectar movimento há um delay para que o LED seja apagado.
----------------------------------------------------------------------------------------------------------------------------------------
int ledPin = 6; 
int sensorPin = 7; 
int leitura = 0; 
bool estadoSensor = false; 
void setup() {
  Serial.begin(9600); 
  pinMode(ledPin, OUTPUT); 
  pinMode(sensorPin, INPUT); 
}
void loop() {
  leitura = digitalRead(sensorPin); 
  if (leitura == HIGH) { 
    digitalWrite(ledPin, HIGH); 
    if (estadoSensor == false) { 
      Serial.println("Movimento detectado"); 
      estadoSensor = true; 
    }
    delay(5000); 
  } else { 
    digitalWrite(ledPin, LOW); 
    if (estadoSensor == true) { 
      Serial.println("Sem movimento"); 
      estadoSensor = false; 
    }
  }
}
