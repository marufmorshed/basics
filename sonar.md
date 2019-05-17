int trigpinb=30;    //trigpinback
int echopinb=31;    //echopinfront
int trigpinf=48;    //trigpinfront
int echopinf=49;    //echopinfront

long durationb;
int distanceb;
long durationf;
int distancef;
int backdistance() {     //back thing distance
  digitalWrite(trigpinb,LOW);
  delay(2);
  digitalWrite(trigpinb,HIGH);
  delay(10);
  digitalWrite(trigpinb,LOW);
  
  durationb=pulseIn(echopinb, HIGH);
  distanceb=durationb*0.034/2;
  Serial.print("Distance back:");
  Serial.println(distanceb);
  return distanceb;
}

int frontdistance() {     //front thing distance
  digitalWrite(trigpinf,LOW);
  delay(2);
  digitalWrite(trigpinf,HIGH);
  delay(10);
  digitalWrite(trigpinf,LOW);
  
  durationf=pulseIn(echopinf, HIGH);
  distancef=durationf*0.034/2;
  Serial.print("Distance front:");
  Serial.println(distancef);
  return distancef;
}

void setup() {
  Serial.begin(9600);
  pinMode(trigpinb,OUTPUT);
  pinMode(echopinb, INPUT);
  pinMode(trigpinf,OUTPUT);
  pinMode(echopinf, INPUT);
}

void loop() {
  int fcd=frontdistance();
  delay(1000);
}
