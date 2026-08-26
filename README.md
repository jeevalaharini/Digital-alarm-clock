# ⏰ Digital Alarm Clock using Verilog

A simple **24-hour Digital Alarm Clock** designed using **Verilog HDL** and verified through simulation.

This project demonstrates how basic digital design concepts such as **counters, registers, clock division, comparison logic, reset, and sequential logic** can be combined to build a functional digital clock with an alarm.

## 📌 Project Overview

The Digital Alarm Clock keeps track of:

```text
Hours   : 00–23
Minutes : 00–59
Seconds : 00–59
```

The alarm is activated when the current time matches the programmed alarm time.

Example:

```text
Current Time : 00:00:59
Alarm Time   : 00:01

             ↓

Current Time : 00:01:00
Alarm        : 1 🔔
```

## ✨ Features

* ⏱️ 24-hour time format
* 🔢 Seconds, minutes and hours counters
* 🔄 Automatic rollover logic
* ⏰ Programmable alarm hour and minute
* 🔔 Alarm enable control
* ♻️ Reset functionality
* 🧮 Clock divider for 1-second timing
* 🧪 Verilog testbench for functional verification
* 📈 Waveform generation using VCD
* 🔍 Simulation using EDA Playground and EPWave

## 🏗️ Design Architecture

```text
                 FPGA / Simulation Clock
                         │
                         ▼
                ┌─────────────────┐
                │  Clock Divider  │
                └────────┬────────┘
                         │
                    1-second tick
                         │
                         ▼
              ┌─────────────────────┐
              │    Time Counter     │
              │                     │
              │ Hour : Min : Sec    │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │  Alarm Comparator   │
              │                     │
              │ Current Time ==     │
              │ Alarm Time          │
              └──────────┬──────────┘
                         │
                         ▼
                    🔔 ALARM
```

## 📂 Project Structure

```text
Digital-Alarm-Clock/
│
├── digital_alarm_clock.v
├── digital_alarm_clock_tb.v
└── README.md
```

### `digital_alarm_clock.v`

Contains the main RTL design.

It implements:

* Clock division
* Hour counter
* Minute counter
* Second counter
* Alarm comparison
* Reset logic

### `digital_alarm_clock_tb.v`

Contains the simulation testbench.

It provides:

* Clock generation
* Reset stimulus
* Alarm configuration
* Simulation control
* Output monitoring
* VCD waveform generation

## 🧠 Main Verilog Concepts Used

| Concept                   | Application                 |
| ------------------------- | --------------------------- |
| Sequential Logic          | Timekeeping                 |
| Non-blocking Assignment   | Register updates            |
| Counters                  | Hours, minutes and seconds  |
| Clock Divider             | 1-second timing             |
| Comparator                | Alarm detection             |
| Reset                     | Initializing the clock      |
| Testbench                 | Functional verification     |
| `$monitor`                | Observing simulation output |
| `$dumpfile` / `$dumpvars` | Waveform generation         |

## 🧪 Simulation

For simulation purposes, a smaller clock-divider value is used instead of an actual FPGA clock frequency.

For example:

```verilog
parameter CLK_FREQ = 2;
```

This allows the clock to advance quickly during simulation.

### Expected Output

When the alarm is programmed for `00:01`:

```text
Time = 00:00:58 | Alarm = 0
Time = 00:00:59 | Alarm = 0
Time = 00:01:00 | Alarm = 1
Time = 00:01:01 | Alarm = 0
```

The alarm becomes HIGH when the current time matches the programmed alarm time.

## 📊 Waveform Verification

The testbench generates a VCD file:

```verilog
$dumpfile("alarm_clock.vcd");
$dumpvars(0, digital_alarm_clock_tb);
```

The waveform can be viewed using **EPWave**.

Important signals to observe:

```text
clk
reset
hour
minute
second
alarm
```

The `alarm` signal should transition to:

```text
0 → 1
```

when the programmed alarm time is reached.

## 🛠️ Tools Used

* **Verilog HDL**
* **EDA Playground**
* **Icarus Verilog**
* **EPWave**

## 🚀 Future Improvements

The current design can be extended into a more complete FPGA-based alarm clock by adding:

* 🔢 7-segment display interface
* 🔘 Push-button controls
* ⏰ Alarm ON/OFF button
* ⬆️ Hour and minute setting buttons
* 🔊 Buzzer output
* 💾 Alarm time storage
* 🕐 Real-time clock interface
* 🖥️ FPGA board implementation

## 🎯 Learning Outcome

This project helped me understand how **sequential digital logic can be used to build a practical hardware system**.

It strengthened my understanding of:

**Clock → Counter → State/Time → Comparison → Output**

and gave me hands-on experience with **RTL coding, simulation, debugging and waveform analysis**.

## 👩‍💻 Author

**Jeevalaharini**

ECE | Digital Electronics | Verilog | RTL Design | VLSI

---

⭐ If you find this project useful, feel free to explore the code and experiment with the design!
