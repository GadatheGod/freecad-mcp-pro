---
name: f-to-tickets
description: Break a FreeCAD design spec into tracer-bullet tickets, each declaring blocking edges.
disable-model-invocation: true
---

# To Tickets — FreeCAD Edition

Break a FreeCAD design spec into tickets — each ticket creates one verifiable part/feature/analysis.

## Context

- FreeCAD MCP at `/home/praveen/Desktop/Freecadmcp`
- Docs at `/home/praveen/Desktop/Freecadmcp/docs/freecad/`

## Process

### 1. Read the spec

Extract all parts, features, constraints, FEM setups, and drawings from the spec.

### 2. Break into vertical slices

Each ticket should create one complete, verifiable FreeCAD object or set of objects:

**Ticket examples:**
- `01-create-base-body` — Create the base Part::Box or PartDesign body
- `02-add-sketch-and-pad` — Create sketch, apply Pad feature
- `03-add-holes` — Create circular holes with Draft::Circle or Part::Cylinder cutouts
- `04-apply-fem-constraints` — Add ConstraintFixed, ConstraintForce
- `05-generate-mesh` — Create FemMeshGmsh with proper size
- `06-run-fem-analysis` — Run CalculiX solver, verify results
- `07-create-drawing` — Generate TechDraw sheet with views

### 3. Define blocking edges

```
01-create-base-body → None
02-add-sketch → 01
03-add-features → 02
04-fem-constraints → 03
05-mesh → 04
06-fem-analysis → 05
07-drawing → 03
```

### 4. Quiz the user

Present the breakdown. Ask:
- Does the granularity feel right?
- Are the blocking edges correct?
- Should any tickets be merged or split?

### 5. Publish tickets

Write to `/home/praveen/Desktop/Freecadmcp/.scratch/<feature-slug>/issues/<NN>-<slug>.md`:

<ticket-template>

# <NN> — <Ticket title>

**What to build:** Create a FreeCAD object/feature that produces visible geometry.

**Blocked by:** the numbers/titles of tickets that gate this one.

**FreeCAD MCP Commands:**
- `create_document` if needed
- `create_object` with obj_type, obj_properties
- `execute_code` for complex operations
- `get_view` to verify

**Acceptance criteria:**
- [ ] Object created in FreeCAD
- [ ] Screenshot confirms correct geometry
- [ ] Dimensions match spec
- [ ] No errors in FreeCAD console

</ticket-template>
