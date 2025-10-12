
# Ph-UI!!!

<details>
	<summary><strong>Instructions for Students (Click to Expand)</strong></summary>
  
	**Submission Cleanup Reminder:**
	- This README.md contains extra instructional text for guidance.
	- Before submitting, remove all instructional text and example prompts from this file.
	- You may delete these sections or use the toggle/hide feature in VS Code to collapse them for a cleaner look.
	- Your final submission should be neat, focused on your own work, and easy to read for grading.
  
	This helps ensure your README.md is clear, professional, and uniquely yours!
</details>

---

## Lab 4 Deliverables

### Part 1 (Week 1)
**Done**

### Part 2 (Week 2)
**Submit the following for Part 2:**  
*️⃣ **E. Multi-Device Demo**
	- Code and video for your multi-input multi-output demo (e.g., chaining Qwiic buttons, servo, GPIO expander, etc.)
	- Reflection on interaction effects and chaining

*️⃣ **F. Final Documentation**
	- Photos/videos of your final prototype
	- Written summary: what it looks like, works like, acts like
	- Reflection on what you learned and next steps

---

## Lab Overview

**Collaborators: Feier Su, Weicong Hong, Jully Li, Sirui Wang**

## Part 1 Lab Preparation

**Down**

## Lab Overview

A) [Capacitive Sensing](#part-a)

B) [OLED screen](#part-b) 

C) [Paper Display](#part-c)

D) [Materiality](#part-d)

E) [Servo Control](#part-e)

F) [Record the interaction](#part-f)


## The Report (Part 1: A-D, Part 2: E-F)

### Quick Start: Python Environment Setup

**Done**

### Part A
### Capacitive Sensing, a.k.a. Human-Twizzler Interaction 
**Done**

### Part B
### More sensors
**Done**

### Part C
### Physical considerations for sensing

The sensors we wanna use are: **Light/Proximity/Gesture sensor (APDS-9960)**

**\*\*\*Draw 5 sketches of different ways you might use your sensor, and how the larger device needs to be shaped in order to make the sensor useful.\*\*\***

#### Rock Paper Scissors
![Rock Paper Scissors](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/rock%20paper%20scissors.png)

- **Sensors/Tech:** Webcam + Teachable Machine (gesture classifier), optional Qwiic Button for “Ready”.
- **Interaction:** Player faces the cam -> presses “Ready” (or waves) -> 3-2-1 countdown on OLED/MiniTFT -> both “throw” a hand sign; model classifies user’s gesture, Pi randomly (or rule-based) picks a move. Best-of-3 option.  
- **Output:** Big icon (✊ ✋ ✌️), win/lose/draw banner, score, playful beep/fanfare.
- **Form/Enclosure:** Small “arcade counter” with a start button and tilted screen; vinyl icons on the faceplate for clarity.
- **Questions to prototype:** Lighting robustness; latency from capture→classify→display; confusion between ✋ and ✌️; adding a fallback (button) if vision fails.
- **Why interesting:** Real-time vision + game loop makes sensing legible and fun.

#### Digital Plant
![Digigtal Plant](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/digital%20plant.png)
- **Sensors/Tech:** APDS-9960 proximity/light/gesture + optional distance sensor.
- **Interaction:** When a hand approaches too fast/close, the “plant” gets shy: leaves (paper/servo fins) droop and the OLED shows a bashful face; if you approach slowly or hold your hand at a kind distance, it “warms up” and perks back. Gentle left/right gestures can “pet” it.
- **Output:** Servo leaf droop/raise, OLED emotions, softly pulsing LEDs for “breathing.”
- **Form/Enclosure:** Paper/felt leaves on a stem; sensor hidden in the pot rim; OLED as a tiny “face tag.”
- **Questions to prototype:** Thresholds for “too close” vs. “just right”; mapping speed of approach to emotion; ambient-light compensation.
- **Why interesting:** Turns abstract proximity into an expressive, relatable behavior.

#### Memory Conductor
![Memory Conductor](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/memory%20conductor.png)
- **Sensors:** Capacitive + OLED + Servo
- **Concept:** Each conductive object (copper tape, Twizzler, metal trinket) stores a “memory.” When you touch it, the OLED displays a word, phrase, or animation that fades as you release — like recalling fleeting memories.
- **Interaction:** Touching = recalling → fading. Multiple pads = multiple memories.
- **Output:** Gentle servo motion (like a heartbeat) as memory fades away.
- **Display form:** A circular base with objects (rings, shells, candy) connected by hidden wires, glowing softly when activated.
- **Notes:** Memory is not stored in objects, but flows through them — just as electricity flows only when we make contact.

#### Gesture DJ
![Gesture DJ](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/gesture%20DJ.png)

- **Sensors:** Rotary encoder + Gesture + OLED
- **Concept:** Control light patterns or sound samples with hand gestures and rotation.
- **Interaction:** Rotate for tempo, gesture for mode (wave left = bass, right = treble).
- **Output:** OLED shows “mix levels” or dynamic shapes.
- **Form:** Flat “DJ board” with one dial and invisible gesture zone.

#### The light between us
![The light Between us](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/the%20light%20between%20us.png)
- **Sensors:** Distance + Gesture + OLED
- **Concept:** Measures how close two people stand. The OLED shows poetic text based on proximity (“Far / Still warm / Close / Too bright”).
- **Output:** Dynamic phrases or shifting brightness levels.
- **Art Message:** Emotional distance visualized as light.
- **Form:** Two small pods that face each other like conversation partners.
- **What does it mean when a machine senses intimacy? Does awareness of being measured change how we express closeness?** In “The Light Between Us,” technology does not replace touch – it reveals its gradients.

**\*\*\*What are some things these sketches raise as questions? What do you need to physically prototype to understand how to anwer those questions?\*\*\***

**Several concerns raised after we did the sketches:**
- How far away can gestures be reliably detected?
- Does the light affect accuracy?
- Does the orientation (horizontal vs. vertical) change detection sensitivity?
- How to give user feedback to show their gesture detected by the device?

**After physically prototyping the device, we could potentially test out:**
- Detection range with different hand speeds and distances.
- Mount it in different angles and to see if they affect sensitivity.
- Test the physical prototype under different environmental conditions. 
- Prototype different feedback we could potentially give to users (maybe LED blink, OLED text, etc.)

**\*\*\*Pick one of these designs to prototype.\*\*\***

Out of five ideas, we picked the Gesture DJ design to prototype. We imagine to prototype this concept by using a rotary encoder and gesture/distance sensors to let users mix music and visuals by turning knobs and waving their hands, blending physical controls with free-form motion. The combination of tangible and touchless input makes the sensing legible, while the sound and light feedback creates an expressive music experience that we can test for responsiveness, accuracy, and user enjoyment.

### Part D
### Physical considerations for displaying information and housing parts

**\*\*\*Sketch 5 designs for how you would physically position your display and any buttons or knobs needed to interact with it.\*\*\***
![1](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/sketch%20design%201.png)

![2](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/sketch%20design%202.png)

![3](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/sketch%20design%203.png)

![4](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/sketch%20design%204.png)

![5](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/sketch%20design%205.png)

**\*\*\*What are some things these sketches raise as questions? What do you need to physically prototype to understand how to anwer those questions?\*\*\***

**Proximity Sensor placement and range:**
- How close does the hand need to be to the distance sensor for reliable pitch control?
- Should the distance sensor face upward, sideways, or at an angle for the most natural interaction?
**Rotary encoder feel and precision:**
- How sensitive should the encoder be for controlling tempo—should it adjust smoothly or in discrete steps ( every 5 BPM)?
- Does the knob need feedback or visual cues (like an LED ring or OLED feedback)?

**Sound output and enclosure design:**
- How does the speaker placement in the device affect perceived sound direction and volume when the device is on a table?
- Is the form enclosing too much resonance (boxy sound), or does it allow clean output?

**Form and ergonomics:**
- Which form is most intuitive for users—flat DJ board, cylinder speaker, or compact disc-shaped base?
- How do users naturally gesture around the sensor—above, across, or in front?

**User feedback / display integration:**
- Does the user need an OLED display or light bulbs showing real-time BPM and pitch shift intensity?
- How visible should the display or light bulb be given the interaction distance?

**What Needs to Be Physically Prototyped**
- Sensor calibration: Test different distance sensor orientations (side vs. top) to find the most responsive zone.
- Test Rotary encoder mapping. Prototype the tempo mapping, for example, encoder rotation to BPM to determine comfortable control range.
- Use cardboard or foam to simulate each shape (box, turntable, cylinder, disc) and observe how users naturally interact with the sensors.

**\*\*\*Pick one of these display designs to integrate into your prototype.\*\*\***

**\*\*\*Explain the rationale for the design.\*\*\*** (e.g. Does it need to be a certain size or form or need to be able to be seen from a certain distance?)

We decided to go with the DJ turntables sketch (Sketch#1 and #3), because it is more intuitive for users to understand how to interact with the device (ex. users immediately associate the top rotary encoder with music tempo control). And also for aesthetic reasons, the circular “record” metaphor makes it more cohesive for a “Gesture DJ” concept, feeling both digital and analog.

The proximity sensor sits on the top surface with a clear interaction zone, reducing accidental triggers from people standing beside the unit. The rotary encoder is top-mounted (~3 cm above) and visually prominent for quick tempo changes. A side speaker grille projects sound cleanly toward the audience without blocking hand gestures on the top.

Build a cardboard prototype of your design.


**\*\*\*Document your rough prototype.\*\*\***
![Paper Prototype](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/8ebb1a31b06836380eb3bbe1ce9dec93ab5ec38b/Lab%204/lab%204%201%20/rough%20prototype.png)

# LAB PART 2

### Part 2

Following exploration and reflection from Part 1, complete the "looks like," "works like" and "acts like" prototypes for your design, reiterated below.



### Part E

#### Chaining Devices and Exploring Interaction Effects

For Part 2, you will design and build a fun interactive prototype using multiple inputs and outputs. This means chaining Qwiic and STEMMA QT devices (e.g., buttons, encoders, sensors, servos, displays) and/or combining with traditional breadboard prototyping (e.g., LEDs, buzzers, etc.).

**Your prototype should:**
- Combine at least two different types of input and output devices, inspired by your physical considerations from Part 1.
- Be playful, creative, and demonstrate multi-input/multi-output interaction.

**Document your system with:**
- Code for your multi-device demo
- Photos and/or video of the working prototype in action
- A simple interaction diagram or sketch showing how inputs and outputs are connected and interact
- Written reflection: What did you learn about multi-input/multi-output interaction? What was fun, surprising, or challenging?

**Questions to consider:**
- What new types of interaction become possible when you combine two or more sensors or actuators?
- How does the physical arrangement of devices (e.g., where the encoder or sensor is placed) change the user experience?
- What happens if you use one device to control or modulate another (e.g., encoder sets a threshold, sensor triggers an action)?
- How does the system feel if you swap which device is "primary" and which is "secondary"?

Try chaining different combinations and document what you discover!

See encoder_accel_servo_dashboard.py in the Lab 4 folder for an example of chaining together three devices.

**`Lab 4/encoder_accel_servo_dashboard.py`**

#### Using Multiple Qwiic Buttons: Changing I2C Address (Physically & Digitally)

If you want to use more than one Qwiic Button in your project, you must give each button a unique I2C address. There are two ways to do this:

##### 1. Physically: Soldering Address Jumpers

On the back of the Qwiic Button, you'll find four solder jumpers labeled A0, A1, A2, and A3. By bridging these with solder, you change the I2C address. Only one button on the chain can use the default address (0x6F).

**Address Table:**

| A3 | A2 | A1 | A0 | Address (hex) |
|----|----|----|----|---------------|
|  0 |  0 |  0 |  0 |    0x6F       |
|  0 |  0 |  0 |  1 |    0x6E       |
|  0 |  0 |  1 |  0 |    0x6D       |
|  0 |  0 |  1 |  1 |    0x6C       |
|  0 |  1 |  0 |  0 |    0x6B       |
|  0 |  1 |  0 |  1 |    0x6A       |
|  0 |  1 |  1 |  0 |    0x69       |
|  0 |  1 |  1 |  1 |    0x68       |
|  1 |  0 |  0 |  0 |    0x67       |
| ...| ...| ...| ... |     ...      |

For example, if you solder A0 closed (leave A1, A2, A3 open), the address becomes 0x6E.

**Soldering Tips:**
- Use a small amount of solder to bridge the pads for the jumper you want to close.
- Only one jumper needs to be closed for each address change (see table above).
- Power cycle the button after changing the jumper.

##### 2. Digitally: Using Software to Change Address

You can also change the address in software (temporarily or permanently) using the example script `qwiic_button_ex6_changeI2CAddress.py` in the Lab 4 folder. This is useful if you want to reassign addresses without soldering.

Run the script and follow the prompts:
```bash
python qwiic_button_ex6_changeI2CAddress.py
```
Enter the new address (e.g., 5B for 0x5B) when prompted. Power cycle the button after changing the address.

**Note:** The software method is less foolproof and you need to make sure to keep track of which button has which address!


##### Using Multiple Buttons in Code

After setting unique addresses, you can use multiple buttons in your script. See these example scripts in the Lab 4 folder:

- **`qwiic_1_button.py`**: Basic example for reading a single Qwiic Button (default address 0x6F). Run with:
	```bash
	python qwiic_1_button.py
	```

- **`qwiic_button_led_demo.py`**: Demonstrates using two Qwiic Buttons at different addresses (e.g., 0x6F and 0x6E) and controlling their LEDs. Button 1 toggles its own LED; Button 2 toggles both LEDs. Run with:
	```bash
	python qwiic_button_led_demo.py
	```

Here is a minimal code example for two buttons:
```python
import qwiic_button

# Default button (0x6F)
button1 = qwiic_button.QwiicButton()
# Button with A0 soldered (0x6E)
button2 = qwiic_button.QwiicButton(0x6E)

button1.begin()
button2.begin()

while True:
		if button1.is_button_pressed():
				print("Button 1 pressed!")
		if button2.is_button_pressed():
				print("Button 2 pressed!")
```

For more details, see the [Qwiic Button Hookup Guide](https://learn.sparkfun.com/tutorials/qwiic-button-hookup-guide/all#i2c-address).

---

### PCF8574 GPIO Expander: Add More Pins Over I²C

Sometimes your Pi’s header GPIO pins are already full (e.g., with a display or HAT). That’s where an I²C GPIO expander comes in handy.

We use the Adafruit PCF8574 I²C GPIO Expander, which gives you 8 extra digital pins over I²C. It’s a great way to prototype with LEDs, buttons, or other components on the breadboard without worrying about pin conflicts—similar to how Arduino users often expand their pinouts when prototyping physical interactions.

**Why is this useful?**
- You only need two wires (I²C: SDA + SCL) to unlock 8 extra GPIOs.
- It integrates smoothly with CircuitPython and Blinka.
- It allows a clean prototyping workflow when the Pi’s 40-pin header is already occupied by displays, HATs, or sensors.
- Makes breadboard setups feel more like an Arduino-style prototyping environment where it’s easy to wire up interaction elements.

**Demo Script:** `Lab 4/gpio_expander.py`

<p align="center">
    <img src="gpio_leds.gif" alt="GPIO Expander LED Demo" width="400"/>
</p>

We connected 8 LEDs (through 220 Ω resistors) to the expander and ran a little light show. The script cycles through three patterns:
- Chase (one LED at a time, left to right)
- Knight Rider (back-and-forth sweep)
- Disco (random blink chaos)

Every few runs, the script swaps to the next pattern automatically:
```bash
python gpio_expander.py
```

This is a playful way to visualize how the expander works, but the same technique applies if you wanted to prototype buttons, switches, or other interaction elements. It’s a lightweight, flexible addition to your prototyping toolkit.

---

### Servo Control with SparkFun Servo pHAT
For this lab, you will use the **SparkFun Servo pHAT** to control a micro servo (such as the Miuzei MS18 or similar 9g servo). The Servo pHAT stacks directly on top of the Adafruit Mini PiTFT (135×240) display without pin conflicts:
- The Mini PiTFT uses SPI (GPIO22, 23, 24, 25) for display and buttons ([SPI pinout](https://pinout.xyz/pinout/spi)).
- The Servo pHAT uses I²C (GPIO2 & 3) for the PCA9685 servo driver ([I2C pinout](https://pinout.xyz/pinout/i2c)).
- Since SPI and I²C are separate buses, you can use both boards together.
**⚡ Power:**
- Plug a USB-C cable into the Servo pHAT to provide enough current for the servos. The Pi itself should still be powered by its own USB-C supply. Do NOT power servos from the Pi’s 5V rail.

<p align="center">
    <img src="Servo_pHAT.gif" alt="Servo pHAT Demo" width="400"/>
</p>

**Basic Python Example:**
We provide a simple example script: `Lab 4/pi_servo_hat_test.py` (requires the `pi_servo_hat` Python package).
Run the example:
```
python pi_servo_hat_test.py
```
For more details and advanced usage, see the [official SparkFun Servo pHAT documentation](https://learn.sparkfun.com/tutorials/pi-servo-phat-v2-hookup-guide/all#resources-and-going-further).
A servo motor is a rotary actuator that allows for precise control of angular position. The position is set by the width of an electrical pulse (PWM). You can read [this Adafruit guide](https://learn.adafruit.com/adafruit-arduino-lesson-14-servo-motors/servo-motors) to learn more about how servos work.

---


### Part F

### Record

Document all the prototypes and iterations you have designed and worked on! Again, deliverables for this lab are writings, sketches, photos, and videos that show what your prototype:
* "Looks like": shows how the device should look, feel, sit, weigh, etc.
* "Works like": shows what the device can do
* "Acts like": shows how a person would interact with the device

