# motor test
int rmp=8;
int rmm=7;
int lmp=2;
int lmm=4;

int rmpwm=10;
int lmpwm=3;

int ms=200;
int ts=150;

//int state;
char command;

void lmfor() {
  digitalWrite(lmp, HIGH);
  digitalWrite(lmm, LOW);
}

void lmrev() {
  digitalWrite(lmp, LOW);
  digitalWrite(lmm, HIGH);
}

void lmstop() {
  digitalWrite(lmp, LOW);
  digitalWrite(lmm, LOW);
}

void rmfor() {
  digitalWrite(rmp, HIGH);
  digitalWrite(rmm, LOW);
}

void rmrev() {
  digitalWrite(rmp, LOW);
  digitalWrite(rmm, HIGH);
}

void rmstop() {
  digitalWrite(rmp, LOW);
  digitalWrite(rmm, LOW);
}

void forward() {
  rmfor();
  lmfor();
  analogWrite(rmpwm, ms);
  analogWrite(lmpwm, ms);
}

void reverse() {
  rmrev();
  lmrev();
  analogWrite(rmpwm, ms);
  analogWrite(lmpwm, ms);
}

void vehstop() {
  rmstop();
  lmstop();
  analogWrite(rmpwm, 0);
  analogWrite(lmpwm, 0);
}

void rspin() {
  lmfor();
  analogWrite(lmpwm, ts);
  rmrev();
  analogWrite(rmpwm, ts);
}

void lspin() {
  lmrev();
  analogWrite(lmpwm, ts);
  rmfor();
  analogWrite(rmpwm, ts);
}

void rturn(){
  lmfor();
  analogWrite(lmpwm, ts);
  rmstop();
  analogWrite(rmpwm, 0);
}

void lturn() {
  rmfor();
  analogWrite(rmpwm, ts);
  lmstop();
  analogWrite(lmpwm, 0);
}

void blturn() {
  rmrev();
  analogWrite(rmpwm, ts);
  lmstop();
  analogWrite(lmpwm, 0);
}

void brturn() {
  lmrev();
  analogWrite(lmpwm, ts);
  rmstop();
  analogWrite(rmpwm, 0);
}


void setup() {
  pinMode(rmp,OUTPUT);
  pinMode(rmm,OUTPUT);
  pinMode(lmp,OUTPUT);
  pinMode(lmm,OUTPUT);
  pinMode(rmpwm,OUTPUT);
  pinMode(lmpwm,OUTPUT);
  /*pinMode(PWMLF,OUTPUT);
  pinMode(PWMLR,OUTPUT);
  digitalWrite(EN1,HIGH);
  digitalWrite(EN2,HIGH);
  digitalWrite(EN3,HIGH);
  digitalWrite(EN4,HIGH);*/
  Serial.begin(9600);
  // put your setup code here, to run once:

}

void loop () {
  reverse();
}
