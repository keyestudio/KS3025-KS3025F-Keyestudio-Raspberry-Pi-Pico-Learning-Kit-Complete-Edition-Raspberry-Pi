# Project 02: Onboard LED flashing

**1. Description：**

There is an onboard LED in Raspberry Pi Pico,which is a GP25 pin
attached to the Raspberry Pi Pico. In this project, we will learn the
effect of making the onboard LED blink.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/8ea81d60b8e2132c358041235490b7d5.jpeg" style="width:2.52639in;height:1.07222in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/3bdcc62cfa661d2b860a76e28537e21e.png" style="width:1.41667in;height:0.76042in" /></td>
</tr>
<tr class="even">
<td>Raspberry Pi Pico*1</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Wiring Up**
    
    In this project, we use a USB cable to connect the Raspberry Pi Pico
    to the computer.

![](/media/8ea81d60b8e2132c358041235490b7d5.jpeg)

**Test Code**

Go to the folder KS3025 Keyestudio Raspberry Pi Pico Learning Kit
Complete Edition\\3. Raspberry Pi System\\Python\_Tutorial\\2.
Projects\\Project 02：Onboard LED flashing.

You can move the code anywhere. We save the code to the pi folder of the
Raspberry Pi system.

Path:home/pi/2. Projects

![](/media/ae27830403a2f741aa9b725e5324c215.png)

Online running

Open“Thonny”, click “This computer”→“home”→“pi”→“2. Projects”→“Project
02：Onboard LED flashing”

![](/media/7132fc82461f7395cfbd63fd62268984.png)

Go to the folder Project 02：Onboard LED flashing\<double-click
“Project\_02\_Onboard\_LED\_flashing.py”, as shown below;

![](/media/dca3b825e4f9fb5f7090dbefadc441d1.png)

<table>
<tbody>
<tr class="odd">
<td><p>from machine import Pin</p>
<p>import time</p>
<p>led = Pin(25, Pin.OUT) # create LED object from Pin 25, Set Pin 25 to output</p>
<p>try:</p>
<p>while True:</p>
<p>led.value(1) # Set led turn on</p>
<p>time.sleep(0.5) # Sleep 0.5s</p>
<p>led.value(0) # Set led turn off</p>
<p>time.sleep(0.5) # Sleep 0.5s</p>
<p>except:</p>
<p>pass</p></td>
</tr>
</tbody>
</table>

Connect the pico board to the Raspberry Pi. Click
![](/media/32e03e9d4211e9ef97c1d2b18f05c902.png)to check the Shell

![](/media/a8313a26331800f383c84ffa64b4e225.png)

Click ![](/media/bb4d9305714a178069d277b20e0934b7.png) to run the code. Then the LED on the pico
board will flash; click ![](/media/32e03e9d4211e9ef97c1d2b18f05c902.png)to exit the program.

![](/media/6dbd11e5159b47b0061c2ed199bdd75e.png)

![](/media/529c3be102eb7414ac1e5e66fb203b6e.png)

Note: This is the code that runs online.  If you disconnect the USB
cable and restart Raspberry Pi Pico, the LEDS on Raspberry Pi Pico stop
flashing. The following information will be displayed in the "Shell"
window of Thonny software:  

![](/media/b7d8c524956cb140d5d04eefff0d9f9f.png)

Code to run offline (upload code to Raspberry Pi Pico) :

Ensure that the Raspberry Pi Pico is connected to the computer andclick
![](/media/32e03e9d4211e9ef97c1d2b18f05c902.png).  

![](/media/3c1df575aecb6514c127558c7b70dfae.png)

As shown in the following figure, right-click the
file“Project\_02\_Onboard\_LED\_Flashing. py”and choose“Upload to/”to
upload the code to Raspberry Pi Pico.  

![](/media/8958426b1b043cd82eab3eb6891a9113.png)

Upload main.py in the same way.

![](/media/ce2c0761a54621a4d363fae29cf0369f.png)

Disconnect the USB cable from the Raspberry Pi Pico and reconnect, and
the Raspberry Pi Pico's LED flashes repeatedly.  

![](/media/529c3be102eb7414ac1e5e66fb203b6e.png)

Note: The code here runs offline.  If you want to Stop running
offlineand display the information in the “Shell” window, simply click
![](/media/32e03e9d4211e9ef97c1d2b18f05c902.png)in Thonny software.

![](/media/a416597bf07fbb471cc82a1c355065af.png)
