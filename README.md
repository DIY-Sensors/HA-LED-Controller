# HA-LED-Controller
DIY Home Assistant LED Controller

Make: Soldering<br>
Code: Easy<br>
Cost: Low<br>

I regularly use LED strips in various projects. Sometimes one color but usually I choose the RGB variant, combined or not with a white LED strip. Making a controller for this is easy, but does mean that you have to solder a little. For people without soldering experience, the perfect opportunity to gain some soldering experience.
In order not to make the project unnecessarily complicated, I chose a WEMOS Mini, but you can use any EPS8266 board or ESP32 board with WiFi.
For the Mosfet I chose the IRF 520n, you can use any other Mosfet for this as long as it has an N-channel as polarity. The IRF 520n can theoretically have 9.7 Ampere at 10 Volt. The most important thing here is the dissipation of heat, 2.5 meters of LED strip (one color) can be done without any problems without cooling. I would definitely mount a heatsink above that. Parts

* WEMOS D1 mini € 1.76 (China)
* 12V version: IRF520n or similar Mosfet € 0.24 (China)
*  5V version: IRF3708
* Resistor 10k € 0.02 (China)
* Prefboard (universal printed circuit board € 0.38 (China) Optional

# Schematics
<img src="images/LED%20Controller%201.jpg" alt="Scheme LED Controller" width="400" >
In order not to make the schematic unnecessarily complicated, I have depicted the control for one color in this schematic. For more colors / LED strips, this can be repeated and connected to the various D-ports of the WEMOS D1 / ESP8266 / ESP32. The code will determine later whether it is an RGB, RGBW or single color.
The entire circuit is connected to ground. An RGB LED strip has a fixed + and switches the different colors based on the -. The Mosfet ensures that the signal from the WEMOS D1 / ESP8266 / ESP32 is translated to the control of 12 volts. Because everything is controlled via the ground and is otherwise separate from the power supply of the LED strip, the 12 volts can also be 24 volts or, for example, 5 volts. Just take into account the specifications of the relevant Mosfet.
<img src="images/LED%20Controller%202.jpg" alt="Schema LED Controller met Buck converter" width="600" />
In many cases I use a single 12 Volt power adapter and I do not have extra 5 Volts available. This is easily solved by using a Step-down or Buck converter that can convert 12 Volts to 5 Volts or, for example, 3.3 Volts.

Mounted on a perf-board it could look like this. I control two LED strips here, both white, one of which has a length of 2 meters and the other a length of 1 meter.<br>
 <img src="images/LED%20Controller%20print.jpg" alt="LED controller op print" width="250" />

# ESP Code
The code in ESP-Home is very simple and I have published it on my GitHub site: <a href="https://github.com/DIY-Sensors/HA-LED-Controller/blob/main/code/2%20LED%20strips.yaml" target="_blank"> GitHub 2 LED strips</a>, <a href="https://github.com/DIY-Sensors/HA-LED-Controller/blob/main/code/RGB%20LED%20strip.yaml" target="_blank">RGB LED strip</a>, <a href="https://github.com/DIY-Sensors/HA-LED-Controller/blob/main/code/RGBW%20LED%20strip.yaml" target="_blank"> RGBW LED strip</a>.
I try to keep this code as up to date as possible, ESPHome asks for adjustments to the code from time to time.
Part, the upper part, is automatically generated by ESPHome, it is not always possible to select the correct ESP board directly. So I manually added the board type: board: d1_mini_lite.

I have two LED strips, one on each side of the window and on one site a RGB strip all combined in one controler.. These strips are controlled from D7 (right) and D8 (left),  D4, D5 and D6 for the RGB. You are of course free to adjust one thing or another yourself. You are of course free to adjust all my code, for your own use. My projects are made for myself and for others to further develop into even more beautiful and extensive projects.
If you found this web page useful, could you let me know via my YouTube page<a href="https://www.youtube.com/watch?v=C99b1UtMZ4w" target="_blank">Maak een LED Dimmer voor Home Assistant met ESP8266 / ESP32 #13</a> (sorry, at this moment only in Dutch ..... working on an Englisch version). A thumbs up not only helps me with the YouTube channel, but also this site.
