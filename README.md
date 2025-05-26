# 🚀 FPGA Projects – Zynq-7000 SoC

Welcome to my collection of FPGA-based projects implemented on the **ZYNQ-7000 SoC**. These projects highlight my experience with interfacing peripherals, working with digital communication protocols, and developing real-time embedded logic.

---

## 🔧 Project 1 – SPI Master Interface: Ambient Light Sensor 🌟

A practical implementation of an **SPI Master** inside the FPGA (PL side) communicating with an external **Ambient Light Sensor** (ADC).  
This project demonstrates hands-on digital interface control via **Serial Peripheral Interface (SPI)** protocol.

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

## 📈 SPI Modes: CPOL & CPHA

SPI operates in **4 modes** defined by **Clock Polarity (CPOL)** and **Clock Phase (CPHA)**:

| Mode | CPOL | CPHA | Description                     |
|------|------|------|---------------------------------|
| 0    | 0    | 0    | Idle Low, Sample on Rising Edge |
| 1    | 0    | 1    | Idle Low, Sample on Falling Edge|
| 2    | 1    | 0    | Idle High, Sample on Falling Edge|
| 3    | 1    | 1    | Idle High, Sample on Rising Edge|

📝 **Best Practice:** Always sample data **in the middle of the data bit period**, not at the edges, to avoid metastability.

---

## 🛠️ What This Project Demonstrates

- ✅ FPGA as **SPI Master**
- ✅ External ADC acting as **SPI Slave**
- ✅ Real-time signal interaction (MOSI, MISO, SCLK)
- ✅ SPI logic implemented without `chip select` for simplicity
- ✅ Clean timing and signal integrity at high speeds

---

## 🧰 Tools & Technologies

- 🧠 **FPGA SoC:** ZYNQ-7000 (Xilinx)
- 📦 **HDL: **VHDL
- 🧪 **Debugging Tools:** Logic Analyzer, ILA (Integrated Logic Analyzer)
- 📊 **Visualization:** Vivado Waveform Viewer

---
