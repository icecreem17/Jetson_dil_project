# jetson_arduino
This repository connects the Jetson Nano and the CO2 sensor to measure the CO2 concentration in real time and inform the result of the ventilation notification system.


```
Supplies
1. Jetson Nano
2. monitor(Recommend having a monitor in addition to your computer. If you use it on your computer (especially a laptop), there is a possibility of an OS collision.)
3. LAN USB
4. power(You have to use 5A with power. If you use more than that, Jetson Nano will be ruined.)
5. Wired mouse and keyboard(Wireless mice and keyboards are also available, but this repository does not show how to connect them.)
6. SD card(least to 32 GB)
7. cm1106(Carbon dioxide sensor)
8. Cable wire connecting Jetson Nano to sensor
```


## 1. Jetson Nano connects to CO2 sensor


![image](https://github.com/user-attachments/assets/6275ddd0-20cd-4292-a50c-cd5b9ef752ae)






## 2. Arduino code


### This code is a code that measures real-time CO2 concentration by connecting with Arduino.
### This code must be entered in Arduino.


```
#include <cm1106_i2c.h>

CM1106_I2C cm1106_i2c;

void setup() {
  cm1106_i2c.begin();
  Serial.begin(9600);
  delay(1000);
}

void loop() {
  uint8_t ret = cm1106_i2c.measure_result();

  if (ret == 0) {
    Serial.print("CO2:");
    Serial.println(cm1106_i2c.co2); 
    Serial.println("Operating normal");//Transfer CO2 data to serial
  } else {
    Serial.println("Error reading sensor data.");
  }
  delay(1000);
}
```






## 3. Jetson Nano Python3 code


### This code connects Arduino and Discord to give a ventilation alarm if the carbon dioxide concentration is 850 ppm or 1000 ppm, and a notification of completion of ventilation if the carbon dioxide concentration has returned to normal after ventilation.
### This code should generate a Python file in Jetson Nano and enter it into that file.


```
import serial
import requests

# Arduino Serial Port Settings
SERIAL_PORT = '/dev/ttyUSB0'  # Check and set the port to which Arduino is connected
BAUD_RATE = 9600  # Set the same board rate as Arduino

# Setting thresholds
THRESHOLD_1 = 850
THRESHOLD_2 = 1000
RESET_THRESHOLD = 700  # Concentration threshold to announce that ventilation is complete

# Discord Web Hook URL
DISCORD_WEBHOOK_URL = 'https://discord.com/api/webhooks/your_webhook_url_here'


class AlertManager:
  def __init__(self):
      self.alert_850_sent = False
      self.alert_1000_sent = False
      self.reset_alert_sent = False

  def reset_alerts(self):
      """Initialize notification status"""
      self.alert_850_sent = False
      self.alert_1000_sent = False
      self.reset_alert_sent = False


def send_discord_alert(message):
  """Send a notification message to Discord"""
  data = {"content": message}
  response = requests.post(DISCORD_WEBHOOK_URL, json=data)
  if response.status_code == 204:
      print("[Discord notification] Your message has been sent successfully.")
  else:
      print(f"[Discord notification] Failed to send message: {response.status_code}")


alert_manager = AlertManager()
ser = None  # Initial value setting

try:
  # Open Serial Port
  ser = serial.Serial(SERIAL_PORT, BAUD_RATE, timeout=1)
  print("Arduino connection complete")

  while True:
      if ser.in_waiting > 0:
          line = ser.readline().decode('utf-8').strip()  # Read Data from Arduino
          print(f"[Arduino Data] {line}")

          if line.startswith("CO2:"):
              co2_value = int(line.split(":")[1])
              print(f"[Sensor] Current CO2 concentration: {co2_value} ppm")

              # Check thresholds and send notifications (send only once)
              if co2_value > THRESHOLD_2 and not alert_manager.alert_1000_sent:
                  alert_message = f"[Warning] CO2 concentration exceeded threshold 1000 ppm with {co2_value} ppm!"
                  print(alert_message)
                  send_discord_alert(alert_message)
                  alert_manager.alert_1000_sent = True  # Update notification status

              elif co2_value > THRESHOLD_1 and not alert_manager.alert_850_sent:
                  alert_message = f"[Caution] CO2 concentration exceeded threshold 850 ppm with {co2_value} ppm!"
                  print(alert_message)
                  send_discord_alert(alert_message)
                  alert_manager.alert_850_sent = True  # Update notification status

              # If the CO2 concentration falls below RESET_THRESHOLD
              elif co2_value <= RESET_THRESHOLD and not alert_manager.reset_alert_sent:
                  reset_message = f"[Notice] Ventilation completed with CO2 concentration of {co2_value} ppm!"
                  print(reset_message)
                  send_discord_alert(reset_message)
                  alert_manager.reset_alert_sent = True  # Update the status of ventilation completed notification

              # Initialize general notification status when the value falls below the threshold
              if co2_value > RESET_THRESHOLD:
                  alert_manager.reset_alert_sent = False

except Exception as e:
  print(f"[Error] {e}")

finally:
  if ser and ser.is_open:  # ser 변수가 정의되었는지 확인
      ser.close()
      print("[Sensor] Serial port closed")
```
