# PWM-based LED Brightness Adjustment using Potentiometer

This project demonstrates how to control an LED’s brightness using **PWM (Pulse Width Modulation)**, with a **potentiometer as the analog input** on an **STM32F3 microcontroller**.
The potentiometer value is read via **ADC**, and mapped to a PWM duty cycle to adjust the LED intensity in real time.

---
> ⚠️ WARNING:
>
> Without using PWM or ADC, you can achieve similar LED brightness control by connecting the potentiometer’s output directly to the LED’s anode.

## 🔧 Hardware Requirements

* STM32F303RE (or similar STM32 board)
* Potentiometer (10kΩ recommended)
* LED + resistor (220Ω–330Ω)
* Breadboard and jumper wires

---

## 💻 Software / Tools

* STM32CubeIDE
* HAL libraries (ADC, TIM/PWM)

---

## ⚙️ How It Works

1. The potentiometer provides an **analog voltage (0–5V)** to the ADC.
2. The ADC reads this value (0–4095 for 12-bit resolution).
3. The value is scaled to match the **ARR (Auto Reload Register)** range of the PWM timer.
4. The duty cycle is updated using `__HAL_TIM_SET_COMPARE`.
5. The LED brightness changes proportionally to the potentiometer position.

---

## 📂 Code Snippet

```c
uint32_t adcValue = HAL_ADC_GetValue(&hadc1);

__HAL_TIM_SET_COMPARE(&htim1, TIM_CHANNEL_1, adcValue);
```

---

## 🚀 Demo

* Turning the potentiometer adjusts the LED brightness smoothly.
* At minimum position → LED is OFF.
* At maximum position → LED is fully ON.

---

“Additionally, you can watch the project demonstration video here
