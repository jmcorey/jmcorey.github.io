# 3d printers

## Points of comparison

### Basic info

* cartesian or delta
  * delta can move faster--no need to move flat bed
  * delta tends to expand upwards--taller parts
  * delta better for round-ish prism shapes
  * cartesian is better for cube-ish shapes (rectangular base)
  * cartesian may have slightly better straight lines
* max print size

### Platform

* heated? max temperature?
* removable cover?
  * e.g. prusa replaceable textured spring steel plate?
* subject to warp?

### Nozzle and extruder assembly

* how smoothly is filament fed?
* what happens when filament breaks or runs out?
* extruder feed: geared? 
* boden feed or direct feed: boden not so good for flexible filaments
* nozzle with multiple feeds?  multiple nozzles?
* all metal tubing feeding hot end, not teflon, for high temp materials
* support multi-color?  multi-material?  both at same time?
* part cooler fan? how many, how good?
* max temperature?
* protection from overheating?
* alternate nozzles readily available?
* alternate extruder assemblies (e.g. multi-material) available?

### General mechanics and quality

* how sturdy is frame
* how tight are tolerances on guide beams
* auto-levelling?
* nozzle height probe: inductive? capacitive (avoid)? optical?
* 12v vs 24v power supply and parts (24 is better, but... 12v batteries?)
* quality of benchmark prints
* don't worry about layer height, it's deceptive
* any proprietary impediments to hacking on the hardware?

### Misc features

* noise level
* number of USB ports
* memory slot type (SD card or USB stick? or none?)
* wifi support? octoprint?
* LCD display and interaction that doesn't suck? touchscreen...
* ease of assembly (are there clear directions?)
* color-mixing hot end?
* support "ironing" top layer?
* "velocity painting"?

### Usability, compatibility, openness

* number of suppliers of filament... use whatever desired? price...
  * hopefully not a proprietary hitch where have to buy filament from them
* is both the hardware and software open?  in deed as well as word--compliance
* are the materials open and plainly communicated or hidden and proprietary?
* is it explicitly listed as working with linux?
  * all the downloadable items?
* compatible with which printer controller (e.g. franklin, printrun)
* is it listed in Cura supported printer list
  * https://github.com/Ultimaker/Cura/tree/master/resources/definitions
  * see also [wikipedia](https://en.wikipedia.org/wiki/Cura_(software))
* vendor website--coded well? which webserver? netcraft uptime?
  * are they buffoons in general?
* have a look at their github repo
  * insights / liveness
  * good commit and coding practices
  * long outstanding issues and/or pull requests?
  * random spot checks
* reputation re user support, and accessibility/friendliness of community
  * can see forums?  random spot checks
* "youtube test" -- how many youtube videos for that specific printer
* they and their printer have been around a while and are shipping
* google trends

## Notes on specific printers

https://www.reddit.com/r/3Dprinting/wiki/printerchart?v=39ae7030-5fed-11e7-af33-0e715cac0d02

### 3DTouch
* $3490
* no linux support?

### Afinia H-Series
* $1499
* pre-assembled
* no linux support? proprietary slicing and drivers

### Anet A8
* $150
* based on Prusa i3
* Shenzhen Anet Technology Co
* reportedly works with linux
* not listed on cura compatability list, but reportedly use as prusa i3
* print size max 220x220x240

### Anycubic Photon
* not FDM
* no Cura support, SLS chemicals

### BQ Haephestos 2
* Prusa clone, a bit pricy unless get good deal
* print size max 450x516x661

### Cetus Mk2
* slightly better quality than Prusa i3 mk3 according to youtube

### Creality CR10s
* not listed at reddit group?
* low price/volume ratio
* print size max 300x300x400, upgradeable to 500x500x500
* supported by Cura

### Cube and Cube Pro
* proprietary filament and software
* assembled

### Deezmaker Bukobot 8
* $1385
* kit
* open source, slic3r
* RepRap-based design, extendable in any axis
* print size 205x205x205
* PLA, ABS, PVA
* no SD card; get the X3 upgrade

### Delta Go
* tiny (max output 115x154), cheaply made

### Felix 1.0
* windows only
* kit

### Flashforge Creator
* not a kit--assembled
* clone of MakerBot Replicator 1
* dual extruder
* print size max 225x145x145
* 2.5 micron vertical res
* 11 micron horizontal res
* no apparent support in Cura
* plywood frame, partially enclosed

### Flashforge Creator Pro
* presumably derived from MakerBot
* their website goes on about open source, then brags about proprietary systems
* no apparent support in Cura

### FLSUN 3d Printer Delta Kossel Diy Kit
* delta frame
* https://reprap.org/wiki/Kossel says GPL
* designer Johann is in Seattle
* named after Albrecht Kossel, biochemist (Nobel for nucleic acid composition)
* supported by Cura
* amazon page says windows and mac... linux support?
* print size max φ180X 300 mm

### Fusion3 printers
* assembled
* proprietary extensions of standard technology; patents

### Lulzbot AO-100
* $1735
* open source
* assembled
* MendalMax design with good accessories

### LulzBot Mini Desktop 3D Printer
* $1250
* print size max 152x152x158
* USB 2.0, no SD card, no thumb drive jack, no wifi, no display
* ABS, PLA, Nylon, HIPS
* lulzbot 3d printers are FSF "respect your freedom" certified
* filament 2.85mm?

### LulzBot TAZ 6
* PROBABLY NOT (3mm filament, huge heated bed plate uses a lot of power)
* $2500
* pre-assembled
* lulzbot 3d printers are FSF "respect your freedom" certified
* designed for heavy duty usage in labs, workshops, maker spaces
* workhorse printer--consistent quality during heavy duty usage
* print size max 280x280x250
* USB, SDcard
* 3mm filament?
* can upgrade for dual extrusion

### Makerbot anything
* see makerware; also, is x3g also somewhat proprietary?
* AND http://www.tridimake.com/2014/06/do-not-buy-makerbot-3d-printers.html
* ALSO https://hackaday.com/2016/04/28/the-makerbot-obituary/

### MakerGear M2
* $1499
* kit
* open source
* RepRap Mendel/Pruse design with steel frame, big print volume, heated bed
* SD card

### MendelMaxPro (Trinity Labs)
* $1295
* kit
* open source
* RepRap Mendel-based with fast-heating 200W glass platform, 24v
* PVA, PLA, ABS
* lacking in documentation?
* dual extruders optional
* SD card optional?
* founder Ezra Zygmuntowicz
  * died 2014/11/26 (diabetes?)
  * rails developer
  * honest and hardworking, GED

### MiniMax (Maker's Tool Works)
* $699
* kit
* print size 205x230x205
* open source
* heated platform (borosilicate)
* automatic levelling
* E3D V6 hotend, 24v
* ABS, PLA, etc

### Monoprice Maker Select Mini v2
* assembled
* clone of some sort
* is this a Makerbot clone?  or a prusa clone?

### MZBot Voron
* kit
* open source
* print size 228x228x240
* heated platform, metal frame
* 80k google hits, not much on youtube

### Peopoly Moai
* not FDM
* cheap for an SLA printer, supported by Cura

### Printrbot line of printers
* printrbot is defunct
* assembled or kit
* kickstarter newcomer, extendable in any axis

### Prusa i3 Mk3
* check: go look at ColorPrint at PrusaPrinters.org... Linux?
* significant improvements over the earlier i3 models
  * parts made from PETG instead of ABS
* open source basis for lots of other printers
* Josef Prusa seems like an awesome character
  * core developer in the reprap project
  * goes to trade shows
  * makes youtube videos
  * big fish in Czech Republic
* good quality output
* very quiet (40 dB)
* removable spring steel base plate
* good controls
* smart adaptation
* super detailed assembly manual and 3d printing handbook
* compatible with Slic3r as well as Cura
* can be modified to use a color-mixing hot end
* no wifi connectivity--have to use a 3rd party product

### Rostock MAX v2
* $799
* 150k google hits, limited youtube content
* kit, extensive (soldering, silicon bonding, at least 35 hrs)
* calibration is tricky
* nozzle is only good for low temperature
* delta frame
* parts slightly wavy
* melamine plates (may strip, watch out for water)
* open source
* print size 375r140

### SeeMeCNC H1.1 (SeeMeCNC)
* $189 to $594
* kit only
* DIY oriented RepRap Huxley spinoff with injected molded parts, supports PVA
* maybe too much DIY? lots of hacking needed, probably won't work first time

### Solidoodle 2 (Solidoodle)
* $499 - $699
* assembled
* print size 150x150x150
* claims open source, supports linux
* Affordable, fully-enclosed original design
* no SD card or USB thumb drive
* you have to carefully remove the printer from the enclosure to change filament

### Tangibot
* these tact-less usurpers are the reason MakerBot went proprietary

### Tevo TornadoUS
* $329
* cartesian
* "95% assembled"
* print size 300x300x400
* looks like the Creality CR-10
* heated bed... poor quality?
* PLA, ABS, PETG, Wood, PVA, flexible
* 1.75mm nozzle

### Tiertime Up Mini 2
* $540
* is this a Makerbot clone?  If so, maybe too proprietary...
* assembled
* not listed on redit printer chart
* everything enclosed including spool
* built-in HEPA filter
* "good quality prints for beginners"
* "best summer 2018 3dPrinter for beginners"
* print size max 120x120x120k

### Titan 1
* PROBABLY NOT--low google count, not too much on youtube
* kit
* partially assembled
* open source
* print size 190x108x241

### Type A Series 1 (Type A Machines)
* $1400
* assembled
* print size 225x225x225
* claims opn source, works with linux
* Big 9-cubic-inch volume, plywood frame, high accuracy, supports PVA
* quick-release build platform

### Ultimaker (Ultimaker)
* $1661
* kit, incl. controller
* Fast, 150mm/sec. speed, 8.3-cubic-inch volume
* designed for PLA; no heated platform
* founded by Erik de Bruijn of the Netherlands
* SD card

### Ultimaker 2+
* $2499
* pre-assembled
* print size max 205x225x225
* USB 2.0, SD card, no thumb drive jack, no wifi
* ABS, PLA
* 20 micron highest res

### Ultimaker 3
* $3495
* print size max approx 200x200x200
* USB 2.0, no SD card, thumb drive jack, wifi
* ABS, PLA, Nylon
* 60 micron highest res
* 2 extruders

### Velleman K8200
* kit
* open source
* 92k matches
* heated bed, metal frame

### Velleman/Vertex Delta K8800 
* delta frame
* Cura supported
* says fully open source hardware and software (hw on github)
* "hybrid kit" -- "easy to build"
* marlin firmware, user upgradable
* PLA, ABS, TPU, PET, more
* print size max 225r200

### Wanhao Duplicator 4
* assembled
* copy of Makebot's Replicator 2
* no longer available on amazon
* open source
* heated bed
* dual extruder

### Wanhao i3Plus Duplicator
* mostly assembled (put main pieces together, connect wires)
* Prusa i3 clone

### XYZ Printing Junior
* proprietary
* have to buy filament from printer maker

### Zortrax M200
* closed/proprietary


