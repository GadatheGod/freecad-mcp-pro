---
name: f-implement
description: Implement a FreeCAD part/assembly/analysis based on a spec or set of tickets using the MCP server.
disable-model-invocation: true
---

# Implement — FreeCAD Edition

Implement FreeCAD geometry, assemblies, or FEM analysis based on a spec or ticket.

## Context

- FreeCAD MCP server running on localhost
- MCP tools: `create_document`, `create_object`, `edit_object`, `delete_object`, `execute_code`, `get_view`, `run_fem_analysis`
- FreeCAD docs: `/home/praveen/Desktop/Freecadmcp/docs/freecad/`
- Object reference: `/home/praveen/Desktop/Freecadmcp/.opencode/skills/freecad-objects/`

## Process

### 1. Read the ticket/spec

Extract the FreeCAD objects, dimensions, materials, and constraints to create.

### 2. Create the document

```
create_document(name="ProjectName")
```

### 3. Create objects in order

Follow the ticket's blocking edges. For each object:

```
create_object(
    doc_name="ProjectName",
    obj_name="ObjectName",
    obj_type="Part::Box",  # or Part::Cylinder, PartDesign::Pad, etc.
    obj_properties={
        "Length": 50,
        "Width": 30,
        "Height": 20,
        "ViewObject": {"ShapeColor": [0.8, 0.2, 0.2, 1.0]},
        "Placement": {"Base": {"x": 0, "y": 0, "z": 0}}
    }
)
```

### 4. Verify with screenshots

After creating each major object:
```
get_view(view_name="Isometric", focus_object="ObjectName")
```

### 5. Run FEM analysis (if applicable)

```
run_fem_analysis(
    doc_name="ProjectName",
    analysis_name="FEMAnalysis",
    timeout=600
)
```

### 6. Verify results

- Check max von Mises stress < material yield strength
- Check displacement within tolerance
- Get screenshot of stress visualization

### 7. Review the work

Use `/f-code-review` to verify:
- Standards: Objects use correct types and properties per FreeCAD docs
- Spec: All dimensions, features, and constraints match the ticket

### 8. Save the document

```
execute_code(code="FreeCAD.ActiveDocument.save('/path/to/file.FCStd')")
```

## FreeCAD Object Quick Reference

| obj_type | Key Properties |
|----------|---------------|
| Part::Box | Length, Width, Height |
| Part::Cylinder | Radius, Height |
| Part::Sphere | Radius |
| Part::Cone | Radius, Radius2, Height |
| Part::Torus | Radius, Radius2 |
| Draft::Circle | Radius |
| Draft::Rectangle | Length, Width |
| Draft::Polygon | Points, Radius |

## Common Workbenches

- **Part**: Basic primitives (Box, Cylinder, Sphere, Cone, Torus)
- **PartDesign**: Body-based modeling (Pad, Pocket, Revolution, Sweep)
- **Sketcher**: 2D sketches with constraints
- **FEM**: Analysis (ConstraintFixed, ConstraintForce, FemMeshGmsh)
- **TechDraw**: 2D drawings from 3D models

## Verification Checklist

- [ ] Document created
- [ ] All objects created with correct properties
- [ ] Screenshot confirms geometry matches spec
- [ ] FEM analysis completed (if applicable)
- [ ] Stress within limits (if FEM)
- [ ] File saved
