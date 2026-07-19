# FreeCAD Object Reference

Quick reference for creating FreeCAD objects via MCP.

## Part Primitives

### Part::Box
Properties: Length, Width, Height (mm)
Example: {"obj_type": "Part::Box", "obj_properties": {"Length": 50, "Width": 30, "Height": 20}}

### Part::Cylinder
Properties: Radius, Height (mm)
Example: {"obj_type": "Part::Cylinder", "obj_properties": {"Radius": 25, "Height": 40}}

### Part::Sphere
Properties: Radius (mm)
Example: {"obj_type": "Part::Sphere", "obj_properties": {"Radius": 20}}

### Part::Cone
Properties: Radius, Radius2, Height (mm)
Example: {"obj_type": "Part::Cone", "obj_properties": {"Radius": 25, "Radius2": 10, "Height": 40}}

### Part::Torus
Properties: Radius, Radius2 (mm)
Example: {"obj_type": "Part::Torus", "obj_properties": {"Radius": 30, "Radius2": 10}}

## Draft Objects

### Draft::Circle
Properties: Radius
Example: {"obj_type": "Draft::Circle", "obj_properties": {"Radius": 25}}

### Draft::Rectangle
Properties: Length, Width
Example: {"obj_type": "Draft::Rectangle", "obj_properties": {"Length": 50, "Width": 30}}

### Draft::Polygon
Properties: Points, Radius
Example: {"obj_type": "Draft::Polygon", "obj_properties": {"Points": 6, "Radius": 25}}

## Placement Examples
{"Placement": {"Base": {"x": 0, "y": 0, "z": 0}, "Rotation": {"Axis": {"x": 0, "y": 0, "z": 1}, "Angle": 45}}}

## Color Examples
{"ViewObject": {"ShapeColor": [0.8, 0.2, 0.2, 1.0]}}
