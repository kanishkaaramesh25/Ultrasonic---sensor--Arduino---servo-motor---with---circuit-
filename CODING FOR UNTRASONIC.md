# **CODING**

# 

# \#include \<Servo.h\>

# 

# Servo servo;

# 

# int trigPin \= 8;

# int echoPin \= 9;

# int irPin \= 7;

# int servoPin \= 6;

# 

# long duration;

# int distance;

# int irValue;

# 

# void setup()

# {

#   Serial.begin(9600);

# 

#   pinMode(trigPin, OUTPUT);

#   pinMode(echoPin, INPUT);

#   pinMode(irPin, INPUT);

# 

#   servo.attach(servoPin);

#   servo.write(0);

# }

# 

# void loop()

# {

#   // Ultrasonic sensor

#   digitalWrite(trigPin, LOW);

#   delayMicroseconds(2);

# 

#   digitalWrite(trigPin, HIGH);

#   delayMicroseconds(10);

#   digitalWrite(trigPin, LOW);

# 

#   duration \= pulseIn(echoPin, HIGH);

#   distance \= duration \* 0.034 / 2;

# 

#   // IR sensor

#   irValue \= digitalRead(irPin);

# 

#   Serial.print("Distance: ");

#   Serial.print(distance);

#   Serial.print(" cm  IR: ");

#   Serial.println(irValue);

# 

#   // Object detected

#   if (distance \< 20 || irValue \== LOW)

#   {

#     servo.write(90);

#     delay(1000);

#   }

#   else

#   {

#     servo.write(0);

#   }

# 

#   delay(200);

# }

# 