# desk buddy - AI Voice Assistant Robot

Welcome to the desk buddy project! This is an interactive ESP32-based robot assistant that uses an OLED screen to display facial expressions based on its current activity. It features a push-to-talk button, a digital I2S microphone for listening, and an I2S audio amplifier with a speaker to talk back.

The project uses a Finite State Machine logic loop to handle transitioning between staying idle, listening to voice input, simulating thinking, and speaking its response.


##  Bill of Materials (BOM)

| Item | Component Description | Quantity | Purpose |
| 1 | ESP32 Development Board (30-pin) | 1 | The main brain of the robot |
| 2 | SSD1306 OLED Display (128x64, I2C) | 1 | Displays the robot's eyes and mouth animations |
| 3 | INMP441 Omnidirectional Microphone | 1 | Captures voice input via I2S |
| 4 | MAX98357A I2S Audio Amplifier | 1 | Decodes digital audio signals for the speaker |
| 5 | 8-Ohm Micro Speaker | 1 | Outputs the voice responses |
| 6 | Tactile Push Button (4-pin) | 1 | Physical push-to-talk trigger |
| 7 | Solderless Breadboard | 1 | Prototyping base for wiring components |
| 8 | Jumper Wires (M-M / M-F) | 1 Pack | Connects components together |


## Hardware Pin Mapping

To ensure stable operation and avoid boot failures, the hardware components are mapped to the ESP32 pins as follows:

### SSD1306 OLED Screen (I2C)
* **VCC** ➡️ 5V / VIN Rail
* **GND** ➡️ GND Rail
* **SCL** ➡️ GPIO 22
* **SDA** ➡️ GPIO 21

### INMP441 Microphone (I2S Input)
* **VDD** ➡️ 3.3V (Crucial: Do not use 5V or it will burn out!)
* **GND** ➡️ GND Rail
* **L/R** ➡️ GND Rail (Configures microphone to the Left audio channel)
* **SCK** ➡️ GPIO 32
* **WS** ➡️ GPIO 33
* **SD** ➡️ GPIO 34

### MAX98357A Amplifier (I2S Output)
* **VIN** ➡️ 5V / VIN Rail (For maximum volume)
* **GND** ➡️ GND Rail
* **BCLK** ➡️ GPIO 14
* **LRC** ➡️ GPIO 15
* **DIN** ➡️ GPIO 27
* *Note: GAIN and SD pins are left disconnected (defaults to 9dB gain, always on).*

### Push Button
* **Pin 1 (Top-Left)** ➡️ GPIO 13 (Safe, non-strapping pin)
* **Pin 2 (Bottom-Right)** ➡️ GND Rail (Configured with internal `INPUT_PULLUP`)

---

## How to Run the Project
1. Open the code inside the `firmware/` folder using the **Arduino IDE**.
2. Make sure you have installed the `Adafruit GFX` and `Adafruit SSD1306` libraries via the Library Manager.
3. Select your ESP32 Dev Module board and correct COM port.
4. Upload the sketch!
5. Open the Serial Monitor at `115200` baud to watch the debug messages as you press the button.
