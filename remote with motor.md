#define in1 4;//right motor
#define in2 8;
#define pwn 10;
#define in3 7;//left motor
#define in4 6;
#define pwn2 5;
const int lrp = 9;
const int udp = 10;
const int vrp = 11;

float s;

void rmfor() { //right motor forward
  digitalWrite(8, HIGH);
  digitalWrite(4, LOW);
  analogWrite(10, s);
}
void rmrev() {  //right motor reverse
  digitalWrite(4, HIGH);
  digitalWrite(8, LOW);
  analogWrite(10, s);
}
void rmstop() { //right motor stop
  digitalWrite(4, LOW);
  digitalWrite(8, LOW);
  analogWrite(10, 0);
}

void lmfor() {  //left motor forward
  digitalWrite(7, LOW);
  digitalWrite(6, HIGH);
  analogWrite(5, s);
}
void lmrev() { //left motor reverse
  digitalWrite(6, LOW);
  digitalWrite(7, HIGH);
  analogWrite(5, s);
}
void lmstop() {
  digitalWrite(6, LOW);
  digitalWrite(7, LOW);
  analogWrite(5, 0);
}
void forward() {//vehicle forward
  rmfor();
  lmfor();
}
void reverse() {//vehicle reverse
  rmrev();
  lmrev();
}
void right() {//right turn
  lmfor();
  rmrev();
  Serial.println("tr");
}
void left() {//left turn
  rmfor();
  lmrev();
  Serial.println("tl");
}
void mstop() {
  rmstop();
  lmstop();
  Serial.println("stop");
}
void setup() {
  Serial.begin(9600);
  pinMode(10, INPUT);
  pinMode(9, INPUT);
  pinMode(11, INPUT);
  pinMode(4, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  
}

void loop() {  
  int x,y,z;
  int lr=pulseIn(lrp, HIGH);
  int ud=pulseIn(udp, HIGH);
  int vr=pulseIn(vrp, HIGH);
  Serial.print("lrp");
  Serial.println(lr);
  Serial.print("udp");
  Serial.println(ud);
  Serial.print("vrp");
  Serial.println(vr);

  /*if ((vr>=1400 && vr<=1600) || vr==0) {
      if (lr>=1580 && lr<=1800) {
          x=constrain(lr, 1580, 1800);
          s=map(x, 1580, 1800, 0, 155);
          tright();
      } else if ( lr>=1250 && lr <=1480) {
          x=constrain(lr, 1250, 1480);
          s=map(x, 1250, 1480, 155, 0);
          tleft();
      }
     else if (ud>=1550) {
        x=constrain(ud, 1550, 1800);
        s=map(x, 1550, 1800, 0, 155);
        fw();
    } else if (ud<=1470 && ud>=1200) {
        x=constrain(ud, 1300, 1470);
        s=map(x, 1300, 1470, 155, 0);
        bw();
      } 
      else {
        mstop();
      }
    
    Serial.println("vr is ok");
  } else {
    mstop();
    Serial.println("not ok");
  }
  delay(50);*/
  // put your main code here, to run repeatedly:

}
