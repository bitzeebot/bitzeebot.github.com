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



###Event handlers###

fun **remote 1**.

fun **remote 2.**

fun **remote 3.**

fun **remote 4.**

fun **remote 5.**

fun **remote 6.**

fun **remote 7.**

fun **remote 8.**

fun **remote 9.**

fun **remote dot.**

fun **remote 0.**

fun **remote enter.**

fun **remote rew.**

fun **remote play.**

fun **remote ff.**

fun **remote rec.**

fun **remote stop.**

fun **remote pause.**

fun **bumper front.**

fun **bumper back.**

###Primitive functions###

fun **forward**.  _(turn both wheels forward)_

fun **forward left**. _(turn left wheel forward)_

fun **forward right**. _(turn right wheel forward)_

fun **backward**. _(turn both wheels backward)_

fun **backward left**.  _(turn left wheel backward)_

fun **backword right**. _(turn right wheel backward)_

fun **stop**. _(stop sending current to both wheels)_

fun **stop left**. _(stop sending current to left wheel)_

fun **stop right**. _(stop sending current to right while)_

fun **power full**.        _(set the speed to full power)_

fun **power half**.        _(set the speed to half power)_

fun **power none**.        _(set the spped to zero power)_

fun **power n:int**.       _(set the speed to n ranging from 0 to 255)_

fun **blink t**.           _(turn lights on for time t and then off for time t)_

fun **blink t r g b**.     _(blink t with the given rgb values)_ 

fun **delay t**.           _(stop execution for time t)_

fun **random min max**.    _(return a random number between min and max)_

fun **calibrate l:list**.  _(calibrate the power sent to wheels based on given list)_

fun **accelerate n**.      _(increase forward power by n in the range of -255 and 255)_

fun **decelerate n**.      _(decrease forward power by n in the range of -255 and 255)_

fun **image record**.      _(take picture)_

fun **sound record**.      _(start / stop recording sound)_

fun **sound play**.        _(play sound)_


###UnitOne in Bit-zee Code###

The following is an approximation of what the code used in the original Bit-zee videos
looks like in Bit-zee Code.

~~~
fun flashLights = 
    blink 100ms high low low.
    blink 100ms low high low.
    blink 100ms low low high.
    blink 300ms high low high.
    blink 300ms high high low.
    blink 300ms low high high.
    blink 100ms high low low.
    blink 100ms low high low.
    blink 100ms low low high.
    blink 100ms high low high.
    blink 100ms high high low.
    blink 100ms low high high.
    blink 300ms high low low.
    blink 300ms low high low.
    blink 300ms low low high.
.

fun powerSlide left =
    speed full.
    forward 2 seconds.
    spin left.
    delay 500 ms.
    backward 300 ms.
.
    
fun powerSlide right =
    speed full.
    forward 2 seconds.
    spin right.
    delay 500 ms.
    backward 300 ms.
.
    
fun figureEight =
    forward left.
    forward right.
    blink 300ms high low low.
    blink 300ms low high low.
    blink 300ms low low high.
    stop left.
    blink 300ms high low low.
    blink 300ms low high low.
    blink 300ms low low high.
    forward left.    
    blink 300ms high low low.
    blink 300ms low high low.
    blink 300ms low low high.
    stop right.
    blink 300ms high low low.
    blink 300ms low high low.
    blink 300ms low low high.
    forward right.
    blink 300ms high low low.
    blink 300ms low high low.
    blink 300ms low low high.
    stop left.
    stop right.
.
    
fun wiggle n =
    if n is zero 
    then
	flashLights.
    else
        speed random full minus 20 full.
        spin left.
        delay random 100 200.
        spin right.
        delay random 100 200.
        wiggle n minus one.
.

fun waddleBackwardLeft =
    stop right.
    backward left.
    blink 300ms high low low.
    stop left.
    backward right.
    blink 300ms low high low.
    stop right.
    backward left.
    blink 300ms low low high.
    stop left.
    backward right.
    blink 300ms low high low.
    stop right.
.

fun waddleBackwardRight =
    stop left.
    backward right.
    blink 300ms high low low.
    stop right.
    backward left.
    blink 300ms low high low.
    stop left.
    backward right.
    blink 300ms low low high.
    stop right.
    backward left.
    blink 300ms low high low.
    stop left.
.

fun waddleBackward n =
    if n is zero
    then
        none.
    else
        speed full.
        waddleBackwardLeft.
        blink 300ms high low low.
        blink 300ms low high low.
        blink 300ms low low high.
        waddleBackwardRight.
        blink 300ms high low low.
        blink 300ms low high low.
        blink 300ms low low high.
        waddleBackward n minus one.
.
        
        
fun waddleForwardLeft =
    stop right.
    forward left.
    blink 300ms high low low.
    stop left.
    forward right.
    blink 300ms low high low.
    stop right.
    forward left.
    blink 300ms low low high.
    stop left.
    forward right.
    blink 300ms low high low.
    stop right.
.

fun waddleForwardRight =
    stop left.
    forward right.
    blink 300ms high low low.
    stop right.
    forward left.
    blink 300ms low high low.
    stop left.
    forward right.
    blink 300ms low low high.
    stop right.
    forward left.
    blink 300ms low high low.
    stop left.
.

fun waddleForward n =
    if n is zero
    then
        none.
    else
        speed full.
        waddleForwardLeft.
        blink 300ms high low low.
        blink 300ms low high low.
        blink 300ms low low high.
        waddleForwardRight.
        blink 300ms high low low.
        blink 300ms low high low.
        blink 300ms low low high.
        waddleForward n minus one.
.

fun remote 1 = waddleForward 5..
fun remote 2 = wiggle 5..
fun remote 3 = powerSlide right..
fun remote 4 = powerSlide left..
fun remote 5 = spin left. delay 3 seconds. stop all..
fun remote 6 = spin right. delay 3 seconds. stop all..
fun remote 7 = forward right..
fun remote 8 = figureEight..
fun remote 9 = waddleBackward 4..
fun remote dot = recordSound..
fun remote play = playSound..
fun remote rew = backwardFaster..
fun remote rec = recordImage..
fun remote ff = forwardFaster..
fun remote pause = stop right. stop left..
fun remote pwr = flashLights..
fun bumper back = playSound. waddleForward 4. flashLights..
fun bumper front = playSound. waddleBacwkard 4. flashLights..
~~~