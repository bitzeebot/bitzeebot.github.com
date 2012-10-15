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

let **remote 1..**

let **remote 2..**

let **remote 3.**

let **remote 4..**

let **remote 5..**

let **remote 6..**

let **remote 7..**

let **remote 8..**

let **remote 9..**

let **remote dot..**

let **remote 0..**

let **remote enter..**

let **remote rew..**

let **remote play..**

let **remote ff..**

let **remote rec..**

let **remote stop..**

let **remote pause..**

let **bumper front..**

let **bumper back..**

###Primitive functions###

let **forward** =  _(turn both wheels forward)_

let **forward left** = _(turn left wheel forward)_

let **forward right** = _(turn right wheel forward)_

let **backward** = _(turn both wheels backward)_

let **backward left** =  _(turn left wheel backward)_

let **backword right** = _(turn right wheel backward)_

let **stop** = _(stop sending current to both wheels)_

let **stop left** = _(stop sending current to left wheel)_

let **stop right** = _(stop sending current to right while)_

let **power full** =        _(set the speed to full power)_

let **power half** =        _(set the speed to half power)_

let **power none** =        _(set the spped to zero power)_

let **power n:int** =       _(set the speed to n ranging from 0 to 255)_

let **blink t** =           _(turn lights on for time t and then off for time t)_

let **blink t r g b** =     _(blink t with the given rgb values)_ 

let **delay t** =           _(stop execution for time t)_

let **random min max** =    _(return a random number between min and max)_

let **calibrate l:list** =  _(calibrate the power sent to wheels based on given list)_

let **accelerate n** =      _(increase forward power by n in the range of -255 and 255)_

let **decelerate n** =      _(decrease forward power by n in the range of -255 and 255)_

let **image record** =      _(take picture)_

let **sound record** =      _(start / stop recording sound)_

let **sound play** =        _(play sound)_


###UnitOne in Bit-zee Code###

The following is an approximation of what the code used in the original Bit-zee videos
looks like in Bit-zee Code.

~~~
let flashLights = 
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

let powerSlide left =
    speed full.
    forward 2 seconds.
    spin left.
    delay 500 ms.
    backward 300 ms.
    .
    
let powerSlide right =
    speed full.
    forward 2 seconds.
    spin right.
    delay 500 ms.
    backward 300 ms.
    .
    
let figureEight =
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
    
let wiggle n =
    if n is zero 
    then
	flashLights
    else
        speed random full minus 20 full.
        spin left.
        delay random 100 200.
        spin right.
        delay random 100 200.
        wiggle n minus one.
    .

let waddleBackwardLeft =
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

let waddleBackwardRight =
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

let waddleBackward n =
    if n is zero
    then
        none
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
        
        
let waddleForwardLeft =
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
 
let waddleForwardRight =
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

let waddleForward n =
    if n is zero
    then
        none
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

let remote 1 = waddleForward 5..
let remote 2 = wiggle 5..
let remote 3 = powerSlide right..
let remote 4 = powerSlide left..
let remote 5 = spin left. delay 3 seconds. stop all..
let remote 6 = spin right. delay 3 seconds. stop all..
let remote 7 = forward right..
let remote 8 = figureEight..
let remote 9 = waddleBackward 4..
let remote dot = recordSound..
let remote play = playSound..
let remote rew = backwardFaster..
let remote rec = recordImage..
let remote ff = forwardFaster..
let remote pause = stop right. stop left..
let remote pwr = flashLights..
let bumper back = playSound. waddleForward 4. flashLights..
let bumper front = playSound. waddleBacwkard 4. flashLights..
~~~