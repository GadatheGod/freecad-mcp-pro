# FreeCAD MCP

[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/neka-nat-freecad-mcp-pro-badge.png)](https://mseep.ai/app/neka-nat-freecad-mcp-pro)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![FreeCAD](https://img.shields.io/badge/FreeCAD-1.1+-blue.svg)](https://freecad.org/)
[![Python](https://img.shields.io/badge/Python-3.12+-green.svg)](https://www.python.org/)

A Model Context Protocol (MCP) server that enables AI assistants (Claude Desktop, opencode, etc.) to control FreeCAD — a parametric 3D CAD modeler.

Create 3D parts, run FEM analysis, generate drawings, and more — all through natural language.

## ✨ Features

- **3D Modeling**: Create boxes, cylinders, spheres, cones, torus, and more
- **FEM Analysis**: Run CalculiX solver for stress/displacement analysis
- **Screenshot Capture**: Get view screenshots from any angle
- **Parts Library**: Insert pre-made parts from FreeCAD library
- **Custom Python**: Execute arbitrary Python code in FreeCAD
- **Remote Connections**: Control FreeCAD from another machine

## 📦 Installation

### 1. Install FreeCAD

```bash
# Ubuntu/Debian (via Flatpak - recommended)
flatpak install flathub org.freecad.FreeCAD -y

# Or download from https://freecad.org/download/
```

### 2. Install FreeCAD Addon

```bash
git clone https://github.com/GadatheGod/freecad-mcp-pro
cd freecad-mcp-pro

# Copy addon to FreeCAD Mod directory
cp -r addon/FreeCADMCP ~/.var/app/org.freecad.FreeCAD/config/FreeCAD/Mod/

# Restart FreeCAD
```

### 3. Install MCP Server

```bash
# Using uv (recommended)
uv sync

# Or using pip
pip install -e .
```

### 4. Configure Claude Desktop

Edit `~/.config/claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "freecad": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/freecad-mcp-pro",
        "run",
        "freecad-mcp-pro"
      ]
    }
  }
}
```

## 🚀 Usage

### Start FreeCAD RPC Server

1. Open FreeCAD
2. Switch to **MCP Addon** workbench
3. Click **Start RPC Server** in the toolbar

### Available Tools

| Tool | Description |
|------|-------------|
| `create_document` | Create a new FreeCAD document |
| `create_object` | Create 3D objects (boxes, cylinders, etc.) |
| `edit_object` | Modify object properties |
| `delete_object` | Delete an object |
| `execute_code` | Run Python code in FreeCAD |
| `get_view` | Get screenshots from any view |
| `get_objects` | List all objects in a document |
| `get_object` | Get details of a specific object |
| `run_fem_analysis` | Run FEM stress analysis |
| `insert_part_from_library` | Insert parts from FreeCAD library |

### Example: Create a Box

```json
{
  "doc_name": "MyPart",
  "obj_name": "BaseBox",
  "obj_type": "Part::Box",
  "obj_properties": {
    "Length": 50,
    "Width": 30,
    "Height": 20,
    "ViewObject": {"ShapeColor": [0.8, 0.2, 0.2, 1.0]}
  }
}
```

## 🛠️ Skills

This repository includes skills for working with FreeCAD via opencode:

### Core Skills
- **freecad** - General FreeCAD MCP usage and workflows
- **freecad-objects** - Quick reference for Part::Box, Part::Cylinder, etc.

### Matt Pocock Skills (FreeCAD-tailored)
- **f-grill-with-docs** - Interview to sharpen FreeCAD design plans, creates ADRs
- **f-to-spec** - Convert conversation into FreeCAD design spec
- **f-to-tickets** - Break design into FreeCAD implementation tickets
- **f-implement** - Create FreeCAD geometry/analysis based on tickets
- **f-code-review** - Review FreeCAD changes against standards and spec

## 📚 Documentation

- **FreeCAD Wiki**: 2,632 markdown files in `docs/freecad/`
- **Source**: Converted from [FreeCAD-documentation](https://github.com/FreeCAD/FreeCAD-documentation)
- **Addon Docs**: See `addon/FreeCADMCP/` for RPC server details

## 🏗️ Architecture

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│  AI Client  │────▶│  MCP Server  │────▶│  FreeCAD    │
│ (Claude,    │     │ (freecad-mcp-pro)│     │  (RPC)      │
│  opencode)  │     │              │     │             │
└─────────────┘     └──────────────┘     └─────────────┘
```

## 📄 License

MIT License. See [LICENSE](LICENSE) for details.

**Copyright (c) 2025 Praveen**

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## 🙏 Acknowledgments

### Original FreeCAD MCP
- **Author**: Shirokuma (k tanaka) / [@neka-nat](https://github.com/neka-nat)
- **Source**: [freecad-mcp-pro](https://github.com/neka-nat/freecad-mcp-pro)
- **License**: MIT

### FreeCAD Documentation
- **Source**: [FreeCAD-documentation](https://github.com/FreeCAD/FreeCAD-documentation)
- **Author**: FreeCAD Community
- **License**: BSD-3-Clause
- **Description**: Automatic markdown-based conversion of the FreeCAD wiki

### FreeCAD
- **Website**: https://freecad.org
- **License**: LGPL-2.1-or-later
- **Description**: Open source parametric 3D CAD modeler

### Matt Pocock Skills
- **Source**: [Matt Pocock Engineering Skills](https://github.com/mattpocock)
- **Skills adapted**: grill-with-docs, to-spec, to-tickets, implement, code-review

### Tools Used
- **[uv](https://github.com/astral-sh/uv)** - Python package manager
- **[MCP](https://github.com/modelcontextprotocol)** - Model Context Protocol
- **[FreeCAD](https://freecad.org)** - Parametric 3D CAD modeler

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📞 Support

- FreeCAD Wiki: https://wiki.freecad.org
- FreeCAD Forum: https://forum.freecad.org
- Issues: [GitHub Issues](https://github.com/GadatheGod/freecad-mcp-pro/issues)

## 📊 Stats

[![Contributors](https://img.shields.io/github/contributors/GadatheGod/freecad-mcp-pro)](https://github.com/GadatheGod/freecad-mcp-pro/graphs/contributors)
[![Stars](https://img.shields.io/github/stars/GadatheGod/freecad-mcp-pro)](https://github.com/GadatheGod/freecad-mcp-pro/stargazers)
[![Forks](https://img.shields.io/github/forks/GadatheGod/freecad-mcp-pro)](https://github.com/GadatheGod/freecad-mcp-pro/network/members)
