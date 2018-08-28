# Data formats relevant to 3D printing

## STL

* originally for stereo lithography
* backronyms "Standard Triangle Language" and "Standard Tessellation Language"
* [wikipedia](https://en.wikipedia.org/wiki/STL_(file_format))
* [old fabbers.com page](http://www.fabbers.com/tech/STL_Format)
* plain version is geometry only--no color, texture, or other attributes
* no scale or units
* objects defined as closed polyhedra--every edge part of exactly 2 triangles
* normal unit vectors for facets should point outwards
  * but may be left zero and filled later via RHR
  * SolidWorks comandeers the normal vector for shading effects
* ascii and binary flavors of the format

### Ascii version

F represents floating point number, sign-mantissa e.g. 1.8e-1; free whitespace
outside of words and numbers

```
( solid ( name )?
  ( facet normal F F F
    outer loop
    vertex F F F
    vertex F F F
    vertex F F F
    endloop
    endfacet
  ) *
) +
```

### Binary version

```
UINT8[80] -- informative string, does not start with "solid"
UINT32 -- NT -- number of triangles

( REAL32[3] -- normal vec
  REAL32[3] -- vertex 1
  REAL32[3] -- vertex 2
  REAL32[3] -- vertex 3
  UINT16 -- attribute byte count
) {N}
```

### Color hacks

* stored in binary format using attribute byte; cf wikipedia article

## X3D

* successor to VRML
* XML-based, but JSON version coming (Part 5 to ISO/IEC 19776)
* [spec](http://www.web3d.org/x3d/what-x3d)
  * seems to be currently viewable by public
* complicated
  * c.f. HAnimHumanoid
* good luck reading the official docs let alone implementing them

## 3MF

* "3D Manufacturing Format"
* additive manufacturing, ala STL, but supports materials, colors, etc
* published by consortium (Autodesk, Dassault, Netfabb, Microsoft, Stratasys)
* also complicated, maybe not quite as bad as X3D
* [spec](https://3mf.io/specification/)
* includes "content protection"

## 3DM

* rhino 3D object format
* ostensibly documented at opennurbs.org (w/ c# wrappers), win & mac libraries

## OBJ

* developed by Wavefront Technologies (for animation software)
* no units, but may specify scale in human readable comment line
* supports polygonal objects
* supports free-form objects
  * curves and surfaces
  * e.g. taylor and B-splines
* normally .obj is ascii, and .mod is binary
* material files (.mtl)
* significantly easier to produce a subset than to consume full spec
* [wikipedia](https://en.wikipedia.org/wiki/Wavefront_.obj_file)
* [good spec writeup](http://www.cs.utah.edu/~boulos/cs3505/obj_spec.pdf)

## PLY

* designed at stanford to store 3D scans
* relatively simple polygon lists, with color, transparency, textures
* influenced by .obj format, but added arbitrary property and element (group)
* different properties for front and back of polygon
* convert to/from via meshlab
* [good spec writeup](http://paulbourke.net/dataformats/ply/)
* [bunny and armadillo](http://graphics.stanford.edu/data/3Dscanrep/)

## GCode

* "numerical control" (of devices)--mainly CAM--typically tool motion
* both additive and subtractive manufacturing
* originally MIT Servomechanisms Laboratory (late 1950s)
* modern versions support high level macros
* "GCode" somewhat of a misnomer--all letters used
  * G (geometric/preparatory) somewhat standardardized
    * G0 -- rapid positioning
    * G1 -- linear interpolation, controlled rate
    * G3, G4 -- circular interpolation (CW and CCW)
    * G28 -- home
    * canned cycles like G81 (modal, so just specify new settings e.g. X2 X3 X4)
    * X, Y, Z -- coordinates
    * R -- arc radius
    * F -- speed
    * E -- feeder control
    * S -- spindle speed (i.e. for CNC milling)
  * M (misc/machine/milling control)
    * M05 -- stop the spindle
    * M07 -- coolant on (mist)
    * M08 -- coolant on (flood)
    * M09 -- coolant off
    * M117 -- display message
    * M104 -- set extruder temperature, return immediate
    * M109 -- set extruder temperature and wait
    * M140 -- set printing bed target temperature, return immediate
    * M190 -- wait for bed current temp to reach target temp
* [good list of commands](https://reprap.org/wiki/G-code)
* [wikipedia](https://en.wikipedia.org/wiki/G-code)

