

# 🔧 SPI Master Interface – VHDL Design & Simulation 🌟

A complete **VHDL implementation and simulation** of a **Serial Peripheral Interface (SPI) Master**. This project demonstrates digital communication protocol design using a **Finite State Machine (FSM)** model in VHDL with **CPOL = 0** and **CPHA = 1**.

---


### 📷 Demo Snapshot

![Screenshot](https://github.com/user-attachments/assets/48bb4e5b-787e-4ca7-bfe3-35e23e5639f2)

---

## 🔌 About SPI (Serial Peripheral Interface)

> SPI is a synchronous, full-duplex communication protocol widely used in embedded systems for interfacing peripherals like sensors, ADCs, memory, and display controllers.

### 📚 Key SPI Concepts:

| Signal | Direction | Description                              |
|--------|-----------|------------------------------------------|
| **SCLK** | Output    | Serial Clock – Drives timing (synchronous) |
| **MOSI** | Output    | Master Out Slave In – Data from Master   |
| **MISO** | Input     | Master In Slave Out – Data from Slave    |
| **SS̅ (CS)** | Output    | Slave Select – Activates the slave device |

---

### 🧠 Why Use SPI?

✅ **Full Duplex Communication**  
✅ **Faster than UART & I2C** (16–32 Mbps typical)  
✅ **Supports Multiple Slaves**  
✅ **Widely Supported in ICs**  

⚠️ **More Pin Usage**  
⚠️ **Not Ideal for Long Distances**  
⚠️ **Many Variants and Modes**  

---

## ⚙️ SPI Modes (CPOL / CPHA)

| **Mode** | **CPOL** | **CPHA** | **Clock Idle** | **Sampling Edge**        |
|----------|----------|----------|----------------|---------------------------|
| 0        | 0        | 0        | LOW            | Rising Edge               |
| 1 ✅     | 0        | 1        | LOW            | Falling Edge *(Used)*     |
| 2        | 1        | 0        | HIGH           | Falling Edge              |
| 3        | 1        | 1        | HIGH           | Rising Edge               |

> 📝 *This project uses SPI Mode 1: CPOL = 0, CPHA = 1.*

---

## 🛠️ Project Features

- ✅ SPI Master designed as a **finite state machine (FSM)** in VHDL  
- ✅ Fully simulated using **Vivado testbench**  
- ✅ Data transmitted and received using `sndData` and `rcvData` signals  
- ✅ Simulated 8-bit transfer (configurable via `USPI_SIZE` generic)  
- ✅ Clean timing and signal transitions observed in waveform

---

## 🧱 FSM State Overview

| **State**      | **Description**                                 |
|----------------|-------------------------------------------------|
| `sidle`        | Idle, waits for `start = 1`                     |
| `sstartx`      | Initializes write buffer                        |
| `sstart_lo`    | Drives first bit of data and sets clock high    |
| `sclk_hi`      | Transfers MSB, shifts output                    |
| `sclk_lo`      | Receives data on falling edge                  |
| `sstop_hi`     | Sends final bit                                 |
| `sstop_lo`     | Deselects slave, returns to idle                |

---

## 🧪 Simulation Setup

### ✅ Testbench Highlights

- Simulates clock (`bclk`), reset (`resetn`), start control, and `sdi/sdo` logic  
- Uses a **clock divider** to make SPI clock observable in simulation  
- Implements data loopback (e.g., `sdi <= NOT sdo`)  
- Tests transmission of `x"5A"` from master to (simulated) slave

```vhdl
signal sndData : std_logic_vector(7 downto 0) := x"5A";
signal rcvData : std_logic_vector(7 downto 0);
- 🧪 **Debugging Tools:** Logic Analyzer, ILA (Integrated Logic Analyzer)
- 📊 **Visualization:** Vivado Waveform Viewer

---

✅ Transmission complete when done = '1'

| **Tool**        | **Description**                             |
| --------------- | ------------------------------------------- |
| 🧠 FPGA Target  | ZYNQ-7000 SoC (Xilinx) *(for hardware use)* |
| 💾 HDL Language | VHDL                                        |
| 🧪 Testbench    | Written in VHDL                             |
| 🛠️ Simulator   | Vivado Simulation & Waveform Viewer         |
| 📐 FSM Tool     | FiZZiM *(for FSM design & visualization)*   |

📌 Result & Conclusion
✅ Successfully simulated an SPI Master in VHDL using a structured FSM
✅ Verified 8-bit SPI Mode 1 (CPOL=0, CPHA=1) communication
✅ Demonstrated timing accuracy and FSM transitions
✅ Ready for integration with real hardware or IP cores


