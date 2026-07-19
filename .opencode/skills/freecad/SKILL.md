# FreeCAD MCP Skill

Use this skill when working with FreeCAD via the MCP server. It provides access to FreeCAD documentation and best practices.

## Documentation Location
FreeCAD wiki documentation: `/home/praveen/Desktop/Freecadmcp/docs/freecad/`

## Available Workbenches & Tools

### Core Objects (Part Workbench)
- **Part::Box** - Create boxes (Length, Width, Height)
- **Part::Cylinder** - Create cylinders (Radius, Height)
- **Part::Sphere** - Create spheres (Radius)
- **Part::Cone** - Create cones (Radius, Radius2, Height)
- **Part::Torus** - Create torus (Radius, Radius2)
- **Part::Cylinder** - Create cylinders (Radius, Height)

### Draft Objects
- **Draft::Circle** - Create circles
- **Draft::Rectangle** - Create rectangles
- **Draft::Polygon** - Create polygons
- **Draft::Arc** - Create arcs

### FEM Analysis
- Create documents, objects, meshes
- Apply constraints (Fixed, Force, Pressure)
- Run CalculiX solver
- Get stress/displacement results

### Parts Library
- Insert pre-made parts from FreeCAD library

## Common Properties
- **ViewObject.ShapeColor** - RGB values [R, G, B, Alpha] (0-1 range)
- **Placement.Base** - Position {x, y, z}
- **Placement.Rotation** - {Axis: {x,y,z}, Angle: degrees}

## Workflow
1. `create_document` - Create new document
2. `create_object` - Create objects with correct obj_type and properties
3. `get_view` - Get screenshots to verify
4. `execute_code` - Run custom Python for complex operations
5. `run_fem_analysis` - For stress analysis

## Documentation Reference
Search `/home/praveen/Desktop/Freecadmcp/docs/freecad/` for:
- Workbench guides
- Part design tutorials
- FEM analysis documentation
- Python API reference
- Sketcher workbench
- TechDraw documentation

## Key Files
- `Part_Workbench.md` - Part workbench guide
- `FEM_Workbench.md` - FEM analysis guide
- `Draft_Workbench.md` - Draft objects guide
- `Sketcher_Workbench.md` - Sketcher guide
- `Python_Console_and_Macro.md` - Python scripting
