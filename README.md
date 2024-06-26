# Projects
# E-Nose For Fruit Spoilage Detection Using MQ-4 Methane Gas Sensor
int pinRedLed = 12;
int pinGreenLed = 11;
int pinSensor = A5;
int THRESHOLD = 250;
int buzzer = 10;
int rdata = 0;

void setup() {
  Serial.begin(9600);
  pinMode(buzzer, OUTPUT);
  pinMode(pinRedLed, OUTPUT);
  pinMode(pinGreenLed, OUTPUT);
  pinMode(pinSensor, INPUT);
}

void loop() {
  int rdata = analogRead(pinSensor);
  Serial.print("Methane Range: ");
  Serial.println(rdata);

  if (rdata >= THRESHOLD) {
    digitalWrite(pinRedLed, HIGH);
    digitalWrite(pinGreenLed, LOW);
    digitalWrite(buzzer, HIGH);
    delay(50);
  } else {
    digitalWrite(pinRedLed, LOW);
    digitalWrite(pinGreenLed, HIGH);
    digitalWrite(buzzer, LOW);
  }

  delay(1000);
}
