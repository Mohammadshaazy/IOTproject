In this technology project you will continue building your project by developing the platform as per project requirement. Use web development technologies wherever needed. After performing the relevant activities create a document around it and share the same for assessment.

---

# Phase 4: Developing the Environmental Monitoring System

In Stage 4 of our technology project, we will continue building and enhancing our environmental monitoring system. This phase will primarily focus on further developing the IoT devices and Python script, ensuring that they meet the project's requirements. Below is an outline for documenting your progress.

## Introduction

In this phase, we will focus on the continuous development of our environmental monitoring system. While we won't be adding a web platform, we will ensure that the IoT devices and Python script meet the project's requirements and expectations.

## Enhancing IoT Devices

**Refining Sensor Data Collection**

- Review the data collected by your IoT devices and the Python script.
- Refine the data collection process to ensure accuracy and consistency.
- Troubleshoot any issues or inconsistencies in sensor data.

**Performance Optimization**

- Optimize the performance of the IoT devices and the Python script.
- Evaluate and address any bottlenecks or inefficiencies.
- Ensure that the system runs smoothly and efficiently.

## Extending Functionality

**Additional Features**

- Consider adding new features or functionalities to the IoT devices.
- Explore possibilities for expanding the capabilities of your environmental monitoring system.

**User Interface Improvements**

- If applicable, improve the user interface of the IoT devices or any display components.
- Ensure that users can easily interact with the system and access data.

## Testing and Quality Assurance

- Conduct thorough testing of the IoT devices and the Python script.
- Test different scenarios, including extreme conditions, to ensure robustness.
- Implement quality assurance measures to identify and resolve any bugs or issues.

## Conclusion

In Stage 4 of our technology project, we have focused on enhancing the IoT devices and the Python script that drive our environmental monitoring system. By refining data collection, optimizing performance, and potentially extending functionality, we have taken significant steps toward building a comprehensive solution. Continue to document your progress and share your work for assessment.

---

## Code

```ino
#include "DHT.h"

#define DHTPIN 15
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  Serial.println(F("DHTxx test!"));

  dht.begin();
}

void loop() {
 
  delay(2000);

  float h = dht.readHumidity();
  float t = dht.readTemperature(); // Read temperature as Celsius
  float f = dht.readTemperature(true); // Read temperature as Fahrenheit

  // Check
  if (isnan(h) || isnan(t) || isnan(f)) {
    Serial.println(F("Failed to read from DHT sensor!"));
    return;
  }

  float hif = dht.computeHeatIndex(f, h); // Compute heat index in Fahrenheit
  float hic = dht.computeHeatIndex(t, h, false); // Compute heat index in Celsius

  Serial.print(F("Humidity: "));
  Serial.print(h);
  Serial.print(F("%  Temperature: "));
  Serial.print(t);
  Serial.print(F("°C "));
  Serial.print(f);
  Serial.print(F("°F  Heat index: "));
  Serial.print(hic);
  Serial.print(F("°C "));
  Serial.print(hif);
  Serial.println(F("°F"));
}
```

## Result

![Image](Result.png)