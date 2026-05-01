#define TRIG 9
#define ECHO 10

#define RED 2
#define BLUE 3

void setup() {
  pinMode(TRIG, OUTPUT);
  pinMode(ECHO, INPUT);
  
  pinMode(RED, OUTPUT);
  pinMode(BLUE, OUTPUT);
  <img width="1916" height="889" alt="asdasdasdas" src="https://github.com/user-attachments/assets/04665c91-bdf3-4e79-b13b-bec7a810bf84" />

  Serial.begin(9600);
}

void loop() {
  long duration;
  float distance;


  digitalWrite(TRIG, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG, LOW);

 
  duration = pulseIn(ECHO, HIGH);

 
  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.println(distance);


  if (distance <= 10) {
    digitalWrite(RED, HIGH);
    digitalWrite(BLUE, LOW);
  } else {
    digitalWrite(RED, LOW);
    digitalWrite(BLUE, HIGH);
  }

  delay(200);
}
//초음파 센서와 물체 사이 거리가 10cm 이하면 빨간 led가 켜지고 그 이외의 경우 파란 led가 켜지도록 한다
