# Software

* http://markwal.github.io/3dprinting/2015/04/27/slicers-gcode-and-x3g.html

## 3d Design

### Blender

* classic

### CloudCompare

* 3D point cloud (and triangular mesh) processing software
* comparisons, resampling, segmentation, ...

### FreeCAD

* parametric 3d design--good for engineering/mechanical design
* highly scriptable

### Makehuman

* reportedly open source, but no fedora package
* chara-design

### MatterControl

* it says free, open-source, all-in-one design, slice, print
* originally closed source, from MatterHackers in Irvine
* written in C#
* https://github.com/MatterHackers/MatterControl
* github shows actively maintained
* no fedora pkg?
* download button goes directly to binary .deb

### MeshLab

* cross-platform, GPL
* system for processing and editing unstructured 3D triangular meshes
  * typically 3D scans as input
  * cleaning, healing, inspecting
* initially created in 2005 as a course assignment at University of Pisa
* no undo?
* conversion between many different formats
* simple recipe to improve a low-poly model:
  * Filters / Remeshing / SubdivisionSurfaces:ButterflySubdivision

### MolView

* free web application
* molecules

### OpenFX

* reportedly open source, but no fedora package
* chara-design

### OpenSCAD

* two modes:
  * constructive solid geometry -- add, subtract
  * classic extrusion

### Scann3d (Android)

* photogrammetry--reconstruct 3d object form photos
* can save in STL format

### SolidPython

* more recent version of PyOpenSCAD--generate OpenSCAD from Python

### Wings3D

* "user friendly"
* good for artistic, not so good for engineering/mechanical design


## Slicing

### Cura

* originally written by David Braam (prior to hire at Ultimaker)
* C++, Python, and Qml
* not just slicing, can also drive printer
* open source, but 90% of features developed at ultimaker
* supports ultimaker 3d printers, but also many others
* lulzbot hacks on a fork for their printers, but plain cura also works
* for some reason, recent versions don't support direct USB connection
* LGPLv3
* [source code](https://github.com/Ultimaker/Cura)   very active as of 2018
  * 100 committers
* [wikipedia](https://en.wikipedia.org/wiki/Cura_(software))

### RepSnapper

* originally written by Kulitorum (Michael Holm of Copenhagan) in C++
* now maintained by Tim Schmidt
* "for controlling the RepRap 3D printer"
  * slicing as well as printer driving
* 3d model input formats: STL, OBJ, **X3D**, 3MF
* https://github.com/timschmidt/repsnapper  still maintained, not much traffic
* https://reprap.org/wiki/RepSnapper_Manual:Introduction
* https://github.com/timschmidt/repsnapper/blob/master/doc/manual.asciidoc

### Slic3r

* originally written by Alessandro Ranellucci in C++11
  * unit tests in Catch2--looking like some good quality software
* originally just slicing (tool path generation) but now does more
  * model conversion and repair
  * USB and Octoprint output, multiple queues
* 3d model input formats: STL, OBJ, **AMF**, 3MF
* GNU Affero General Public License
* [source code](https://github.com/slic3r/Slic3r)  very active as of 2018
  * 83 committers
* http://slic3r.org/
* command line or GUI
* prusa has a fork optimized for i3

### Skeinforge

* originally written by Enrique Perez in Python
* early G-code translator alternative to Bowyer's RepRap Host
* GNU Affero General Public License
* seems somewhat defunct (last commit ~2012) (webpage down)
* blog http://fabmetheus.blogspot.com/ ends ~2012

### SFACT

* improved version of Skeinforge, also in Python
* GNU Affero General Public License
* https://reprap.org/wiki/Sfact
* https://github.com/ahmetcemturan/SFACT
* only 55 commits from 3 devs from 2012 to 2013

### Makerware

* from MakerBot, "free" rather than open
* their linux install page is worse than adobe; various half-baked binary pkgs

### Non-open-source or non-linux-support

Not worth pursuing:

* CraftWare (slicer)
* Fusion 360 (design)
* IdeaMaker/Raise3d
* Meshmixer (STL editor)
* Netfabb (STL repair and slicer)
* Sculptris (design)
* Simplify3D (slicer)

### Features

* what does it do with a high-res mesh from zbrush?
  * do you have to manually decimate?
* can you add manual support structures
* how good are the automatically generated supports?
* what does it do if you try to print something with walls thinner than nozzle?
* can you postprocess gcode in user-selected language (slic3r supports this)
* how fast does it generate the slices, and how quickly they print
  * ideal visualization: an objective quality metric graph vs print speed
* octoprint integration?
* command-line mode available?

## Printer controller

### Franklin

* firmware for printer
* allows 3D printer to also be used for milling etc not just FDM

### Printrun

Contents:
* printcore (dumb G-code sender)
* pronsole (featured command line G-code sender)
* pronterface (featured G-code sender with graphical user interface)
* small collection of helpful scripts

### RepetierHost

* mono, exe, ini, ico files, and the like
* reportedly went from apache license to closed source

### ReplicatorG

* used by MakerBot, intended as general GCode based reprap / cnc controller
* contains a GUI top level interface
* can supply either GCode or STL inputs
* lots of java code
* no updates to git repo since 2012
* fork of arduino
