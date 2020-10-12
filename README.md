# AD_Power
A Power Conditioner for Audio Damage Eurorack modules.

## Background

At one time Audio Damage manufactured and sold a line of Eurorack synthesizer
modules which provided a range of unique functions. Many of these modules are
based on the STM32F4 series of microcontrollers and suffer from a power supply
sequencing issue that causes the CPU to hang up when power is applied.

The problem arises when the -12V supply stabilizes more slowly than the +12V -
a sneak path through the input buffer op-amps and codec power supply locks up the
MCU in a way which cannot be recovered without power cycling. The only way to
prevent this without modifying the module is to insert a switch into the +12V
supply and hold it off until the -12V begins to rise.

I have prototyped a small PCB with the proper circuitry for this which can be
added into the power supply cable. The design info is available here if you are
able to DIY such things. I do not manufacture or sell these myself.

## Hardware

The design is very simple, consisting of just a board, two connectors and four
SMT components. The theory of operation is simple - a P-channel MOSFET in the
+12V rail is held in the OFF state until the -12V rail drop low enough to turn
it on, the threshold for this is set by a zener diode and several resistors.

[ad_pwr schematic](ad_pwr_schematic.pdf)

The bare board looks like this:

![ad_pwr board](/ad_pwr_front.jpg)

and is available from OSHpark for a small fee.

[ad_pwr at OSHpark](https://oshpark.com/shared_projects/LjTaLjEs)

alternatively, the raw gerber files for the PCB are here:

[ad_pwr gerbers](oshpark.ad_pwr.zip)

The Bill of Materials (BOM) is here:

[ad_pwr_bom](ad_pwr_bom.pdf)

It's essential to use the specified components to ensure proper sequencing
of the power supplies.



