# DazzleNodes

**ComfyUI Custom Nodes for AI Image Generation**

[![GitHub](https://img.shields.io/badge/GitHub-DazzleNodes-blue?logo=github)](https://github.com/DazzleNodes)
[![ComfyUI Registry](https://img.shields.io/badge/ComfyUI-Registry-green.svg)](https://registry.comfy.org/publishers/djdarcy/nodes/comfyui-dazzlenodes)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Sponsor](https://img.shields.io/badge/Sponsor-GitHub-ea4aaa?logo=github-sponsors)](https://github.com/sponsors/djdarcy)

> Custom nodes for ComfyUI that solve common workflow pain points. Smart resolution handling, automatic mask fitting, and productivity enhancements for AI image generation.

---

## What is DazzleNodes?

**DazzleNodes** is a curated collection of ComfyUI custom nodes focused on making common image generation workflows easier and more efficient. Each node solves a real workflow problem - from calculating aspect ratios to automatically resizing masks.

### Philosophy

- **Workflow Solutions** - Nodes solve actual pain points, not theoretical features
- **Replace Complexity** - One node replaces multi-node workarounds
- **Preview Everything** - Visual feedback before committing to generation
- **Smart Defaults** - Sensible starting values for common use cases
- **Independent Yet Integrated** - Each node works standalone but plays well with others

---

## Who Should Use DazzleNodes?

### 🎨 Digital Artists
- Calculate perfect aspect ratios without math
- Preview resolution changes before generating
- Simplify inpainting workflows with automatic mask fitting
- Spend time creating, not configuring

### 🎮 Game Developers
- Generate consistent sprite dimensions
- Create texture sets with precise resolution control
- Batch produce assets with reliable sizing
- Integrate AI generation into asset pipelines

### 📸 Content Creators
- Match social media aspect ratios (1:1, 16:9, 9:16, etc.)
- Quickly test different resolutions
- Preview before generation saves compute time
- Streamline content production workflows

### 🔬 AI Researchers
- Systematic resolution testing for model evaluation
- Reproducible latent generation
- Debug dimension mismatches in complex workflows
- Document workflow configurations

---

## Featured Nodes

### 🌟 Smart Resolution Calculator

**[GitHub](https://github.com/djdarcy/ComfyUI-Smart-Resolution-Calc) | [ComfyUI Registry](https://registry.comfy.org/publishers/djdarcy/nodes/comfyui-smart-resolution-calc)**

Flexible resolution and latent generation with intelligent aspect ratio handling. Calculate missing dimensions, preview results, and generate latents - all in one node.

**Before DazzleNodes:**
```
Math node for width → Math node for height → Math node for aspect ratio
→ Empty Latent node → Hope you got the math right
```

**After DazzleNodes:**
```
Smart Resolution Calculator → Done
(Toggle to set width, height auto-calculates. See preview before generating.)
```

**Features**:
- **Toggle-based dimension control** - Enable width/height/ratio independently
- **Automatic calculation** - Set one dimension, others calculate automatically
- **Preview image generation** - See resolution before generating
- **Direct latent output** - Ready for KSampler
- **Custom widgets** - Enhanced UX with intuitive controls
- **Common presets** - Quick access to standard aspect ratios

**Use Cases**:
- **Social media content**: Set width to 1080px, toggle 16:9 ratio → instant Instagram dimensions
- **Print work**: Set height to 2400px for poster, width auto-calculates from ratio
- **Quick experimentation**: Try different aspect ratios without manual calculation
- **Batch generation**: Lock ratio, vary dimensions for different sizes
- **Resolution testing**: Systematically test model performance at different resolutions

**Status**: Published standalone in [ComfyUI Registry](https://registry.comfy.org/publishers/djdarcy/nodes/comfyui-smart-resolution-calc) and in [DazzleNodes package](https://registry.comfy.org/publishers/djdarcy/nodes/comfyui-dazzlenodes)

---

### 🎭 Fit Mask to Image

**[GitHub](https://github.com/DazzleNodes/fit-mask-to-image)**

Automatically resizes masks to match image dimensions for inpainting workflows. Solves the "mask dimensions don't match" error that breaks inpainting.

**Before DazzleNodes:**
```
[10-node workflow with ImageScale, MaskScale, ImagePadForOutpaint,
 MaskComposite, multiple coordinate calculations, and hope nothing breaks]
```
**See the old workflow**: [10-node Gist](https://gist.github.com/djdarcy/5796b7b2d705278aa4ad612248fd7c77)

**After DazzleNodes:**
```
Fit Mask to Image → Done
(Mask automatically matches image dimensions, ready for inpainting)
```

**Features**:
- **Automatic dimension matching** - Mask instantly resizes to image
- **Preview output** - Verify mask before inpainting
- **Latent masking support** - Works with both image and latent workflows
- **Nearest-exact scaling** - Quality preservation during resize
- **Zero configuration** - Just connect and go

**Use Cases**:
- **Inpainting workflows**: Generated image size changed? Mask auto-adjusts
- **Upscaling inpaints**: Upscale image, mask scales with it
- **Complex compositions**: Multiple generation steps with different resolutions
- **Iterative refinement**: Change image size mid-workflow, mask follows
- **Batch processing**: Different image sizes, masks always match

**Common Problem Solved**:
```
Error: "RuntimeError: The size of tensor a (512) must match
        the size of tensor b (1024) at non-singleton dimension 3"
```
This node eliminates this error by ensuring mask dimensions always match image dimensions.

**Status**: Available from [DazzleNodes package](https://registry.comfy.org/publishers/djdarcy/nodes/comfyui-dazzlenodes) in the ComfyUI Registry; download from [GitHub](https://github.com/DazzleNodes/fit-mask-to-image) to `ComfyUI\custom_nodes` for standalone install

---

## Installation

### Method 1: ComfyUI Manager (Recommended)

```
Search for "DazzleNodes" in ComfyUI Manager and click Install
```

All nodes install as a single package. Restart ComfyUI after installation.

### Method 2: ComfyUI Registry (CLI)

```bash
comfy node install comfyui-dazzlenodes
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

### Quick Start Examples

#### Example 1: Social Media Image Generation

```
Smart Resolution Calculator
├─ Toggle: Enable Width (1080)
├─ Toggle: Enable Aspect Ratio (1:1)
└─ Output: Latent (1080x1080) → KSampler
```

#### Example 2: Inpainting with Resolution Changes

```
Image (generated at 512x512)
↓
Upscale (to 1024x1024)
↓
Fit Mask to Image (mask from original 512x512)
↓
KSampler Inpainting (dimensions match perfectly)
```

#### Example 3: Aspect Ratio Experimentation

```
Smart Resolution Calculator
├─ Try 16:9 (landscape) → Generate
├─ Try 9:16 (portrait) → Generate
├─ Try 4:3 (classic) → Generate
└─ Preview before each generation
```

### Workflow Files

See `examples/` directory in the [DazzleNodes repository](https://github.com/DazzleNodes/DazzleNodes) for complete workflow JSON files demonstrating node usage.

---

## Architecture

DazzleNodes uses **git submodules** to maintain clean, independent histories for each node:

```
DazzleNodes/
├── __init__.py                    # Aggregator that imports all nodes
├── nodes/                         # Node submodules
│   ├── smart-resolution-calc/    # Submodule → separate git repo
│   └── fit-mask-to-image/        # Submodule → separate git repo
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

**Workflow Productivity**:
- **Smart Batch Processor** - Intelligent batch processing with automatic error recovery
- **Resolution Upscaler** - Multi-step upscaling with dimension tracking
- **Aspect Ratio Matcher** - Match aspect ratio of reference image

**Latent Operations**:
- **Latent Mixer** - Blend multiple latents with preview
- **Latent Tiler** - Generate tileable latents for seamless textures

**Mask Tools**:
- **Mask Featherer** - Adjustable feathering for smoother inpainting
- **Mask Combiner** - Combine multiple masks with operations (union, intersect, subtract)

**Utility Nodes**:
- **Dimension Inspector** - Debug dimension mismatches in workflows
- **Metadata Extractor** - Extract generation parameters from images

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

### Contributing to Existing Nodes

1. Fork the individual node repository
2. Create a feature branch
3. Test in ComfyUI with various workflows
4. Ensure backwards compatibility
5. Submit pull request to node repository

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

## 💰 Sustainability

**DazzleNodes** is part of the [DazzleProj](https://github.com/DazzleProj) ecosystem.

**Current sponsorship: $0/month | Goal: $1,000/month**

### Why Sponsor?

DazzleNodes development takes time:
- Researching common workflow pain points
- Developing robust solutions
- Testing across different workflows and models
- Maintaining compatibility with ComfyUI updates
- Supporting users and fixing issues

**If you use DazzleNodes regularly:**
- Time saved per workflow: ~5-10 minutes
- Workflows per week: ~20
- Time saved per month: **6-13 hours**
- Your time value: $50-100/hour
- Monthly value: **$300-1,300**

Contributing $10-25/month helps ensure continued development of workflow-improving nodes.

### How to Help

1. 💵 **[Sponsor on GitHub](https://github.com/sponsors/djdarcy)** - Direct support
2. ⭐ **Star node repositories** - Increases visibility
3. 💬 **Share workflows** - Help others discover useful patterns
4. 📝 **Write tutorials** - Blog about your favorite nodes
5. 🔧 **Contribute nodes** - Solve workflow problems for everyone

### Sponsor Benefits

- 🌟 **$5/month** - Supporter: Name in README
- 🌟🌟 **$25/month** - Contributor: Logo on DazzleProj.com
- 🌟🌟🌟 **$100/month** - Bronze Sponsor: Priority issue handling
- 🌟🌟🌟🌟 **$500/month** - Silver Sponsor: Influence node roadmap
- 🌟🌟🌟🌟🌟 **$2,000/month** - Gold Sponsor: Custom node development

---

## Related Projects

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

### Platform Support

| Node | ComfyUI Version | Python | Status |
|------|----------------|---------|--------|
| Smart Resolution Calculator | 0.1.0+ | 3.10+ | ✅ Published |
| Fit Mask to Image | 0.1.0+ | 3.10+ | ✅ Published |

### Dependencies

DazzleNodes has minimal dependencies:
- ComfyUI (obviously)
- Python 3.10+ (for ComfyUI compatibility)
- Standard ComfyUI node dependencies (torch, PIL, numpy)

Some nodes may use [DazzleLib](https://github.com/DazzleLib) libraries for file operations, but this is optional.

### Testing

Each node includes:
- Unit tests for core functionality
- Integration tests with ComfyUI
- Workflow JSON examples for manual testing

---

## Node Design Philosophy

### Problems DazzleNodes Solves

1. **Too Many Nodes for Simple Tasks**
   - Old way: 10 nodes to resize a mask
   - DazzleNodes: 1 node

2. **Math You Shouldn't Have To Do**
   - Old way: Calculate aspect ratios manually
   - DazzleNodes: Toggle aspect ratio, dimensions auto-calculate

3. **Dimension Mismatches Breaking Workflows**
   - Old way: Cryptic error messages, rebuild workflow
   - DazzleNodes: Automatic dimension matching

4. **No Visual Feedback Before Generation**
   - Old way: Generate and hope dimensions are right
   - DazzleNodes: Preview before committing compute

### What Makes a Good DazzleNode?

✅ **Solves a real workflow pain point**
✅ **Replaces multiple nodes with one**
✅ **Provides visual feedback where possible**
✅ **Has sensible defaults**
✅ **Works reliably across different workflows**

❌ **Doesn't solve an actual problem**
❌ **Just rearranges existing functionality**
❌ **Requires extensive configuration to use**
❌ **Only works in specific edge cases**

---

## Documentation

- **Installation Guide**: See above
- **Node Documentation**: See individual node repositories
- **Example Workflows**: `examples/` directory in main repo
- **Tutorials**: [DazzleProj.com](https://dazzleproj.com) *(coming soon)*
- **Video Guides**: Coming based on sponsorship support

---

## License

DazzleNodes uses **MIT License** for maximum compatibility with the ComfyUI ecosystem.

Individual nodes are MIT licensed unless otherwise specified. See individual node repositories for specific licensing information.

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

*Nodes that solve real problems, one workflow pain point at a time.*
