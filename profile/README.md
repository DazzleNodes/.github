# DazzleNodes

**ComfyUI Custom Nodes for AI Image Generation**

[![GitHub](https://img.shields.io/badge/GitHub-DazzleNodes-blue?logo=github)](https://github.com/DazzleNodes)
[![ComfyUI Registry](https://img.shields.io/badge/ComfyUI-Registry-green.svg)](https://registry.comfy.org/publishers/djdarcy/nodes/comfyui-dazzlenodes)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Sponsor](https://img.shields.io/badge/Sponsor-GitHub-ea4aaa?logo=github-sponsors)](https://github.com/sponsors/djdarcy)

> Custom nodes for ComfyUI that solve common workflow pain points. Smart resolution handling, automatic mask fitting, and productivity enhancements for AI image generation.

---

## What is DazzleNodes?

**DazzleNodes** ([main project](https://github.com/DazzleNodes/DazzleNodes)) is a curated collection of ComfyUI custom nodes focused on making common image generation workflows easier and more efficient. Each node solves a real workflow problem - from calculating aspect ratios to automatically resizing masks.

---

## Featured Nodes

### 🌟 Smart Resolution Calculator

**[GitHub](https://github.com/djdarcy/ComfyUI-Smart-Resolution-Calc) | [ComfyUI Registry](https://registry.comfy.org/publishers/djdarcy/nodes/comfyui-smart-resolution-calc)**

Flexible resolution and latent generation with intelligent aspect ratio handling. Calculate missing dimensions, preview results, and generate latents - all in one node.

---

## Installation

### Method 1: ComfyUI Manager (Recommended)

```
Search for "DazzleNodes" in ComfyUI Manager and click Install
```

All nodes install as a single package. Restart ComfyUI after installation.

### Method 2: ComfyUI Registry (CLI)

```bash
comfy set-default C:/ComfyUI
comfy node install comfyui-dazzlenodes
```

To see what's installed
```bash
cd C:/ComfyUI
venv/Scripts/python.exe custom_nodes/ComfyUI-Manager/cm-cli.py show installed
```

### Method 3: Git Clone with Submodules

```bash
cd ComfyUI/custom_nodes
git clone --recursive https://github.com/DazzleNodes/DazzleNodes.git
```

**⚠️ Important:** The `--recursive` flag is required to download all node submodules!

### Method 4: Manual Submodule Setup

```bash
cd ComfyUI/custom_nodes
git clone https://github.com/DazzleNodes/DazzleNodes.git
cd DazzleNodes
git submodule update --init --recursive
```

---

## Usage

After installation, restart ComfyUI. All nodes will appear under the **DazzleNodes** category in the node menu.

### Workflow Files

See `examples/` directory in the [DazzleNodes repository](https://github.com/DazzleNodes/DazzleNodes) for complete workflow JSON files demonstrating node usage.

---

## Architecture

DazzleNodes uses **git submodules** to maintain clean, independent histories for each node:

```
DazzleNodes/
├── __init__.py                    # Aggregator that imports all nodes
├── nodes/                         # Node submodules
│   ├── smart-resolution-calc/     # Submodule → separate git repo
│   └── fit-mask-to-image/         # Submodule → separate git repo
└── examples/                      # Collection-level examples
```

### Why Submodules?

- **Independent development** - Each node maintains its own git history
- **Selective installation** - Users can install individual nodes if desired
- **Version locking** - Prevents unexpected breakage from updates
- **Clean extraction** - Nodes can move to standalone repos easily

### Individual Node Repositories

Each node is independently developed:

- **Smart Resolution Calculator**: [GitHub Repo](https://github.com/djdarcy/ComfyUI-Smart-Resolution-Calc)
- **Fit Mask to Image**: [GitHub Repo](https://github.com/DazzleNodes/fit-mask-to-image)

---

## Updating

### Update All Nodes

```bash
cd ComfyUI/custom_nodes/DazzleNodes
git pull
git submodule update --remote
```

### Update Individual Node

```bash
cd ComfyUI/custom_nodes/DazzleNodes/nodes/smart-resolution-calc
git pull
```

---

## Node Development Roadmap

### Current Nodes (Available Now)

- ✅ **Smart Resolution Calculator** - Published on ComfyUI Registry
- ✅ **Fit Mask to Image** - Available in DazzleNodes package

### Planned Nodes

*Node development prioritized based on community feedback and sponsorship support.*

---

## Troubleshooting

### Nodes Not Loading

**Symptom:** ComfyUI says "No nodes loaded!" or specific nodes are missing.

**Solution:** Initialize submodules:
```bash
cd ComfyUI/custom_nodes/DazzleNodes
git submodule update --init --recursive
```

### Empty Node Directories

**Symptom:** `nodes/` subdirectories exist but are empty.

**Solution:** You cloned without `--recursive` flag. Run:
```bash
cd ComfyUI/custom_nodes/DazzleNodes
git submodule update --init --recursive
```

### Import Errors

**Symptom:** Python import errors in console.

**Solution:**
1. Verify submodules are initialized: `git submodule status`
2. Check each node's `__init__.py` exists
3. Restart ComfyUI completely (not just refresh)
4. Check ComfyUI console for detailed error messages

### Dimension Mismatch Errors

**Symptom:** "RuntimeError: The size of tensor a (X) must match the size of tensor b (Y)"

**Solution:** Use **Fit Mask to Image** node before inpainting operations. This is exactly the problem it solves.

---

## Contributing

Contributions welcome! Each node has its own repository and contribution guidelines.

### Proposing New Nodes

1. Open an issue describing the workflow problem
2. Explain current workaround (how many nodes it takes now)
3. Describe proposed solution (how one node would solve it)
4. Provide example use cases
5. Discuss implementation approach

**Good node proposals solve real workflow pain points**, like:
- "I need 8 nodes to do X, could we make it 1 node?"
- "This error happens constantly in Y workflow, can we prevent it?"
- "I repeat this 5-node pattern in every workflow, can we simplify it?"

### Development Guidelines

- **Test thoroughly** - Nodes should work in various workflows
- **Preview when possible** - Visual feedback improves UX
- **Sensible defaults** - Common use cases should "just work"
- **Document use cases** - Help users understand when to use each node
- **Backwards compatibility** - Don't break existing workflows

---

## Community

- **Discussions**: [GitHub Discussions](https://github.com/DazzleNodes/discussions)
- **Issues**: [Node-specific issue trackers](https://github.com/DazzleNodes)
- **ComfyUI Community**: [Official ComfyUI Discussions](https://github.com/comfyanonymous/ComfyUI/discussions)
- **Workflow Sharing**: Post your DazzleNodes workflows in discussions!

---

## Related Projects

**DazzleNodes** is part of the [DazzleProj](https://github.com/DazzleProj) ecosystem.

### Part of DazzleProj Ecosystem

- **[DazzleProj](https://github.com/DazzleProj)** - Ecosystem coordination
- **[DazzleLib](https://github.com/DazzleLib)** - Foundation libraries
- **[DazzleTools](https://github.com/DazzleTools)** - Command-line tools
- **[DazzleNodes](https://github.com/DazzleNodes)** - ComfyUI custom nodes ← *You are here*
- **[DazzleAI](https://github.com/DazzleAI)** - AI development tools

### Related AI Projects

- **[ComfyUI](https://github.com/comfyanonymous/ComfyUI)** - The powerful node-based UI for Stable Diffusion
- **[ComfyUI-Manager](https://github.com/ltdrdata/ComfyUI-Manager)** - Essential tool for managing custom nodes
- **[DazzleAI](https://github.com/DazzleAI)** - More AI tools including ComfyUI Triton installer

---

## Technical Details

### Dependencies

DazzleNodes has minimal dependencies:
- ComfyUI (obviously)
- Python 3.10+ (for ComfyUI compatibility)
- Standard ComfyUI node dependencies (torch, PIL, numpy)

Some nodes may use [DazzleLib](https://github.com/DazzleLib) libraries for file operations, but this is optional.

---

## Acknowledgments

Built with inspiration from:
- The ComfyUI community's incredible workflows
- Real workflow pain points experienced during thousands of generations
- Feedback from artists, developers, and content creators
- The open-source AI image generation community

Special thanks to [comfyanonymous](https://github.com/comfyanonymous) for creating ComfyUI.

---

## Contact

- **GitHub**: [@djdarcy](https://github.com/djdarcy)
- **Issues**: Use node-specific issue trackers
- **Discussions**: [GitHub Discussions](https://github.com/DazzleNodes/discussions)
- **Sponsorship**: [GitHub Sponsors](https://github.com/sponsors/djdarcy)
- **Website**: [DazzleProj.com](https://dazzleproj.com) *(coming soon)*

---

**Built by someone who got tired of rebuilding workflows** 🎨
