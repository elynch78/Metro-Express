# CircuitPython

## Table of Contents
* [Table of Contents](#TableOfContents)
* [Blink Led](#Blink_Led_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_Distance LED](#CircuitPython_Distance_LED)
* [Photointurrupter](#Photointurrupter)
* [new assignment](#new_assignment)
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

![Blink led](Images/gif-led.gif)

### Wiring

No wiring was needed, the Metro express had the neopixel.

### Reflection
The led was changing too fast in the beginning, so I made the time.sleep (.5) seconds long so you could see each color fully before it switched to the next. It was easy to add more colors once you got the first 2 running, you would just copy the above code format, and then change the color you have written and the numbers for the color calibration. 



## CircuitPython_Servo

### Description & Code
I had to code the servo to turn 180 degrees repeatedly. 
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


### Reflection

I didn't realize the different colors of the motor had designated spots in the Metro. The red wire goes to 5V, the blue wire goes to GND , and the yellow wire goes to A2. Once I had the wires in the right spots, the servo started turning right. 


## CircuitPython_Distance_LED

### Description & Code
The neopixel needs to change colors according to the distance measured by the servo. For values between 0 and 20 the color is red, values between 20 and 35 are blue, and for any value greater than 35 the color is green. 

```
import time
import board
import adafruit_hcsr04
import neopixel
import simpleio

sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D5, echo_pin=board.D6)
cm = 0

dot = neopixel.NeoPixel(board.NEOPIXEL, 1)
dot.brightness = (.1)

while True:
    try:
        cm = sonar.distance
        print((cm,))
        if cm < 20:
            print("red")
            r = simpleio.map_range(cm, 5, 20, 255, 0)
            g = 0
            b = 0
            
            time.sleep(0.1)

        if cm > 20 and cm < 35:
            print("blue")
            time.sleep(0.1)
            r = 0
            g = 0
            b = simpleio.map_range(cm, 0, 20, 255, 0)
        if cm > 35:
            print("green")
            time.sleep(0.1)
            r = 0
            g = simpleio.map_range(cm, 20, 30, 0, 255)
            b = 0
        dot.fill((r, g, b))

    except RuntimeError:
        print("Retrying!")
    time.sleep(0.1)

```

### Evidence

![servo](Images/gif-distance.gif)


### Reflection
This assignment was more complicated than previous ones for me. Using simpleio made the color changing work, and earlier I had been using dot.fill but that was required determining dot and simpleio just made sense and worked. simpleio.map_range(x, in_min, in_max, out_min, out_max) is what I used, but replaced x with cm, because that was what I am using to determine distance and that is what determines the color change. The values where the color changes goes in for in_max or min, and the neopixel number (255) goes in for out_min or max. [I downloaded this to my lib folder so I could use simpleio.](https://circuitpython.readthedocs.io/projects/simpleio/en/latest/_modules/simpleio.html#map_range)


## Photointurrupter

### Description & Code

I had to make the code tell when the photointerrupter was interrupted. The red light on the side of the t interrupter would go out when it was interrupted, and if it was red then I had it wired correctly. 


```
photo = False
state = False

max = 4
start = time.time()
while True:
    photo = interrupter.value
    if photo and not state:
            counter += 1
    state = photo

    remaining = max - time.time()

    if remaining <= 0:
        print("The number of interrupts is :", str(counter))
        max = time.time() + 4
        counter = 0

```

### Evidence

![Photointerrupter](Images/gif-photointerrupter.gif)


### Reflection

The code I grabbed was originally from user gventr04 on github. At first I had my wiring wrong because the OUT was put in an Analog Input instead of a Digital input. You CANNOT let the + or L outputs touch OUT or (-). You should connect the + and L outputs by either soldering or using tape or a metal clip to put them together. I had them soldered together which is the easiest in my opinion. 

## new

### Description & Code

write stuff


```
code

```

### Evidence

gif

### Wiring

### Reflection
























Make an account with your google ID at [tinkercad.com](https://www.tinkercad.com/learn/circuits), and use "TinkerCad Circuits to make a wiring diagram."  It's really easy!  
Then post an image here.   [here's a quick tutorial for all markdown code, like making links](https://guides.github.com/features/mastering-markdown/)


















