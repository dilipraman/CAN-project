# 🚗 Body Control Module (BCM) using ARM7 LPC2129

This project implements a **Body Control Module (BCM)** on the **ARM7 LPC2129** microcontroller.  
The goal is to simplify vehicle wiring, reduce manufacturing and maintenance costs, and ensure real-time performance using **CAN (Controller Area Network)** communication.

---

## 📌 Key Features

- 🧠 **Microcontroller**: ARM7 LPC2129
- 📡 **Communication**: CAN Protocol
- 🔁 **Functions Controlled**:
  - Left & Right Indicator LEDs
  - Windshield Wiper
  - 16x2 LCD Display (4-bit Mode)
- 💡 **Interface**:
  - Push buttons for manual control
  - LCD for status display

---

## 🛠️ Modules & Files

| File Name       | Description |
|----------------|-------------|
| `trans.c`       | Transmitter logic with LCD display and push button controls. Sends CAN frames to nodes based on input. |
| `left_led.c`    | Receives CAN ID `0x0A` and toggles the **left indicator LED**. |
| `right_led.c`   | Receives CAN ID `0x0B` and toggles the **right indicator LED**. |
| `wiper.c`       | Receives CAN ID `0x0C` and controls **wiper motor** direction. |
| `can_fun.c`     | CAN protocol initialization, frame TX/RX, delay functions. |
| `4bitdisplay.c` | LCD initialization and display functions using 4-bit mode. |

---

## 🔧 How It Works

1. **BCM Transmitter (`trans.c`)**:
   - Listens for button presses (SW1, SW2, SW3).
   - Displays status on LCD.
   - Sends corresponding CAN frame (`0x0A`, `0x0B`, `0x0C`) to activate modules.

2. **Receivers**:
   - Each receiver node listens for its respective CAN ID.
   - Toggles the corresponding output: left LED, right LED, or wiper motor.

3. **CAN Communication**:
   - Initialized with `can_init()`.
   - Uses `txd()` and `rxd()` to transmit and receive CAN frames.

---

## 📚 What I Learned

- Register-level programming with LPC2129.
- CAN protocol configuration and real-time messaging.
- Peripheral control using GPIO and I/O registers.
- LCD interfacing in 4-bit mode.
- Code modularity, interrupt-free logic for real-time systems.

