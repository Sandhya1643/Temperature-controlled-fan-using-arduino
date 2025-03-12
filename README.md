# Temperature-controlled-fan-using-arduino

A temperature-controlled fan automatically adjusts its speed based on the surrounding temperature. This project uses an LM35 temperature sensor and PWM (Pulse Width Modulation) control to regulate the fan speed with an Arduino.

🛠  Components Required:
 
Arduino Uno
LM35 Temperature Sensor
DC Fan (5V or 12V)
Transistor (TIP120 or BC547 for small fans, IRF540 for large fans)
Diode (1N4007) – To prevent back EMF
Resistor (1kΩ)
12V Power Supply (if using a 12V fan)
Wires & Breadboard

code

#define LM35 A0    // Temperature sensor connected to A0
#define FAN 9      // PWM pin for fan control

void setup() {
  pinMode(FAN, OUTPUT);
  Serial.begin(9600);
}
void loop() {
  int sensorValue = analogRead(LM35);
  float temperature = sensorValue * (5.0 / 1023.0) * 100.0; // Convert to Celsius
  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.println(" °C");

  if (temperature < 25) {
    analogWrite(FAN, 0);  // Fan OFF
  }
  else if (temperature >= 25 && temperature < 30) {
    analogWrite(FAN, 100);  // Low Speed
  }
  else if (temperature >= 30 && temperature < 35) {
    analogWrite(FAN, 180);  // Medium Speed
  } 
  else {
    analogWrite(FAN, 255);  // Full Speed
  }
  delay(1000);
}

🎯 How It Works:
The LM35 sensor measures temperature.
The Arduino reads the temperature and determines the fan speed based on the conditions.
A transistor acts as a switch, controlling the fan speed using PWM (Pulse Width Modulation).
The fan adjusts speed automatically depending on the temperature.

🚀 Enhancements:
✅ LCD Display – Show temperature readings.
✅ Relay Module – Control AC fans instead of DC fans.
✅ IoT Integration – Monitor and control the fan using a mobile app.
