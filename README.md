# GS-edge

int ledPin = 6; //Pino do LED
int sensorPin = 7; //Pino do sensor de presença
int leitura = 0; //Variável para armazenar a leitura do sensor
bool estadoSensor = false; //Variável para armazenar o estado do sensor
void setup() {
  Serial.begin(9600); //Inicializa a comunicação serial
  pinMode(ledPin, OUTPUT); //Define ledPin como saída
  pinMode(sensorPin, INPUT); //Define sensorPin como entrada
}
void loop() {
  leitura = digitalRead(sensorPin); //Realiza a leitura do sensor de presença
  if (leitura == HIGH) { //Se leitura for igual a HIGH, o movimento foi detectado
    digitalWrite(ledPin, HIGH); //Aciona o LED
    if (estadoSensor == false) { //Compara o valor de estado do LED
      Serial.println("Movimento detectado"); //Imprime a mensagem no monitor serial
      estadoSensor = true; //Altera o valor de estadoSensor para HIGH
    }
    delay(5000); //Tempo de LED acionado
  } else { //Se leitura for igual a LOW, não houve movimento detectado
    digitalWrite(ledPin, LOW); //Desliga o LED
    if (estadoSensor == true) { //Compara o valor de estado do LED
      Serial.println("Sem movimento"); //Imprime a mensagem no monitor serial
      estadoSensor = false; //Altera o valor de estadoSensor para HIGH
    }
  }
}
