# Extremely Low Noise Regulator

This details a regulator that is used by the Auteur Audio [Lilienfeld's Choir](http://auteuraudio.com/lilienfelds-choir) amplifier.  It
was designed to have both extremely low noise and to be extremely precise.  The reason is that the topology of Lilienfeld's 
Choir, being a non-feedback topology, does not have the power supply rejection witnessed in other topologies.  The objective
of the amplifier was incredibly low noise and extremely fast response, so a highly performance power supply regulator was a necessity.



## Background

The basic notion of regulation has not changed appreciably since the use of a triode and a neon regulator tube.  That is to say, 
regulation has always been an active device comparing the output with a reference and making a correction.  However, there is a lot
of finesse that is required to do this job well, and there are a lot of ways of achieving this effect that work better for certain
scenarios.  Lilienfeld's Choir is an amplifier with nearly constant power requirements, which is an affordance for a regulator 
having some very good qualities at the expense of flexibility.  

Long ago in the semiconductor world it was commonplace to see discreet regulators.  We all have had a bench supply built this 
way.  Like many commonly used things, it made its way to a specialized product.  In this case, it was the LM317, released in 
1976 by National Semiconductor.  Since it solved many problems for many people, it rapidly became a hit.  However, like many 
products that solve something reasonably well for a lot of people, it didn't solve some problems as well as might be desired.  This
sentiment was the focus of Mike Sulzer's 1980 _Audio Amateur_ article, where the venerable LM317 was updated using discreet components
to afford a better output.

Over the years there have been a series of better and better variants on the audio regulator.  These have been discussed by many 
in the field -- people like Mike Sulzer, Erno Borbely, Jan Didden, Walt Jung, Gary Galo and others -- each building on 
the lessons of the design predecessor.  The focus of this particular regulator is the lowest noise possible.  I will attempt to 
describe how it is different than some of the more commonly seen modern discreet regulators, and why.



## The Circuit

Below is the general circuit:

![Schematic](schematic.png)

The most notable feature of this regulator is the op amp being powered on the regulated side.  This was a great innovation on the 
part of Walt Jung's [Super Regulator 2](http://waltjung.org/PDFs/Improved_PN_Regs.pdf) compared with its predecessors.  Not only was 
placement of the op amp an improvement for further reducing power supply coupled noise, but the pass transistor to this day is 
a fantastic choice for medium-sized regulators.  While this regulator has a very novel feedback mechanism using a green LED as as 
a high bandgap voltage supply in a constant current circuit driving the main pass transistor, in practice this leads to higher 
noise than other configurations.  The regulator appearing in the circuit above omits this by directly sinking from the pass 
transistor.  This has clear limitations, as the sink capacity of the op amp and the gain of the pass transistor set the maximum
current the regulator can accommodate.  While this works well for the modest current requirements of Lilienfeld's Choir, if your 
requirements are higher it may be prudent to use a different design.

