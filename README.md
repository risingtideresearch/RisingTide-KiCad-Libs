# Rising Tide Research Foundation KiCad Libraries

This repository is a collection of KiCad schematic symbols and part footprints for components used on RTRF's electrical designs. 
The libraries contain everything down to passives, power symbols, and silkscreen logos. All 3D models and datasheets are embedded. This serves to prevent redundant work, keep our part selections consistent across designs, and maintain portability of our source files.

These libraries were created in KiCad 9.0 and, as such, may not be compatible with earlier versions. 

## Naming, Structure and Style

### Symbols

#### Naming
Symbols are generally named as follows: `{Device Type} {Mfr Part#} {Top line specs}` but there are exceptions based on the part type and relevant specs.

In the case of common components such as passives, no datasheets are part numbers are specified as these parts are completely fungible so long as they are within spec. 
- A typical capacitor may be named `0.1uF 0402 16V 10%` with the voltage and tolerance specified. 
- A resistor may be named `4.7K 0402`. No power rating is specified as this will trend with value and package size. If a particular tolerance or power rating is required by a design, it should be noted on the relevant instance of the symbol.     
- A diode may be named `D Schottky 0.5A/20V/0.47V` with the top line specs `IMax/VMax/Vdrop`. Diodes are prefixed with "D" to differentiate them from other parts because they share a library with other discrete semiconductors.

Other parts are named using a descriptive prefix (LDO, OptoIsolator, LED, CAN XCVR, etc.) followed by the manufacturer's part number and any relevant top line specs (e.g. regulated voltage for an LDO or color for an LED)

Normal spaces are used between words for the sake of readability.

#### Style
Symbol bodies are drawn with a line weight of 0.254mm in KiCad's default symbol color (dark red) and are filled with the background color. 

Pins have a length of 2.54 with a text size of 1.27. 

Pins should be grouped in whatever way makes layout of the part most readable. In some cases this means grouping pins by function, in others it may mean grouping pins by physical layout. There is no obligation for a symbol to represent its associated footprint, readability of the schematic is paramount. As a rule of thumb, GND, VSS, AGND, etc. should be located near the bottom of the symbol so that ground symbols can be oriented downward while crossing the least number of signals. Similarly, VCC, VIO, etc. as well as pins that are likely to be pulled up to them such as RST, EN, etc. should be located near the top of the symbol. Wherever two parts have complementary pins (RX/TX, CANH/CANL, USB+/USB-) it is acceptable to position the pins on both symbols to avoid having to cross the pair. By default, part prefixes are placed above the top left corner of the symbol and part values are placed below the bottom left corner This is arbitrary as these can be moved after placement on the schematic. 

### Footprints

#### Naming 
Footprints are named as generically as possible unless they pertain specifically to a manufacturer's nonstandard layout.

Where possible, generic package outline names are used (e.g. SOIC, SOP, TSSOP, SMA, TO) 

Package outline dimensions, part heights, and conductor pitch are appended where relevant.

Footprint names are written in ["Snake_case"](https://en.wikipedia.org/wiki/Snake_case) as a byproduct of many footprints being script-generated.

#### Style
Silkscreen should indicate part polarity in whatever way is most common for each component type (pin 1 dot for ICs, cathode line for diodes, etc.) as well as component outlines to aid hand placement. Part numbers and values are placed on the `F.Fab` layer and should not appear in the silkscreen. 

Courtyards, margins, paste aperture, and mask keepouts should be defined in their respective layers. 

Round holes smaller than 6mm diameter should be defined as pads with the "NPTH, Mechanical" property so that they are added to the drill list. Larger holes and irregular slots should be drawn on the `Edge.Cuts` layer using a line weight of 0.05. 

## Contents
- /Footprints - PCB footprints
- /Symbols - Schematic symbols
