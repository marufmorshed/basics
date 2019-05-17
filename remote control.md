const int ch1pin = 3;
const int ch2pin = 4;
const int ch3pin = 5;
const int ch4pin = 6;
const int ch5pin = 7;
const int ch6pin = 8;

void setup() {
  pinMode(ch1pin, INPUT);
  pinMode(ch2pin, INPUT);
  pinMode(ch3pin, INPUT);
  pinMode(ch4pin, INPUT);
  pinMode(ch5pin, INPUT);
  pinMode(ch6pin, INPUT);
  Serial.begin(9600);
  
  // put your setup code here, to run once:

}

void loop() {
 int rslr=pulseIn(ch1pin, HIGH);
 int rsud=pulseIn(ch2pin, HIGH);
 int lsud=pulseIn(ch3pin, HIGH);
 int lslr=pulseIn(ch4pin, HIGH);
 int vra=pulseIn(ch5pin, HIGH);
 int vrb=pulseIn(ch6pin, HIGH);
 Serial.print("rslr ");
 Serial.println(rslr);
 Serial.print("rsud ");
 Serial.println(rsud);
 Serial.print("lsud ");
 Serial.println(lsud);
 Serial.print("lslr");
 Serial.println(lslr);
 Serial.print("vra ");
 Serial.println(vra);
 Serial.print("vrb ");
 Serial.println(vrb);
 delay(5000);// put your main code here, to run repeatedly:

}
