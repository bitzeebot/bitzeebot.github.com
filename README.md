Bit-zee Bot
===========
Bit-zee Bot is a robot made for [Khan Academy](http://www.khanacademy.org/science/Projects/Bit-zee) out of household
items, an Arduino board and a motor controller. Here is a video of 
[Bit-zee Bot in action](http://youtu.be/CcziDRr5Myc "Bit-zee Bot").


##Bit-zee Code##

Bit-zee Code is a programming language for controlling Bit-zee Bot. Bit-zee Code is based on Graffiti Code a language
framework developed at [Art Compiler](http://artcompiler.org "Art Compiler"). Graffiti Code uses a semantic subset of
ML, and a syntax that is light on punctuation. Languages are created in Graffiti Code by defining a primitive 
vocabulary made up of events and functions. User programs define functions that handle the events and call the 
primitive functions.



###Sample Bit-zee Code###

_(This code defines two handlers for remote control events. Pressing button 1 on the remote causes the robot's 
lights to flash. Pressing button 2 causes the robot to spin counter clockwise for 3 seconds.)_

def **remote 1**. **flash lights**.

def **remote 2**. **spin left**.

def **flash lights**. **blink 100ms 1 0 0**. **blink 100ms 0 1 0**. **blink 100ms 0 0 1**.

def **spin left**. **power full**. **forward right**. **backward left**. **delay 3s**. **stop**.


###Event handlers###

def **remote 1**.

def **remote 2.**

def **remote 3.**

def **remote 4.**

def **remote 5.**

def **remote 6.**

def **remote 7.**

def **remote 8.**

def **remote 9.**

def **remote dot.**

def **remote 0.**

def **remote enter.**

def **remote rew.**

def **remote play.**

def **remote ff.**

def **remote rec.**

def **remote stop.**

def **remote pause.**

def **bump front.**

def **bump back.**

def **time t.** 

###Primitive functions###

def **forward**.  _(turn both wheels forward)_

def **forward left**. _(turn left wheel forward)_

def **forward right**. _(turn right wheel forward)_

def **backward**. _(turn both wheels backward)_

def **backward left**.  _(turn left wheel backward)_

def **backword right**. _(turn right wheel backward)_

def **stop**. _(stop sending current to both wheels)_

def **stop left**. _(stop sending current to left wheel)_

def **stop right**. _(stop sending current to right while)_

def **power full**.        _(set the speed to full power)_

def **power half**.        _(set the speed to half power)_

def **power none**.        _(set the spped to zero power)_

def **power n:int**.       _(set the speed to n ranging from 0 to 255)_

def **blink t**.           _(turn lights on for time t and then off for time t)_

def **blink t r g b**.     _(blink t with the given rgb values)_ 

def **delay t**.           _(stop execution for time t)_

def **random min max**.    _(return a random number between min and max)_

def **calibrate l:list**.  _(calibrate the power sent to wheels based on given list)_

def **accelerate n**.      _(increase forward power by n in the range of -255 and 255)_

def **decelerate n**.      _(decrease forward power by n in the range of -255 and 255)_

def **image record**.      _(take picture)_

def **sound record**.      _(start / stop recording sound)_

def **sound play**.        _(play sound)_


