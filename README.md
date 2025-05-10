# AutomaticGateDemoKit


This project uses an ultrasonic sensor, servo motor, LEDs, and a buzzer to create a simple **proximity-based gate system**. When an object is detected within a certain distance, the gate opens and gives visual and audio feedback. If no object is detected for a while, the gate closes automatically.

## 🚀 Features

- Automatic gate control based on object proximity
- Visual feedback using red and blue LEDs
- Buzzer alert with a "bump-bump" rhythm when gate is open
- Customizable distance threshold and delays

---

## 🔧 Components Used

| Component          | Description                  |
|-------------------|------------------------------|
| Ultrasonic Sensor | Measures object distance     |
| Servo Motor       | Opens and closes the gate    |
| Red LED           | Indicates gate is closed     |
| Blue LED          | Indicates gate is open       |
| Buzzer            | Emits "bump bump" sound      |
| Arduino Board     | Main microcontroller         |

---

## ⚙️ Wiring (Pin Configuration)

| Arduino Pin | Component              |
|-------------|------------------------|
| 2           | Ultrasonic Trigger     |
| 3           | Ultrasonic Echo        |
| 4           | Red LED (Anode)        |
| 8           | Red LED (Cathode)      |
| 7           | Blue LED (Cathode)     |
| 5           | Blue LED (Anode)       |
| 6           | Servo Signal           |
| 12          | Buzzer                 |

---

## 📏 How It Works

1. **Distance Detection:**
   - The ultrasonic sensor continuously measures the distance to nearby objects.
   - If an object is detected closer than `12 cm`, it triggers the gate to open.

2. **Gate Control:**
   - The servo moves to `90°` to open and returns to `0°` to close.
   - The gate closes only if no object is detected for `5 seconds`.

3. **Visual Feedback:**
   - When closed, the **red LED** turns on.
   - When open, the **blue LED** turns on.

4. **Buzzer Alert:**
   - While the gate is open, the buzzer beeps in a **"bump-bump"** rhythm.
   - Beep pattern: 100 ms ON, 800 ms OFF.

---

## 🛠️ Code Configuration

You can change the following constants to modify behavior:

```cpp
const float thresholdDistance = 12.0;  // Distance in cm to trigger opening
const int closedAngle = 0;             // Servo angle when gate is closed
const int openAngle = 90;              // Servo angle when gate is open
const unsigned long closeDelay = 5000; // Time in ms before auto-closing
const unsigned long bumpOnTime = 100;  // Buzzer ON duration
const unsigned long bumpOffTime = 800; // Time between buzzes
