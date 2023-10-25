# Project 19：Servo Sweep

## 1. Introduction

Servo is a kind of motor that can rotate very precisely. It has been widely used in toy cars, RC helicopters, airplanes, robots, etc. In this project, we will use a Raspberry Pi Pico to control the rotation of the servo.

2. Components Required

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/b18fe281156b29c44796f72222718d58.jpeg" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/bbed91c0b45fcafc7e7163bfeabf68f9.png"  /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png"  /></td>
</tr>
<tr class="even">
<td>Raspberry Pi Pico*1</td>
<td>Raspberry Pi Pico Expansion Board*1</td>
<td>USB Cable*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/cd0bc424e9916881a1a903793821a042.png"  /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" /></td>
<td></td>
</tr>
<tr class="even">
<td>Servo*1</td>
<td><p>Jumper</p>
<p>Wires</p></td>
<td></td>
</tr>
</tbody>
</table>

3. Component Knowledge

**Servo:**

![](/media/99830768916233a9c5900ac399006c17.png)

The servo is a kind of position servo driver, which is mainly composed of housing, circuit board, coreless motor, gear and position detector. The working principle is that the receiver or microcontroller sends a signal to the servo, which has an internal reference circuit that generates a reference signal with a period of 20ms and a width of 1.5ms, and compares the DC bias voltage with the voltage of the potentiometer to output voltage difference. The IC on the circuit board determines the direction of rotation, and then drives the coreless motor to start rotation and transmits the power to the swing arm through the reduction gear, while the position detector sends back a signal to determine whether it has reached the positioning. It is suitable for those control systems that require constant change of angle and can be maintained.

When the motor rotates at a certain speed, the potentiometer is driven by the cascade reduction gear to rotate so that the voltage difference is 0 and the motor stops rotating. The angle range of general servo rotation is 0 to 180 degrees.

The pulse period for controlling the servo is 20ms, the pulse width is 0.5ms to 2.5ms, and the corresponding position is -90° to +90°. The following is an example of a 180 degree servo.

![](/media/708316fde05c62113a3024e0efb0c237.jpeg)

Servo motors have many specifications, but they all have three connecting wires, which are brown, red, and orange (different brands may have different colors). The brown is GND, the red is the positive power supply, and the orange is the signal line.

![](/media/3f5bc31305e64108bed3b3619d602891.jpeg)

## 4. Wiring Diagram
    
When supplying the servo, please note that the power supply voltage should be 3.3V-5V. Make sure there are no errors when connecting the servo to the power supply.

![](/media/64a80947d0cd45b50d4bd1d125509bbe.png)

## 5. Test Code

The code used in this project is saved in the file <span style="color: rgb(255, 76, 65);">KS3025 Keyestudio Raspberry Pi Pico Learning Kit Complete Edition\\3. Raspberry Pi System\\Python\_Tutorial\\2. Projects\\Project 19：Servo Sweep</span>. You can move the code anywhere. We save the code to the pi folder of the Raspberry Pi system. The path: <span style="color: rgb(255, 76, 65);">home/pi/2. Projects</span>.

![](/media/ae27830403a2f741aa9b725e5324c215.png)

Open“Thonny”, click“This computer”→“home”→“pi”→“2. Projects”→“Project 19：Servo Sweep”. Select“myservo\.py”，right-click and select“Upload to/”, waiting for the“myservo\.py”to be uploaded to the Raspberry Pi Pico. And double-click the“Project\_19\_Servo\_Sweep.py”.

![](/media/19500404b4592580e637218a8302e048.png)

![](/media/b73dea82f7b22b16b1db0449e8383d10.png)

```Python
from myservo import Servo
import time

servo=Servo(16)
servo.ServoAngle(0)
time.sleep_ms(1000)

try:
    while True:       
        for i in range(0, 180, 1):
            servo.ServoAngle(i)
            time.sleep_ms(15)
        for i in range(180, 0, -1):
            servo.ServoAngle(i)
            time.sleep_ms(15)        
except:
    servo.deinit()
```

## 6. Test Result
    
Ensure that the Raspberry Pi Pico is connected to the computer，click“![](/media/ec00367ea605788eab454cd176b94c7b.png)Stop/Restart backend”.

![](/media/0ac752d69e93df3280606c598df08b5a.png)

Click ![](/media/bb4d9305714a178069d277b20e0934b7.png)“Run current script”, the code starts executing, we will see that the servo will rotate from 0° to 180°, then reverse direction to rotate from 180° to 0°in a loop. 
Press“Ctrl+C”or click![](/media/ec00367ea605788eab454cd176b94c7b.png)“ Stop/Restart backend”to exit the program.

![](/media/fa2eefbf0876ed0fe8010741e05b29a2.png)

![](/media/c5250405a4290ecb2d758ff1097310c7.png)
