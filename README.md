int redPin = 9;
int greenPin = 8;
int yellowPin = 12;

int buzzer = 10;
// int buzzer = 9;
int smokeA0 = A5;
int sensorThres = 400;

void setup() 
{
  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  pinMode(yellowPin, OUTPUT);
  pinMode(buzzer, OUTPUT);
  // pinMode(buzzer1, OUTPUT);
  pinMode(smokeA0, INPUT);
  // Serial.begin(9600);
}

void loop() 
{
  int analogSensor = analogRead(smokeA0);

  // Serial.print("Pin A0: ");
  // Serial.println(analogSensor);
  // Checks if it has reached the threshold value
  if (analogSensor > sensorThres)
  {
    analogWrite(redPin, 255);
    analogWrite(greenPin, 0);
    tone(buzzer, 2048, 200);
    // tone(buzzer1, 2048, 200);
  }
  else
  {
    analogWrite(redPin, 0);
    analogWrite(greenPin, 255);
    noTone(buzzer);
    // noTone(buzzer1);
  }
  delay(100);
}
