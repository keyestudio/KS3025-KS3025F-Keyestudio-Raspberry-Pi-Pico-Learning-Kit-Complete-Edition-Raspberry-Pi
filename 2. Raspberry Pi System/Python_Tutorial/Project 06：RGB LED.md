# Project 06: RGB LED

**1. Introduction**

![](/media/94bdff69e438989d8e0934e57f2e5c00.png)

RGB LEDS are made up of three colors (red, green, and blue) , which can
emit different colors by mixing these three basic colors. In this
project, we will introduce the RGB LED and show you how to use the
Raspberry Pi Pico to control the RGB LED. Even though RGB LED is very
basic, it is also a great way to learn the fundamentals of electronics
and coding.

2.  **Components Required**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/b18fe281156b29c44796f72222718d58.jpeg" style="width:2.37431in;height:0.94514in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/bbed91c0b45fcafc7e7163bfeabf68f9.png" style="width:1.67014in;height:1.28472in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/f1a86fc81ab4b043263ce7e01e14d470.png" style="width:0.23056in;height:1.27847in" /></td>
<td></td>
</tr>
<tr class="even">
<td>Raspberry Pi Pico*1</td>
<td>Raspberry Pi Pico Expansion Board*1</td>
<td>RGB LED*1</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:1.22639in;height:0.49236in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.50347in;height:1.23333in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.66736in;height:0.64097in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>220ΩResistor*3</td>
<td>Breadboard*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

**. Component Knowledge**

The monitors mostly adopt the RGB color standard, and all the colors on
the computer screen are composed of the three colors of red, green and
blue mixed in different proportions.

![](/media/8bf1339719a922f2fbc1e01a4347b4ab.png)

This RGB LED has 4 pins and a common cathode. To change its brightness,
we can use the PWM of the Raspberry Pi Pico pins, which can give
different duty cycle signals to the RGB LED to produce different colors.

If we use three 10-bit PWM to control the RGBLED, theoretically we can
create 210\*210\*210= 1,073,741,824(1 billion) colors through different
combinations.

4.  **Circuit Diagram and Wiring Diagram**

![](/media/f6950bc8498e6139cbb67db84cdd5a9a.png)

![](/media/fdab8c2fd2dfdd1670c09962e7b458ce.png)

**Note:**

RGB LED longest pin (common cathode) connected to GND.

![](/media/1584356c63bf99934ae0810ee02dced3.png)

How to identify the 220Ω 5-band resistor

![](/media/55c0199544e9819328f6d5778f10d7d0.png)

**Test Code**

The code used in this project is saved in the file KS3025 Keyestudio
Raspberry Pi Pico Learning Kit Complete Edition\\3.Raspberry Pi
System\\Python\_Tutorial\\2. Projects\\Project 06：RGB LED. You can move
the code to anywhere.For example, we can save the pi folder of the
Raspberry Pi System, the route is home/pi/2. Projects

![](/media/ae27830403a2f741aa9b725e5324c215.png)

Open“Thonny, click“This computer”→“home”→“pi”→“2. Projects”→“Project
06：RGB LED”and double left-click the“Project\_06\_RGB\_LED.py”.

![](/media/fa2c2f91ec4700ce6c73e4acb045df45.png)

<table>
<tbody>
<tr class="odd">
<td><p># import Pin, PWM and Random function modules.</p>
<p>from machine import Pin, PWM</p>
<p>from random import randint</p>
<p>import time</p>
<p>#configure ouput mode of GP18, GP17 and GP16 as PWM output and PWM frequency as 10000Hz.</p>
<p>pins = [18, 17, 16]</p>
<p>freq_num = 10000</p>
<p>pwm0 = PWM(Pin(pins[0])) #set PWM</p>
<p>pwm1 = PWM(Pin(pins[1]))</p>
<p>pwm2 = PWM(Pin(pins[2]))</p>
<p>pwm0.freq(freq_num)</p>
<p>pwm1.freq(freq_num)</p>
<p>pwm2.freq(freq_num)</p>
<p>#define a function to set the color of RGBLED.</p>
<p>def setColor(r, g, b):</p>
<p>pwm0.duty_u16(65535 - r)</p>
<p>pwm1.duty_u16(65535 - g)</p>
<p>pwm2.duty_u16(65535 - b)</p>
<p>try:</p>
<p>while True:</p>
<p>red = randint(0, 65535)</p>
<p>green = randint(0, 65535)</p>
<p>blue = randint(0, 65535)</p>
<p>setColor(red, green, blue)</p>
<p>time.sleep_ms(200)</p>
<p>except:</p>
<p>pwm0.deinit()</p>
<p>pwm1.deinit()</p>
<p>pwm2.deinit()</p></td>
</tr>
</tbody>
</table>

**Test Result**

Ensure that the Raspberry Pi Pico is connected to the computer, click
![](/media/ec00367ea605788eab454cd176b94c7b.png)“Stop/Restart backend”.

![](/media/c338d727e51749fcf4e331cc729207ae.png)

Click “![](/media/bb4d9305714a178069d277b20e0934b7.png)Run current script”, the code starts
executing, we will see that RGB LED starts showing random colors.
Press“Ctrl+C”or click“![](/media/ec00367ea605788eab454cd176b94c7b.png)Stop/Restart backend”to
exit the program.

![](/media/b6f35a993624aa56b058ca411d43e096.png)
