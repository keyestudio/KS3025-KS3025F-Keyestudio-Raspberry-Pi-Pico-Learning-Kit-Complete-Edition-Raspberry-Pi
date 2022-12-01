# Project 22 : Dimming Light

1.  **Introduction**

A potentiometer is a three-terminal resistor with a sliding or rotating
contact that forms an adjustable voltage divider. It works by varying
the position of a sliding contact across a uniform resistance. In a
potentiometer, the entire input voltage is applied across the whole
length of the resistor, and the output voltage is the voltage drop
between the fixed and sliding contact.

In this project, we are going to learn how to use Raspberry Pi Pico to
read the values of the potentiometer, and make a dimming lamp with LEDs.

2.  **Components Required**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/b1265f71184b5d144248ea3e847a18c9.jpeg" style="width:1.75486in;height:0.69861in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/bbed91c0b45fcafc7e7163bfeabf68f9.png" style="width:1.67014in;height:1.28472in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/03ab81e8b4f09287d2781ef0fd297f85.png" style="width:0.70556in;height:1.08125in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/ef77f5a64c382157fc2dea21ec373fef.png" style="width:0.29514in;height:1.25903in" /></td>
</tr>
<tr class="even">
<td>Raspberry Pi Pico*1</td>
<td>Raspberry Pi Pico Expansion Board*1</td>
<td>Potentiometer*1</td>
<td>Red LED*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.59028in;height:1.44583in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/845d05a6108b1662b828610ba9dcb788.png" style="width:0.25833in;height:1.13681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:0.77222in;height:0.77986in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>Breadboard*1</td>
<td>220ΩResistor*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**
    
    ![](/media/03ab81e8b4f09287d2781ef0fd297f85.png)

**Adjustable potentiometer:** It is a kind of resistor and an analog
electronic component, which has two states of 0 and 1(high level and low
level). The analog quantity is different, its data state presents a
linear state such as 1 \~ 1024.

4.  **Read the Potentiometer Value**
    
    We connect the adjustable potentiometer to the analog IO of the
    Raspberry Pi Pico to read its value and voltage value . Please refer
    to the following wiring diagram for wiring.

![](/media/b8ee6320bce8729a4309857f257d30ec.png)

![](/media/cb970a340d830569e9ac4462a1318e44.png)

The code used in this project is saved in the file KS3025 Keyestudio
Raspberry Pi Pico Learning Kit Complete Edition\\3. Raspberry Pi
System\\Python\_Tutorial\\2. Projects\\Project 22：Dimming Light

You can move the code anywhere. We save the code to the pi folder of the
Raspberry Pi system. The path:home/pi/2. Projects

![](/media/ae27830403a2f741aa9b725e5324c215.png)

Open“Thonny, click““This computer”→“home”→“pi”→“2. Projects”→“Project
22：Dimming Light”. And double-click
the“Project\_22.1\_Read\_Potentiometer\_Analog\_Value.py”.

![](/media/a15ac026d4ffddcfa4092a73ec94db62.png)

<table>
<tbody>
<tr class="odd">
<td><p>from machine import ADC, Pin</p>
<p>import time</p>
<p># Initialize the potentiometer to pin 26 (ADC function)</p>
<p>adc = ADC(26)</p>
<p># Print the current adc value of the potentiometer cyclically</p>
<p># Print the current voltage value of the potentiometer cyclically</p>
<p>try:</p>
<p>while True:</p>
<p>adcValue = adc.read_u16() # read the ADC value of potentiometer</p>
<p>voltage = adcValue / 65535.0 * 3.3</p>
<p>print("ADC Value:", adcValue, "Voltage:", voltage, "V")</p>
<p>time.sleep(0.1)</p>
<p>except:</p>
<p>pass</p></td>
</tr>
</tbody>
</table>

Ensure that the Raspberry Pi Pico is connected to the
computer，click“![](/media/ec00367ea605788eab454cd176b94c7b.png)Stop/Restart backend”.

![](/media/24576fd319aa242673e032410c3a4274.png)

Click“![](/media/bb4d9305714a178069d277b20e0934b7.png)Run current script”, the code starts
executing, we will see that the "Shell" window of Thonny IDE will print
the ADC value and voltage value of the potentiomete, turn the
potentiometer handle, the ADC value and voltage value will change.
Click“![](/media/ec00367ea605788eab454cd176b94c7b.png)Stop/Restart backend”to exit the program.

![](/media/e48bc2d7a4b4c78f615a38b15b4028c2.png)

![](/media/969b9de3cf505f05d6a9361286cef9c9.png)

5.  **Circuit Diagram and Wiring Diagram**

In the last step, we read the value of the potentiometer, and now we
need to convert the value of the potentiometer into the brightness of
the LED to make a lamp that can adjust the brightness. The wiring
diagram is as follows:

![](/media/66f721b77035d40556c873e0c4577b4a.png)

![](/media/93b03f3cdc8af506d9035b748839ac33.png)

6.  **Test Result**

The code used in this project is saved in the file KS3025 Keyestudio
Raspberry Pi Pico Learning Kit Complete Edition\\3. Raspberry Pi
System\\Python\_Tutorial\\2. Projects\\Project 22：Dimming Light.

You can move the code anywhere. We save the code to the pi folder of the
Raspberry Pi system. The path:home/pi/2. Projects

![](/media/ae27830403a2f741aa9b725e5324c215.png)

Open“Thonny”, click“This computer”→“home”→“pi”→“2. Projects”→“Project
22：Dimming Light”. And double left-click
the“Project\_22.2\_Dimming\_Light.py”.

![](/media/5721f7690258b3da3e3ca26f9b2a16af.png)

<table>
<tbody>
<tr class="odd">
<td><p>from machine import ADC, Pin, PWM</p>
<p>import time</p>
<p>adc = ADC(26) # Initialize the potentiometer to pin 26 (ADC function)</p>
<p>pwm = PWM(Pin(16)) # Initialize the led's PWM to pin 16</p>
<p>pwm.freq(1000) # Define the PWM frequency as 1000</p>
<p>try:</p>
<p>while True:</p>
<p>adcValue = adc.read_u16() # read the ADC value of potentiometer</p>
<p>pwm.duty_u16(adcValue) #map it to the duty cycle of PWM to control led brightness</p>
<p>time.sleep(0.1)</p>
<p>except:</p>
<p>pwm.deinit()</p></td>
</tr>
</tbody>
</table>

7.  **Test Result**
    
    Ensure that the Raspberry Pi Pico is connected to the
    computer，click“![](/media/ec00367ea605788eab454cd176b94c7b.png)Stop/Restart backend”.

![](/media/d335fc1670c6c486420472d4435092e8.png)

Click ![](/media/bb4d9305714a178069d277b20e0934b7.png)“Run current script”, the code starts
executing, we will see that turn the potentiometer handle and the
brightness of the LED will change accordingly.
Click“![](/media/ec00367ea605788eab454cd176b94c7b.png)Stop/Restart backend”to exit the program.

![](/media/56349a69c557c5302c5d0721bfac0048.png)

![](/media/eca30dead3f4923afa0dcb0306db2319.jpeg)
