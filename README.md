# CircuitPython
This repository will actually serve as an aid to help you get started with your own template.  You should copy the raw form of this readme into your own, and use this template to write your own.  If you want to draw inspiration from other classmates, feel free to check [this directory of all students!](https://github.com/chssigma/Class_Accounts).
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Ultrasonic](#Ultrasonic)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_motor](#CircuitPython_motor)
* [onshape hanger](#onshape hanger)
* [onshape hanger](#onshape swingarm)
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
Wire up a 6v battery pack to this circuit with a motor. Write Python code to make the motor speed up and slow down, based on input from a potentiometer.

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





https://github.com/cflores90/engr3/assets/143544973/415094bf-beea-458f-959c-fa09aa172058




### Wiring

![277768794-6fb0ca37-a0aa-448e-a162-6938d98fd2b8](https://github.com/cflores90/engr3/assets/143544973/bebed8d0-90a5-46b1-82b7-f04ca6545a11)

Image credit goes to Raffi Chen
### Reflection
The hardest part of this assignment was getting the wiring right.The code was the easier part of this assignment. 




## onshape hanger

### Description & Code Snippets
In this assignment was to create a hanger in onshape. The reason we did this was os when we have the onshape sertification test we will be prepared. 

### part link
https://cvilleschools.onshape.com/documents/14b2ce2aac42fef6773cf68a/w/072cfd2284c6a5c82ebc9c3d/e/b55676c6b81bcc5e9b4ea96b?renderMode=0&uiState=653811dca78729041873fff3

### Evidence
![Part Studio 1](https://github.com/cflores90/engr3/assets/143544973/2bae1356-4a1f-4d73-9f36-d7d668c7f8eb)

### Reflection
This assignement took me a while to complete because this was the first time I was using onshape again in months.I forgot what a lot of tools could and where they were at after that everything else was pretty easy. 



## onshape swingarm 

### Description
For this assignment we had to follow the directions from the drawing given to us and we had use the variables that we had to use.And at the of the assignment you had to change the material of the part and make sure you had the correct mass.


### part link 
https://cvilleschools.onshape.com/documents/dc61b52afe52b7ba40b499f7/w/2660b688390bbf930c08e1fa/e/723d0baba4e010c838dec2d5?renderMode=0&uiState=6538164c4bc15d0b339a5611

### Evidence
![Part Studio 1 (1)](https://github.com/cflores90/engr3/assets/143544973/058a2144-395f-46fb-afc1-c0043449839f)


### Reflection 

For me this swing arm was one of the harder assignment I didn't know how to start the sketch.And I got some help from some of my classmates and then I started to understand how to read the drawings and the rest was not hard. 

## Rotary encoder and LCD

### Description 
For this assignment we had to get a LCD screen to display options such as Stop, caution, go. That could be selceted through the rotary encoder and have the neopixel react with it. 
### Wiring 
![image (1)](https://github.com/cflores90/engr3/assets/143544973/978ab41a-7316-4d32-8c8a-fbbf7e2c5f0e)


### Code

```python
# Rotary Encodare light thingksf;ja             # [lines 1-7] Import and set up neccesary libraries
import time
import rotaryio
import neopixel
import board
from lcd import LCD
from i2c_pcf8574_interface import I2CPCF8574Interface
from digitalio import DigitalInOut, Direction, Pull


encoder = rotaryio.IncrementalEncoder(board.D4, board.D3) # [lines 9-24] Start all Variables and define INs and OUTs
last_position = 0
btn = DigitalInOut(board.D2)
btn.direction = Direction.INPUT
btn.pull = Pull.UP
state = 0
Button = 1
led = neopixel.NeoPixel(board.NEOPIXEL, 1)
led.brightness = .3
i2c = board.I2C()
lcd = LCD(I2CPCF8574Interface(i2c, 0x3f), num_rows=2, num_cols=16)





while True:                #[lines 27-38] Set up varible for encoder, limit it to >0 and <3
    position = encoder.position
    if position != last_position:
        state = position % 3
        if state == 0:     #[lines 39-47] Print to LCD based on Encoder Var
            lcd.clear()
            lcd.set_cursor_pos(0, 0) # [39
            lcd.print("Don't stop")
        elif state == 1:
            lcd.clear()
            lcd.set_cursor_pos(0, 0)
            lcd.print("Speed up")
        elif state == 2:
            lcd.clear()
            lcd.set_cursor_pos(0, 0)
            lcd.print("Slam on brakes")
    if btn.value == 0 and Button == 1: #[lines 48-63] If the button is pressed make the Encoder Var match the lights.
        print("buttion")
        if state == 0:
            print('g')
            led[0] = (0, 255, 0)
        elif state == 1:
            print('y')
            led[0] = (255, 234, 0)
        elif state == 2:
            print('r')
            led[0] = (250, 0, 0)
        Button = 0       #[lines 64-68] Resets and delay
    if btn.value == 1:
        time.sleep(.1)
        Button = 1
    last_position = position
```


### Evidence


### Reflection 
  


## Stepper motor and limt switch 


### Description 
This assigment was to code a stepper motor to rotate until touched the limit switch and then roate back and when it tocuhed with the motor arm.

### Code

```
import asyncio
import board
import keypad
import time
import digitalio
from adafruit_motor import stepper


DELAY = 0.01  
STEPS = 100
coils = (
    digitalio.DigitalInOut(board.D9),   # A1
    digitalio.DigitalInOut(board.D10),  # A2
    digitalio.DigitalInOut(board.D11),  # B1
    digitalio.DigitalInOut(board.D12),  # B2
)


for coil in coils:
    coil.direction = digitalio.Direction.OUTPUT
motor = stepper.StepperMotor(coils[0], coils[1], coils[2], coils[3], microsteps=None)

async def catch_pin_transitions(pin):

    with keypad.Keys((pin,), value_when_pressed=False) as keys:
        while True:
            event = keys.events.get()
            if event:
                if event.pressed:
                    print("Limit Switch was pressed.")
                    for step in range(STEPS):
                        motor.onestep(direction=stepper.BACKWARD, style=stepper.DOUBLE)
                        time.sleep(DELAY)
                elif event.released:
                    print("Limit Switch was released.")
            await asyncio.sleep(0)

async def run_motor():
    while(True):
        motor.onestep(style=stepper.DOUBLE)
        time.sleep(DELAY)
        await asyncio.sleep(0)

async def main():
    while(True):
        interrupt_task = asyncio.create_task(catch_pin_transitions(board.D2))
        motor_task = asyncio.create_task(run_motor())
        await asyncio.gather(interrupt_task, motor_task)

asyncio.run(main())
```

### Evidence

https://github.com/cflores90/engr3/assets/143544973/bef0e231-7bab-40a2-a50e-6e07453b49b8



### Wirring



![motor and switches](https://github.com/cflores90/engr3/assets/143544973/690fc8ad-d293-41bd-bfe7-bf903e0702a4)

### Reflection 
Thsi assignment was a bit diffcult for me since i've never used a stepper motor ever and the instructions on canvas were a bit hard to understand for me.But the main I struggled with was getting the motor to move back and forth when it clicked the limit switch. 


## Single part 

### Description 
The goal of this assignment was to create a V-Block based on the given drawings. Then one would modify the part based on the instructions, to produce a part with the desired ms
### Evidence
<img width="1470" alt="Screenshot 2024-03-27 at 10 01 42 PM" src="https://github.com/cflores90/engr3/assets/143544973/e71ebcb5-fdd5-4ff3-927c-8ae895cdc3a5">

### Part Link
https://cvilleschools.onshape.com/documents/8b5a0c398acd568c60daf4dd/w/c5d04eea9fe9b6e0758b2aac/e/6473427d3c7ad8cfb3e46b23?renderMode=0&uiState=6604d058e156161559daf46e
### Reflection 
This onshape part was not hard at all and was a great way to get back into using onshape.The only problem that I had was gettig the angle right but with the help of my classmates I got everything correct and how it was supposed to be. 


## Multi Part

### Description 
For this assignment we had to create mic stand by creating multiple parts in one part studio. 
### Evidence 
![image](https://github.com/cflores90/engr3/assets/143544973/137103cc-689d-49b8-9bd6-8d78d700b829)

### Part Link 

### Reflection 


## Locking Pilers

### Description 
The goal of this assignment to assemble a locking piler assembly in onshape to match the drawings we got. 
### Evidence
<img width="1022" alt="Screenshot 2024-03-27 at 10 46 45 PM" src="https://github.com/cflores90/engr3/assets/143544973/569c7c41-14cb-4a60-9400-cd472ec60db9">

### part Link 
https://cvilleschools.onshape.com/documents/88c76c6edc0e60a6c0d17511/w/6d3dd856036b4a2daa965a6f/e/0ec9514862a6dd307b75e2e6?renderMode=0&uiState=6604d9cfdc68b67a3d548e67
### Reflection
This assignment I struggled with the mates and conncecting all the parts togther but with some help I got everything figured out.And made everything work how it was intend to work. 

## Multi part Cylinder

### Description 
The goal for this assignment was to a create a cylinder assembly using different parts in one studio.And using the drawings to guide us. 
The goal of this assignment to create a cylinder assembly using multiple parts within one studio. This was important for practicing how to make multiple parts from their shared dimensions.
### Evidence
<img width="995" alt="Screenshot 2024-03-27 at 11 00 20 PM" src="https://github.com/cflores90/engr3/assets/143544973/97de7184-b647-495d-8be3-748c8e225365">

### Part link 
https://cvilleschools.onshape.com/documents/5f334e560a190e0c223d311d/w/3b39bbc061217ebbc34836bc/e/8a747a6da7a31fa629eaf9b6?renderMode=0&uiState=6604de0157042e6d2b0443fe
### Reflection 
  
