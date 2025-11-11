# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.

<img width="500" height="500" alt="Screenshot 2025-11-11 125627" src="https://github.com/user-attachments/assets/00009bbc-4225-45e8-91cc-1570635c9dc3" />


2. Click **File → New STM32 Project**.

   <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/4ba9b08a-beb8-43e2-bfb6-53b813f4d7cc" />
   <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/994352bd-5f55-4dc0-ad9f-07c4a4e3df58" />

3. Select the **target microcontroller** or board and click **Next**.
  
 <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/a022f01f-e5ce-4613-95cb-ee77c1a0d4e7" />


4. Name the project.

   <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/56b019c3-8c37-4c3f-a6ed-e380137ca763" />


5. The corresponding `.ioc` file will be generated automatically.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/95321e89-0abd-47ae-9775-6297d0659d38" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/8694a85e-f957-427b-a199-7998695bc1a9" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7a92c121-21a9-43cc-ae17-9274ce784705" />

 
8. Edit the generated main program as required.

    <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/b811314b-3183-4073-b773-6564202c6ee9" />

   <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/fa53e253-004d-4c3f-aa71-98b8aa28d1e1" />

10. Click **Project → Build All**.
   <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e6b9360f-9e30-4977-9c1f-95716b6f8e72" />

11. Link the **HEX file** using the post-build process.
   <img width="654" height="348" alt="image" src="https://github.com/user-attachments/assets/be4b2929-99bd-444e-ba74-fcf77f237bf0" />

12. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/fcc3de8d-5184-4cfc-a858-c3cd9a5ef4d4" />

13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
#### CASE 1: LED ON:
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/b3542a47-77ff-48ed-a297-617d024884cf" />


#### CASE 2: LED OFF:
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/d982561b-dbc1-4a59-8c73-d4ba3eba283d" />


---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
