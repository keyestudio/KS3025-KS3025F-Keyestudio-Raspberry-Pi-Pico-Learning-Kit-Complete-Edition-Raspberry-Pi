# Project 12：Active Buzzer

1.  **Introduction**

Active buzzer is a sound making element, which is widely used on
computers, printers, alarms, electronic toys, telephones, timers, etc.
It has an inner vibration source. In this project, we will use a
Raspberry Pi Pico to control the active buzzer to buzz.

2.  **Components Required**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/b18fe281156b29c44796f72222718d58.jpeg" style="width:2.37431in;height:0.94514in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/bbed91c0b45fcafc7e7163bfeabf68f9.png" style="width:1.67014in;height:1.28472in" /></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Raspberry Pi Pico*1</td>
<td>Raspberry Pi Pico Expansion Board*1</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/4b4f653a76a82a3b413855493cc58fba.png" style="width:0.86111in;height:0.70069in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.69375in;height:1.70139in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.77778in;height:0.74792in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>Active Buzzer*1</td>
<td>Breadboard*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

**3. Component Knowledge**

# ![](/media/11ec5ddc982db9928341e858aab94652.png)

The active buzzer inside has a simple oscillator circuit , which can
convert constant direct current into a certain frequency pulse signal.
Once active buzzer receives a high level, it will sound. The passive
buzzer is an integrated electronic buzzer with no internal vibration
source. It must be driven by 2K to 5K square wave instead of a DC
signal. The appearance of the two buzzers is very similar, but passive
buzzers come with a green circuit board, and active buzzers come with a
black tape. Passive buzzers don't have positive pole, but active buzzers
have. As shown below:

![](/media/0f9825969867ac2d65bb1a19ed0ad2ab.png)

3.  **Circuit Diagram and Wiring Diagram**

<!-- end list -->

4.  ![](/media/48e73ef2d6090fe7cda58c385bad2ab2.png)

![](/media/56df73f7ac711e510b30164c5759615f.png)

Note:

1\. The buzzer power supply in this circuit is 5V.  On a 3.3V power
supply, the buzzer will work, but it will reduce the loudness.  

2\. The VUSB should connect to the positive terminal of the USB cable,
if it connects to GND, it could burn out the computer or Raspberry Pi
Pico.  Similarly, the Raspberry Pi Pico's 36-40 pins need to be
connected carefully to avoid short circuits. 

3\. The positive terminal ("+"/long pin) of the active buzzer is
connected to pin 16, and the negative terminal (short pin) is connected
to GND.

**5. Test Code**

The code used in this project is saved in the file KS3025 Keyestudio
Raspberry Pi Pico Learning Kit Complete Edition\\3. Raspberry Pi
System\\Python\_Tutorial\\2. Projects\\Project 12：Active Buzzer. You can
move the code anywhere. We save the code to the pi folder of the
Raspberry Pi system.

The path:home/pi/2. Projects

![](/media/ae27830403a2f741aa9b725e5324c215.png)

Open“Thonny”, click This computer”→“home”→“pi”→“2. Projects”→“Project
12: Active Buzzer”. And double-click the
Project\_12\_Active\_Buzzer.py”.

![](/media/ea2bb3dcb76907238d836020d837a605.png)

<table>
<tbody>
<tr class="odd">
<td><p>from machine import Pin</p>
<p>import time</p>
<p>buzzer = Pin(16, Pin.OUT) # create buzzer object from Pin 16, Set Pin 16 to output</p>
<p>try:</p>
<p>while True:</p>
<p>buzzer.value(1) # Set buzzer turn on</p>
<p>time.sleep(0.5) # Sleep 0.5s</p>
<p>buzzer.value(0) # Set buzzer turn off</p>
<p>time.sleep(0.5) # Sleep 0.5s</p>
<p>except:</p>
<p>pass</p></td>
</tr>
</tbody>
</table>

6.  **Text Result**
    
    Ensure that the Raspberry Pi Pico is connected to the
    computer，click“![](/media/ec00367ea605788eab454cd176b94c7b.png)Stop/Restart backend”.
    
    ![](/media/8166e15e1eeff8fe85a176be7cd6c9c2.png)
    
    Click ![](/media/bb4d9305714a178069d277b20e0934b7.png)“Run current script”, the code starts
    executing, we will see that the the active buzzer starts to buzz.
    Click“![](/media/ec00367ea605788eab454cd176b94c7b.png)Stop/Restart backend”to exit the
    program.
    
    ![](/media/95dc4875728d03ac8c4c48b62afb48fa.png)
