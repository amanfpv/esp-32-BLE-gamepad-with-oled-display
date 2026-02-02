# Project Roadmap & Idea

This project started with a simple goal:  
to build a custom Bluetooth game controller using an ESP32, similar in layout to an Xbox-style controller.

## Phase 1 – Hardware Bring-up
The first step was connecting and testing individual components:
- ESP32 board
---- the main purpose of using this specific board was that it supports both wifi and bluetooth and 32 pin for more component unlike audrion uno or nano
- Analog joysticks
---- 2 ps2 joysticks are used in this project , both of the joystick works as the axis of the controller 
- Push buttons
---- total of 10 push button are used in this project for the d-pad adn ABCD controls and the other two push button for the debugging of the ui 
- 0.96" OLED display
---- 0.96 inch oled screen is used in this project for the displaying of the debbuging menu and the joystick axis 

At this stage, the focus was only on verifying that:
- The OLED could display text
- Joysticks produced analog values
- Buttons could be detected reliably

No Bluetooth was involved yet.

---

## Phase 2 – OLED Interface
Once the hardware worked, an OLED user interface was designed:
- Two boxes representing left and right joysticks
- A moving dot inside each box showing joystick position
- Text showing controller name and Bluetooth status

This UI became a visual debugging tool, not just a display.

---

## Phase 3 – Debug Mode System
To test hardware without a computer, a debug system was added:
- Press **L3** to enter or exit debug mode
- Press **R3** to switch debug pages
- Pages for:
  - ABXY buttons
  - D-Pad buttons
  - Bumper buttons

Each button press is shown as a bar on the OLED.

---

## Phase 4 – Bluetooth Gamepad (BLE HID)
The ESP32 was then configured to act as a Bluetooth gamepad using BLE HID:
- Left stick mapped to X / Y axes
- Right stick mapped to RX / RY axes
- Buttons mapped to standard gamepad buttons
- D-Pad mapped as a HAT switch

At this stage, the controller appeared in Gamepad Tester and games.

---

## Phase 5 – Calibration & Analog Problems
Major issues appeared with joystick behavior:
- Center values were not at 2048
- Joystick snapped to corners
- Gamepad Tester showed values like -1 and 1
- Small movements were not detected

These problems were solved by:
- Auto-calibrating joystick center at boot
- Adding a deadzone
- Correctly mapping analog values to the HID range (-32767 to +32767)
- Avoiding normalized axis functions

---

## Phase 6 – Stability & Polishing
Final work focused on stability:
- Removing joystick vibration at rest
- Making OLED movement smooth and accurate
- Ensuring debug mode did not interfere with gameplay
- Keeping the system usable even without a PC

---

## Current State
The project is now a fully working prototype:
- Bluetooth gamepad works reliably
- OLED provides real-time feedback
- Debug mode allows hardware testing
- Joystick movement is smooth and centered

The project is intended as a learning-focused prototype and a base for future improvements.

