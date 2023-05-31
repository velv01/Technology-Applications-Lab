# DHT11 with ESP32

## To interface the DHT11 temperature and humidity sensor with the ESP32 microcontroller, you can follow these steps:

1. Wiring Connections:
   - Connect the VCC pin of the DHT11 to the 3.3V power supply of the ESP32.
   - Connect the GND pin of the DHT11 to the ground (GND) of the ESP32.
   - Connect the DATA pin of the DHT11 to any GPIO pin of the ESP32 (e.g., GPIO 4).

2. Install Required Libraries:
   - Open the Arduino IDE or your preferred development environment.
   - Install the "DHT sensor library" for ESP32. You can install it by going to "Tools" -> "Library Manager" and searching for "DHT sensor library".

3. Upload the Code:
   - Open a new sketch in the Arduino IDE.
   - Copy and paste the following code to read the DHT11 sensor data and print it to the serial monitor:

```cpp
#include <DHT.h>

#define DHTPIN 4     // Define the GPIO pin to which the DHT11 data pin is connected
#define DHTTYPE DHT11   // Define the DHT type (DHT11 or DHT22)

DHT dht(DHTPIN, DHTTYPE);   // Create an instance of the DHT sensor

void setup() {
  Serial.begin(115200);
  dht.begin();
  
  Serial.println("DHT11 Connection Successful");
}

void loop() {
  // Read temperature and humidity data
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();
  
  // Check if any reading failed
  if (isnan(temperature) || isnan(humidity)) {
    Serial.println("Failed to read data from DHT sensor");
    return;
  }
  
  // Print the sensor data
  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.println(" °C");
  
  Serial.print("Humidity: ");
  Serial.print(humidity);
  Serial.println(" %");
  
  delay(2000); // Adjust the delay as per your requirement
}
```

4. Select the ESP32 Board:
   - In the Arduino IDE, go to "Tools" -> "Board" and select your ESP32 board.

5. Select the COM Port:
   - In the Arduino IDE, go to "Tools" -> "Port" and select the COM port to which the ESP32 is connected.

6. Upload and Run:
   - Click the "Upload" button in the Arduino IDE to upload the code to the ESP32.
   - Open the serial monitor by going to "Tools" -> "Serial Monitor" to see the DHT11 sensor data.

Ensure that you have properly connected the DHT11 sensor to the ESP32 and have selected the correct board and COM port in the Arduino IDE. The code will read the temperature and humidity data from the DHT11 sensor and print it to the serial monitor. You can modify the code to suit your specific requirements and integrate it into your project accordingly.