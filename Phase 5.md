# Phase 5: Project Summary - IoT-Based Environmental Monitoring

## Project Overview

The IoT-Based Environmental Monitoring project is a comprehensive endeavor aimed at providing real-time environmental data, specifically temperature and humidity, to visitors in public parks. This innovative system facilitates informed decision-making for outdoor activities and aims to enhance visitor satisfaction by promoting data-driven experiences in natural settings.

## Design

**Project Objectives**
- The primary goals of this project are to deliver real-time environmental data to park visitors, assist them in planning outdoor activities based on current conditions, and ultimately, to enhance visitor satisfaction.
- The project design includes the deployment of IoT sensors in public parks, a web-based platform for environmental data display, and a robust integration strategy to connect IoT devices with the platform.

**Ideas and Prototypes**
- Our project team engaged in brainstorming sessions and ideation workshops to generate creative concepts for the IoT-based environmental monitoring system.
- We followed a structured approach, including defining objectives and testing throughout the project's lifecycle to ensure continuous refinement based on feedback from park visitors and other stakeholders.
- Prototypes were developed for both the IoT sensor deployment and the environmental monitoring platform. These prototypes focus on cost-effectiveness, energy efficiency, user-friendliness, and accessibility.

**Implementation Plan**
- The project scope encompasses the implementation of the IoT-based system within a specified timeframe.
- An estimated budget of over 3000 rupees was allocated for this project, covering resources such as hardware, software development, and personnel.

**Evaluation and Feedback**
- Key performance indicators (KPIs) were established to measure the project's success, including visitor engagement and satisfaction levels.
- Regular evaluations and adjustments, based on collected data and user feedback, ensure the project's continuous improvement.

**Sustainability and Future Expansion**
- A commitment to the long-term sustainability of this system is evident, as maintenance plans for IoT devices and the monitoring platform have been documented.
- Exploration of opportunities for expanding the system to more parks or incorporating additional environmental parameters highlights the project's forward-looking perspective.

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

### Simulated Images:
![Image](Phase_3/Image.png)

### Results:
![Image](Result.png)


## Project Output

The project's output is a fully functioning IoT-based environmental monitoring system that collects and displays real-time temperature and humidity data to park visitors. This system is designed to enhance outdoor experiences in public parks, promoting data-driven decision-making for visitors.

The IoT-Based Environmental Monitoring project represents a user-centric, innovative approach to environmental data collection and presentation. By combining IoT technology with web development and Python scripting, we have created a system that has the potential to transform the way people enjoy public parks. The project's use of Design Thinking, careful hardware and software selection, and a focus on user-friendly features contribute to its overall success.
