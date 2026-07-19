---
name: f-grill-with-docs
description: A relentless interview to sharpen a FreeCAD design plan, which also creates ADRs and glossary as we go. Uses FreeCAD documentation and MCP capabilities.
disable-model-invocation: true
---

# Grill With Docs — FreeCAD Edition

Run a `/grilling` session focused on FreeCAD design, using the `/domain-modeling` skill and FreeCAD documentation.

## Context

This workspace has:
- FreeCAD MCP server at `/home/praveen/Desktop/Freecadmcp`
- 2,632 FreeCAD wiki docs at `/home/praveen/Desktop/Freecadmcp/docs/freecad/`
- FreeCAD skills at `/home/praveen/Desktop/Freecadmcp/.opencode/skills/freecad/`
- FreeCAD object reference at `/home/praveen/Desktop/Freecadmcp/.opencode/skills/freecad-objects/`

## Process

### 1. Load FreeCAD context

Read the user's design idea. Search the FreeCAD docs for relevant workbenches, object types, and constraints.

### 2. Grill the design

Ask relentless questions about:
- **Geometry**: Dimensions, tolerances, material properties, load cases
- **Workbenches**: Which workbench (Part, PartDesign, Sketcher, FEM, TechDraw)?
- **Constraints**: Mating constraints, degrees of freedom, assembly hierarchy
- **FEM**: Boundary conditions, mesh size, expected stress, safety factors
- **Manufacturing**: Tolerances, surfaces, features (fillets, chamfers, holes)

### 3. Create ADRs

Write Architecture Decision Records to `/home/praveen/Desktop/Freecadmcp/.scratch/adrs/` for each design decision:

```markdown
# ADR-NNN: <Decision Title>

**Context**: What was the situation?
**Decision**: What did we decide?
**Consequences**: What are the trade-offs?
**FreeCAD Implementation**: How will this be built (objects, workbench, constraints)?
```

### 4. Update Glossary

Maintain `/home/praveen/Desktop/Freecadmcp/.scratch/glossary.md` with FreeCAD-specific terms:
- PartDesign terms (Pad, Pocket, Revolution, Sweep, etc.)
- FEM terms (ConstraintFixed, ConstraintForce, Mesh, Solver)
- Assembly terms (Joint, DegreeOfFreedom, Mating)

### 5. Produce spec or tickets

Use `/f-to-spec` or `/f-to-tickets` to formalize the design.
