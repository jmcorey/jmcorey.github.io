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

* system for processing and editing unstructured 3D triangular meshes
  * typically 3D scans as input
  * cleaning, healing, inspecting

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

* ultimaker 3d printers, but supports others
* can drive printer

### RepSnapper

* "for controlling the RepRap 3D printer"
* can convert STL to GCode

### Slic3r

### SFACT

* improved version of Skeinforge
* python scripts

### Skeinforge

### Makerware?

### Non-open-source or non-linux-support

I.e. not worth pursuing:

* CraftWare (slicer)
* Fusion 360 (design)
* IdeaMaker/Raise3d
* Makerbot/Makerware?
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
* how fast does it generate the slices, vs how quickly they print
* octoprint integration?
* command-line mode available?

## Printer controller

### Franklin

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
