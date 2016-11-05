#include <SPI.h>
#include <Dhcp.h>
#include <Dns.h>
#include <Ethernet.h>
#include <EthernetClient.h>
#include <Temboo.h>
#include "TembooAccount.h" // Contains Temboo account information
#include<SoftwareSerial.h>
SoftwareSerial mySerial(9,10);

#define GASLIMIT 400

byte ethernetMACAddress[] = ETHERNET_SHIELD_MAC;
EthernetClient client;

// The number of times to trigger the action if the condition is met
// We limit this so you won't use all of your Temboo calls while testing
int maxCalls = 10;

// The number of times this Choreo has been run so far in this sketch
int calls = 0;

int inputPin = A0;
int buzz=3;

void setup() {
  Serial.begin(9600);
  
  // For debugging, wait until the serial console is connected
  delay(4000);
  while(!Serial);

  Serial.print("DHCP:");
  if (Ethernet.begin(ethernetMACAddress) == 0) {
    Serial.println("FAIL");
    while(true);
  }
  Serial.println("OK");
  delay(5000);

  // Initialize pins
  pinMode(inputPin, INPUT);
  pinMode(buzz, OUTPUT);
  Serial.println("Setup complete.\n");
}

void loop() {
  int sensorValue = analogRead(inputPin);
  Serial.println("Sensor: " + String(sensorValue));

  if (sensorValue > GASLIMIT) {
    digitalWrite(buzz,HIGH);
    Serial.println("Calling through GSM Modem");
    mySerial.begin(9600);
    delay(2000);
    mySerial.println("ATD9962879906;");
    Serial.println("Called ATD9962879906");
    delay(30000);
    if(mySerial.available())
      Serial.write(mySerial.read());
    if (calls < maxCalls) {
      Serial.println("\nTriggered! Calling SendEmail Choreo...");
      runSendEmail(sensorValue);
      calls++;
      delay(1000);
    } else {
      Serial.println("\nTriggered! Skipping to save Temboo calls. Adjust maxCalls as required.");
    }
  }
  digitalWrite(buzz,LOW);
  delay(250);
}

void runSendEmail(int sensorValue) {
  TembooChoreo SendEmailChoreo(client);

  // Set Temboo account credentials
  SendEmailChoreo.setAccountName(TEMBOO_ACCOUNT);
  SendEmailChoreo.setAppKeyName(TEMBOO_APP_KEY_NAME);
  SendEmailChoreo.setAppKey(TEMBOO_APP_KEY);

  // Set profile to use for execution
  SendEmailChoreo.setProfile("Asmita");
  // Identify the Choreo to run
  SendEmailChoreo.setChoreo("/Library/Google/Gmail/SendEmail");

  // Run the Choreo
  unsigned int returnCode = SendEmailChoreo.run();

  // Read and print the error message
  while (SendEmailChoreo.available()) {
    char c = SendEmailChoreo.read();
    Serial.print(c);
  }
  Serial.println();
  SendEmailChoreo.close();
}
