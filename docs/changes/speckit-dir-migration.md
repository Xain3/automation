# Migration to .speckit Directory

|  |  |
|-------|-------|
| Created on | 2025-09-09 |
| Modified on | 2025-09-09 |
| Commit range | [2bf5d50..1297c51](https://github.com/Xain3/automation/commit/2bf5d50..1297c51) |
| Author | Xain3 |
| Version | 1.0 |

## Migration Overview

This document details the migration of meta-development assets (templates, scripts, and governance documents) from scattered root directories to a unified `.speckit` namespace. The goal was to isolate tooling from implementation code, improve organization, and provide stable paths for automation.

### What Was Migrated

- **Templates**: `spec-template.md`, `plan-template.md`, `tasks-template.md`, `agent-file-template.md`
- **Scripts**: All shell scripts (`create-new-feature.sh`, `setup-plan.sh`, etc.)
- **Memory/Governance**: `constitution.md`, `constitution_update_checklist.md`

### Migration Timeline

- **Before**: Assets in root-level `scripts/`, `templates/`, `memory/` directories
- **After**: All assets consolidated under `.speckit/` subdirectory
- **Status**: Migration completed; old directories removed\
*Migration completed on 2025-09-09*

### Commit Reference

| Commit   | Description |
|----------|-------------|
| [`2bf5d508`](https://github.com/Xain3/automation/commit/2bf5d508afe361c56bcda8c80bb71a79f87a1da7) | Migrate memory files to `.speckit/memory/` directory |
| [`512e185c`](https://github.com/Xain3/automation/commit/512e185c1da718e2b5f21cea041f85192ba8fa7d) | Migrate template files to `.speckit/templates/` directory |
| [`a757ba4c`](https://github.com/Xain3/automation/commit/a757ba4c028cddbc98a4b175de5e499cbd977e99) | Migrate and add scripts to `.speckit/scripts/` directory |
| [`922496e0`](https://github.com/Xain3/automation/commit/922496e0901c365be16db0b745ad597dc80f2ec4) | Update script references to use `.speckit/` paths |
| [`1297c511`](https://github.com/Xain3/automation/commit/1297c5116cb550bc6c04a5f9662eaf94127f0fc2) | docs: Update file paths in prompts to use `.speckit/` directory |

## Before and After Structure

### Before Migration

``` text
repository-root/
├── scripts/
│   ├── create-new-feature.sh
│   ├── setup-plan.sh
│   ├── check-task-prerequisites.sh
│   └── update-agent-context.sh
├── templates/
│   ├── spec-template.md
│   ├── plan-template.md
│   ├── tasks-template.md
│   └── agent-file-template.md
├── memory/
│   ├── constitution.md
│   └── constitution_update_checklist.md
└── [other files]
```

### After Migration

``` text
repository-root/
├── .speckit/
│   ├── scripts/
│   │   ├── create-new-feature.sh
│   │   ├── setup-plan.sh
│   │   ├── check-task-prerequisites.sh
│   │   └── update-agent-context.sh
│   ├── templates/
│   │   ├── spec-template.md
│   │   ├── plan-template.md
│   │   ├── tasks-template.md
│   │   └── agent-file-template.md
│   └── memory/
│       ├── constitution.md
│       └── constitution_update_checklist.md
└── [other files]
```

## Updated References

All internal references have been updated to reflect new paths:

### Script References

- **Prompt Files** (`.github/prompts/*.prompt.md`):
  - `scripts/create-new-feature.sh` → `.speckit/scripts/create-new-feature.sh`
  - `scripts/setup-plan.sh` → `.speckit/scripts/setup-plan.sh`
  - `scripts/check-task-prerequisites.sh` → `.speckit/scripts/check-task-prerequisites.sh`
  - `scripts/update-agent-context.sh` → `.speckit/scripts/update-agent-context.sh`

### Template References

- **Scripts** (`.speckit/scripts/*.sh`):
  - `templates/spec-template.md` → `.speckit/templates/spec-template.md`
  - `templates/plan-template.md` → `.speckit/templates/plan-template.md`
  - `templates/agent-file-template.md` → `.speckit/templates/agent-file-template.md`

- **Templates** (`.speckit/templates/*.md`):
  - `/memory/constitution.md` → `/.speckit/memory/constitution.md`
  - `/templates/tasks-template.md` → `/.speckit/templates/tasks-template.md`
  - `/scripts/update-agent-context.sh` → `/.speckit/scripts/update-agent-context.sh`

### Constitution References

- **Checklist** (`.speckit/memory/constitution_update_checklist.md`):
  - `/templates/plan-template.md` → `/.speckit/templates/plan-template.md`
  - `/templates/spec-template.md` → `/.speckit/templates/spec-template.md`
  - `/templates/tasks-template.md` → `/.speckit/templates/tasks-template.md`
  - `/memory/constitution.md` → `/.speckit/memory/constitution.md`

## Key Files and Locations

### Core Governance

- `/.speckit/memory/constitution.md` – Constitutional rules enforced during planning
- `/.speckit/memory/constitution_update_checklist.md` – Update procedures for constitution changes

### Templates

- `/.speckit/templates/spec-template.md` – Feature specification scaffold
- `/.speckit/templates/plan-template.md` – Implementation planning flow
- `/.speckit/templates/tasks-template.md` – Task breakdown scaffold
- `/.speckit/templates/agent-file-template.md` – Agent context file template

### Scripts

- `/.speckit/scripts/create-new-feature.sh` – Feature branch and spec creation
- `/.speckit/scripts/setup-plan.sh` – Plan template setup
- `/.speckit/scripts/check-task-prerequisites.sh` – Task prerequisite validation
- `/.speckit/scripts/update-agent-context.sh` – Agent context file updates
- `/.speckit/scripts/get-feature-paths.sh` – Feature path utilities
- `/.speckit/scripts/common.sh` – Shared functions

## Script Invocation (Updated)

All scripts are now invoked from repository root using their new `.speckit` paths:

```bash
# Feature creation
.speckit/scripts/create-new-feature.sh --json "Add user onboarding"

# Plan setup
.speckit/scripts/setup-plan.sh --json

# Task prerequisites
.speckit/scripts/check-task-prerequisites.sh --json

# Agent context update
.speckit/scripts/update-agent-context.sh claude
```

## Generated Artifacts

Feature-specific artifacts continue to be written under `specs/<feature-branch>/`:

``` text
specs/
  001-sample-feature/
    spec.md
    plan.md
    research.md
    data-model.md
    quickstart.md
    contracts/
    tasks.md
```

## Rationale

- **Isolation**: Keeps meta-development tooling separate from production code
- **Organization**: Unified namespace prevents scattering across root
- **Reusability**: Easy to archive or copy `.speckit` to other repositories
- **Stability**: Provides consistent paths for automation prompts and scripts
- **Maintenance**: Simplifies updates and reduces path conflicts

## Migration Verification

### Files Moved

- ✅ All templates migrated to `.speckit/templates/`
- ✅ All scripts migrated to `.speckit/scripts/`
- ✅ All memory docs migrated to `.speckit/memory/`

### References Updated

- ✅ Prompt files (`.github/prompts/*.md`) updated
- ✅ Script internal references updated
- ✅ Template cross-references updated

### Cleanup

- ✅ Old `scripts/`, `templates/`, `memory/` directories removed
- ✅ No broken links or missing files

### Testing

- ✅ Scripts executable from new paths
- ✅ Templates loadable from new locations
- ✅ Constitution references resolved

## Migration Notes

- **External References**: Update any external documentation, scripts, or tools referencing the old paths
- **Git History**: Old directories were removed; use `git log --follow` if historical access needed
- **Backwards Compatibility**: None maintained; all references updated to new structure
- **Future Changes**: New assets should be added under appropriate `.speckit` subdirectories

If you encounter any issues with the migrated structure, check that all references have been updated as listed above.
