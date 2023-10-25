# Project 09：4-Digit Digital Tube

## 1. Introduction
    
The 4-digit 7-segment digital tube is a very practical display device, and it is used for devices such as electronic clocks and
score counters. Due to the low price and it is easy to use, more and more projects will use 4-digit 7-segment digital tubes. In this project, we will use the Raspberry Pi Pico to control a 4-bit 7-segment digital tube to create a manual counter.

<!-- end list -->

## 2. Components Required

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/b18fe281156b29c44796f72222718d58.jpeg" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/bbed91c0b45fcafc7e7163bfeabf68f9.png" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png"  /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/e380dd26e4825be9a768973802a55fe6.png"  /></td>
</tr>
<tr class="even">
<td>Raspberry Pi Pico*1</td>
<td>Raspberry Pi Pico Expansion Board*1</td>
<td>220Ω Resistor*8</td>
<td>Breadboard*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/ee7a4ecd35ef268149e31fb9d62c8227.png" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS3025-KS3025F-Keyestudio-Raspberry-Pi-Pico-Learning-Kit-Complete-Edition-Raspberry-Pi/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" /></td>
<td></td>
</tr>
<tr class="even">
<td>4-Digit Digital Tube Module*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
<td></td>
</tr>
</tbody>
</table>

## 3. Component Knowledge

![](/media/ce987bf9a2ab398945c98b34d3f8a003.png)

Four-digit digital tube: The four-digit digital tube has two types of four-digit digital tubes: a common anode and a common cathode. The display principle is similar to that of a one-digit digital tube. They are all 8 GPIO ports to control the display segment of the digital tube, that is, 8 LED lights, however, here are 4 bits, so 4 GPIO ports are needed to control the bit selection terminal, that is, to choose which single digital tube is on, the bit switching is very fast, and the naked eye can't distinguish it. A digital tube is displayed at the same time. It is common cathode.

**G1, G2, G3 and G4 are pins of control bit**.

![](/media/37113fa53213973132086c285d67686b.png)

Schematic Diagram

![](/media/ea75d1b7414bf6f8c187fb32fea9bc83.png)

## 4. Circuit Diagram and Wiring Diagram

![](/media/4f64b9bf6b74ab49584f69c7465efa73.png)

![](/media/6bf1bae6af0324d50a37ab7a0cabee11.png)

## 5. Test Code

The code used in this project is saved in the file <span style="color: rgb(255, 76, 65);">KS3025 Keyestudio Raspberry Pi Pico Learning Kit Complete Edition\\3. Raspberry Pi System\\Python\_Tutorial\\2. Projects\\Project 09：4-Digit Digital Tube</span>.

You can move the code to anywhere.For example, we save it in the pi folder of the Raspberry Pi system, the route is <span style="color: rgb(255, 76, 65);">home/pi/2. Projects</span>.

![](/media/ae27830403a2f741aa9b725e5324c215.png)

Open“Thonny”, click“This computer”→“home”→“pi”→“2. Projects”→“Project 09：4-Digit Digital Tube” and then double-click“Project_09_Four_Digit_Digital_Tube.py”.

![](/media/333a7cbe71f2ecabcecf12c0b1d8c95c.png)

```Python
from machine import Pin
import time

#Pin of each digit of nixie tube
a = machine.Pin(21, machine.Pin.OUT)
b = machine.Pin(28, machine.Pin.OUT)
c = machine.Pin(16, machine.Pin.OUT)
d = machine.Pin(18, machine.Pin.OUT)
e = machine.Pin(19, machine.Pin.OUT)
f = machine.Pin(22, machine.Pin.OUT)
g = machine.Pin(15, machine.Pin.OUT)
dp = machine.Pin(17, machine.Pin.OUT)

G1 = machine.Pin(20, machine.Pin.OUT)
G2 = machine.Pin(26, machine.Pin.OUT)
G3 = machine.Pin(27, machine.Pin.OUT)
G4 = machine.Pin(14, machine.Pin.OUT)
 
#digital tube a to dp corresponding development board pins
d_Pins=[machine.Pin(i,machine.Pin.OUT)  for i in [21,28,16,18,19,22,15,17]]
#Pin corresponding to digital tube segment G1, G2, G3, and G4
w_Pins=[machine.Pin(i,machine.Pin.OUT)  for i in [20,26,27,14]]
 
number={
    '0':
    [1,1,1,1,1,1,0,0],#0
    '1':
    [0,1,1,0,0,0,0,0],#1
    '2':
    [1,1,0,1,1,0,1,0],#2
    '3':
    [1,1,1,1,0,0,1,0],#3
    '4':
    [0,1,1,0,0,1,1,0],#4
    '5':
    [1,0,1,1,0,1,1,0],#5
    '6':
    [1,0,1,1,1,1,1,0],#6
    '7':
    [1,1,1,0,0,0,0,0],#7
    '8':
    [1,1,1,1,1,1,1,0],#8
    '9':
    [1,1,1,1,0,1,1,0],#9
}
 
def display(num,dp):
    global number
    count=0
    for pin in d_Pins:#displays the value of num 
        pin.value(number[num][count])
        count+=1
    if dp==1:
        d_Pins[7].value(0)
def clear():
    for i in w_Pins:
        i.value(0)
    for i in d_Pins:
        i.value(1)
def showData(num):
   #the hundreds, thousands, ones, and fractional values of a numeric value
    d_num=num
    location=d_num.find('.')
    if location>0:
        d_num=d_num.replace('.','')
        while len(d_num)<4:
            d_num='0'+d_num
        for i in range(0,4):
            time.sleep(2)
            clear()
            w_Pins[3-i].value(1)
            if i==location-1:
                display(d_num[i],1)
            else:
                display(d_num[i],0)
    if location<0:
        for i in range(0,4):
            time.sleep(2)
            clear()
            w_Pins[3-i].value(1)
            display(d_num[i],0)
while True:
 
    num='9016'
    showData(num)
```

## 6. Test Result：

Connect the pico board to the Raspberry Pi. Click ![](/media/32e03e9d4211e9ef97c1d2b18f05c902.png)to check the Shell

![](/media/7336ab33350378f16514393ce2f0ed37.png)

Click “![](/media/bb4d9305714a178069d277b20e0934b7.png)”, the code starts executing, we will see that the 4-digit digital tube circularly displays numbers from 0000 to 9999. 
Click“![](/media/ec00367ea605788eab454cd176b94c7b.png)”to exit the program.

![](/media/f0796c7080e70cac96dc4e42b39f0918.png)








