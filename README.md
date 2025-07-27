# E7 AI Demoscene Challenge

> "Making obsolete hardware sing with 2025 AI techniques"

## About The Project

This repository contains the complete setup for the **E7 AI Demoscene Challenge**, a next-generation benchmark designed to test the limits of modern AI agents. Moving beyond simple code generation, this challenge evaluates an AI's ability to perform complex, multi-step reverse engineering, system design, and creative optimization.

The challenge centers on porting a modern operating system to the **2011 Nokia E7**, a device with severe hardware constraints. The AI agent's task is not just to make the hardware functional, but to create "demos"—software showcases that are elegant, hyper-efficient, and push the hardware beyond its original capabilities.

## The Demos (AI Software Showcases)

The AI will be tasked with creating three core software demonstrations:

🎨 **Visual Demo: Computational Photography Engine**
- Design novel algorithms to overcome the fixed-focus camera limitations
- Implement techniques like micro-diffusion, burst enhancement, depth effects
- Constraint: Real-time or near-real-time processing on 600MHz ARM11

💬 **Connectivity Demo: Ultra-Efficient LLM Client**
- Create custom tokenization, minimal UI, optimized protocols
- Enable modern AI chat functionality on 2011 hardware
- Constraint: Responsive performance within 256MB RAM limits

🎮 **System Demo: Procedural UX Engine**
- Generate UI elements at runtime vs storing static assets
- Implement modern interface paradigms on constrained hardware
- Constraint: Smooth performance with minimal memory footprint

## Repository Structure

```
e7-challenge/
├── LICENSE                      # MIT License for challenge framework
├── README.md                    # This file
├── challenge_prompt.md          # Main AI instructions
├── firmware/                    # Nokia E7 firmware files
│   ├── LICENSE.md              # Educational use license for firmware
│   ├── UNPACKING.md            # Firmware extraction instructions
│   ├── RM-626-firmware.7z.001 # Split archive part 1 (download from releases)
│   ├── RM-626-firmware.7z.002 # Split archive part 2 (download from releases)
│   ├── ...                     # Additional split archive parts
│   └── (extracted firmware files will appear here after unpacking)
├── documentation/               # Hardware documentation
│   ├── LICENSE.md              # Educational use license for documentation
│   ├── nokia_e7-00_rm-626_service_manual-12_v1.pdf
│   ├── nokia_e7-00_rm-626_service_manual-34_v1.pdf
│   ├── nokia_e7-00_rm-626_service_manual-12_v2.pdf
│   └── nokia_e7-00_rm-626_service_schematics_v1.pdf
├── validation/                  # Test procedures
│   └── test_procedures.md
└── artifacts/                   # AI-generated outputs
    └── (Generated code and documentation will appear here)
```

**Note:** Firmware files are distributed as split archives in GitHub releases due to size limitations. See `firmware/UNPACKING.md` for extraction instructions.

## Prerequisites

- **Git** for cloning the repository
- **7zip** for extracting firmware files (`p7zip-full` on Linux, download from 7-zip.org on Windows)
- **AI CLI tool** for your chosen platform (see options below)
- **Docker** (optional, for isolated build environments)
- **Disk space:** ~400MB for firmware extraction and challenge artifacts

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/e7-challenge.git
cd e7-challenge
```

### 2. Extract Firmware Files
The Nokia E7 firmware is distributed as compressed split archives due to GitHub size limits.

**Quick Setup:**
```bash
# Download firmware from releases page (split archive parts)
# Extract firmware files
7z x RM-626-firmware.7z.001

# Verify extraction
ls -la firmware/
```

**Detailed Instructions:** See [firmware/UNPACKING.md](firmware/UNPACKING.md) for complete setup instructions, troubleshooting, and alternative download methods.

### 3. Choose Your AI Agent

This challenge is designed to work with any capable AI agent. Select your preferred platform:

#### Option A: Google Gemini
```bash
# Install the CLI tool
npm install -g @google/gemini-cli

# Run the challenge
gemini run challenge_prompt.md \
    --context . \
    --mode=agentic \
    --throttle=on-approval \
    --output-dir ./artifacts
```

#### Option B: Anthropic Claude
```bash
# Using Claude Code (actual tool)
claude-code run challenge_prompt.md --context-dir .
```

#### Option C: OpenAI ChatGPT
```bash
# Install hypothetical CLI
pip install openai-cli-plus

# Run the challenge
openai-cli start-project \
    --prompt-file challenge_prompt.md \
    --context-dir . \
    --output ./artifacts \
    --interactive
```

#### Option D: Local Models (Ollama)
```bash
# Using local Qwen model
ollama run qwen2.5:72b --prompt-file challenge_prompt.md --context-dir .

# Using local DeepSeek model  
ollama run deepseek-coder:33b --prompt-file challenge_prompt.md --context-dir .
```

#### Option E: Other AI Platforms
```bash
# Hugging Face
transformers-cli chat --model deepseek-coder --file challenge_prompt.md

# Generic pattern for future tools
[ai-tool] run challenge_prompt.md --context . --mode agentic
```

### 3. Manual Mode (Any AI Chat Interface)

If your AI doesn't have a CLI tool:

1. Copy the contents of `challenge_prompt.md` 
2. Upload the firmware and documentation files
3. Paste the prompt into your AI chat
4. Use the AI's project/memory features to maintain context

## The Workflow

This is an **interactive, multi-stage process**:

1. **Phase 1: Firmware Analysis** - AI parses Nokia Belle firmware structure
2. **Phase 2: Hardware Mapping** - Extract register maps and driver details  
3. **Phase 3: QEMU Modeling** - Build emulation environment
4. **Phase 4: Linux Porting** - Create minimal OS port
5. **Phase 5: Demo Implementation** - Build the three showcase applications
6. **Phase 6: Hardware Validation** - Test on real Nokia E7 hardware

The AI should **throttle between phases**, presenting findings and waiting for approval before continuing.

## Expected AI Behavior

Regardless of platform, the AI agent should:

✅ **Analyze files systematically** (not all at once)  
✅ **Generate concrete, testable artifacts** at each stage  
✅ **Ask for approval** before major phase transitions  
✅ **Document all findings** before moving to implementation  
✅ **Create deliverable code** that can be validated  
✅ **Think like a demoscene coder** - optimize for elegance and efficiency  

## Success Metrics

- **Hardware register map** completed and documented
- **QEMU model** successfully boots original Nokia firmware  
- **Linux kernel** boots on emulated hardware
- **Demo applications** run with measurable performance improvements
- **Undocumented features** discovered and utilized
- **Token burn efficiency** tracked and optimized

## Hardware Availability

**Nokia E7 devices are still obtainable for testing:**
- **Current availability:** ~80 units globally available on secondary markets
- **Price range:** €60-100+ depending on condition and seller location
- **Primary source:** eBay and other electronics marketplaces
- **Search link:** [Nokia E7 on eBay](https://www.ebay.com/sch/i.html?_nkw=nokia+e7&_sacat=0&_from=R40&_trksid=m570.l1313)
- **Collector premium:** Mint condition units command higher prices

**Note:** While hardware is available, this challenge is designed to work primarily through emulation. Physical hardware testing is optional but provides the ultimate validation experience.

## Legal & Ethical Notes

### Firmware and Documentation Usage
- **Abandoned Hardware:** Nokia mobile division discontinued 2014, no active support
- **Educational Purpose:** Firmware analysis for research and open source development only
- **Fair Use:** Technical analysis of owned hardware under right-to-repair principles
- **Preservation:** Historical documentation of important mobile technology development

### Project Licensing
- **Generated Code:** All AI-generated code released under MIT License
- **Firmware Files:** Educational use only, see `firmware/LICENSE.md` for details
- **Service Documentation:** Research use only, see `documentation/LICENSE.md` for details
- **No Commercial Interest:** Purely educational and open source advancement

### Responsible Use
- Respect intellectual property rights while advancing technical education
- Acknowledge Nokia's original engineering contributions
- Focus on interoperability and educational value
- Contribute findings back to open source community

## Contributing

This benchmark is designed to evolve with AI capabilities:

- Submit improvements to challenge methodology
- Add support for new AI platforms  
- Document new optimization techniques discovered
- Share validation results and token burn metrics

## Time to burn some tokens! 🔥

Ready to see what your AI can do with obsolete hardware? Start the challenge and let's push the boundaries of what's possible with creative engineering.

---

*"In the demoscene, constraints breed creativity. In AI development, the Nokia E7 is our Commodore 64."*
