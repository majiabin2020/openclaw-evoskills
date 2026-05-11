# OpenClaw EvoSkills

A permanent meta-skill for routing, creating, auditing, and self-evolving skills through an iterative generator-verifier loop.

## Overview

OpenClaw EvoSkills is designed to be the always-on meta-skill in your OpenClaw workspace. It supervises other skills, automatically captures repeated workflows into new skills, and evolves existing skills through short, verifier-driven iterations instead of one-shot rewrites.

## Features

- **Skill Evolution**: Iteratively improve existing skills through baseline → patch → verify loops
- **Automatic Skill Capture**: Detect repeated workflows and automatically create reusable skills
- **Meta-Skill Architecture**: Acts as the highest-priority skill that routes and manages other skills
- **Surrogate Verification**: Static checks + forward testing with realistic prompts
- **Self-Healing**: Automatic repair of common skill issues (broken links, thin bodies, malformed frontmatter)

## Quick Start

### Installation

1. Clone this repository into your OpenClaw workspace:
   ```bash
   git clone https://github.com/majiabin2020/openclaw-evoskills.git
   ```

2. Activate as meta-skill:
   ```bash
   python scripts/activate_meta_skill.py --workspace <openclaw-workspace> --json
   ```

### Basic Usage

**Evolve an existing skill:**
```bash
python scripts/evolve_skill.py <target-skill-dir> --goal "desired improvement" --rounds 3 --json
```

**Create a new skill from repeated work:**
```bash
python scripts/scaffold_skill.py <skills-root> --goal "repeated workflow goal" --evidence "example 1" --evidence "example 2" --rounds 2 --json
```

**Auto-discover skill candidates:**
```bash
python scripts/observe_repetition.py --workspace <openclaw-workspace> --json
```

## Scripts

| Script | Description |
|--------|-------------|
| `activate_meta_skill.py` | Install and activate as workspace-level meta-skill |
| `evolve_skill.py` | Run full evolution loop (audit → repair → verify → report) |
| `scaffold_skill.py` | Create new skill from repeated workflow evidence |
| `observe_repetition.py` | Scan memory/session traces for skill candidates |
| `skill_audit.py` | Static structure and metadata validation |
| `repair_skill.py` | Auto-fix common skill issues |
| `surrogate_verify.py` | Generate and run prompt verification matrix |

## Evolution Workflow

1. **Baseline**: Read target skill, capture current state and failures
2. **Define Eval Set**: Create 3-7 realistic prompts covering trigger fit, core workflow, failure recovery
3. **Patch**: Fix highest-value bottleneck (structure → triggers → workflow → resources → verification)
4. **Verify**: Run static checks + forward testing on realistic prompts
5. **Upgrade Verifier**: If skill passes checks but fails real tasks, strengthen the evaluation matrix
6. **Repeat**: Continue until convergence or round cap

## Project Structure

```
openclaw-evoskills/
├── SKILL.md                 # Main skill definition
├── agents/
│   └── openai.yaml          # Agent interface configuration
├── references/
│   ├── evolution-loop.md    # Co-evolution loop documentation
│   ├── hermes-alignment.md  # Hermes-style skill patterns
│   └── meta-skill-policy.md # Meta-skill integration policy
└── scripts/
    ├── activate_meta_skill.py
    ├── evolve_skill.py
    ├── observe_repetition.py
    ├── repair_skill.py
    ├── scaffold_skill.py
    ├── skill_audit.py
    └── surrogate_verify.py
```

## Meta-Skill Contract

When installed as a meta-skill:

- Loads before other skill routing
- Decides whether to invoke, evolve, merge, split, or create task skills
- Automatically captures repeated workflows
- Maintains highest priority in workspace skill hierarchy

## Documentation

- [Evolution Loop](references/evolution-loop.md) - Core evolution methodology
- [Meta-Skill Policy](references/meta-skill-policy.md) - Integration with OpenClaw workspaces
- [Hermes Alignment](references/hermes-alignment.md) - Progressive disclosure patterns

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

- **majiabin2020** - [GitHub Profile](https://github.com/majiabin2020)

## Acknowledgments

- Built for the OpenClaw ecosystem
- Inspired by EvoSkills iterative improvement methodology
