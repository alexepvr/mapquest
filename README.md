#include <WiFiNINA.h>

char ssid[] = "your_SSID";
char pass[] = "your_PASSWORD";
WiFiClient client;

void setup() {
  WiFi.begin(ssid, pass);
  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("Connecting to WiFi...");
  }
  Serial.println("Connected to WiFi");
  client.connect("www.mapquestapi.com", 80);
  client.println("GET /directions/v2/route?key=zdWxz8eG63PNLm1HqdqxU7AWzdAiHFEL&from=38.688398%2C-9.318559&to=38.695012%2C-9.312746&ambiguities=ignore&routeType=pedestrian HTTP/1.1");
  client.println("Host: www.mapquestapi.com");
  client.println();
}

void loop() {
  if (client.available()) {
    char c = client.read();
    // Do something with the response
  }
}
