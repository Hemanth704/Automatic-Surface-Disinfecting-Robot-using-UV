# Automatic-Surface-Disinfecting-Robot-using-UV
// defining the pins
const int trigPin1 = 3;
const int echoPin1 = 5;
const int trigPin2 = 6;
const int echoPin2 = 9;
const int trigPin3 = 10;
const int echoPin3 = 11;
// defining variables
long duration1;
long duration2;
long duration3;
int distanceleft;
int distancefront;
int distanceright;
void setup() {
  pinMode(trigPin1, OUTPUT);
  pinMode(trigPin2, OUTPUT);
  pinMode(trigPin3, OUTPUT);// Sets the trigPin as an Output
  pinMode(echoPin1, INPUT); // Sets the echoPin as an Input
  pinMode(echoPin2, INPUT);
  pinMode(echoPin3, INPUT);
  Serial.begin(9600); // Starts the serial communication
  pinMode(4, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(12, OUTPUT);
}
void loop() {
  digitalWrite(trigPin1, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin1, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin1, LOW);
  duration1 = pulseIn(echoPin1, HIGH);
  distanceleft = duration1 * 0.034 / 2;
  Serial.print("Distance1: ");
  Serial.println(distanceleft);
  digitalWrite(trigPin2, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin2, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin2, LOW);
  duration2 = pulseIn(echoPin2, HIGH);
  distancefront = duration2 * 0.034 / 2;
  Serial.print("Distance2: ");
  Serial.println(distancefront);
  digitalWrite(trigPin3, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin3, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin3, LOW);
  duration3 = pulseIn(echoPin3, HIGH);
  distanceright = duration3 * 0.034 / 2;
  Serial.print("Distance3: ");
  Serial.println(distanceright);
  if ((distanceleft <= 15 && distancefront > 15 && distanceright <= 15) || (distanceleft > 15 && distancefront > 15 && distanceright > 15))
  {
    digitalWrite(4, HIGH);
    digitalWrite(7, LOW);
    digitalWrite(8, HIGH);
    digitalWrite(12, LOW);
  }
  if ((distanceleft <= 15 && distancefront <= 15 && distanceright > 15) || (distanceleft <= 15 && distancefront > 15 && distanceright > 15))
  {
    digitalWrite(4, HIGH);
    digitalWrite(7, LOW);
    digitalWrite(8, LOW);
    digitalWrite(12, HIGH);
  }
  if ((distanceleft > 15 && distancefront <= 15 && distanceright <= 15) || (distanceleft > 15 && distancefront > 15 && distanceright <= 15) ||  (distanceleft > 15 && distancefront <= 15 && distanceright > 15) )
  {
    digitalWrite(4, LOW);
    digitalWrite(7, HIGH);
    digitalWrite(8, HIGH);
    digitalWrite(12, LOW);
  } 
}
