# -Smart-street-Light-


# project code

const int ldrPin = 36; // ADC pin for LDR
const int relayPin = 23; // Digital pin for relay control

int ldrValue = 0; // Variable to store the LDR value
int threshold = 500; // Threshold value for LDR to activate the relay

void setup() {
  Serial.begin(115200); // Start serial communication for debugging
  pinMode(ldrPin, INPUT); // Set the LDR pin as input
  pinMode(relayPin, OUTPUT); // Set the relay pin as output
  digitalWrite(relayPin, LOW); // Ensure relay is off initially
}

void loop() {
  ldrValue = analogRead(ldrPin); // Read the LDR value
  Serial.print("LDR Value: ");
  Serial.println(ldrValue); // Print the LDR value to the serial monitor

  // Check if the LDR value is below the threshold
  if (ldrValue < threshold) {
    digitalWrite(relayPin, HIGH); // Turn on the relay (and the LED)
  } else {
    digitalWrite(relayPin, LOW); // Turn off the relay (and the LED)
  }

  delay(500); // Wait for half a second before reading again
}
