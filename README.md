# Task--2-Weather-Reporting-System-using-IoT
Project Summary: A top-tier IoT project, the Weather Report system provides localized forecasts, minimizing reliance on external agencies.

1.Sensor Data Collection: Code to interface with temperature, humidity, and rain sensors to collect real-time data.

2.Data Processing: Logic to process the sensor data and calculate parameters like average temperature, humidity levels, and rainfall intensity.

3.Alert System: Implement an alert system based on predefined thresholds for extreme events like volcanoes, tsunamis, or heavy rainfall. This could involve setting up different color-coded alerts (red, yellow, green) depending on the severity of the event.

4.Online Reporting: Code to establish an internet connection and upload the processed data to a web server for online reporting. This could involve using protocols like HTTP or MQTT for communication.

5.User Interface (Optional): If you want a user interface for configuring alerts or viewing real-time data locally, you'll need code for that as well. This could be a simple web interface or a mobile app.

Here's a simplified example of what the source code might look like in Arduino for collecting temperature data from a sensor:
Source Code

#include <Wire.h>
#include <Adafruit_Sensor.h>
#include <Adafruit_BME280.h>

#define SEALEVELPRESSURE_HPA (1013.25)

Adafruit_BME280 bme; // I2C

void setup() {
  Serial.begin(9600);
  if (!bme.begin()) {
    Serial.println("Could not find a valid BME280 sensor, check wiring!");
    while (1);
  }
}

void loop() {
  float temperature = bme.readTemperature();
  float humidity = bme.readHumidity();
  float pressure = bme.readPressure() / 100.0F;
  float altitude = bme.readAltitude(SEALEVELPRESSURE_HPA);

  Serial.print("Temperature = ");
  Serial.print(temperature);
  Serial.println(" *C");

  Serial.print("Humidity = ");
  Serial.print(humidity);
  Serial.println(" %");

  Serial.print("Pressure = ");
  Serial.print(pressure);
  Serial.println(" hPa");

  Serial.print("Approx. Altitude = ");
  Serial.print(altitude);
  Serial.println(" m");

  delay(2000);
}

