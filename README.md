# hp10544-retrofit
Use this circuit to replace HP10544 OCXO with an off-the-shelf OCXO 8663-XS unit 

The HP10544 OCXO is used in the HP5328 Universal Counter. My OCXO failed a while ago, and after being
absolutely disgusted with the performance of the internal xtal oscillator (simply awful) I used the
counter for a long time with an external OCXO or Rb Osc. I finally decided to take a look at the 
HP10544 unit, and realized that it could be replaced with an off the shelf OCXO. The circuit consists
of three sections: 1) OCXO voltage regulator; 2) OCXO --> TTL converter; 3) OCXO Fine Tuning.

The OCXO that I used was an Oscilloquartz 8663-XS unit. There are lots of units that share this same
physical size and footprint. I imagine that any comparable unit would work just as well. YMMV.

I chose an LM2675 to regulate the (nominal) 28VDC supply down to the 12VDC for the OCXO. As this 
supply is working continuously, it made the most sense to use a DC-DC switching regulator, rather
than a linear regulator. My observation is that the OCXO does not seem to have any measurable 
dependence upon supply voltage 'cleanliness'. (DC-DC vs. LDO vs. Lab Supply).

The OCXO output is a clipped sine 10 MHz analog output, which needs to be shifted and squared up to
match the output of the HP 10544 OCXO. I used a circuit from the Efratom LPRO 101 Rb oscillator
datasheet which has worked very well for me in the past. The sine signal is AC coupled into the 
input of a fast CMOS inverter. I used a 74AC04 here. See the LPRO 101 Rb oscillator datasheet for
a great comparison of several ways to convert a 10 MHz sine into a 10 MHz square wave.

The fine tuning is simply a potentiometer connected across the VREF and GND pins of the OCXO, with
the wiper connected to the VFC terminal. I used a 20 turn pot to make trimming easy.

Circuit and PCB were designed in March 2015. PCB was fabricated by OSHpark in April. Build/test was
completed in June 2015. 

Tom LeMense
June 13, 2015

