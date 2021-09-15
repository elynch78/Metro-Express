# CircuitPython

## Table of Contents
* [Table of Contents](#TableOfContents)
* [Blink Led](#Blink_Led_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [NextAssignmentGoesHere](#NextAssignment)
---

## Blink_Led_CircuitPython

### Description & Code
I had to make code in Mu that would make the Metro Express change colors. [This website](https://www.w3schools.com/colors/colors_picker.asp) was a great source because it had all the codes for lots of different colors. 


```
import board
import neopixel
import time

dot = neopixel.NeoPixel(board.NEOPIXEL, 1)

while True:
    dot.brightness = (.1)
    print("Make it red!")
    dot.fill((255, 51, 0))
    time.sleep(.5)
    print("Make it dark blue!")
    dot.fill((0, 0, 102))
    time.sleep(.5)
    print("Make it fuscia!")
    dot.fill((204, 0, 102))
    time.sleep(.5)
    print("Make it yellow!")
    dot.fill((255, 255, 0))
    time.sleep(.5)
```


### Evidence


### Wiring
Make an account with your google ID at [tinkercad.com](https://www.tinkercad.com/learn/circuits), and use "TinkerCad Circuits to make a wiring diagram."  It's really easy!  
Then post an image here.   [here's a quick tutorial for all markdown code, like making links](https://guides.github.com/features/mastering-markdown/)

### Reflection
The led was changing too fast in the beginning, so I made the time.sleep (.5) seconds long so you could see each color fully before it switched to the next. It was easy to add more colors once you got the first 2 running, you would just copy the above code format, and then change the color you have written and the numbers for the color calibration. 



## CircuitPython_Servo

### Description & Code

```
import board
import pwmio
from adafruit_motor import servo

# create a PWMOut object on Pin A2.
pwm = pwmio.PWMOut(board.A2, duty_cycle=2 ** 15, frequency=50)

# Create a servo object, my_servo.
my_servo = servo.Servo(pwm)

while True:
    for angle in range(0, 180, 5):  # 0 - 180 degrees, 5 degrees at a time.
        my_servo.angle = angle
        time.sleep(0.05)
    for angle in range(180, 0, -5): # 180 - 0 degrees, 5 degrees at a time.
        my_servo.angle = angle
        time.sleep(0.05)
```

### Evidence

![Servo](Images/gif-servo.gif)

### Wiring

### Reflection




## CircuitPython_LCD

### Description & Code

```python
Code goes here

```

### Evidence

### Wiring

### Reflection





## NextAssignment

### Description & Code

```python
Code goes here

```

### Evidence

### Wiring

### Reflection




















