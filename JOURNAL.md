# 30th of June 2025
I actually got this idea Yesterday, But I didn't work on it. Basically I want a little 6502 powered conference badge with important info about me.
Such inclusions include:
- Name
- Email
- Website

As far as little interactive elements, I wanted some LEDS that go around the outside.
Kinda like

![Steelcon 2024 Kids Track Badge](Journal/Images/steelcon-badge.jpg)

But with 8 LEDs instead of 6 (for all 8 data lines obviously... Or is it 7? do you count from 0 to 7 or 1 to 8, hmmm)

I also wanted to make life significantly harder on myself, as I wanted to use OSHParks super freaking cool [After Dark](https://docs.oshpark.com/services/afterdark/) PCB stuff, which limits you to 2 copper layers.
And obviously the traces need to look good because like they are on display

Now, to decide on a layout for my information I opened up a figma and just started putting text down :)

All Icons are from [@hackclub/icons](https://icons.hackclub.com) because while limited in selection, I prefer them.

## First Attempt:

![Text V1](Journal/Images/text-v1.png)

While I enjoyed the simplicity of this approach, I decided to redesign because:
a) It doesn't really describe me and my personality
b) It would very easily get lost in the busyness of the camp.

## Second Attempt

![Text V2](Journal/Images/text-v2.png)

The main differences are:
- Centering
- Little invitational text
- A row of icons describing my hobbies and major features (rainbow = lgbtq, code = programming, image = photography)

I wanted a ring of icons, but I ran out of things that describe me 😭, and I'm much happier with this anyway (it's not like anyone will look tbh)

# 1st of July 2025

Now that I know what the center looks like and a bit of my specs, I can start working on the Schematic.
This is optimised for looks and size over price.

I also realised that I need to provide a 5V voltage rail for my chips, To do this, I settled on a 9V battery and then voltage regulating it down to 5V. I'll leave the battery holder off the PCB since this is a pin badge of sorts

The specific parts I have gone for are:
- W65C02 (CPU)
- W65C22S6TPG (VIA)
- AT28C256 (EEPROM/ROM)
- AS6C62256 (RAM)
- Red LEDs
- 1Mhz Clock IC

I however need to size my Voltage regulator properly, to do this I found the datasheets for all my parts and started adding!

CPU: 1.5mA (I think?)
VIA: 0.5mA
ROM: 10mA
RAM: 15mA

So like, not too bad and a 150mA regulator should easily be able to do it.
Specifically I chose the [TPS7250QP](https://www.mouser.co.uk/ProductDetail/Texas-Instruments/TPS7250QP) because it's the closest equivalent that mouser had. Although I'm not a fan of the number of support components

The Typical Application Configuration is below:
![TPS7250QP](Journal/Images/TPS7250QP.png)

Meaning it needs 2 resistors and 2 capacitors.

