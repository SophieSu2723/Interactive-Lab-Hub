
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

**Collaborators: Jully Li (hl2568), Weicong Hong (wh528), Feier Su (fs495), Sirui Wang (sw2449)**

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
### Part E
**Feedback from peers on Physical UI & general experiences with Gesture DJ’s rough prototype:**

**- Participant #1:** “At first, it was unclear which part of the device controlled the music’s pitch, song switch, and low-pass filter, but after you explained the setup, it became intuitive to use.”

**- Participant #2:**  “Interesting DJ board! Would love to see more features coming up and how this could be more robust in controlling the music.”

**- Participant #3:** “Love to see if we could control the song of our choice in the future.”

Based on the feedback we received, we decided to add labels to the device to guide users in how to interact with it. However, due to time constraints, we chose to continue focusing on the proximity sensor and rotary encoder for this week. We also expanded the song bank to offer a wider selection of music.

![Final prototype](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/bcc0d5081aec5250fc4cea137a0674482a903d04/Lab%204/lab%204%201/final%20physical%20ui.jpg)

**Documentation for the system**
- Code for our multi-device demo:

Source code: https://github.com/siruiii/Interactive-Lab-Hub/blob/Fall2025/Lab%204/dj.py

- Photos and/or video of the working prototype in action:

Working prototype photo:![Working Prototype](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/bcc0d5081aec5250fc4cea137a0674482a903d04/Lab%204/lab%204%201/physical%20UI.jpg)

Working prototype video(before implementing physical UI):https://www.youtube.com/watch?v=9f7XT1SAkN0


- A simple interaction diagram showing how inputs and outputs are connected and interact:

Diagram: ![Diagram](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/bcc0d5081aec5250fc4cea137a0674482a903d04/Lab%204/lab%204%201/interaction%20diagram.png)

- Written reflection:

What we learned about multi-input/multi-output interaction is that coordinating multiple sensors and outputs requires careful setting-up and debugging, each component (like the rotary encoder and proximity sensor we used in this DJ device). It was surprising how sensitive the hardware setup could be. Connections on the breadboard were easy to come loose, causing unexpected behavior that looked like code errors but were actually wiring issues.

What was fun was seeing how different inputs could work together to create a more dynamic and expressive experience. For example, controlling the music’s pitch and low-pass filter (audio filter that lets the low frequencies pass through, while reducing or cutting out the high frequencies) through rotation and the hand’s distance to the proximity sensor of the rotary encoder felt very rewarding.

The most challenging part was debugging interactions that depended on multiple sensors updating simultaneously, especially figuring out which input was causing unexpected errors and changes in output.



**Questions to consider:**

- **What new types of interaction become possible when you combine two or more sensors or actuators?**
  - Combining sensors like the proximity detector and rotary encoder allows both tactile precision and expressive motion control in a single experience. Users can modulate one variable through turning a knob while simultaneously influencing another through touchless gestures, creating multi-layered input. This combination enables more fluid, musical, or performative interactions that go beyond simple button presses.

- **How does the physical arrangement of devices (e.g., where the encoder or sensor is placed) change the user experience?**
	- The placement of sensors and controls directly influences how intuitive and comfortable they feel. For example, positioning a sensor above the encoder encourages hand hovering and gesture-like input, while placing it on the side might suggest triggering or navigation. This setup shapes user posture and rhythm, promoting either precise, anchored control or dynamic, spatial interaction. 

- **What happens if you use one device to control or modulate another (e.g., encoder sets a threshold, sensor triggers an action)?**
	- Hierarchical linking of sensors creates more complex control logic and emergent behaviors. For example, configuring the encoder to adjust the proximity sensor’s sensitivity threshold allows users to modify how reactive or “emotional” the system appears. This integration enhances adaptability and imparts a sense of personality, as if the system learns or shifts mood in response to user interactions.

- **How does the system feel if you swap which device is "primary" and which is "secondary"?**
	- If the rotary encoder becomes primary, the experience feels precise and mechanical, similar to a mixing desk. But if proximity takes the lead, the interaction would feel softer and more embodied, like conducting or shaping sound in mid-air. Swapping the hierarchy fundamentally changes the perceived intent from tool operation to creative expression.

**Preparing for final prototype:**

Physical UI:

![3D Model Source](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/bcc0d5081aec5250fc4cea137a0674482a903d04/Lab%204/lab%204%201/3D%20model%20Source.png)

3D Model Source: Bambu Studio - Rotary Encoder Knobs by ershared

![phyical UI](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/bcc0d5081aec5250fc4cea137a0674482a903d04/Lab%204/lab%204%201/physical%20UI.jpg)

![Physical UI2](https://github.com/SophieSu2723/Interactive-Lab-Hub/blob/bcc0d5081aec5250fc4cea137a0674482a903d04/Lab%204/lab%204%201/final%20physical%20ui.jpg)

### Part F

### Record

Document all the prototypes and iterations you have designed and worked on! Again, deliverables for this lab are writings, sketches, photos, and videos that show what your prototype:
* "Looks like": shows how the device should look, feel, sit, weigh, etc.
* "Works like": shows what the device can do
* "Acts like": shows how a person would interact with the device

Video: https://youtu.be/KbzEK73YYX4?si=bayvnmF0tJXfD38B

### Contribution
Sirui Wang: technical implementation, Raspberry Pi setup, device testing

Jully Li: storyboarding, physical UI, help with the device set-up, final report write-up.

Feier Su: storyboarding, final report writeup, video shooting, interaction diagram

Weicong Hong: physical UI, 3d printing, final report writeup, video shooting


