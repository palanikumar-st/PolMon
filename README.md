## System Design

The Air Quality Monitoring System consists of an ESP32-based sensing unit and a Raspberry Pi Pico 2 W-based display unit.

The ESP32 collects data from multiple environmental sensors, including NOx, SO₂, PM2.5, PM10, noise, ambient light, and ammonia sensors. After processing and calibrating the sensor readings, the ESP32 transmits the environmental parameters to the Raspberry Pi Pico 2 W.

The Raspberry Pi Pico 2 W drives a 3.5-inch display, providing real-time visualization of air quality data. This allows users to monitor environmental conditions directly from the device without requiring an external computer or mobile application.

### Power System

The device is powered using four rechargeable Lithium-Ion cells connected as a 4S battery pack.

The power subsystem includes:

* 4S Battery Management System (BMS) for battery protection
* 4S Lithium-Ion Charger Module for charging
* Buck Converter (5V) for powering the ESP32
* Buck Converter (5V) for powering the Raspberry Pi Pico 2W and display

This architecture enables portable operation while ensuring safe battery charging and discharge.

### Air Sampling System

To improve sensor response and measurement consistency, a 12V DC fan is integrated into the enclosure.

The fan:

* Draws ambient air into the system
* Passes air through a dust filter
* Directs filtered airflow across the gas and particulate sensors
* Improves sensor exposure to environmental conditions
* Reduces contamination from larger dust particles

### System Architecture

```text
Ambient Air
      │
      ▼
 Dust Filter
      │
      ▼
 12V DC Fan
      │
      ▼
 Sensor Chamber
 ├── NOx Sensor
 ├── SO₂ Sensor
 ├── NH₃ Sensor
      │
      ▼
    ESP32
      │
      ▼
 Raspberry Pi Pico 2 W
      │
      ▼
 3.5-inch Display
```
The PM Sensor needs dust inlet, so it is placed separately. The sensors light and noise were exposed out for much better sensing which are covered to prevent dust acquisition.

### Key Specifications

| Feature               | Description                            |
| --------------------- | -------------------------------------- |
| Controller            | ESP32                                  |
| Display Controller    | Raspberry Pi Pico 2 W                  |
| Display               | 3.5-inch TFT Display                   |
| Power Source          | 4 × Li-Ion Cells (4S Pack)             |
| Battery Protection    | 4S BMS                                 |
| Charging              | 4S Charger Module                      |
| Airflow System        | 12V Fan with Dust Filter               |
| Communication         | ESP32 ↔ Pico 2 W                       |
| Monitoring Parameters | NOx, SO₂, NH₃, PM2.5, PM10, Noise, Lux |
| Real-Time Clock       | DS3231                                 |
