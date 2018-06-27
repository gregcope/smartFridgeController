# A smart Fridge Controller

For use on a boat or other place of limited batter power to better control the Fridge.  Use Latent heat (or cool) to limit power use when on batteries by loweringh the fridge temp when there is a surplas (ie charging/motoring), and when there is less power, let the fridge temp rise a little. 

For example when Battery (VCC) volts are around 13V, which implies charging, have a target fridge temp of 2C. ie Run the compressor by making a connection. When Battery volts are less than 13V (ie not charging) aim for the fridge temp to be 6C.

# How it works

* There is a temp sensor to be placed in the fridge/coolbox to sense the fridge temp
* There is piggy back connectoin on the main battery connections to the fridge to run the device and allow it to sense Battery volts
* There is a connetion to the thermostat pins, that allows it to override the normal thermostat
* If it fails the normal thermostat works as is
* The normal theromostat should be set to the "economy" temp setting
* LEDs show the mode its in (Boost or economy)

# Eagle Files

0. Uses Sparkfun DRC file
1. ERC and DRC check clean!
2. Bottom and Top Copper Pour

## Design
 
0. Uses a [Moteino](https://lowpowerlab.com/guide/moteino/)
1. The JST is to connect the VCC (Ie battery power) and Thermostat connection
2. Their is a 1.8M/3.3M VCC voltage divider to monitor the LIPO, with a 0.1uF capacitor - see [Jeelabs post here](https://jeelabs.org/2013/05/16/measuring-the-battery-without-draining-it/)
3. A 27M/3.3M voltage divider to measure 30+VCC on an ADC pin
4. Two (One for the fridge the other for ambient temp)[DS18B20 Waterproof Digital Probe Temperature Sensor with Silicone Cable (higher temp) Thermometer](https://www.ebay.co.uk/sch/i.html?_from=R40&_trksid=p2380057.m570.l1313.TR0.TRC0.H0.Xvermont+l+tent.TRS0&_nkw=DS18B20+Waterproof+Digital+Probe+Temperature+Sensor+Silicone+Cable+Thermometer&_sacat=0)
5. An efficient 7-36V to 3.3V regulator : [Murata OKI-78SR-5/1.5-W36-C](https://power.murata.com/data/power/oki-78sr.pdf)
6. [RGB LED](https://www.proto-pic.co.uk/content/datasheets/5mm_RGB_led_common_anodeDatasheet.pdf)
6. Three Status LEDS; Power, Boost mode, Economy mode
7. Six pin header for the two DS18 temp sensors to be connected too
8. [IXYS CPC 1706](http://www.ixysic.com/home/pdfs.nsf/www/CPC1706.pdf/$file/CPC1706.pdf) Power relay to control the compressor (ie make the connection as the thermostat does)
