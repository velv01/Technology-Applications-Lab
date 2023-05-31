# Interface the MPU6050 sensor with the ESP32 using the Arduino IDE.

1. Install the Required Libraries:
   - Open the Arduino IDE.
   - Go to "Sketch" -> "Include Library" -> "Manage Libraries".
   - Search for "MPU6050" and install the "MPU6050" library by Electronic Cats.
   - Install the "Wire" library if it is not already installed.

2. Wiring Connections:
   - Connect the VCC pin of the MPU6050 to the 3.3V power supply of the ESP32.
   - Connect the GND pin of the MPU6050 to the ground (GND) of the ESP32.
   - Connect the SDA pin of the MPU6050 to the SDA pin of the ESP32 (GPIO pin).
   - Connect the SCL pin of the MPU6050 to the SCL pin of the ESP32 (GPIO pin).

3. Upload the Code:
   - Open a new sketch in the Arduino IDE.
   - Copy and paste the following code to read the MPU6050 sensor data and print it to the serial monitor:

```cpp
#include <Wire.h>
#include <MPU6050.h>

MPU6050 mpu;

void setup() {
  Serial.begin(115200);
  Wire.begin();
  
  mpu.initialize();
  
  Serial.println("MPU6050 Connection Successful");
}

void loop() {
  int16_t ax, ay, az;
  int16_t gx, gy, gz;
  
  mpu.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);
  
  // Print the sensor data
  Serial.print("Accelerometer: ");
  Serial.print("X = "); Serial.print(ax);
  Serial.print(" Y = "); Serial.print(ay);
  Serial.print(" Z = "); Serial.println(az);
  
  Serial.print("Gyroscope: ");
  Serial.print("X = "); Serial.print(gx);
  Serial.print(" Y = "); Serial.print(gy);
  Serial.print(" Z = "); Serial.println(gz);
  
  delay(1000); // Adjust the delay as per your requirement
}
```

4. Select the Board and Port:
   - In the Arduino IDE, go to "Tools" -> "Board" and select your ESP32 board.
   - Go to "Tools" -> "Port" and select the COM port to which the ESP32 is connected.

5. Upload and Run:
   - Click the "Upload" button in the Arduino IDE to upload the code to the ESP32.
   - Open the serial monitor by going to "Tools" -> "Serial Monitor" to see the MPU6050 sensor data.

Ensure that you have properly connected the MPU6050 sensor to the ESP32 and have selected the correct board and COM port in the Arduino IDE. The code will read the accelerometer and gyroscope data from the MPU6050 sensor and print it to the serial monitor. You can modify the code to suit your specific requirements and integrate it into your project accordingly.