// ----------------- BLYNK CONFIG -----------------
#define BLYNK_TEMPLATE_ID "TMPL3pNDENe7-"
#define BLYNK_TEMPLATE_NAME "Vabby Room"
#define BLYNK_AUTH_TOKEN "wEa6v4kjynpk23LTXqI3CU3sfCD6iKcS"

#include <WiFi.h>
#include <BlynkSimpleEsp32.h>

char auth[] = BLYNK_AUTH_TOKEN;
char ssid[] = "Vaibhav";
char pass[] = "12345678";

// ----------------- RELAY PINS -----------------
#define R1 5    // Relay 1 - Light 1
#define R2 18   // Relay 2 - Light 2
#define R3 19   // Relay 3 - Light 3
#define R4 21   // Relay 4 - Fan

// ----------------- BLYNK CONTROL -----------------
BLYNK_WRITE(V1) { digitalWrite(R1, !param.asInt()); } // Light 1
BLYNK_WRITE(V2) { digitalWrite(R2, !param.asInt()); } // Light 2
BLYNK_WRITE(V3) { digitalWrite(R3, !param.asInt()); } // Light 3
BLYNK_WRITE(V4) { digitalWrite(R4, !param.asInt()); } // Fan

// ----------------- SETUP -----------------
void setup() {
  Serial.begin(115200);

  pinMode(R1, OUTPUT);
  pinMode(R2, OUTPUT);
  pinMode(R3, OUTPUT);
  pinMode(R4, OUTPUT);

  // All OFF initially (Relay LOW Triggered)
  digitalWrite(R1, HIGH);
  digitalWrite(R2, HIGH);
  digitalWrite(R3, HIGH);
  digitalWrite(R4, HIGH);

  Blynk.begin(auth, ssid, pass);
}

// ----------------- LOOP -----------------
void loop() {
  Blynk.run();
}
