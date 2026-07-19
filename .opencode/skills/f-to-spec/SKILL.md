---
name: f-to-spec
description: Turn a FreeCAD design conversation into a spec — no interview, just synthesis of what you've already discussed.
disable-model-invocation: true
---

# To Spec — FreeCAD Edition

Turn the current conversation about a FreeCAD design into a spec. Do NOT interview the user — synthesize what you already know.

## Context

- FreeCAD docs: `/home/praveen/Desktop/Freecadmcp/docs/freecad/`
- Object reference: `/home/praveen/Desktop/Freecadmcp/.opencode/skills/freecad-objects/`
- ADRs: `/home/praveen/Desktop/Freecadmcp/.scratch/adrs/` (if any)

## Process

### 1. Read conversation context

Extract all design decisions, dimensions, materials, constraints, and workbenches discussed.

### 2. Search FreeCAD docs

Look up relevant documentation for the chosen workbench, object types, and FEM setup.

### 3. Write the spec using this template:

<spec-template>

## Part Name

The name and purpose of the FreeCAD part/assembly.

## Design Intent

From the user's perspective — what this part does, how it fits into a larger assembly, what it supports.

## Dimensions & Tolerances

All key dimensions with units. Tolerances where relevant.

## Workbench & Objects

| Layer | Workbench | Object Type | Key Properties |
|-------|-----------|-------------|----------------|
| Base | PartDesign/Part | Part::Box/Part::Cylinder etc. | Length, Width, Height, Radius |
| Features | PartDesign | Pad/Pocket/Revolution etc. | Sketch references, depth |
| FEM | FEM | ConstraintFixed, ConstraintForce, FemMeshGmsh | References, values |

## Material

Material name, density, Young's modulus, Poisson's ratio.

## FEM Setup (if applicable)

- Mesh: CharacteristicLengthMax/Min
- Constraints: Fixed faces, force locations/magnitudes
- Expected results: Max stress, displacement

## Assembly Structure (if applicable)

- Parts involved
- Mating constraints between parts
- Degrees of freedom

## FreeCAD File Structure

```
Document: <name>
├── Body: <name>
│   ├── Sketch: <name>
│   ├── Pad: <name>
│   ├── Pocket: <name>
│   └── FEM:
│       ├── ConstraintFixed
│       ├── ConstraintForce
│       └── FemMeshGmsh
```

## Out of Scope

Features or analyses not included in this spec.

## Further Notes

Any additional context, references, or assumptions.

</spec-template>
