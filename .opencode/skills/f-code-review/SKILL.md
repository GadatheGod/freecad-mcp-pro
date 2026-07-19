---
name: f-code-review
description: Review FreeCAD MCP changes along two axes — Standards (correct object types, properties per FreeCAD docs) and Spec (matches the design spec/ticket).
disable-model-invocation: true
---

# Code Review — FreeCAD Edition

Review FreeCAD geometry creation, FEM setup, or assembly changes along two axes:

- **Standards** — Do objects use correct types/properties per FreeCAD documentation?
- **Spec** — Does the geometry match the design spec or ticket?

## Context

- FreeCAD docs: `/home/praveen/Desktop/Freecadmcp/docs/freecad/`
- Object reference: `/home/praveen/Desktop/Freecadmcp/.opencode/skills/freecad-objects/`
- Spec/ticket: Provided by user or found in `.scratch/`

## Process

### 1. Identify what was changed

Get the list of FreeCAD objects created/modified:
```
get_objects(doc_name="ProjectName")
```

### 2. Standards Review (parallel sub-agent)

Check against FreeCAD documentation:

**Object Type Standards:**
- Part::Box uses Length/Width/Height (not XSize/YSize/ZSize)
- Part::Cylinder uses Radius/Height (not Diameter)
- Part::Cone uses Radius/Radius2/Height
- Part::Torus uses Radius/MainRadius/MinorRadius
- Draft::Circle uses Radius (not Diameter)
- ViewObject.ShapeColor is [R,G,B,Alpha] with 0-1 range
- Placement.Base uses {x,y,z} not {X,Y,Z}

**FEM Standards:**
- ConstraintFixed references valid faces
- ConstraintForce references valid faces with correct direction
- FemMeshGmsh references valid shape
- CharacteristicLengthMax/Min are reasonable for part size

**Common Errors to Flag:**
- Wrong property names (e.g., "Diameter" instead of "Radius")
- Invalid face references (Face1 vs Face.1)
- Missing required properties
- Incorrect data types (string vs number)

### 3. Spec Review (parallel sub-agent)

Check against the design spec:
- All dimensions match spec values
- All features are present (holes, fillets, chamfers)
- Material properties match spec
- FEM constraints match spec (location, magnitude)
- Assembly hierarchy matches spec

### 4. Aggregate

Present findings under `## Standards` and `## Spec`:

**Standards findings:**
- Object type errors
- Property name/value errors
- FEM constraint errors

**Spec findings:**
- Missing features
- Dimension mismatches
- Missing constraints

End with summary: total findings per axis, worst issue per axis.
