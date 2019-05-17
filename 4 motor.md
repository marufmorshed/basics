
int mt11=34;//front left motor plus
int mt12=35;//front left motor minus
int mt21=30;//back right motor plus
int mt22=31;//back right motor minus
int pwm1=4;//front right motor pwm
int pwm2=3;//front left motor pwm
int mt31=42;//back right motor plus
int mt32=43;//back right motor minus
int mt41=38;//back left motor plus
int mt42=39;//back right motor minus
int pwm3=7;//back rightmotor pwm
int pwm4=6;//back left motor pwm
const int lrp = 9;//left right pin
const int udp = 10;//up down pin
const int vrp = 11;//vrpin

void brmf() {  //back right motor forward
  digitalWrite(42, HIGH);
  digitalWrite(43, LOW);
  analogWrite(7, 255);
}

void brmr() { //back right motor reverse
  digitalWrite(43, HIGH);
  digitalWrite(42, LOW);
  analogWrite(7, 255);
}

void blmf() { //back left motor forward
  digitalWrite(39, LOW);
  digitalWrite(38, HIGH);
  analogWrite(6, 255);
}

void blmr() { //back left motor reverse
  digitalWrite(38, LOW);
  digitalWrite(39, HIGH);
  analogWrite(6, 255);
}
void flmr() { //front left motor reverse
  digitalWrite(34, LOW);
  digitalWrite(35, HIGH);
  analogWrite(3, 255);
}

void flmf() { //front left motor forward
  digitalWrite(35, LOW);
  digitalWrite(34, HIGH);
  analogWrite(3, 255);
}

void frmr() { //front right motor reverse
  digitalWrite(30, LOW);
  digitalWrite(31, HIGH);
  analogWrite(4, 255);
}

void frmf() { //front right motor forward
  digitalWrite(31, LOW);
  digitalWrite(30, HIGH);
  analogWrite(4, 255);
}

void brms() { //back right motor stop
  digitalWrite(43, LOW);
  digitalWrite(42, LOW);
  analogWrite(7, 0);
}

void blms() { //back left motor stop
  digitalWrite(39, LOW);
  digitalWrite(38, LOW);
  analogWrite(6, 0);
}

void flms() { //front left motor stop
  digitalWrite(34, LOW);
  digitalWrite(35, LOW);
  analogWrite(3, 0);
}

void frms() { //front right motor stop
  digitalWrite(30, LOW);
  digitalWrite(31, LOW);
  analogWrite(4, 0);
}



void forward() {
  brmf();
  blmf();
  frmf();
  flmf();
}

void backward() {
  brmr();
  blmr();
  frmr();
  flmr();
}
void tright() {
  brms();
  blmf();
  frms();
  flmf();
}
void tleft() {
  brmf();
  blms();
  frmf();
  flms();
}
void sright() {
  brmr();
  blmf();
  frmr();
  flmf();
}
void sleft() {
  brmf();
  blmr();
  frmf();
  flmr();
}
void mstop() {
  brms();
  blms();
  frms();
  flms();
}
void setup() {
  Serial.begin(9600);
  pinMode(10, INPUT);
  pinMode(9, INPUT);
  pinMode(11, INPUT);
  pinMode(38, OUTPUT);
  pinMode(39, OUTPUT);
  pinMode(42, OUTPUT);
  pinMode(43, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(34, OUTPUT);
  pinMode(35, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(30, OUTPUT);
  pinMode(31, OUTPUT);
  pinMode(4, OUTPUT);
  // put your setup code here, to run once:

}

void loop() {
int x,y,s;
  int lr=pulseIn(lrp, HIGH);
  int ud=pulseIn(udp, HIGH);
  int vr=pulseIn(vrp, HIGH);
  Serial.print("lrp");
  Serial.println(lr);
  Serial.print("udp");
  Serial.println(ud);
  Serial.print("vrp");
  Serial.println(vr);

  if ((vr>=1400 && vr<=1600) || vr==0) {
      if (lr>=1580) {
          tright();
      } else if (lr <=1480) {
          tleft();
      }
     else if (ud>=1550) {
        
        forward();
    } else if (ud<=1300) {
        backward();
      } 
      else {
        mstop();
      }
    
    Serial.println("vr is ok");
  } else {
    mstop();
    Serial.println("not ok");
  }
  delay(50);
 // put your main code here, to run repeatedly:

}
