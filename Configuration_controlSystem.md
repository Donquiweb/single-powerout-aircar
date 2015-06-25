## Overview ##
It's like traditional helicopter CCPM system, but not exactly same. Three servos control three valve.

![http://single-powerout-aircar.googlecode.com/svn/wiki/pic/control-1.jpg](http://single-powerout-aircar.googlecode.com/svn/wiki/pic/control-1.jpg)

#### Servo action List ####
![http://single-powerout-aircar.googlecode.com/svn/wiki/pic/col_sys-1.jpg](http://single-powerout-aircar.googlecode.com/svn/wiki/pic/col_sys-1.jpg)

## Setup by MWC ##
The concept model fly with multiwii, The mode is helicopter ccpm 120. Finish setup by [MWC Heli manual](http://fotoflygarn.blogspot.com/2012/04/multiwii-helicopter.html).
### notice!!! ###
channel 1, you need set to fix value such as 1500, it's not throttle!, your must control throttle by other channel, for example ESC(THR) connect to channel 5.<br><br>
Then we need change servo behavior:<br>
<img src='http://single-powerout-aircar.googlecode.com/svn/wiki/pic/control-2.jpg' /><br>
Open config.h<br>
Find:<pre><code><br>
#define SERVO_ENDPOINT_LOW {1020,1020,1020,1020,1020,1020,1020,1020};<br>
</code></pre>
change to<br>
<pre><code><br>
#define SERVO_ENDPOINT_LOW {1020,1020,1020,1510,1510,1020,1510,1020};<br>
</code></pre>
The value about is 1500, it's the center point for servo. It will limit route of servo become half.<br>
Find:<br>
<pre><code><br>
#define SERVO_NICK   { +10, -10, -0 }<br>
#define SERVO_LEFT   { +10, +5, -10 }<br>
#define SERVO_RIGHT  { +10, +5, +10 }<br>
</code></pre>
change to<br>
<pre><code><br>
#define SERVO_NICK   { +10, -18, -0 }<br>
#define SERVO_LEFT   { +10, +9, -18 }<br>
#define SERVO_RIGHT  { +10, +9, +18 }<br>
</code></pre>
It's zoom in servo end point<br>
<h3>Check valve's position</h3>
<img src='http://single-powerout-aircar.googlecode.com/svn/wiki/pic/control-3.jpg' /><br>
Place model a level surface, then all of the valve's position must is 0 degree(neutarl)! You need try your best to let them close to 0 degree!<br>
Push stick on your radio, all of the valve's end position about is 60 degree. Try keep every valve's end position is same! You maybe need turn down the value of  (2000) a little:<br>
<pre><code><br>
#define SERVO_ENDPOINT_HIGH {2000,2000,2000,2000,2000,2000,2000,2000};<br>
</code></pre>
Don't turn down too much, the route of servo possible isn't enough, fly will be not stabilize.<br>
<h3>Check MWC's stabilize function</h3>
Catch model with your hand, move it. Check every action of valve are right, aren't them? If you feel pitch or roll was Opposite, you can switch (+,-) in there:<br>
<pre><code><br>
#define SERVO_NICK   { +10, -18, -0 }<br>
#define SERVO_LEFT   { +10, +9, -18 }<br>
#define SERVO_RIGHT  { +10, +9, +18 }<br>
</code></pre>
If you feel yaw was reverse, you can switch (1 or -1) in there:<br>
<pre><code><br>
#define YAW_DIRECTION 1<br>
</code></pre>

<h3>Check radio reverse</h3>
move stick on radio,  If you feel pitch or roll was Opposite, you can switch reverse on radio, don't modify MWC's code.<br>
<br>
<h2>All be done, you can try to fly</h2>


