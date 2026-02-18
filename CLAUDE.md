# CLAUDE.md — learning-resources

**ORGAN II** (Art) · `organvm-ii-poiesis/learning-resources`
**Status:** ACTIVE · **Branch:** `main`

## What This Repo Is

Educational layer: workshop curricula, tiered learning paths, and creative coding tutorials for generative art and interactive performance

## Stack

**Languages:** Python
**Build:** Python (pip/setuptools)
**Testing:** pytest (likely)

## Directory Structure

```
📁 .github/
📁 docs/
    adr
📁 src/
    __init__.py
    curriculum.py
    exercises.py
    paths.py
📁 tests/
    __init__.py
    test_curriculum.py
    test_paths.py
  .gitignore
  CHANGELOG.md
  LICENSE
  README.md
  pyproject.toml
  seed.yaml
```

## Key Files

- `README.md` — Project documentation
- `pyproject.toml` — Python project config
- `seed.yaml` — ORGANVM orchestration metadata
- `src/` — Main source code
- `tests/` — Test suite

## Development

```bash
pip install -e .    # Install in development mode
pytest              # Run tests
```

## ORGANVM Context

This repository is part of the **ORGANVM** eight-organ creative-institutional system.
It belongs to **ORGAN II (Art)** under the `organvm-ii-poiesis` GitHub organization.

**Registry:** [`registry-v2.json`](https://github.com/meta-organvm/organvm-corpvs-testamentvm/blob/main/registry-v2.json)
**Corpus:** [`organvm-corpvs-testamentvm`](https://github.com/meta-organvm/organvm-corpvs-testamentvm)
