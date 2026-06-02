# -Smart-street-Light-

# Smart Street Light using ESP32

## Project Overview
This project automatically turns ON street lights during low light conditions and turns them OFF during daylight using an LDR sensor and relay module.

## Components Required

- ESP32 Board
- LDR Sensor
- Relay Module
- LED / Bulb
- Jumper Wires
- Breadboard
- Resistors
## Working Principle

1. LDR continuously measures ambient light.
2. ESP32 reads analog values from LDR.
3. If light intensity decreases below threshold:
   - Relay activates
   - Street light turns ON
4. If brightness increases:
   - Relay deactivates
   - Street light turns OFF

## Threshold Setting

Default threshold:

500

Adjust according to your environment.

## Output

Dark Environment:
Street Light ON

Bright Environment:
Street Light OFF


// Pin Definitions
const int ldrPin = 36;      // LDR connected to ADC pin
const int relayPin = 23;    // Relay control pin

// Variables
int ldrValue = 0;
int threshold = 500;        // Adjust according to lighting conditions

void setup() {

  // Start Serial Monitor
  Serial.begin(115200);

  // Configure Pins
  pinMode(ldrPin, INPUT);
  pinMode(relayPin, OUTPUT);

  // Keep relay OFF initially
  digitalWrite(relayPin, LOW);

  Serial.println("Smart Street Light System Started");
}

void loop() {

  // Read light intensity
  ldrValue = analogRead(ldrPin);

  // Print value on Serial Monitor
  Serial.print("LDR Reading: ");
  Serial.println(ldrValue);

  // Dark condition
  if (ldrValue < threshold) {

    digitalWrite(relayPin, HIGH);

    Serial.println("Dark Detected");
    Serial.println("Street Light ON");
  }

  // Bright condition
  else {

    digitalWrite(relayPin, LOW);

    Serial.println("Bright Environment");
    Serial.println("Street Light OFF");
  }

  Serial.println("----------------");

  delay(500);
}
