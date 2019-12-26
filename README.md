# node-twinkle

This code is used to controlling Twinkly LED xmas lights in real time using rt mode built into Twinkly LED xmas lights.
This is extremely basic ATM. This code is more a working proof on concept then a code base.

## Unofficial

This is an Unofficial code, with no warranty or support, use at your own risk.

I am in no way associated with Twinkly, and or LedWorks S.R.L.
Twinkly & LedWorks S.R.L. belong to their associated copyright owners.


### How to use

#### Build Code

```
cd /pathToProject/node-twinkle/
npm i express
```

#### Configuring Code Base


##### Set IP
Make sure you've configured your Twinkly LED lights to connect to your wifi network
Make sure your smart phone is connect to the same wifi network
Make sure your computer is connect to the same wifi network.
Open the Twinkly Smart App
Touch Menu
Touch Devices
Touch The gear to the right of your Twinkly LED lights
Find the IP address of your Twinkly LED lights

In Twinkle.js Change HOST ip to the IP address of your Twinkly LED lights

```
var HOST = '192.168.2.17';
```

##### Set LEDs Packet
Currently the UDP packet to set LEDs is formated for a Twinkly that is RGB, and has 224 LEDs.
IF your LED type is diffrent then RGB, you may need a diffrent amount of hex per LED.
If your Twinkly has more or less LEDS, you'll need to change the number of HEX to match your number of LEDS.

Change LEDs = [ ]; to the correct number of LEDs.


Example: if your Twinkly has 1 LED of type RGB
```
var LEDs = [ 0x00, 0x00, 0x00 ];

```
Example: if your Twinkly has 2 LED of type RGB
```
var LEDs = [ 0x00, 0x00, 0x00, 0x00, 0x00, 0x00 ];
```


#### Running the Code
Using the Code
```
node /pathToProject/Twinkle.js
```

#### Changing LEDs by sending LED values to http server (local host aka 127.0.0.1)

Example: set the first LED (closest to power strip) to white
```
http://127.0.0.1:8088/1/0x0ff/0xff/0xff
```

Example: set the second LED (2nd closest to power strip) to white
```
http://127.0.0.1:8088/2/0x0ff/0xff/0xff
```

Example: set the first LED (closest to power strip) to red
```
http://127.0.0.1:8088/1/0x0ff/0x00/0x00
```


#### Stopping Node
To re-start node, node must first be stopped. 

You may be able to use

```
sudo killall node
```
to force quite node.

Or you may need to use 

```
sudo kill -9 `ps aux | grep node | grep -v grep | awk '{print $2}'`
```

windows, it might be 
```
taskkill /im node.exe /F
```
