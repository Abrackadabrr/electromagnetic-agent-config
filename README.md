# electromagnetic-agent-config

Shared Codex skills for scientific software development in computational electromagnetics, with emphasis on surface integral equations (SIE), volume integral equations (VIE), coupled surface-volume formulations (VSIE), operator discretization, and regular-grid / FFT-accelerated VIE.

The canonical electromagnetic convention used by these skills is `exp(-i*omega*t)`, with outgoing Green function `G = exp(+ikR)/(4*pi*R)`. The project notation treats `K_project = k^2 L_Gibson` and `R_project = K_Gibson` after full convention translation.

## Repository layout

This repository is intentionally laid out so that the repository root can be mounted directly at a Codex repository skill directory:

```text
electromagnetic-agent-config/
├── electromagnetics-notation/
│   ├── SKILL.md
│   └── references/
├── surface-integral-equations/
│   ├── SKILL.md
│   └── references/
├── volume-integral-equations/
│   ├── SKILL.md
│   └── references/
├── operator-discretization/
│   ├── SKILL.md
│   └── references/
├── uniform-grid-vie/
│   ├── SKILL.md
│   └── references/
└── SOURCES.md
```

There is deliberately no shared project `AGENTS.md` here. Repository-specific operating rules belong in the root `AGENTS.md` of each consuming project.

## Recommended installation as a Git submodule

From the root of a Codex-enabled project:

```bash
mkdir -p .agents
git submodule add https://github.com/Abrackadabrr/electromagnetic-agent-config.git .agents/skills
git submodule update --init --recursive
```

This yields:

```text
project/
├── AGENTS.md
└── .agents/
    └── skills/   # this repository as a submodule
```

Codex discovers repository skills under `$REPO_ROOT/.agents/skills`. Each skill has its own `SKILL.md` with `name` and `description` metadata; references are loaded only when needed.

## Update workflow

After updating this repository:

```bash
cd .agents/skills
git pull
cd ../..
git add .agents/skills
git commit -m "Update electromagnetic Codex skills"
```

The parent project therefore pins a concrete revision of the shared scientific configuration.

## Scope

The current skill set covers:

- electromagnetic sign and notation conventions;
- PEC and dielectric SIE formulations;
- PWC/collocation and RWG/Galerkin surface discretization branches;
- E-VIE / J-VIE / D-VIE formulation distinctions;
- coupled SIE-VIE / VSIE block formulations;
- singular and near-singular operator discretization;
- voxel Galerkin discretization on uniform Cartesian grids;
- block-Toeplitz structure and FFT acceleration;
- mapping to the current EMW C++ code architecture.

FEM / FE-BI is intentionally outside the current configuration.
