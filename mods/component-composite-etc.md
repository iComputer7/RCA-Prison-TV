# Mods

## Misc. Important Notes

* ***My instructions are not perfect! I do not know if there are multiple board revisions with different layouts! Sometimes I forget to write stuff down!***
* The silkscreen on this board is awful. Some labels are incredibly ambiguous. 
* BC847A is a SOT-23 surface mount NPN transistor
* All SMD passives are imperial 0603 unless noted otherwise
* The SMD diodes are kind of a crapshoot but seem to mostly be SOD-323?
* THT caps are polarized electrolytic unless specified otherwise. There are no specific ESR requirements.
* Some parts on the list may already be populated from the factory. If they are, double-check that they're the correct value. Replace them if they're not.
* The PCB has some sort of conformal coating on the bottom side that makes soldering a bit of a pain. Use plenty of flux. Prepare for an unpleasant chemical smell when cleaning with IPA.

---

## Service menu tweaks

TODO: double check the values I set, I think I changed them on my TV and forgot to write the new values down

Some settings need to be set before TV recognizes the new inputs.

Go into service menu, on page FAC07 and change these values:

* OPT = 3F (for front composite input)
* OPTM1 = 8F (for rear component input and possibly rear composite input)

---

## DTV tuner connections from the factory

Useful if you're content with removing the DTV tuner to get component video without having to do anything fancy

* JP901: TV tuner Pb
* JP904: TV tuner Y
* JP902: TV tuner Pr
* JP905: TV tuner left audio

---

## Misc Jumper Wires

These are the jumper wires I had to add back. Again, your board may be different. Follow the traces and make sure things are connected to where they need to be. J seems to refer to a through-hole jumper wire while JP seems to be a SMD 0 ohm resistor but not everything follows that rule.

* J204
* JP910
* J931
* J917
* J903
* JP915
* J902
* J932
* J907
* J906
* J904
* J922
* J905
* J912

---

## Composite input

This is the front composite input, which is mounted on a separate PCB that has a few passives on it (not listed here. TODO)

Refdes | Type | Location | Part
--- | --- | --- | ---
Q907 | SMD | col KK row 3+4 | BC847A (NPN)
C907 | THT | col LL row 3+4, next to Q907 | 10uF 16v
C909 | THT | next to jungle IC | 1uF 16v, already populated with 0.1uF ceramic cap
C917 | SMD | next to Q907 | 0.01uF
C921 | THT | next to C907 | 100uF 16v
R910 | SMD | col KK row 3, near D425 | 82 ohm
R912 | SMD | near Q907 | 10k ohm
R924 | SMD | col KK row 8, near C909 | 470 ohm, already populated with 0 ohm resistor
JP903 | THT | in between analog tuner and C921 | jumper wire
D910 | SMD | TODO | zener TVS diode? "5V1"

---

## Audio switch circuit

Schematic calls for a Toshiba TC4052 specifically for whatever reason but I used a generic 74HC4052 and it works fine.

Refdes | Type | Location | Part
--- | --- | --- | ---
IC901 | SMD | todo | 4052 analog multiplexer, SOIC-16/SOP-16 package
R007 | SMD | col MM row 11 above silk screen notch for jungle chip | 10k ohm, already populated with 10k ohm resistor
R928 | SMD | col KK row 2 near C953 | 47k ohm
R931 | SMD | col KK row 2 right next to R928 | 47k ohm
R940 | SMD | col KK row 5 | 4.7k ohm
R941 | SMD | col KK row 5 | 10k ohm
R944 | SMD | col KK row 4 next to C907 and C917 | 10k ohm
R945 | SMD | col KK row 5 | 10k ohm
R953 | SMD | col KK row 3 next to C921 | 1k ohm
C904 | THT | col NN row 4 next to IC902 | 0.01uF
C905 | THT | right next to analog tuner | 10uF 16v
C918 | SMD | col MM row 2+3 in between IC901 and IC902 | 0.01uF
C919 | THT | next to J903 | 10uF 16v
C952 | THT | next to P904 | 10uF 16v
Q903 | SMD | next to R941, R945, R940, Q901 | BC847A (NPN)
D914? | SMD | TODO | zener TVS diode? "12V"
Q901 | SMD | in between Q901 and Q907 | BC847 (NPN)

---

## Component Video + Video 2

Remove these jumpers if populated: (**TODO: double check this is correct**)

* JP901 (SMD resistor)
* JP902 (SMD resistor)
* JP905 (SMD resistor)

Refdes | Type | Location | Part
--- | --- | --- | ---
IC902 | SMD | col MM row 3 | PI5V330, SSOP-16 package
C901 | THT | todo | 10uF 16v
C902 | THT | todo | 10uF 16v
C906 | SMD | next to D901 | 2.2uF ceramic
C909 | THT | by jungle chip | 1uF, already populated from composite mod
C910 | SMD | right next to jungle chip pins | 0.1uF, already populated
C912 | SMD | right next to jungle chip pins | 0.1uF, already populated
C920 | THT | by the analog tuner | 100uF 16v
C953 | THT | next to P903 | 10uF 16v
D901 | SMD | col NN row 1 | 5.1v TVS diode
D903 | SMD | col MM row 1 | 5.1v TVS diode
D904 | SMD | col LL row 1 | 5.1v TVS diode
D906 | SMD | next to D904 | 12v TVS diode
D907 | SMD | col LL row 1 | 5.1v TVS diode
D909 | SMD | col KK row 1 | 12v TVS diode
D915? | SMD | ??? | 12v TVS diode
R901 | SMD | col KK row 1 | 1k ohm resistor
R902 | SMD | col LL row 1 | 1k ohm resistor
R903 | SMD | col MM row 1 | 82 ohm resistor
R904 | SMD | col NN row 1 | 82 ohm resistor
R905 | SMD | col MM row 2 | 82 ohm resistor
R906 | SMD | col LL row 2 | 82 ohm resistor
R915 | SMD | right next to jungle chip pins | 100 ohm resistor, already populated
R916 | SMD | right next to jungle chip pins | 100 ohm resistor, already populated
R926 | SMD | next to R926 | 47k ohm resistor
R927 | SMD | col KK row 2 | 47k ohm resistor
R930 | SMD | col MM row 3, by IC901 | 47k ohm resistor
R932 | SMD | col MM row 3, by IC901 | 47k ohm resistor
R936 | SMD | col MM row 2 | 47k ohm resistor
R937 | SMD | next to IC901 | 47k ohm resistor
R942 | SMD | col NN row 3 | 10k ohm resistor
R943 | THT | by analog tuner and L891 | 10k ohm resistor
R954 | SMD | next to C953, col KK row 2 | 1k ohm resistor
JP910 | TODO | by C907 next to the analog tuner | *TODO: forgot if this is a 0 ohm SMD or a jumper wire*
JP914 | THT | next to R219 | jumper wire, white
J931 | THT | TODO | jumper wire
Q902 | SMD | next to IC902 | BC847 NPN transistor
