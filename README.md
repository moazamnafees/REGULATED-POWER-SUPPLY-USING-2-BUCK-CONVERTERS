# REGULATED-POWER-SUPPLY-USING-2-BUCK-CONVERTERS
## 📌 Project Overview
This project focuses on designing and simulating a **reliable power supply system** for an **ESP32-based Infinity Swimming Pool Control System**.  
The main goal is to provide **stable 5V power** to the ESP32 using **rechargeable Li-ion battery cells**, with proper **charging, protection (BMS), and voltage regulation**.

The complete system is **designed and tested in Proteus 8 Professional** before real-world implementation.

---

## ⚙️ General Power Architecture
The power system follows this flow:

### Description
- **12V DC Input:** External power source (SMPS / adapter).
- **Buck Converter (12V → 8.4V):** Steps down voltage to safely charge the 2S battery pack.
- **2S Li-ion Battery Pack:** Two 3.7V cells connected in series for energy storage.
- **2S BMS:** Provides overcharge, overdischarge, and overcurrent protection.
- **Buck Converter (8.4V → 5V):** Regulates battery voltage to stable 5V.
- **ESP32 Controller:** Main control unit powered through 5V supply.

This architecture ensures **safe charging**, **long battery backup**, and **stable operation** of the ESP32-based system.

---

## 🔋 Battery System
- **Battery Type:** Rechargeable Li-ion
- **Configuration:** 2 cells in series (2S)
- **Each Cell:** 3.7V nominal
- **Pack Voltage:**  
  - Nominal: 7.4V  
  - Fully charged: 8.4V
- **Capacity:** As per design requirement (1000mAh – 5000mAh)
- **Backup Target:** Multiple days (depending on capacity)

---

## 🔐 Battery Management System (BMS)
A **2S BMS module (HX-2S-D01 concept)** is used for battery protection.

### BMS Functions:
- Over-charge protection
- Over-discharge protection
- Over-current / short-circuit protection
- Cell balancing (basic)

The BMS is placed **between the battery pack and the load/charger** to ensure safety.

---

## 🔌 Charging Section
- **Input Supply:** 12V DC (adapter or SMPS)
- **Buck Converter #1:**  
  - Converts 12V → 8.4V  
  - Used as a **charging voltage** for the 2S battery pack
- Charging is done **through the BMS**, not directly to the cells.

⚠️ Directly connecting 12V to batteries is unsafe and avoided.

---

## 🔧 Regulation for ESP32
- **Buck Converter #2:**  
  - Input: 7.4V–8.4V (battery output)  
  - Output: **Regulated 5V**
- This 5V output powers:
  - ESP32
  - Display module
  - Control electronics

The buck converter ensures:
- High efficiency
- Stable voltage
- Safe current delivery

---

## 🧠 ESP32 Power Requirement
- Operating Voltage: **5V (VIN pin)**
- Average Current: 80–150 mA
- Peak Current (WiFi/Bluetooth): up to 500–600 mA

The selected buck converter supports sufficient current for safe operation.

---

## 🧪 Proteus Simulation
This project includes a **full Proteus 8 Professional simulation**, which contains:

### Simulated Blocks:
- 12V DC source
- Buck converter (12V → 8.4V)
- 2S Li-ion battery model
- 2S BMS protection circuit
- Buck converter (8.4V → 5V)
- Load representing ESP32
- LEDs for protection status

### Purpose of Simulation:
- Verify charging behavior
- Verify cut-off during over-charge / over-discharge
- Validate stable 5V output
- Test fault conditions safely

---

## 🛠 Tools & Software
- **Proteus 8 Professional**
- Arduino IDE (for ESP32 firmware – future step)
- Basic electronics components (comparators, MOSFETs, resistors)

---




