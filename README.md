/////;;;;;# CircuitPython
This repository will actually serve as an aid to help you get started with your own template.  You should copy the raw form of this readme into your own, and use this template to write your own.  If you want to draw inspiration from other classmates, feel free to check [this directory of all students!](https://github.com/chssigma/Class_Accounts).
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Ultrasonic](#Ultrasonic)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_motor](#CircuitPython_motor)
* [NextAssignmentGoesHere](#NextAssignment)
---

## Ultrasonic 

### Description & Code Snippets
the purpose of this assignment was to make the neo pixel of the metro express board turn differnt colors.It would change differnt colors due to the disatce the ultrasonic distance sensor would read.

```python
# SPDX-FileCopyrightText: 2021 ladyada for Adafruit Industries
# SPDX-License-Identifier: MIT

import time
import board
import adafruit_hcsr04
import neopixel

NUMPIXELS = 1  # Update this to match the number of LEDs.
SPEED = 0.05  # Increase to slow down the rainbow. Decrease to speed it up.
BRIGHTNESS = 1.0  # A number between 0.0 and 1.0, where 0.0 is off, and 1.0 is max.
PIN = board.NEOPIXEL
pixels = neopixel.NeoPixel(PIN, NUMPIXELS, brightness=BRIGHTNESS, auto_write=False)
sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D5, echo_pin=board.D6)

while True:
    try:
        print((sonar.distance,))
        if sonar.distance < 5:
            for pixel in range(len(pixels)):  # pylint: disable=consider-using-enumerate
                pixels[pixel] = (255, 0,0)
                pixels.show()
        if sonar.distance > 5 and sonar.distance < 20:
            for pixel in range(len(pixels)):  # pylint: disable=consider-using-enumerate
                pixels[pixel] = (255-(sonar.distance - 5 / 15 * 255), 0, (sonar.distance - 5 / 15 * 255))
                pixels.show()
             
        if sonar.distance > 20 and sonar.distance < 35:
            for pixel in range(len(pixels)):  # pylint: disable=consider-using-enumerate
                pixels[pixel] = ( 0, (sonar.distance - 5 / 15 * 255), 255-(sonar.distance - 5 / 15 * 255))
                pixels.show()
        if sonar.distance > 35:
            for pixel in range(len(pixels)):  # pylint: disable=consider-using-enumerate
                pixels[pixel] = ( 0, 255, 0)
                pixels.show()   
    except RuntimeError:
        print("Retrying!")
    time.sleep(0.1)

```

**Lastly, please end this section with a link to your code or file.**  

### Evidence




https://github.com/cflores90/engr3/assets/143544973/5bb3b99b-b46a-4f9e-8c2e-a2fa328c7b93




### Wiring
![134725601-72db0fcb-0d50-486c-aff5-9e0ec1772057](https://github.com/cflores90/engr3/assets/143544973/24c6ff78-af17-4a81-b45e-1a1eff04cf90)


### Reflection
The easiest part of this assignment was the wirring becasuse all you have to wire up is ultrasonic distance sensor and that isn't hard.The code it was a bit easy only problem had is that I was having problems with my boards Neo pixel not working.But overall this assignemnt was fun. 


## CircuitPython_Servo

### Description & Code Snippets
For this assignment all we had to do was wire up a servo and make the servo turn left and turn right with cappative touch wires.And create the code for it to work. 

```python
# SPDX-FileCopyrightText: 2018 Kattni Rembor for Adafruit Industries
#
# SPDX-License-Identifier: MIT

"""CircuitPython Essentials Capacitive Touch on two pins example. Does not work on Trinket M0!"""
import time
import board
import touchio
import pwmio
from adafruit_motor import servo

# create a PWMOut object on Pin A2.
pwm = pwmio.PWMOut(board.A2, duty_cycle=2 ** 15, frequency=50)

# Create a servo object, my_servo.
my_servo = servo.ContinuousServo(pwm)

touch_A4 = touchio.TouchIn(board.A4)  # Not a touch pin on Trinket M0!
touch_A5 = touchio.TouchIn(board.A5)  # Not a touch pin on Trinket M0!

while True:
    my_servo.throttle = 0.0
    while touch_A4.value:
        my_servo.throttle = 1.0
        time.sleep(.5)
    while touch_A5.value:
        my_servo.throttle = -1.0
        time.sleep(.5)


```

**Lastly, please end this section with a link to your code or file.**  


### Evidence





https://github.com/cflores90/engr3/assets/143544973/ea6e1f96-3e5b-460f-9d82-f9f2e96ca9c6






### Wiring
![133495354-0ef9219e-2658-4c7b-bef3-01cff6986baf](https://github.com/cflores90/engr3/assets/143544973/25b286fe-0648-46f8-bac4-1ce46578eee7)


### Reflection
This assignment wasn't diffuclt I found most of the code online and combinded two pieces of code that i found togther to make this assigment work efficientl. 


## CircuitPython_motor

### Description & Code Snippets
Write a couple sentences here, describing this assignment, and make sure that you hit these two points:
* What was the goal of the assignment?
* How did you accomplish that goal?
  How you accomplished the goal is NOT a reflection, it is you telling the reader how to do this assignment, in broad strokes.

  Your description is the right place to draw the reader's attention to any important chunks of code. Here's how you make code look like code:

```python
Code goes here

```

**Lastly, please end this section with a link to your code or file.**  


### Evidence
Pictures / Gifs of your finished work should go here.  You need to communicate what your thing does.
For making a GIF, I recommend [ezgif.com](https://www.ezgif.com) Remember you can insert pictures using Markdown or HTML to insert an image.


And here is how you should give image credit to someone if you use their work:

Image credit goes to [Rick A](https://www.youtube.com/watch?v=dQw4w9WgXcQ&scrlybrkr=8931d0bc)



### Wiring
[tinkercad.com](https://www.tinkercad.com/learn/circuits).  If you can't find the particular part you need, get creative, and just drop a note into the circuit diagram, explaining.
For example, I use an Arduino Uno to represent my Circuitpython device but write a note saying which board I'm actually using.
Then post an image here.   [Here's a quick tutorial for all markdown code, like making links](https://guides.github.com/features/mastering-markdown/)


### Reflection
Don't just tell the reader what went wrong or was challenging!  Describe how you figured it out, share the things that helped you succeed (tutorials, other people's repos, etc.), and then share what you learned from that experience.  **Your underlying goal for the reflection, is to concisely pass on the RIGHT knowledge that will help the reader recreate this assignment better or more easily.  Pass on your wisdom!**





## NextAssignment

### Description & Code Snippets
Write a couple sentences here, describing this assignment, and make sure that you hit these two points:
* What was the goal of the assignment?
* How did you accomplish that goal?
  How you accomplished the goal is NOT a reflection, it is you telling the reader how to do this assignment, in broad strokes.

  Your description is the right place to draw the reader's attention to any important chunks of code. Here's how you make code look like code:

```python
import board
import analogio

motor=analogio.AnalogOut(board.A0)
pot=analogio.AnalogIn(board.A1)
while True:
    speed=pot.value
    motor.value=speed

```

**Lastly, please end this section with a link to your code or file.**  

### Evidence

### Wiring
[tinkercad.com](https://www.tinkercad.com/learn/circuits).  If you can't find the particular part you need, get creative, and just drop a note into the circuit diagram, explaining.
For example, I use an Arduino Uno to represent my Circuitpython device but write a note saying which board I'm actually using.
Then post an image here.   [Here's a quick tutorial for all markdown code, like making links](https://guides.github.com/features/mastering-markdown/)
### Reflection
Don't just tell the reader what went wrong or was challenging!  Describe how you figured it out, share the things that helped you succeed (tutorials, other people's repos, etc.), and then share what you learned from that experience.  **Your underlying goal for the reflection, is to concisely pass on the RIGHT knowledge that will help the reader recreate this assignment better or more easily.  Pass on your wisdom!**

